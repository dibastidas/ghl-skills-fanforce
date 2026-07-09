---
name: lf-diseno-carrusel
description: >
  Diseña visualmente uno o más carruseles a partir del copy que el usuario pega
  directamente en el chat, produciendo slides PNG 1080×1350px listos para
  Instagram. Usar cuando alguien diga: "diseña este carrusel", "hazme las
  imágenes de este carrusel", "convierte este copy en slides", "renderiza estos
  slides", o cualquier variación que combine un copy de carrusel (slide 1 / slide
  2 / etc.) con la intención de tener los PNG finales. No depende de ningún
  cliente cargado de antemano ni de Google Drive — primero verifica que
  Playwright y Nanobanana estén conectados (guiando la configuración paso a
  paso, con una prueba real antes de continuar, si falta la API key de
  Nanobanana), luego pide el copy, los colores de marca y el handle
  directamente en el chat, elige un estilo visual de una biblioteca de 40
  estilos incluida en este mismo skill, y entrega el resultado en el chat,
  guardado como archivos en el computador, o ambas cosas (a elección del
  usuario). Si ningún estilo de la biblioteca convence, dirige a
  `lf-prompt-diseno-carrusel` para crear uno personalizado.
argument-hint: "[pega aquí el copy del carrusel, o dime cuántos carruseles vas a diseñar]"
---

# lf-diseno-carrusel — Diseño Visual de Carruseles

Convierte el copy de un carrusel en slides PNG listos para publicar, con un
estilo visual elegido por carrusel. Todo el proceso ocurre en el chat: se pide
el copy y la info de marca al inicio, y se entrega el resultado donde el
usuario prefiera (chat, carpeta del computador, o ambas) — no se guarda nada
en Drive ni en ninguna cuenta externa.

> ⚠️ **REGLA #1 DE ESTE SKILL — TAMAÑO FIJO, SIN EXCEPCIÓN:**
> Todo slide final — sea HTML/CSS, imagen generada con Nanobanana, o foto real
> procesada — debe medir **1080×1350px** (formato carrusel de Instagram, 4:5
> vertical). Esto aplica siempre, sin importar el estilo elegido. Verificar el
> tamaño real de cada PNG antes de darlo por terminado; si algo salió en otra
> medida, corregirlo (recapturar, regenerar, o hacer crop/resize) antes de
> mostrarlo o guardarlo. Nunca entregar un slide que no sea 1080×1350px.

---

## PASO 0 — Verificar que todo esté conectado

Antes de pedir el copy, confirmar en silencio que las 2 herramientas que este
skill necesita están disponibles:
- **Playwright** (`mcp__plugin_ghl-skills-fanforce_playwright__*`) — fallback de captura y ver la biblioteca visual de estilos
- **Nanobanana** (`mcp__plugin_ghl-skills-fanforce_nanobanana__*`) — generar imágenes con IA (Motor Banana)

**Si las 2 están disponibles y responden, no decir nada de esto al usuario —
pasar directo al PASO 1.**

### Si falta Nanobanana (lo más común — necesita una API key personal)

> "Antes de arrancar necesito que conectes una cosa: Nanobanana, el motor que
> genera las imágenes. Vamos paso a paso, es rápido."

Dar los pasos más específicos posibles, como si la persona nunca hubiera
sacado una API key — sin asumir que sabe qué es eso:

1. "Abre esta página en tu navegador: [aistudio.google.com/apikey](https://aistudio.google.com/apikey)"
2. "Inicia sesión con tu cuenta de Google si te lo pide"
3. "Busca el botón que dice 'Create API key' o 'Get API key' y haz clic ahí"
4. "Te va a aparecer un código que empieza con `AIza...` — ese es tu 'API key'.
   Haz clic en el ícono de copiar al lado del código."
5. "Pégamelo aquí en el chat."

Cuando la dé, configurarla (mismo procedimiento técnico que en "Si falta la
API key de Nanobanana" del PASO 6.4) y **probarla antes de seguir**: generar
una imagen mínima de prueba (ej. `gemini_generate_image` con un prompt corto
tipo "círculo azul simple, sin texto") para confirmar que responde de verdad.
Si funciona, confirmar al usuario y descartar esa imagen de prueba. Si falla:

> "Diste la key, pero todavía no está respondiendo. Puede ser que necesite un
> momento para activarse, o que se copió algo de más o de menos. Espero unos
> segundos y vuelvo a probar — si sigue sin funcionar, revisa que la copiaste
> completa, sin espacios extra."

Esperar y reintentar un par de veces antes de escalar. Nunca decir que el
motor "no funciona" sin haber intentado esto primero.

### Si falta Playwright (menos común — no necesita ninguna key)

> "Playwright no está respondiendo. Esto normalmente se arregla reiniciando
> Claude Code/Desktop por completo, o resincronizando el plugin
> `ghl-skills-fanforce` desde el marketplace. ¿Puedes intentarlo y avisarme
> cuando esté listo?"

No hay nada que configurar aquí con una key — si falta, es un problema de
instalación del plugin, no de credenciales, así que no hay auto-configuración
posible.

**Solo cuando todo esté confirmado conectado** (probado con una llamada real,
no solo "dijo que sí"), pasar al PASO 1.

---

## PASO 1 — Copy y marca

Preguntar en un solo bloque:

> "Para diseñar tu(s) carrusel(es) necesito:
>
> 1. **El copy** — pega cada carrusel completo, slide por slide
>    (Slide 1: ... / Slide 2: ... / etc.). Si son varios carruseles, sepáralos
>    claramente.
> 2. **Colores de marca** — color principal y de acento (hex si los tienes,
>    o una descripción como "azul marino" y "naranja").
> 3. **Handle de Instagram** — @[tu handle], para el slide final."

Ser flexible con el formato del copy: parsear lo que llegue y mapear a slides,
sin importar si viene con numeración distinta o en texto libre.

Si falta el copy, no continuar — es lo único indispensable para arrancar.
Colores y handle se pueden completar más adelante si el usuario no los tiene a mano.

---

## PASO 2 — Elegir estilo por carrusel

Con el copy cargado, mostrar el listado:

> "Tenemos [N] carrusel(es) para diseñar:
>
> · [tipo si se identifica] — "[tema]"
> · ...
>
> ⚠️ **Si son varios, no recomiendo usar el mismo estilo para todos** — la
> variedad visual hace el feed más atractivo y evita que se vea como plantilla
> repetida.
>
> Tenemos 40 estilos disponibles. Si quieres ver cada uno con su imagen de
> ejemplo antes de decidir:
> 🔗 **https://lanzafacil.com/biblioteca-de-carruseles** · Contraseña: `lanzafacil2026`
>
> ¿Cómo quieres elegir los estilos?
>
> **A) Yo elijo** — dime un estilo para cada carrusel (nombre o número del 1 al 40)
>
> **B) Tú eliges** — analiza el copy y elige el estilo que mejor encaje con
>    cada tipo de contenido
>
> **C) Ninguno me convence** — quiero usar un diseño de referencia propio"

El link se manda siempre de una vez, junto con la pregunta — no esperar a que
el usuario pida ver los estilos para dárselo.

### Si elige A:
Leer `references/biblioteca-estilos.md` (en este mismo skill) para conocer los 40
estilos disponibles. Esperar la asignación (nombre o número). Si repite estilo
en varios carruseles, advertir. Si no conoce los estilos, listar los nombres y
una línea de descripción de cada uno desde ese mismo archivo — no hace falta
abrir ningún navegador para elegir.

**En cuanto el usuario diga un nombre o número** (haya visto la web o no), ir
directo a `references/biblioteca-estilos.md` y leer el prompt completo de ese
estilo desde ahí — nunca desde la web, incluso si el usuario la usó solo para
mirar las imágenes de ejemplo.

### Si elige B — Claude elige:
Leer `references/biblioteca-estilos.md` y asignar el estilo (de los 40) que mejor
encaje según el tipo de contenido, usando los tags de cada estilo como guía:
- **Contrarian** → estilos de alto contraste y composición directa (ej. Bold Statement, Brutalist/Swiss Grid, Acid/Maximalista)
- **Autoridad Sutil** → estilos limpios con jerarquía visual clara (ej. Minimalista Limpio, Editorial Revista, Diccionario/Definición)
- **Conexión** → estilos cálidos, con espacio para foto si hay (ej. Scrapbook/Collage, Full Bleed Atmosférico, Highlighter/Notas Estéticas)
- **Vehículo / CTA** → estilos de acento fuerte y energía alta (ej. Gradiente Fluido, Dark Neón Tech, Paso a Paso con Progress Bar)

Mostrar propuesta y esperar confirmación:
> "Propuesta:
> · [tipo] → **[N] · [Nombre]** — [razón en 1 línea]
> ..."

### Si elige C — Ningún estilo convence:
> "Si quieres usar un diseño de referencia propio, el skill que te ayuda es:
> → `lf-prompt-diseno-carrusel`
>
> Cuando tengas el prompt, regresa aquí y pégalo — seguimos desde donde
> quedamos sin perder el copy que ya cargaste."

Esperar. Si pega el prompt, usarlo como guía de diseño.

---

## PASO 3 — Fotos (opcional)

> "¿Quieres incluir fotos en algún carrusel?
>
> **A) Sí, fotos reales** — dame la ruta de la carpeta local con las fotos
> **B) Sí, generadas con IA** — Nanobanana crea las imágenes por ti (útil si
>    no tienes fotos propias pero quieres el estilo con foto)
> **C) No** — diseño 100% tipográfico"

Si el estilo elegido ya es muy visual por sí mismo (mucha decoración, texturas,
subrayados, elementos gráficos — ej. Scrapbook/Collage, Highlighter/Notas
Estéticas), se puede sugerir la opción C como recomendada antes de preguntar,
pero sin decidir por el usuario.

### Si dice A — fotos reales:
- `ls "[ruta_carpeta_fotos]"` → listar los archivos disponibles

**No leer todas las fotos de golpe.** Estrategia de selección (igual que lf-render-carrusel):
1. Listar la carpeta y elegir 4-6 candidatas por fecha de modificación reciente o tamaño de archivo (proxy de calidad)
2. Leer/previsualizar solo esas candidatas
3. Elegir la que mejor encaje con cada slide según composición y tono

### Si dice B — fotos generadas con IA:

> "¿Qué quieres que muestren las imágenes? Puedes darme:
> - Una descripción general (ej. 'escenas de trabajo, computadora, café, luz natural')
> - O una descripción específica por slide, si son distintas entre sí"

Generar cada una con el MCP de Nanobanana, llamando directamente:
```
mcp__plugin_ghl-skills-fanforce_nanobanana__gemini_generate_image
→ "[descripción de la escena] · Estilo [nombre] · Paleta [colores] · 1080x1350px, vertical 4:5 (formato carrusel Instagram) · Sin texto"
```
Mismo tamaño obligatorio 1080×1350px que cualquier otra imagen Banana del
carrusel (ver PASO 6.4) — sin foto de origen que editar, se genera desde cero.

### Si dice A o B:

Preguntar el modo de disposición:
> "¿Cómo usamos las fotos?
> **A) Hero de fondo** — foto llena el slide, texto encima con overlay
> **B) Split** — foto arriba, texto abajo
> **C) Circular (Cutout)** — foto en círculo
> **D) Polaroid** — foto con borde blanco rotada, como recorte de álbum
> **E) Photo strip** — tira de 2-3 fotos tipo fotomatón (ideal para narrativa)
> **F) Mezcla** — varía según el slide y el contenido"

Asignar el patrón según el rol del slide:
- **Polaroid** → slides personales, intros, testimonios, "esto soy yo"
- **Hero** → slide impactante con UNA frase fuerte, tipo cover de revista
- **Circular/Cutout** → slides donde la foto es secundaria (junto a una cita, dato, lista)
- **Photo strip** → slides de "evolución", "antes vs ahora", "mi semana"

**Regla de convivencia:** la foto es UN elemento más del diseño, no el protagonista
que aplasta todo. Siempre debe convivir con elementos del estilo (tipografía,
colores de marca, decoración del prompt). Si la foto está sola se ve plano.

---

## PASO 4 — Modo de trabajo y dónde ver el resultado

> "¿Cómo quieres que trabaje?
>
> **A) 1 x 1** — diseño cada carrusel, te lo muestro y espero tu aprobación
>    antes de pasar al siguiente
>
> **B) Todos de una** — diseño todos en secuencia y te muestro todo al terminar
>
> ¿Y dónde quieres los PNG finales?
>
> **A) Aquí en el chat** — te los muestro directamente en la conversación, sin
>    dejar archivos guardados
> **B) Guardados en mi computador** — te dejo los PNG en una carpeta (por
>    defecto tu Escritorio, o dime otra ruta)
> **C) Ambas** — te los muestro aquí y también te dejo los archivos guardados"

Guardar la elección como `destino_resultado`.

Si eligió B o C y no dio una carpeta propia, detectar el sistema operativo
para construir la ruta del Escritorio:
- **macOS / Linux:** `$HOME/Desktop`
- **Windows:** `%USERPROFILE%\Desktop` (equivalente a `$HOME/Desktop` si Claude
  Code corre sobre una shell tipo Git Bash o WSL, que normalmente ya resuelve ahí)

Verificar que la carpeta exista antes de usarla (`ls "$HOME/Desktop"` o
equivalente). Si no existe ni se puede detectar, preguntar la ruta exacta en
vez de asumir.

---

## PASO 5 — Confirmación antes de empezar

> "Listo para empezar. Confirma:
>
> **Carruseles:**
> · [tipo] → Estilo [N] · [Nombre]
> · ...
>
> **Fotos:** [Reales — carpeta: X — modo: Y / Generadas con IA — modo: Y / No]
> **Modo:** [1x1 / Todos de una]
> **Resultado:** [Chat / Guardado en: X / Ambas]
>
> ¿Empezamos?"

---

## PASO 6 — DISEÑAR CADA CARRUSEL

### 6.1 — Cargar el estilo visual

Leer `references/biblioteca-estilos.md` (en este mismo skill) y localizar la
sección del estilo [N] · [Nombre] asignado — trae el prompt completo, las
paletas sugeridas, características y tags de uso listos para aplicar.

Si viene de prompt personalizado (opción C del Paso 2), usarlo directamente.
Aplicar los colores de marca y el handle que el usuario dio en el PASO 1 sobre
la paleta del estilo.

### 6.2 — Preparar fotos (si aplica)

**Fotos reales:** copiar las elegidas al scratchpad del carrusel con nombre simple
(`foto-slide1.jpg`, `foto-slide3.jpg`) para usar ruta relativa en el HTML —
igual que lf-render-carrusel: nunca rutas absolutas en `<img src>`.

**Fotos generadas con IA:** generarlas ya directamente en el scratchpad del
carrusel con el mismo nombre simple (`foto-slide1.jpg`, `foto-slide3.jpg`) —
ver el prompt de Nanobanana en el PASO 3.

Aplicar en todas las fotos `filter: contrast(1.02) saturate(1.05)` para
tono consistente sin perder la calidez del diseño.

### 6.3 — Generar el HTML

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <!-- Google Fonts del estilo vía CDN — siempre en el head -->
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { width: 1080px; background: transparent; }
    .slide {
      width: 1080px;
      height: 1350px;
      position: relative;
      overflow: hidden;
      /* No display:none aquí — el render captura cada .slide directamente */
    }
  </style>
</head>
<body>
  <div class="slide s1"><!-- Slide 1 · Hook --></div>
  <div class="slide s2"><!-- Slide 2 · Desarrollo --></div>
  <!-- ... -->
  <div class="slide sN"><!-- Slide N · CTA + handle --></div>
</body>
</html>
```

**Reglas de composición:**
- **Asimetría obligatoria** — cada slide con una composición diferente al anterior
- **Slide 1 (Hook):** composición de máximo impacto — texto masivo, pocos elementos
- **Slide final:** siempre CTA + handle visibles
- **Slides intermedios:** rotar posición de título, cuerpo y elementos decorativos
- **Un punto principal por slide** — si hay dos ideas, dividir en dos slides
- Cuerpo mínimo 28px · Títulos 72px+

**Checklist por slide antes de pasar al siguiente:**
- [ ] ¿Composición diferente al slide anterior?
- [ ] ¿Handle visible?
- [ ] ¿Numeración de slide visible?
- [ ] ¿UN solo punto principal?
- [ ] ¿Si hay foto: convive con otros elementos del estilo?

**CSS de fotos (con filter de calidad):**

```css
/* Aplicar a todas las imágenes */
.foto-real { filter: contrast(1.02) saturate(1.05); }

/* HERO DE FONDO */
.slide-hero { position: relative; overflow: hidden; }
.hero-bg {
  position: absolute; inset: 0;
  background-image: url('foto-slide1.jpg');
  background-size: cover; background-position: center;
  filter: contrast(1.05) saturate(1.05);
}
.hero-overlay {
  position: absolute; inset: 0;
  background: rgba([R],[G],[B], 0.52);
}
.hero-content { position: relative; z-index: 2; }

/* SPLIT */
.zona-foto {
  height: 570px;
  background-image: url('foto-slide2.jpg');
  background-size: cover; background-position: center;
  filter: contrast(1.02) saturate(1.05);
}
.zona-texto { height: 780px; background: [color_marca]; padding: 56px 64px; }

/* CIRCULAR / CUTOUT */
.cutout {
  width: 260px; height: 260px;
  border-radius: 50%; overflow: hidden;
  background: [color_fondo]; padding: 8px;
  box-shadow: 0 14px 30px rgba(0,0,0,0.18), 0 4px 8px rgba(0,0,0,0.10);
  transform: rotate(-3deg);
}
.cutout img {
  width: 100%; height: 100%;
  border-radius: 50%; object-fit: cover; object-position: center top;
  filter: contrast(1.02) saturate(1.05);
}

/* POLAROID */
.polaroid {
  background: #ffffff;
  padding: 18px 18px 56px 18px;
  box-shadow: 0 22px 44px rgba(0,0,0,0.20), 0 6px 12px rgba(0,0,0,0.12);
  transform: rotate(-3deg);
  display: inline-block;
}
.polaroid img { width: 100%; object-fit: cover; display: block; filter: contrast(1.02) saturate(1.05); }
.polaroid .caption { font-size: 36px; text-align: center; margin-top: 12px; }

/* PHOTO STRIP — tira de fotomatón */
.photo-strip {
  background: #ffffff; padding: 14px;
  box-shadow: 0 16px 34px rgba(0,0,0,0.18);
  transform: rotate(2.5deg);
  display: flex; flex-direction: column; gap: 10px;
  width: 240px;
}
.photo-strip img {
  width: 100%; aspect-ratio: 1/1; object-fit: cover; display: block;
  filter: contrast(1.02) saturate(1.05);
}
```

**Sombras dramáticas** en polaroid y strip — dan peso de objeto físico, no usar sombras planas.

### 6.4 — Motor Banana (si el estilo lo requiere)

**Tamaño obligatorio, sin excepción:** toda imagen generada con Nanobanana para un
slide completo de carrusel debe ser **1080×1350px (formato carrusel de Instagram,
4:5 vertical)**. Nunca cuadrada, nunca 16:9, nunca el tamaño default del modelo.
Antes de generar, fijar el aspect ratio:

```
mcp__plugin_ghl-skills-fanforce_nanobanana__set_aspect_ratio
→ "4:5"
```

Sin fotos reales:
```
mcp__plugin_ghl-skills-fanforce_nanobanana__gemini_generate_image
→ "[escenario visual] · Estilo [nombre] · Paleta [colores] · 1080x1350px, vertical 4:5 (formato carrusel Instagram) · Sin texto"
```

Con fotos reales:
```
mcp__plugin_ghl-skills-fanforce_nanobanana__gemini_edit_image
→ image: [foto en scratchpad]
→ prompt: "Estilo [nombre]. Overlay [color] 50%. Mantén el rostro visible. Sin texto añadido. Salida 1080x1350px, vertical 4:5 (formato carrusel Instagram)."
```

Excepción explícita: si el estilo usa Banana solo para una imagen PARCIAL del
slide (ej. Split Screen = mitad superior 1080×640px, o un tile de Bento/Pinterest
más pequeño que el slide completo), usar el tamaño parcial indicado en
`references/biblioteca-estilos.md` para ese estilo — la regla de 1080×1350px
aplica a imágenes que van a ocupar el slide completo.

Generar en paralelo todos los slides Banana que no dependan entre sí.
Guardar en scratchpad y referenciar en HTML con ruta relativa.

Después de generar, verificar las dimensiones reales del archivo antes de
darlo por bueno — si Nanobanana devolvió otro tamaño, regenerar o hacer
crop/resize a 1080×1350px antes de continuar. Nunca capturar/usar una imagen
que no sea 1080×1350px en un slide completo.

#### Si falta la API key de Nanobanana

Si la tool `mcp__plugin_ghl-skills-fanforce_nanobanana__*` no está disponible,
o falla con un error de autenticación/API key, no reportarlo simplemente como
"no se pudo" y seguir sin la imagen. En vez de eso, ofrecer configurarla:

> "Para generar imágenes necesito una API key de Google AI (gratis).
>
> 1. Sácala en [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
> 2. Pégamela aquí y yo la dejo configurada — no hace falta que abras terminal ni edites nada a mano."

Cuando la dé, configurarla directamente (Claude tiene acceso al sistema de
archivos, no hace falta que el usuario lo haga manualmente):

- **macOS / Linux:** detectar el shell (`echo $SHELL`) y agregar la línea al
  archivo de perfil correspondiente (`~/.zshrc` para zsh, `~/.bashrc` o
  `~/.bash_profile` para bash) — revisar primero si ya existe una línea
  `export GOOGLE_AI_API_KEY=` para no duplicarla, y reemplazarla en vez de
  agregar una nueva si ya está:
  ```bash
  export GOOGLE_AI_API_KEY="[key]"
  ```
- **Windows:** correr `setx GOOGLE_AI_API_KEY "[key]"` — persiste en las
  variables de entorno del usuario sin necesidad de editar ningún archivo.

En ambos casos, avisar que **debe reiniciar Claude Code/Desktop por completo**
(cerrar y volver a abrir) para que la nueva variable se cargue — un proceso ya
abierto no la ve hasta reiniciar. No repetir la key en texto plano en el chat
más de lo necesario para confirmarla.

### 6.5 — Capturar los slides

**Opción A — skill `lf-render-carrusel` (recomendado, resolución retina 2x):**

Invocar el skill `lf-render-carrusel` (carpeta hermana de este skill, dentro de
`skills/` en este mismo plugin) pasándole la ruta del HTML generado en el paso
anterior: `[scratchpad]/[carrusel N]/slides.html`.

Ese skill se encarga de verificar/instalar su propia dependencia (`puppeteer-core`)
y de exportar cada `.slide` como `slide-01.png`, `slide-02.png`, etc. en la misma
carpeta del HTML, esperando `document.fonts.ready` + 1.5s antes de capturar para
que las Google Fonts queden renderizadas correctamente.

Si por algún motivo `lf-render-carrusel` no está disponible en la instalación
(plugin desactualizado, Chrome no instalado, etc.), usar la Opción B como fallback.

**Opción B — Playwright MCP (si `lf-render-carrusel` no está disponible):**

```
1. mcp__plugin_ghl-skills-fanforce_playwright__browser_navigate
   → file:///[scratchpad]/[carrusel N]/slides.html
   waitUntil: networkidle (esperar que carguen las fonts del CDN)

2. mcp__plugin_ghl-skills-fanforce_playwright__browser_wait_for
   → selector: .slide  (confirmar que los slides existen en el DOM)

3. mcp__plugin_ghl-skills-fanforce_playwright__browser_resize
   → width: 1080, height: 1350

4. Esperar 1.5s para que Google Fonts terminen de renderizar:
   mcp__plugin_ghl-skills-fanforce_playwright__browser_evaluate
   → "await document.fonts.ready"

5. Para cada slide s1 ... sN:
   a. Mostrar solo ese slide:
      document.querySelectorAll('.slide').forEach(s => s.style.display='none');
      document.querySelector('.sN').style.display='block';
   b. mcp__plugin_ghl-skills-fanforce_playwright__browser_take_screenshot
      → path: [scratchpad]/[carrusel N]/slide-0N.png
```

### 6.6 — Verificar resultado

```bash
ls "[scratchpad]/[carrusel N]/" | grep "slide-.*\.png" | wc -l
```

Confirmar que el número de PNGs coincide con el número de slides del carrusel.
Si hay discrepancia → identificar qué slide faltó y recapturar.

**Verificación visual:** revisar cada PNG antes de declararlo listo:
- ¿Texto completo sin cortarse?
- ¿Colores de marca correctos?
- ¿Google Fonts renderizadas (no fallback)?
- ¿Foto legible con overlay?
- ¿Handle en el slide final?

Si algo falla → corregir el div en el HTML → recapturar solo ese slide.

---

## PASO 7 — Entregar el resultado

No se guarda nada en Drive ni en ninguna cuenta externa. Qué tan lejos llega
cada carrusel depende de `destino_resultado` (PASO 4):

**Si es "Chat":** solo mostrar cada PNG directamente en la conversación (leer
cada archivo de imagen para que se renderice inline) — no copiar a ninguna
carpeta permanente, los PNG quedan solo en el scratchpad como paso intermedio.

**Si es "Guardado en mi computador":** copiar los PNG a la carpeta confirmada
y NO mostrarlos inline — solo confirmar la ruta y el conteo.
```bash
mkdir -p "[destino]/[nombre-carrusel]"
cp [scratchpad]/[carrusel N]/slide-*.png "[destino]/[nombre-carrusel]/"
```

**Si es "Ambas":** hacer los dos pasos anteriores — copiar a la carpeta Y
mostrar cada PNG inline.

Si el usuario eligió modo **1x1**, entregar cada carrusel apenas esté listo:

> "✅ **Carrusel [tipo]** listo — [N] slides · Estilo [N] · [Nombre]
>
> [PNGs inline si el destino incluye chat]
> [Guardado en: `[destino]/[nombre-carrusel]/` si el destino incluye computador]
>
> ¿Lo aprobamos y seguimos con el siguiente?
> O dime qué ajustar antes de continuar."

Si eligió **todos de una**, entregar todos los carruseles completos al final,
uno detrás de otro, cada uno con su encabezado de tipo y estilo.

---

## PASO 8 — Ajustes posteriores

| Pedido | Acción |
|--------|--------|
| Texto de un slide | Editar el div → recapturar ese slide → mostrarlo de nuevo en el chat |
| Color o layout | Modificar CSS → recapturar afectados → mostrarlos de nuevo |
| Cambiar la foto | Elegir otra candidata → reemplazar en scratchpad → recapturar |
| Regenerar imagen Gemini | Ajustar prompt → regenerar → recapturar |
| Cambiar estilo de un carrusel | Cargar nuevo estilo de la biblioteca → regenerar todos sus slides |
| No gusta ningún estilo | → `lf-prompt-diseno-carrusel`, luego volver a pegar el prompt aquí |

---

## REGLAS

- **PASO 0 siempre primero, en silencio si todo está bien.** Nunca pedir el
  copy sin haber confirmado que Playwright y Nanobanana responden. Si falta
  Nanobanana, guiar la configuración paso a paso (ver PASO 0) y probarla con
  una imagen real antes de continuar — nunca solo asumir que ya quedó lista.
- No requiere ningún cliente cargado de antemano — el copy, los colores de
  marca y el handle se piden directamente en el chat en el PASO 1.
- Advertir si se repite el mismo estilo en varios carruseles.
- Si ningún estilo convence: redirigir a `lf-prompt-diseno-carrusel`.
- **Fotos: copiar al scratchpad local con nombre simple y usar ruta relativa en HTML.**
  Nunca rutas absolutas en `<img src>`.
- Aplicar `filter: contrast(1.02) saturate(1.05)` a todas las fotos.
- Las fotos conviven con el diseño — nunca están solas sin elementos del estilo.
- Para fotos + Banana: usar `gemini_edit_image` sobre la foto real, no generar desde cero.
- **Toda imagen Banana para un slide completo: 1080×1350px (4:5), sin excepción.**
  Fijar `set_aspect_ratio` a "4:5" antes de generar y verificar el tamaño real del
  archivo resultante. Nunca dejar pasar una imagen cuadrada o en otro formato.
- **El handle en los slides es siempre el que el usuario dio en el chat** — nunca
  un handle genérico ni el de otra marca. Si no lo dio, preguntarlo antes del PASO 6.
- **Preferir el skill `lf-render-carrusel`** para captura retina 2x con fonts correctas.
  Usar Playwright MCP como fallback.
- Esperar `document.fonts.ready` + 1.5s antes de capturar — las Google Fonts
  deben estar renderizadas o los slides quedan sin tipografía.
- Verificar el conteo de PNGs contra el número de slides antes de reportar listo.
- **El resultado se entrega según `destino_resultado`** (PASO 4: chat / carpeta
  del computador / ambas) — nunca asumir uno sin preguntar. Si es carpeta o
  ambas, el Escritorio (detectado según el sistema operativo) es el default,
  pero siempre se confirma antes de empezar. No se guarda nada en Drive ni en
  ninguna cuenta externa, y no se envían notificaciones externas (Slack u otras).
- **El PASO 3 (fotos) nunca se salta** — siempre presentar las 3 opciones
  (reales / generadas con IA / ninguna), incluso si el estilo elegido no usa
  fotos por defecto.
- Si `mcp__plugin_ghl-skills-fanforce_nanobanana__*` no está disponible cuando
  se necesita (fotos con IA o Motor Banana), ver "Si falta la API key de
  Nanobanana" en el PASO 6.4 antes de continuar — no simplemente omitir la
  imagen y seguir.
