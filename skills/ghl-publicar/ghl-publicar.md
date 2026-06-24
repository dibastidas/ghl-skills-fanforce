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
  version: "1.0.0"
  depends-on: []
  mcp-required: ["HighLevel"]
  external-deps:
    - "GHL Private Integration Token (Settings > Private Integrations)"
    - "MCP de HighLevel conectado como 'HighLevel' con el token de la sub-cuenta"
---

# ghl-publicar — Publicar o Programar Video en Redes desde GHL

Recopila los datos del video, verifica que los canales estén conectados en GHL y publica o programa el post.

---

## PRE-VUELO — Verificar conexión con GHL

```
mcp__HighLevel__social-media-posting_get-account()
```

Si la herramienta no responde o devuelve error de autenticación, mostrar:

> "Para usar este skill necesitas conectar el MCP de GoHighLevel.
>
> **Pasos:**
> 1. Entra a tu sub-cuenta GHL → Settings → Private Integrations
> 2. Crea una nueva integración con el scope: **Social Media Posting**
> 3. Copia el Private Integration Token generado
> 4. En Claude, agrega el MCP con estos datos:
>    - **Nombre:** HighLevel
>    - **URL:** `https://services.leadconnectorhq.com/mcp/`
>    - **Header:** `Authorization: Bearer TU_TOKEN`
>    - **Header:** `locationId: TU_LOCATION_ID`
>       *(el Location ID aparece en la URL de GHL cuando estás en tu sub-cuenta)*
> 5. Una vez conectado, ejecuta este skill de nuevo"

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

Ejecutar:
```
mcp__HighLevel__social-media-posting_get-account()
```

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

Después de que el usuario confirme, volver a ejecutar `social-media-posting_get-account()` para verificar. Repetir el ciclo hasta que todos los canales seleccionados estén conectados. No avanzar si alguno sigue pendiente.

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

### Si es "ahora mismo":
```
mcp__HighLevel__social-media-posting_create-post({
  "platforms": ["instagram", "facebook", ...],
  "content": "CAPTION",
  "mediaUrls": ["URL_VIDEO"],
  "thumbnailUrl": "URL_PORTADA",
  "publishNow": true
})
```

### Si es programado:
```
mcp__HighLevel__social-media-posting_create-post({
  "platforms": ["instagram", "facebook", ...],
  "content": "CAPTION",
  "mediaUrls": ["URL_VIDEO"],
  "thumbnailUrl": "URL_PORTADA",
  "scheduledAt": "2024-06-25T19:00:00Z"
})
```

**Notas:**
- Omitir `thumbnailUrl` si el usuario no proporcionó portada
- Convertir siempre la hora del usuario a UTC antes de enviar (preguntar zona horaria si no está clara)
- Nombres de plataforma en minúsculas: `instagram`, `facebook`, `tiktok`, `linkedin`, `twitter`, `youtube`

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
| `Media URL not accessible` | La URL del video no es pública. Pedir otra URL. |
| `Account not authorized` | El token no tiene scope de Social Media Posting. Regenerar con ese scope. |
| `Platform not connected` | Volver al PASO 2 con el canal afectado. |
| `Scheduled time in the past` | La hora programada ya pasó. Pedir nueva fecha/hora. |

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
