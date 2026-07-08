---
name: ghl-publicar
description: >
  Skill para publicar o programar un video en redes sociales desde GoHighLevel.
  Activar cuando alguien diga: "publicar video en GHL", "subir reel a GHL",
  "programar post en GHL", "quiero publicar en redes desde GHL", "sube este
  video a Instagram desde GHL", "programa este reel", o cualquier variación
  que combine publicar/programar contenido en canales sociales usando GHL.
argument-hint: "[URL del video — opcional, se pide en el flujo]"
metadata:
  version: "2.0.0"
  depends-on: []
  mcp-required: ["HighLevel"]
  external-deps:
    - "MCP de HighLevel/LeadConnector conectado al endpoint v2: https://services.leadconnectorhq.com/mcp/anthropic/v2 (en Claude.ai vía Settings > Connectors > Add custom connector con OAuth; en Claude Code CLI vía mcp-remote con Private Integration Token + locationId)"
---

# ghl-publicar — Publicar o Programar Video en Redes desde GHL

Recopila los datos del video, verifica que los canales estén conectados en GHL y publica o programa el post.

---

## CÓMO FUNCIONA EL MCP v2 DE GHL (leer antes de cualquier llamada)

El MCP de HighLevel (endpoint `https://services.leadconnectorhq.com/mcp/anthropic/v2`) NO expone tools fijos por función. Expone 5 meta-tools que dan acceso a toda la API pública de GHL:

- `search_operations` — buscar una operación por descripción (ej: "create social media post")
- `describe_operation` — ver parámetros y campos del body de una operación
- `execute_operation` — ejecutar la operación
- `search` / `fetch` — buscar registros del CRM (no se usan en este skill)

Reglas de `execute_operation`:
1. Las operaciones de **escritura** (create-post, bulk-delete) exigen `idempotencyKey` (cualquier UUID nuevo por llamada). Sin él → error 400.
2. Las de **lectura** (get-account) no lo necesitan.
3. Soporta `dryRun: true` para previsualizar la request sin ejecutarla.
4. El body va en `params.body`, los path params en `params.path`, query en `params.query`. El `locationId` lo inyecta el MCP desde el header — no hace falta pasarlo.

**Fallback sin MCP:** si el MCP no está cargado en la sesión, el mismo endpoint acepta curl directo (JSON-RPC + SSE) con headers `Authorization: Bearer {token}`, `locationId: {id}`, `Accept: application/json, text/event-stream`. También sigue funcionando el REST clásico (`POST /social-media-posting/{locationId}/posts` con header `Version: 2021-07-28`).

---

## PRE-VUELO — Verificar conexión con GHL

```
mcp__HighLevel__execute_operation({
  "operationId": "get-account",
  "params": {"path": {}, "query": {}}
})
```

Devuelve la lista de cuentas sociales conectadas en `data.results.accounts` (cada una con `platform`, `name` e `id` — **guardar los `id`, son los `accountIds` para publicar**).

Si la herramienta no responde o devuelve error de autenticación, mostrar:

> "Para usar este skill necesitas conectar el MCP de GoHighLevel.
>
> **Pasos:**
> 1. Abre Claude.ai → **Settings** → **Connectors** → **Add custom connector**
> 2. Pon como server URL: `https://services.leadconnectorhq.com/mcp/anthropic/v2`
> 3. Haz clic en **Connect** y completa el sign-in de LeadConnector (iniciar sesión → elegir tu location/sub-cuenta → aprobar)
> 4. Abre un chat nuevo — las herramientas de LeadConnector ya estarán disponibles
> 5. Ejecuta este skill de nuevo"

*(Alternativa para Claude Code CLI: agregar el MCP en `mcp.json` vía `mcp-remote` con la misma URL y headers `Authorization: Bearer {Private Integration Token}` + `locationId: {LOCATION_ID}`.)*

Detener aquí hasta que el usuario confirme que el MCP está conectado.

---

## PASO 1 — Recolectar información del post

Hacer todas las preguntas en un solo mensaje:

> "Vamos a publicar tu video en GHL. Necesito estos datos:
>
> **1. URL del video** *(obligatorio)*
> Debe ser una URL pública y accesible directamente (no un Drive privado, no Dropbox con restricción).
>
> **2. Portada/thumbnail** *(opcional)*
> ¿Tienes imagen de portada? Pega la URL. Si no, GHL usará el fotograma del video por defecto.
>
> **3. Caption** *(obligatorio)*
> El texto que acompañará el video.
>
> **4. Canales donde publicar** *(elige uno o varios)*
> - Instagram
> - Facebook
> - TikTok
> - LinkedIn
> - Twitter/X
> - YouTube
>
> **5. Fecha y hora**
> - Escríbela directamente: *"mañana a las 7pm"*, *"25 de junio a las 12pm"*
> - O escribe **"ahora mismo"** para publicar en este momento
> - O escribe **"no sé"** y te doy recomendaciones por canal"

Esperar respuesta completa antes de continuar.

### Si dice "no sé" en fecha/hora

Mostrar solo los canales que seleccionó:

| Canal | Mejores días | Mejores horas (hora local) |
|-------|-------------|---------------------------|
| Instagram | Mar, Mié, Jue | 11am–1pm · 7pm–9pm |
| Facebook | Mié, Jue, Vie | 1pm–3pm · 7pm–9pm |
| TikTok | Mar a Jue | 7am–9am · 7pm–11pm |
| LinkedIn | Mar a Jue | 8am–10am · 5pm–6pm |
| Twitter/X | Lun a Vie | 9am–11am · 6pm–8pm |
| YouTube | Vie, Sáb, Dom | 3pm–6pm |

Proponer 2 opciones concretas de fecha/hora y preguntar cuál prefieren antes de continuar.

---

## PASO 2 — Verificar canales conectados en GHL

Usar la respuesta del `get-account` del pre-vuelo (o volver a ejecutarlo si pasó tiempo).

Comparar la respuesta con los canales que el usuario seleccionó.

**Si todos están conectados:** continuar al PASO 3.

**Si algún canal no está conectado**, mostrar instrucciones específicas. La ruta para conectar cualquier red social en GHL es siempre la misma:

> **Cómo conectar una red social en GHL:**
> 1. Ve a **Marketing** en el menú lateral
> 2. Entra a **Planificador de Redes Sociales**
> 3. Haz clic en el botón **"+ Redes Sociales"** (esquina superior derecha)
> 4. Selecciona la red social que quieres conectar
> 5. Inicia sesión con tu cuenta
> 6. Autoriza los permisos que solicita GHL
> 7. Avísame cuando quede conectada

Personalizar el mensaje según el canal que falta:

### Instagram no conectado:
> "Tu cuenta de Instagram no está conectada en GHL.
>
> Ve a **Marketing → Planificador de Redes Sociales → + Redes Sociales**, selecciona Instagram e inicia sesión con tu cuenta Instagram Business.
>
> *Importante: tu Instagram debe ser una cuenta Business o Creator vinculada a una Facebook Page. Si es cuenta personal, primero conviértela desde la app de Instagram (Configuración → Cuenta → Cambiar a cuenta profesional).*
>
> Avísame cuando quede conectada y verifico."

### Facebook no conectado:
> "Tu página de Facebook no está conectada en GHL.
>
> Ve a **Marketing → Planificador de Redes Sociales → + Redes Sociales**, selecciona Facebook e inicia sesión. Cuando te lo pida, asegúrate de seleccionar la **Página** (no tu perfil personal).
>
> Avísame cuando quede conectada y verifico."

### TikTok no conectado:
> "Tu cuenta de TikTok no está conectada en GHL.
>
> Ve a **Marketing → Planificador de Redes Sociales → + Redes Sociales**, selecciona TikTok e inicia sesión con tu cuenta TikTok Business o Creator.
>
> Avísame cuando quede conectada y verifico."

### LinkedIn no conectado:
> "Tu cuenta de LinkedIn no está conectada en GHL.
>
> Ve a **Marketing → Planificador de Redes Sociales → + Redes Sociales**, selecciona LinkedIn e inicia sesión. Podrás elegir entre tu perfil personal o una página de empresa.
>
> Avísame cuando quede conectada y verifico."

### Twitter/X no conectado:
> "Tu cuenta de Twitter/X no está conectada en GHL.
>
> Ve a **Marketing → Planificador de Redes Sociales → + Redes Sociales**, selecciona Twitter/X e inicia sesión con tu cuenta.
>
> Avísame cuando quede conectada y verifico."

### YouTube no conectado:
> "Tu canal de YouTube no está conectado en GHL.
>
> Ve a **Marketing → Planificador de Redes Sociales → + Redes Sociales**, selecciona YouTube e inicia sesión con la cuenta de Google asociada a tu canal.
>
> Avísame cuando quede conectada y verifico."

Después de que el usuario confirme, volver a ejecutar `execute_operation` con `get-account` para verificar. Repetir el ciclo hasta que todos los canales seleccionados estén conectados. No avanzar si alguno sigue pendiente.

---

## PASO 3 — Confirmación antes de publicar

Mostrar resumen:

```
📤 LISTO PARA PUBLICAR
─────────────────────────────────────────────
Video:    [URL del video]
Portada:  [URL / "por defecto (GHL)"]
Caption:  [primeros 120 caracteres]...
Canales:  [lista de canales]
Cuándo:   [fecha y hora local / "Ahora mismo"]
─────────────────────────────────────────────
¿Publicamos? (sí / cancela)
```

NUNCA ejecutar la publicación sin un "sí", "dale", "publica" o confirmación explícita.

---

## PASO 4 — Publicar

Se publica con `execute_operation` → operationId `create-post`. Un post por llamada (si son varios canales, GHL acepta varios `accountIds` en el mismo post; si son varios videos, una llamada por video).

El payload base de abajo funciona **para todas las redes** (Instagram, Facebook, LinkedIn, Twitter/X, YouTube, Google Business, TikTok) — la única diferencia por red es el bloque extra de TikTok indicado más abajo. No agregar bloques extra para las demás redes.

```
mcp__HighLevel__execute_operation({
  "operationId": "create-post",
  "idempotencyKey": "{UUID nuevo por cada llamada}",
  "params": {
    "path": {},
    "query": {},
    "body": {
      "accountIds": ["{id de cuenta del get-account}", ...],
      "type": "post",
      "userId": "{userId de GHL}",
      "status": "published",              // "published" = ahora mismo | "scheduled" = programado
      "scheduleDate": "2026-07-25T19:00:00.000Z",  // solo si status=scheduled (SIEMPRE en UTC)
      "scheduleTimeUpdated": true,        // solo si status=scheduled
      "summary": "CAPTION completo con hashtags",
      "media": [{
        "url": "URL_VIDEO",
        "type": "video/mp4",              // usar "type", NO "mimeType"
        "thumbnail": "URL_PORTADA o \"\"",
        "defaultThumb": "URL_PORTADA o \"\""
      }]
    }
  }
})
```

### Si algún canal es TikTok — OBLIGATORIO agregar al body:
```
"tiktokPostDetails": {
  "privacyLevel": "PUBLIC_TO_EVERYONE",
  "promoteOtherBrand": false,
  "enableComment": true,
  "enableDuet": false,
  "enableStitch": false,
  "videoDisclosure": false,
  "promoteYourBrand": false
}
```
Sin este bloque, GHL devuelve 400 (`toLowerCase on undefined`) para cualquier status distinto de draft. Usar los campos `enable*` (no `disable*`).

**Notas:**
- `userId` es **obligatorio** para posts no-draft en canales OAuth. Es el ID del usuario de GHL que "crea" el post — se obtiene una vez (aparece en `createdBy` de cualquier post existente, o vía la operación de users) y se reutiliza.
- `idempotencyKey`: generar un UUID distinto por cada post. Sin él la operación falla con 400.
- Dejar `thumbnail` y `defaultThumb` como `""` si el usuario no dio portada.
- Convertir siempre la hora del usuario a UTC antes de enviar (preguntar zona horaria si no está clara). CDMX = UTC-6 fijo (México eliminó el DST en 2023).
- Ante duda con el payload, ejecutar primero con `dryRun: true` y revisar el `resolvedRequest`.
- El Post ID viene en `data.results.post._id`.

---

## PASO 5 — Reportar resultado

### Si éxito:
```
✅ VIDEO PUBLICADO EN GHL
─────────────────────────────────────────────
Canales:  [lista]
Estado:   [Publicado ahora / Programado para FECHA HORA]
Post ID:  [ID devuelto por GHL]
─────────────────────────────────────────────
```

Guardar el Post ID en la sesión — se necesita si el usuario quiere crear la automatización de comentarios.

### Si falla:
Mostrar el error exacto sin modificarlo. Errores comunes:

| Error | Causa y solución |
|-------|-----------------|
| `requires idempotencyKey` | Falta el `idempotencyKey` en los arguments. Generar un UUID y reintentar. |
| `toLowerCase on undefined` (400) | Post de TikTok sin `tiktokPostDetails`. Agregar el bloque completo. |
| `Media URL not accessible` | La URL del video no es pública. Pedir otra URL. |
| `Account not authorized` | La conexión no tiene scope de Social Media Posting. Reconectar/regenerar con ese scope. |
| `Platform not connected` | Volver al PASO 2 con el canal afectado. |
| `Scheduled time in the past` | La hora programada ya pasó. Pedir nueva fecha/hora. |

Para borrar un post creado por error: `execute_operation` con operationId `bulk-delete-social-planner-posts`, `idempotencyKey` nuevo, y `body: {"postIds": ["{postId}"]}`.

No reintentar automáticamente. Reportar y esperar instrucciones.

---

## PASO 6 — Ofrecer crear automatización de comentarios

Una vez publicado con éxito:

> "**¿Quieres crear la automatización de respuesta a comentarios para este video?**
>
> Con `/lf:ghl-automatizar-comentarios-chrome` configuro que cuando alguien comente una palabra clave en el reel:
> - GHL responde automáticamente en el comentario
> - Le envía un DM con tu mensaje
> - Lo etiqueta en tu CRM
>
> (sí, arrancamos / no por ahora)"

Si dice sí → lanzar el skill `ghl-automatizar-comentarios-chrome` pasando el Post ID guardado.
Si dice no → terminar aquí.

---

## REGLAS

1. Confirmación explícita antes de publicar. Siempre.
2. No avanzar si hay canales seleccionados sin conectar.
3. Siempre convertir hora local → UTC antes de la llamada a la API.
4. Guardar el Post ID en sesión para la automatización.
5. No reintentar publicaciones fallidas automáticamente.
