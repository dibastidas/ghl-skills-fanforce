---
name: ghl-automatizar-comentarios
description: >
  Skill para crear una automatización de respuesta a comentarios en Instagram
  y/o Facebook desde GoHighLevel. Activar cuando alguien diga: "crear automatización
  de comentarios", "auto-responder comentarios", "autoresponder de comentarios GHL",
  "cuando comenten esta palabra quiero que les llegue un DM", "configurar respuesta
  automática a comentarios", o cualquier variación que combine automatizar respuestas
  a comentarios en redes sociales. Solo funciona para Instagram y Facebook.
argument-hint: "[Post ID del reel — opcional, se puede ingresar en el flujo]"
metadata:
  version: "1.0.0"
  depends-on: []
  mcp-required: ["HighLevel", "playwright"]
  external-deps:
    - "GHL Private Integration Token con scope Workflows"
    - "MCP de HighLevel conectado como 'HighLevel'"
    - "Playwright MCP conectado para navegar la UI de GHL"
    - "Instagram for Business y/o Facebook Page conectados en GHL (Configuración → Integraciones)"
---

# ghl-automatizar-comentarios — Automatización de Respuesta a Comentarios en GHL

Verifica prerrequisitos, recopila la configuración y crea el workflow en GHL para que cuando alguien comente una palabra clave en un reel, GHL responda automáticamente en el comentario y envíe un DM.

**Solo disponible para Instagram y Facebook.** TikTok, LinkedIn, Twitter/X y YouTube no tienen esta funcionalidad en GHL.

---

## PASO 1 — Verificar prerrequisitos

Mostrar al usuario lo que necesita antes de continuar:

> "Antes de crear la automatización, verifica que tienes todo listo:
>
> **Checklist:**
> - [ ] **Instagram for Business conectado** en GHL (Configuración → Integraciones)
> - [ ] **Facebook Page conectada** en GHL (Configuración → Integraciones)
> - [ ] **El reel ya está publicado** — si está programado, la automatización se activa cuando se publique
> - [ ] **Plan GHL que incluye Workflows/Automatizaciones** (Unlimited o SaaS Pro)
>
> ¿Tienes todo listo? (sí / tengo dudas)"

Si tiene dudas → explicar el ítem específico y esperar antes de continuar.

### Si Instagram o Facebook no están conectados para el autoresponder:

La conexión para la automatización de comentarios se hace desde **Configuración → Integraciones**, no desde el Planificador de Redes Sociales.

> "Para conectar Instagram o Facebook para el autoresponder de comentarios:
> 1. Ve a **Configuración** en el menú lateral de GHL
> 2. Entra a **Integraciones**
> 3. Busca Instagram o Facebook en la lista
> 4. Haz clic en **Conectar** y sigue el proceso de autorización
> 5. Avísame cuando quede conectada y verifico"

*Nota: aunque ya tengas las redes conectadas en el Planificador de Redes Sociales para publicar, la integración para el autoresponder de comentarios es independiente y debe hacerse desde Configuración → Integraciones.*

---

## PASO 2 — Definir canales de la automatización

> "¿Para qué canales quieres crear la automatización de comentarios?
> - Instagram
> - Facebook
> - Ambos"

Si el usuario menciona TikTok, LinkedIn, Twitter/X u otra red:
> "La automatización de comentarios para [red social] no está disponible en GHL por ahora. Puedo crearla solo para Instagram y/o Facebook. ¿Cuál de estos dos quieres usar?"

---

## PASO 3 — Recolectar configuración en un solo mensaje

> "Perfecto. Necesito estos datos para configurar la automatización:
>
> **1. ¿Cuál es el reel o post?**
> - Si acabas de publicarlo con `/lf:ghl-publicar`, tengo el ID. Solo confírmame que es el mismo.
> - Si no, dime el nombre o fecha del post para buscarlo en GHL.
>
> **2. Palabra o frase del comentario** *(el disparador)*
> ¿Qué debe escribir alguien en los comentarios para activar la respuesta automática?
> Ejemplo: INFO, PRECIO, QUIERO, LINK, ACCEDER, etc.
>
> **3. Primer mensaje del DM** *(lo que les llega por privado)*
> Escríbelo tal como quieres que llegue. Puede incluir emojis y saltos de línea.
>
> **4. ¿Incluyes un enlace?**
> ¿Quieres agregar un botón con un enlace en el DM?
> - Sí → pega la URL
> - No → el DM irá sin botón"

Esperar respuesta completa antes de continuar.

---

## PASO 4 — Generar variaciones de la palabra clave

Con la palabra que dio el usuario, generar todas las variaciones posibles que alguien puede escribir en los comentarios. Cubrir:
- Mayúsculas, minúsculas y mixtas
- Con y sin tildes/acentos
- Versiones cortas y frases comunes con esa palabra
- Errores de tipeo frecuentes si aplica

Ejemplo con "INFO":
`INFO`, `info`, `Info`, `información`, `Información`, `informacion`, `Informacion`, `quiero info`, `dame info`, `más info`, `mas info`, `necesito info`, `pásame info`, `pasame info`, `quiero información`, `dame información`, `necesito información`, `info porfavor`, `info por favor`, `info!`, `info?`

Mostrar al usuario:

> "Usaré estas variaciones para capturar todas las formas en que alguien puede escribir la palabra:
> [lista de variaciones]
>
> ¿Quieres agregar alguna variación adicional? (escríbelas o di 'está bien así')"

Esperar respuesta antes de continuar.

---

## PASO 5 — Generar 10 variaciones de respuesta al comentario

Crear 10 formas diferentes y naturales de decirle al usuario que revise su DM. Variar tono, longitud y emojis. Adaptar al tono del negocio si se conoce por el contexto de la sesión.

Ejemplos base (adaptar según contexto):
1. "¡Hola! Te acabo de escribir por privado, revisa tu DM 📩"
2. "Te mandé la información por mensaje directo, échale un vistazo 👀"
3. "Listo, revisa tus mensajes privados, ya te escribí 🙌"
4. "¡Ya te escribí! Entra a tu DM para ver la info completa"
5. "Revisa tu inbox, ahí está todo lo que necesitas saber 📬"
6. "Te envié los detalles por privado, no te los pierdas 🔔"
7. "¡Perfecto! La información está en tu DM esperándote"
8. "Ya te mandé todo por mensaje privado, revísalo cuando puedas"
9. "Entra a tus mensajes directos, te compartí la info ahí 💌"
10. "Listo, chequea tus DMs, ya está todo ahí para ti ✅"

Mostrar al usuario:
> "Estas son las 10 respuestas que rotarán en los comentarios. ¿Las apruebas o quieres ajustar alguna?"

Esperar aprobación antes de continuar.

---

## PASO 6 — Confirmación final

Mostrar resumen completo:

```
🤖 CONFIGURACIÓN DE LA AUTOMATIZACIÓN
─────────────────────────────────────────────────────
Post:       [nombre o ID del reel]
Canales:    [Instagram / Facebook / Ambos]

Disparador: Comentario que contenga "[PALABRA_CLAVE]"
            ([N] variaciones configuradas)

Flujo automático:
  1. Etiqueta al contacto: instagram-comment / fb-comment
  2. Responde en el comentario (10 variaciones rotativas)
  3. Envía DM: "[primeros 60 chars del mensaje]..."
     [+ botón "[texto]" → URL   /   sin botón]
     [si hace clic en el botón → etiqueta: ig-click-boton / fb-click-boton]
─────────────────────────────────────────────────────
¿Creo la automatización? (sí / cancela)
```

NUNCA crear el workflow sin confirmación explícita.

---

## PASO 7 — Crear la automatización en GHL via Playwright

### Inicializar

```
mcp__plugin_formula100k_playwright__browser_take_screenshot()
```

Verificar si GHL ya está abierto y el usuario está logueado. Si no:

> "Para crear la automatización necesito que estés logueado en GHL en el browser.
> 1. Abre https://app.gohighlevel.com en tu navegador
> 2. Entra a tu sub-cuenta
> 3. Avísame cuando estés dentro"

Esperar confirmación y volver a tomar screenshot.

### Navegar a Automations

```
mcp__plugin_formula100k_playwright__browser_navigate({
  "url": "https://app.gohighlevel.com/v2/location/LOCATION_ID/automation/list"
})
```

Si no se conoce el LOCATION_ID pedirlo al usuario — aparece en la URL de GHL cuando está en su sub-cuenta.

Verificar con screenshot que la pantalla de Automatizaciones cargó correctamente.

---

### WORKFLOW DE INSTAGRAM (si aplica)

**1. Crear nuevo workflow**
- Clic en "Create Workflow" o "+ New Workflow"
- Seleccionar "Start from Scratch"
- Nombre: `Auto-Comentario [PALABRA_CLAVE] - IG - [fecha de hoy]`

**2. Agregar Trigger: Instagram Comment**
- Clic en "Add Trigger"
- Buscar y seleccionar **"Instagram Comment"**
- Connected Page: seleccionar la cuenta de Instagram conectada
- Post Type: **"Published Post"**
- Post: buscar y seleccionar el reel (por nombre o fecha)
- Keywords: agregar todas las variaciones generadas en PASO 4
- Guardar trigger

**3. Acción 1 — Agregar etiqueta**
- Clic en "+" para agregar acción
- Seleccionar **"Add Contact Tag"**
- Tag: `instagram-comment`
- Guardar

**4. Acción 2 — Responder en el comentario**
- Clic en "+" para agregar acción
- Seleccionar **"Respond on Comment"** o **"Reply to Comment"**
- Agregar las 10 variaciones de respuesta del PASO 5
- Activar rotación aleatoria si está disponible
- Guardar

**5. Acción 3 — Enviar DM por Instagram**
- Clic en "+" para agregar acción
- Seleccionar **"Instagram Interactive Messenger"** o **"Send Instagram DM"**
- Escribir el mensaje configurado en PASO 3

- **Si el usuario proporcionó un enlace:**
  - Agregar botón con texto descriptivo (ej: "Ver aquí", "Acceder ahora", "Ir al link")
  - URL del botón: el enlace proporcionado
  - En la rama "Botón clickeado" agregar:
    - **"Add Contact Tag"** → tag: `ig-click-boton`
- **Si no hay enlace:** guardar sin botón

**6. Activar el workflow**
- Clic en "Save"
- Clic en "Publish" o activar el toggle → estado **Active**
- Tomar screenshot para confirmar que quedó activo

---

### WORKFLOW DE FACEBOOK (si aplica)

Repetir el mismo proceso con estas diferencias:
- Nombre: `Auto-Comentario [PALABRA_CLAVE] - FB - [fecha de hoy]`
- Trigger: **"Facebook Comment"** en lugar de Instagram Comment
- Connected Page: seleccionar la Facebook Page conectada
- Acción 3: **"Facebook Interactive Messenger"** en lugar de Instagram DM
- Tag de etiqueta inicial: `fb-comment`
- Tag en clic de botón: `fb-click-boton`

---

## PASO 8 — Reporte final

```
✅ AUTOMATIZACIÓN CREADA EXITOSAMENTE
─────────────────────────────────────────────────────
Workflows activos:
  ✓ Instagram: Auto-Comentario [PALABRA_CLAVE] - IG  →  ACTIVO
  ✓ Facebook:  Auto-Comentario [PALABRA_CLAVE] - FB  →  ACTIVO

Qué pasará cuando alguien comente "[PALABRA_CLAVE]":
  1. GHL etiqueta al contacto en el CRM
  2. El post responde automáticamente en el comentario
  3. Le llega un DM con tu mensaje
     [+ botón con enlace si configuraste uno]

Puedes editar estos workflows en:
GHL → Automatizaciones → buscar "Auto-Comentario [PALABRA_CLAVE]"
─────────────────────────────────────────────────────
```

### Si algún paso falla en Playwright:
- Tomar screenshot inmediatamente
- Indicar en qué paso específico falló
- Ofrecer: "¿Quieres que lo intente de nuevo, o prefieres que te guíe paso a paso para hacerlo tú?"
- No reportar éxito si hubo un error. Siempre mostrar el estado real.

---

## REGLAS

1. Nunca crear el workflow sin confirmación explícita del resumen final.
2. Solo Instagram y Facebook. Si el usuario pide otro canal, informar que no está disponible.
3. La conexión para el autoresponder se hace en **Configuración → Integraciones**, no en el Planificador de Redes Sociales.
4. Generar y mostrar variaciones de keyword antes de usarlas. Pedir aprobación.
5. Mostrar y aprobar las 10 respuestas al comentario antes de continuar.
6. Si Playwright falla, reportar con screenshot. Nunca simular éxito.
7. Crear workflows separados para Instagram y Facebook — no un solo workflow combinado.
