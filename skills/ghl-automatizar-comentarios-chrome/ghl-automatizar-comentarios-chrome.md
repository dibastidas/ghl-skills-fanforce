---
name: "Automatizar Comentarios GHL — Plugin Chrome"
description: "Recopila la configuración del autoresponder de comentarios, genera todas las variaciones y produce un prompt listo para ejecutar con la extensión Claude for Chrome sobre GoHighLevel. Solo Instagram y Facebook."
---

# ghl-automatizar-comentarios-chrome

Este skill NO crea la automatización directamente. Su trabajo es recopilar toda la información, procesarla y generar un **prompt optimizado y completo** que el estudiante copiará y usará en Claude con la extensión de Chrome instalada y GHL abierto. Claude ejecutará todo automáticamente sin hacer más preguntas.

**Requisito:** Tener instalada la extensión [Claude for Chrome](https://claude.com/claude-for-chrome) y GHL abierto en el navegador.

**Solo disponible para Instagram y Facebook.**

---

## PASO 1 — Recolectar toda la información en un solo mensaje

Preguntar todo de una vez. No hacer preguntas en rondas separadas.

> "Vamos a configurar tu automatización de comentarios. Necesito toda esta info para generarte el prompt listo:
>
> **1. Canales** — ¿Instagram, Facebook o ambos?
>
> **2. El reel o post** — Nombre o fecha del post en GHL (ej: 'el reel del 20 de junio', 'video de precios').
>
> **3. Palabra clave del comentario** — ¿Qué debe escribir alguien para activar la respuesta? (ej: INFO, PRECIO, LINK)
>
> **4. Mensaje del DM** — Escribe exactamente el mensaje que recibirán por privado.
>
> **5. ¿Incluyes enlace?** — ¿Va un botón con URL en el DM? Si sí, pega la URL. Si no, escribe 'no'."

Esperar respuesta completa. No continuar hasta tenerla toda.

---

## PASO 2 — Generar variaciones de la palabra clave

Sin mostrarlas aún al usuario. Procesar internamente.

Generar todas las formas posibles que alguien puede escribir la palabra:
- Mayúsculas, minúsculas, mixtas
- Con y sin tilde/acento
- Frases cortas que la contengan (quiero X, dame X, más X, necesito X, pásame X)
- Formas con puntuación (X!, X?, X.)

Guardar lista completa para el prompt final.

---

## PASO 3 — Generar 10 variaciones de respuesta al comentario

Sin mostrarlas aún. Procesar internamente.

Crear 10 respuestas distintas, naturales y con variación de tono y emojis, que le digan al usuario que revise su DM. Adaptar al tono del mensaje del DM si es formal, casual o con emojis.

Guardar las 10 para el prompt final.

---

## PASO 4 — Mostrar resumen para aprobación

Antes de generar el prompt mostrar todo junto:

```
✅ RESUMEN DE TU AUTOMATIZACIÓN
──────────────────────────────────────────────────
Post:         [nombre del post]
Canales:      [Instagram / Facebook / Ambos]
Keyword:      [palabra clave]
Variaciones:  [lista completa]

Respuestas al comentario (10 rotativas):
  1. [respuesta 1]
  2. [respuesta 2]
  ... (todas las 10)

Mensaje DM:   [mensaje completo]
Botón:        [texto del botón → URL / sin botón]
──────────────────────────────────────────────────
¿Todo correcto? (sí / ajusta X cosa)
```

Esperar aprobación. Si pide ajuste, corregir solo ese punto y volver a mostrar el resumen.

---

## PASO 5 — Generar el prompt optimizado

Una vez aprobado, generar el prompt final. Debe ser:
- **Directo:** sin preguntas, sin confirmaciones, con todos los datos embebidos
- **Eficiente:** sin texto de relleno, sin explicaciones innecesarias
- **Completo:** todo lo que Claude necesita saber está dentro, no depende de contexto externo
- **Estructurado:** primero contexto, luego acciones ordenadas, luego datos

Usar esta plantilla para construir el prompt:

---

```
Eres un agente de automatización. Tienes GoHighLevel abierto en el navegador. 
Crea la siguiente automatización de comentarios. Ejecuta cada paso sin preguntar, 
navega la UI, haz los clics necesarios y confirma cuando termines cada sección.

DATOS DE LA AUTOMATIZACIÓN:
- Post: [nombre del post]
- Canales: [Instagram / Facebook / Ambos]
- Keyword disparador: [palabra clave]
- Variaciones del keyword: [lista separada por comas]
- Mensaje DM: [mensaje completo]
[- Botón en DM: "[texto del botón]" → [URL]]

RESPUESTAS AL COMENTARIO (10 — agregar todas en modo rotación):
1. [respuesta 1]
2. [respuesta 2]
3. [respuesta 3]
4. [respuesta 4]
5. [respuesta 5]
6. [respuesta 6]
7. [respuesta 7]
8. [respuesta 8]
9. [respuesta 9]
10. [respuesta 10]

INSTRUCCIONES:

[PARA INSTAGRAM — omitir si no aplica]
1. Ve a Automations (o Automatizaciones) → crear nuevo workflow → Start from Scratch
2. Nombre: "Auto-Comentario [KEYWORD] - IG - [fecha de hoy]"
3. Add Trigger → "Instagram Comment" (o "Comentario de Instagram")
   - Connected Page: cuenta de Instagram conectada
   - Post Type: "Published Post" (o "Publicación publicada")
   - Post: [nombre del post]
   - Keywords: agregar TODAS las variaciones listadas arriba
4. Add Action → "Add Contact Tag" (o "Agregar etiqueta") → tag: instagram-comment
5. Add Action → "Respond on Comment" (o "Responder al comentario") → agregar las 10 respuestas, activar rotación
6. Add Action → "Instagram Interactive Messenger" (o "Messenger Interactivo de Instagram")
   - Response Type: "Reply to comment via DM" (o "Responder al comentario por DM")
   - Mensaje: [mensaje DM completo]
   [- Agregar botón: "[texto]" → [URL]
     - En la rama del botón (NO en Default timeout): Add Action → "Add Contact Tag" → tag: ig-click-boton]
7. Save → Publish → verificar que quede en estado Active

[PARA FACEBOOK — omitir si no aplica]
Repetir el mismo flujo con:
- Nombre: "Auto-Comentario [KEYWORD] - FB - [fecha de hoy]"
- Trigger: "Facebook Comment" (o "Comentario de Facebook")
- Acción 3: "Facebook Interactive Messenger" (o "Messenger Interactivo de Facebook"), mismo tipo de respuesta
- Tag inicial: fb-comment
- Tag en rama del botón: fb-click-boton

NOTA DE IDIOMA: GHL puede estar en inglés o español. Si no encuentras una opción en inglés, búscala en español y viceversa.

Al terminar confirma: nombre del workflow creado + estado (activo/inactivo) para cada canal.
```

---

Mostrar el prompt al usuario con este mensaje:

> "Aquí está tu prompt listo. Para usarlo:
>
> 1. Instala la extensión **Claude for Chrome** en tu navegador → [claude.com/claude-for-chrome](https://claude.com/claude-for-chrome)
> 2. Abre **GHL** en Chrome y entra a tu sub-cuenta
> 3. Abre Claude en el browser (claude.ai) con la extensión activa
> 4. Copia y pega el prompt de abajo en el chat
> 5. Claude navegará GHL y creará toda la automatización solo
>
> ──────────────────
> [PROMPT GENERADO]
> ──────────────────"

---

## REGLAS

1. No generar el prompt hasta tener todo aprobado en el resumen.
2. El prompt final no lleva preguntas ni confirmaciones — todos los datos van embebidos.
3. Si el usuario pide solo Instagram o solo Facebook, omitir la sección del otro canal en el prompt.
4. Si no hay enlace, omitir completamente el bloque del botón del prompt.
5. Las variaciones del keyword van en una sola línea separadas por comas — no en lista — para ahorrar tokens en el prompt.
6. El prompt debe ser copiable tal cual, sin ediciones adicionales por parte del usuario.
