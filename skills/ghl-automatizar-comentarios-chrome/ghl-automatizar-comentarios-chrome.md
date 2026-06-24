---
name: "Automatizar Comentarios GHL — Plugin Chrome"
description: "Recopila la configuración del autoresponder de comentarios, genera todas las variaciones y produce un prompt listo para ejecutar con la extensión Claude for Chrome sobre GoHighLevel. Solo Instagram y Facebook."
---

# ghl-automatizar-comentarios-chrome

Este skill NO crea la automatización directamente. Su trabajo es recopilar toda la información, procesarla y generar un **prompt detallado y completo** que el estudiante copiará y usará en Claude con la extensión de Chrome instalada y GHL abierto. Claude ejecutará todo automáticamente sin hacer más preguntas.

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
> **5. ¿Incluyes enlace?** — ¿Va un botón con URL en el DM? Si sí, pega la URL y el texto del botón. Si no, escribe 'no'."

Esperar respuesta completa. No continuar hasta tenerla toda.

---

## PASO 2 — Generar variaciones de la palabra clave

Sin mostrarlas aún. Procesar internamente.

Generar todas las formas posibles que alguien puede escribir la palabra:
- Mayúsculas, minúsculas, mixtas
- Con y sin tilde/acento
- Frases cortas que la contengan (quiero X, dame X, más X, necesito X, pásame X)
- Formas con puntuación (X!, X?, X.)

Guardar lista completa separada por comas para el prompt final.

---

## PASO 3 — Generar 10 variaciones de respuesta al comentario

Sin mostrarlas aún. Procesar internamente.

Crear 10 respuestas distintas, naturales y con variación de tono y emojis, que le digan al usuario que revise su DM. Adaptar al tono del mensaje del DM si es formal, casual o con emojis.

Guardar las 10 para el prompt final.

---

## PASO 4 — Mostrar resumen para aprobación

Mostrar todo junto antes de generar el prompt:

```
✅ RESUMEN DE TU AUTOMATIZACIÓN
──────────────────────────────────────────────────
Post:         [nombre del post]
Canales:      [Instagram / Facebook / Ambos]
Keyword:      [palabra clave]
Variaciones:  [lista completa separada por comas]

Respuestas al comentario (10 rotativas):
  1. [respuesta 1]
  2. [respuesta 2]
  ... (todas las 10)

Mensaje DM:   [mensaje completo]
Botón:        [texto del botón → URL / sin botón]
──────────────────────────────────────────────────
¿Todo correcto? (sí / ajusta X cosa)
```

Esperar aprobación. Si pide ajuste, corregir solo ese punto y mostrar resumen actualizado.

---

## PASO 5 — Generar el prompt optimizado

Una vez aprobado, construir el prompt final con esta estructura. Debe ser directo, con todos los datos embebidos, sin preguntas y con instrucciones de UI tan detalladas que Claude no tenga que adivinar ningún clic.

Usar esta plantilla llenando todos los campos con los datos reales del usuario:

---

```
Eres un agente de automatización con acceso al navegador. GoHighLevel está abierto.
Tu tarea es crear una automatización de comentarios siguiendo estas instrucciones exactas.
Ejecuta cada paso en orden. No hagas preguntas. Si no encuentras algo en inglés, búscalo en español.
Toma un screenshot después de cada sección completada para verificar.

═══════════════════════════════
DATOS
═══════════════════════════════
Post: [NOMBRE DEL POST]
Canales: [INSTAGRAM / FACEBOOK / AMBOS]
Keyword: [PALABRA CLAVE]
Variaciones: [VAR1, VAR2, VAR3, VAR4, VAR5, ...]
Mensaje DM: [MENSAJE COMPLETO]
[Botón: "[TEXTO BOTÓN]" → [URL]]

Respuestas al comentario:
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

═══════════════════════════════════════════════════════════
INSTRUCCIONES — WORKFLOW DE INSTAGRAM
[Incluir esta sección solo si el canal es Instagram o Ambos]
═══════════════════════════════════════════════════════════

SECCIÓN A — CREAR EL WORKFLOW

A1. En el menú lateral izquierdo de GHL, busca y haz clic en "Automations" o "Automatizaciones".
A2. Busca el botón "+ New Workflow" o "Crear Workflow" y haz clic en él.
A3. Se abre un modal con opciones. Haz clic en "Start from Scratch" o "Empezar desde cero".
A4. Se abre el editor del workflow. En la parte superior verás el nombre actual (probablemente dice "New Workflow" o algo por defecto).
A5. Haz clic directamente sobre ese nombre. Se activa un campo de texto editable.
A6. Presiona Ctrl+A (Windows) o Cmd+A (Mac) para seleccionar todo el texto. Luego bórralo con Backspace o Delete.
A7. Escribe el nuevo nombre: "Auto-Comentario [KEYWORD] - IG - [FECHA DE HOY EN FORMATO DD-MM-YYYY]"
A8. Presiona Enter o haz clic fuera del campo para confirmar el nombre.

SECCIÓN B — CONFIGURAR EL DISPARADOR

B1. En el editor del workflow verás un bloque que dice "Add New Trigger" o "Agregar Disparador" (puede tener un ícono de rayo). Haz clic en él.
B2. Se abre un panel lateral o modal con la lista de triggers disponibles.
B3. En el campo de búsqueda escribe "Instagram" para filtrar. Selecciona "Instagram Comment" o "Comentario de Instagram".
B4. Aparecen los campos de configuración. Completa cada uno:
    - Campo "Connected Page" o "Página conectada": haz clic en el dropdown y selecciona la cuenta de Instagram conectada.
    - Campo "Post Type" o "Tipo de publicación": haz clic en el dropdown y selecciona "Published Post" o "Publicación publicada".
    - Campo "Post" o "Publicación": haz clic en el dropdown o campo de búsqueda, escribe parte del nombre del post "[NOMBRE DEL POST]" y selecciónalo cuando aparezca.
    - Campo "Keywords" o "Palabras clave": agrega cada variación. Escribe la primera y presiona Enter, luego la siguiente y Enter, así hasta agregar TODAS: [VAR1, VAR2, VAR3, ...] (agregar una por una).
B5. Haz clic en "Save" o "Guardar" para confirmar el trigger.
B6. Toma screenshot para verificar que el trigger quedó configurado.

SECCIÓN C — AGREGAR ETIQUETA AL CONTACTO

C1. Después de guardar el trigger, mira DEBAJO del bloque del trigger. Verás un botón "+" o un círculo con un signo más. Haz clic en ese "+".
C2. Se abre un panel con la lista de acciones disponibles.
C3. Busca "Add Contact Tag" o "Agregar etiqueta al contacto". Haz clic en ella.
C4. En el campo de etiqueta que aparece, escribe: instagram-comment
C5. Haz clic en "Save" o "Guardar".
C6. Toma screenshot para verificar que la etiqueta quedó agregada debajo del trigger.

SECCIÓN D — RESPONDER EN EL COMENTARIO

D1. Mira DEBAJO del bloque de etiqueta que acabas de agregar. Haz clic en el botón "+" que aparece ahí.
D2. En el panel de acciones, busca "Respond on Comment" o "Responder al comentario". Haz clic en ella.
D3. Aparece un editor de mensajes. Agrega la primera respuesta: "[respuesta 1]"
D4. Busca un botón "Add Message", "+" o "Agregar mensaje" dentro de esta acción para agregar más respuestas. Haz clic en él.
D5. Agrega la segunda respuesta: "[respuesta 2]". Repite este proceso hasta agregar las 10 respuestas.
D6. Si hay una opción "Random", "Aleatorio" o "Rotate" (rotar), actívala para que las respuestas roten automáticamente.
D7. Haz clic en "Save" o "Guardar".
D8. Toma screenshot para verificar las 10 respuestas.

SECCIÓN E — INSTAGRAM INTERACTIVE MESSENGER

E1. Mira DEBAJO del bloque de "Respond on Comment". Haz clic en el botón "+" que aparece ahí.
E2. En el panel de acciones, busca "Instagram Interactive Messenger" o "Messenger Interactivo de Instagram". Haz clic en ella.
E3. Busca el campo "Response Type" o "Tipo de respuesta". Haz clic en su dropdown y selecciona "Reply to comment via DM" o "Responder al comentario por DM".
E4. En el campo de mensaje escribe exactamente: [MENSAJE DM COMPLETO]

[SI HAY BOTÓN — incluir E5 a E9, omitir si no hay enlace]
E5. Busca la opción "Add Button" o "Agregar botón" dentro del messenger. Haz clic en ella.
E6. En el campo de texto del botón escribe: [TEXTO DEL BOTÓN]
E7. En el campo de URL del botón pega: [URL DEL ENLACE]
E8. Haz clic en "Save" o "Guardar" para guardar el messenger completo.
E9. Después de guardar, verás que DEBAJO del bloque del messenger aparecen DOS ramas:
    - Una rama que dice "Default timeout" o "Tiempo de espera por defecto" — IGNORAR esta.
    - Otra rama que muestra el texto del botón o "Button clicked" — ESTA es la correcta.
    Haz clic en el botón "+" que está dentro de la RAMA DEL BOTÓN (la segunda).
E10. En el panel de acciones selecciona "Add Contact Tag" o "Agregar etiqueta".
E11. Escribe la etiqueta: ig-click-boton
E12. Haz clic en "Save".
[FIN BLOQUE BOTÓN]

[SI NO HAY BOTÓN]
E5. Haz clic en "Save" o "Guardar" para guardar el messenger.
[FIN BLOQUE SIN BOTÓN]

SECCIÓN F — GUARDAR Y PUBLICAR

F1. Busca el botón "Save" en la parte superior derecha del editor y haz clic.
F2. Busca el botón "Publish" o un toggle/interruptor que diga "Active" o "Activo". Haz clic para activar el workflow.
F3. Verifica que el estado del workflow muestre "Active" o "Activo".
F4. Toma screenshot final del workflow activo con todos sus pasos visibles.

═══════════════════════════════════════════════════════════
INSTRUCCIONES — WORKFLOW DE FACEBOOK
[Incluir esta sección solo si el canal es Facebook o Ambos]
═══════════════════════════════════════════════════════════

Repite exactamente las mismas secciones A a F con estos cambios:
- Nombre del workflow: "Auto-Comentario [KEYWORD] - FB - [FECHA DE HOY]"
- Trigger: "Facebook Comment" o "Comentario de Facebook"
  - Connected Page: seleccionar la Facebook Page conectada
- Etiqueta inicial (Sección C): fb-comment (en lugar de instagram-comment)
- Acción de mensaje (Sección E): "Facebook Interactive Messenger" o "Messenger Interactivo de Facebook"
  - Mismo Response Type: "Reply to comment via DM"
  - Mismo mensaje DM
  - Si hay botón: mismo texto y URL
  - Etiqueta en rama del botón: fb-click-boton (en lugar de ig-click-boton)

═══════════════════════════════
CONFIRMACIÓN FINAL
═══════════════════════════════
Al terminar reporta:
- Nombre exacto del workflow de Instagram creado + estado (Activo/Inactivo)
- Nombre exacto del workflow de Facebook creado + estado (Activo/Inactivo)
- Cualquier paso donde hayas tenido dificultad o no hayas podido completar
```

---

Mostrar el prompt al usuario con este mensaje:

> "Aquí está tu prompt listo. Para usarlo:
>
> 1. Abre **GHL** en Chrome y entra a tu sub-cuenta
> 2. Abre **claude.ai** en el mismo Chrome con la extensión activa
> 3. Copia todo el prompt de abajo y pégalo en el chat
> 4. Claude navegará GHL y creará la automatización paso a paso
>
> ─────────────────────────────
> [PROMPT GENERADO]
> ─────────────────────────────"

---

## REGLAS

1. No generar el prompt hasta tener todo aprobado en el resumen.
2. El prompt final no lleva preguntas — todos los datos van embebidos con los valores reales.
3. Si el usuario pide solo Instagram, omitir completamente la sección de Facebook y viceversa.
4. Si no hay enlace, omitir los pasos E5 a E12 y usar solo el bloque "SIN BOTÓN".
5. Las variaciones del keyword van separadas por comas en una sola línea dentro del bloque DATOS, pero en la Sección B4 se indica agregarlas una por una.
6. El prompt debe ser copiable tal cual, sin que el usuario tenga que editar nada.
7. Reemplazar TODOS los placeholders con los valores reales del usuario antes de entregar el prompt.
