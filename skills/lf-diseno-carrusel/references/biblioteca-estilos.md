# Biblioteca de Estilos de Carrusel — 40 estilos

> Copia local de la Guía Maestra de Carruseles (40 estilos · V3). Cada estilo trae
> descripción, tags de uso, características, paletas sugeridas y el prompt completo
> listo para copiar y pegar. Léela directamente en vez de navegar a la web — más
> rápido y no depende de conexión ni contraseña.
>
> **Todo lo que aparece entre `[corchetes]`** (tema, paleta, y especialmente
> `[@handle del cliente]` / `HANDLE:`) es un placeholder — reemplázalo siempre por
> el dato real del cliente activo en la sesión antes de usar el prompt. El handle
> nunca es genérico ni de otra marca.
>
> **Todo prompt que genere un slide completo debe pedir 1080×1350px (formato
> carrusel de Instagram, 4:5 vertical)** — ya viene así en cada prompt de esta
> guía; no lo quites ni lo cambies por otro tamaño.

---

## Los 3 motores

**MOTOR 1 — HTML/CSS**
Claude genera un `.html` completo. Cada slide es una pantalla con diseño real:
gradientes, glass, tipografía de Google Fonts, formas. Se abre en el navegador y
se captura cada slide.

**MOTOR 2 — BANANA (IMÁGENES)**
Claude genera cada slide como imagen PNG real (Gemini). Ideal cuando se quieren
fotografías, personas o escenas reales dentro del carrusel.

**MOTOR 3 — HÍBRIDO**
Banana genera las imágenes y se usan como fondos dentro de un HTML/CSS. Máximo
control visual.

## Los 5 datos para pedir un carrusel

1. **Motor:** HTML/CSS, Banana o Híbrido
2. **Estilo:** el nombre del estilo de esta guía
3. **Propósito:** tutorial, lista, historia, estadísticas…
4. **Tema:** de qué trata el carrusel
5. **Slides:** cuántos se quieren (recomendado 7-10)

---

## 01 — BOLD STATEMENT
**Tags:** Impacto inmediato · Autoridad · Ventas · `HTML/CSS`

Palabras gigantes, fondo sólido, sin imágenes. Impacto puro.

**Características:**
- Tipografía Display ultra bold — ocupa 70-80% del slide
- Máximo 3-5 palabras por slide
- Fondo color sólido saturado (puede variar por slide)
- Sin imágenes — la tipografía ES el diseño
- Emojis opcionales como acento visual

**Paletas sugeridas:**
- Negro `#000` + Amarillo eléctrico `#FFE600`
- Naranja intenso `#FF6B35` + Blanco
- Morado oscuro `#1A0033` + Blanco

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo BOLD STATEMENT:

TEMA: [tu tema aquí]
SLIDES: [ej: 8]
PALETA: [ej: fondo negro, texto amarillo #FFE600]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Bebas Neue para titulares, DM Sans para secundarios (Google Fonts)
- Mensaje corto por slide: máximo 5 palabras, tipografía gigante (mínimo 80px)
- Fondo sólido saturado, alto contraste con el texto
- Sin imágenes, solo tipografía y color
- Slide 1: hook de apertura impactante
- Slides 2-N: un punto por slide, ultra corto y directo
- Slide final: CTA simple ("Guárdalo 💾")
- HTML con slides en secuencia vertical para capturar pantalla
```

---

## 02 — MINIMALISTA LIMPIO
**Tags:** Coaches premium · Personal branding · Bienestar · `HTML/CSS`

Elegancia, espacio en blanco, serif. Lujo sin ruido visual.

**Características:**
- Serif elegante (Playfair Display) para titulares
- Sans fina (DM Sans Light) para cuerpo
- Mucho espacio en blanco — los elementos respiran
- Máximo 2 colores + 1 acento pequeño
- Líneas decorativas finas (1-2px) como acentos
- Numeración elegante: 01, 02, 03...

**Paletas sugeridas:**
- Crema `#FAF8F5` + Marrón oscuro + Terracota (acento)
- Blanco + Negro + Dorado `#C9A84C` (acento)
- Gris perla + Negro + Verde salvia

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo MINIMALISTA LIMPIO:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]
PALETA: [ej: fondo crema #FAF8F5, texto marrón oscuro, acento terracota #C17F5A]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: Playfair Display (titulares serif) + DM Sans (cuerpo) — Google Fonts
- Fondo claro (blanco, crema o gris muy suave)
- Mucho espacio en blanco — elementos que respiran, no llenan el slide
- Líneas decorativas finas (1-2px) bajo títulos o como separadores
- Numeración elegante ("01", "02") en pequeño, color acento
- Máximo 2-3 colores en todo el carrusel
- Slide 1: título del tema + subtítulo corto
- Slides 2-N: número + titular serif + 2-3 líneas DM Sans
- Slide final: frase de cierre + handle pequeño
- HTML con slides en secuencia vertical
```

---

## 03 — DARK NEÓN TECH
**Tags:** Marketing digital · Emprendimiento · Dinero · `HTML/CSS`

Fondo negro, texto que brilla. Premium, misterioso, futurista.

**Características:**
- Fondo negro `#000` o gris carbón `#0D0D0D`
- Texto principal en color neón (verde, lila, rosa, cyan)
- Efecto glow real con CSS `text-shadow` en múltiples capas
- Cards/badges con borde del color neón
- Tipografía bold moderna (Space Grotesk)

**Paletas sugeridas:**
- Verde neón `#39FF14` (tech, dinero)
- Lila neón `#BF5FFF` (premium, misterio)
- Rosa neón `#FF6B9D` (femenino premium)
- Cyan neón `#00FFFF` (futurista)

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo DARK NEÓN TECH:

TEMA: [tu tema aquí]
SLIDES: [ej: 8]
COLOR NEÓN: [verde #39FF14 / lila #BF5FFF / rosa #FF6B9D / cyan #00FFFF]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Space Grotesk bold — Google Fonts
- Fondo: negro #000000 o gris muy oscuro #0D0D0D
- Texto principal en el neón elegido con glow real:
  text-shadow: 0 0 10px [neón], 0 0 30px [neón], 0 0 60px [neón]40
- Texto cuerpo: blanco #FFF o gris claro #CCC
- Elementos: líneas finas en neón, badges con borde neón
- Slide 1: portada — hook en neón grande
- Slides 2-N: badge número en neón + titular + desarrollo en blanco
- Slide final: CTA en neón + handle
- HTML con slides en secuencia vertical
```

---

## 04 — EDITORIAL REVISTA
**Tags:** Personal branding premium · Liderazgo · `HTML/CSS`

Serif + Sans, columnas, numeración. Sofisticado como una portada.

**Características:**
- Contraste tipográfico fuerte: Serif grande + Sans pequeña
- Numeración como elemento de diseño visible
- Composición asimétrica — no todo centrado
- Color acento solo en detalles, nunca en bloques
- Líneas horizontales como estructura

**Paletas sugeridas:**
- Blanco + Negro + Vino `#8B0000`
- Blanco + Negro + Dorado `#C9A84C`
- Blanco + Negro + Azul royal `#1B3A6B`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo EDITORIAL REVISTA:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]
COLOR ACENTO: [vino #8B0000 / dorado #C9A84C / azul royal #1B3A6B]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: Playfair Display (titulares serif grandes) + Inter (cuerpo sans pequeña) — Google Fonts
- Estructura de revista: zonas de texto, líneas horizontales de separación, numeración visible
- Fondo blanco o crema muy suave
- Titular: mayúsculas o small-caps, serif grande
- Color acento solo en número, línea decorativa, o una palabra clave
- Composición asimétrica con jerarquía clara
- Slide 1: portada estilo cover de revista
- Slides 2-N: número grande (acento) + titular serif + desarrollo en sans
- Slide final: cierre editorial + handle
- HTML con slides en secuencia vertical
```

---

## 05 — PASTEL SOFT + EMOJI HERO
**Tags:** Bienestar · Educación · Comunidad · `HTML/CSS`

Emoji gigante como imagen. Fondos pastel, tipografía redondeada.

**Características:**
- Emoji gigante (150-200px) como elemento visual principal — reemplaza imagen
- Fondo pastel diferente por slide dentro de la misma paleta
- Tipografía redondeada (Poppins, Nunito)
- Badges/pills redondeadas para numeración

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo PASTEL SOFT con EMOJI HERO:

TEMA: [tu tema aquí]
SLIDES: [ej: 8]
PALETA: [ej: rosa #FFD1DC, lila #DCC6E0, menta #C8E6C9, melocotón #FFDAB9]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Poppins o Nunito redondeada — Google Fonts
- Emoji gigante (150-200px) como elemento principal de cada slide
- Fondo de cada slide: tono pastel diferente de la paleta
- Texto corto: máximo 2 líneas titular + 1-2 desarrollo
- Esquinas redondeadas en elementos internos
- Badge pequeño redondeado con número del tip
- Slide 1: portada — emoji grande + título
- Slides 2-N: emoji central + tip claro
- Slide final: emoji celebración + CTA amigable
- HTML con slides en secuencia vertical
```

---

## 06 — GRADIENTE FLUIDO
**Tags:** Lanzamientos · Marketing · Tecnología · `HTML/CSS`

El gradiente ES el diseño. Texto blanco, energía vibrante.

**Características:**
- Fondo: gradiente de 2-3 colores que cubre todo el slide
- Texto blanco con `text-shadow` sutil para legibilidad
- Formas geométricas semitransparentes opcionales
- El ángulo del gradiente puede variar por slide

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo GRADIENTE FLUIDO:

TEMA: [tu tema aquí]
SLIDES: [ej: 8]
GRADIENTE: [ej: morado #7B2D8B → rosa #FF6B9D / o elige tú]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: DM Sans o Montserrat bold — Google Fonts
- Fondo: CSS linear-gradient (varía el ángulo entre slides para dinamismo)
- Texto: blanco con text-shadow suave para legibilidad
- Círculos semitransparentes (rgba blanco 10-20%) como decoración de fondo
- Badge de número: redondeado blanco semi-transparente
- Slide 1: portada + título grande + subtítulo
- Slides 2-N: badge número + titular bold + 2-3 líneas desarrollo
- Slide final: CTA + handle
- HTML con slides en secuencia vertical
```

---

## 07 — GLASSMORPHISM PREMIUM
**Tags:** Tecnología · Fintech · Educación digital · `HTML/CSS`

Cards de vidrio sobre gradiente. Futurista, con profundidad real.

**Características:**
- Fondo: gradiente colorido brillante
- Card central: `backdrop-filter: blur(20px)`
- Borde del card: `1px solid rgba(255,255,255,0.3)`
- Círculos difuminados de colores en el fondo

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo GLASSMORPHISM PREMIUM:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]
GRADIENTE: [ej: azul #1B3A6B → morado #7B2D8B / o elige tú]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Inter — Google Fonts
- Fondo del slide: gradiente colorido intenso
- Card central con efecto glassmorphism real:
    background: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.3);
    border-radius: 24px;
    box-shadow: 0 8px 32px rgba(0,0,0,0.2);
- Texto dentro del card: blanco para titulares, rgba(255,255,255,0.85) para cuerpo
- Círculos difuminados (blur-circles) como elementos decorativos de fondo
- Slide 1: portada — card glassmorphism + título + subtítulo
- Slides 2-N: badge número + titular + desarrollo dentro del card
- Slide final: CTA + handle
- HTML con slides en secuencia vertical
```

---

## 08 — SCRAPBOOK / COLLAGE
**Tags:** Detrás de escenas · Marca personal · Historia · `HTML/CSS`

Elementos rotados, handwriting, post-its. Auténtico y humano.

**Características:**
- Elementos en ángulos distintos (±2° a ±5°)
- Mezcla Caveat (handwriting) + Poppins (legible)
- Fondo texturizado beige/crema simulado en CSS
- Bloques tipo post-it como fondo de partes del texto
- Cada slide tiene composición diferente

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo SCRAPBOOK / COLLAGE:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]
PALETA: [ej: beige, verde salvia #8FAF8A, terracota #C17F5A]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: Caveat (handwriting, Google Fonts) + Poppins (sans legible)
- Fondo: beige o crema con textura sutil de papel (CSS SVG noise o pattern)
- Rotaciones en elementos: transform: rotate(±2deg a ±5deg)
- Emojis como stickers decorativos, algunos rotados
- Subrayados y círculos decorativos en SVG inline (estilo a mano)
- Bloques de color tipo post-it (amarillo, rosa, verde pálido) bajo partes del texto
- Cada slide con composición diferente (no todas iguales)
- Slide 1: portada tipo nota personal con el tema
- Slides 2-N: composición asimétrica con el punto principal
- Slide final: nota de cierre + "guárdalo para después" + handle
- HTML con slides en secuencia vertical
```

---

## 09 — HEADLINE HERO
**Tags:** Estadísticas · Resultados · Autoridad numérica · `HTML/CSS`

El número ocupa todo el slide. Dato que golpea, texto que explica.

**Características:**
- Número/porcentaje: mínimo 180px, idealmente 220-280px
- Texto explicativo: 1 sola frase, debajo del número
- Tipografía: Bebas Neue o Anton para el número
- 1 color de acento destaca el número

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo HEADLINE HERO (dato gigante):

TEMA: [tu tema — datos, estadísticas, resultados]
SLIDES: [ej: 7]
PALETA: [ej: fondo blanco, número en naranja #FF6B35, texto secundario #444]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: Bebas Neue o Anton (número hero, 180-280px) + DM Sans (texto explicativo) — Google Fonts
- El número/porcentaje/dato: tipografía gigante, centrado, color de acento
- Texto explicativo: sans pequeña (18-24px), debajo del número, máximo 1 frase
- Fondo limpio (sólido o gradiente muy sutil)
- Línea o punto decorativo del color acento como separador
- Slide 1: portada con el dato más impactante
- Slides 2-N: 1 dato grande + explicación corta
- Slide final: síntesis o CTA
- HTML con slides en secuencia vertical
```

---

## 10 — SPLIT SCREEN
**Tags:** Tutoriales · Testimoniales · Pasos con ejemplo · `Banana + HTML/CSS`

Mitad imagen generada por IA, mitad texto. Equilibrado y visual.

**Características:**
- Paso 1: pedir las imágenes a Banana (Gemini AI)
- Paso 2: Claude construye el HTML con las imágenes insertadas
- División horizontal: imagen arriba / texto abajo (portrait)
- División vertical: imagen izquierda / texto derecha (más editorial)

**Prompt:**
```
Necesito un carrusel SPLIT SCREEN con imagen generada por IA.
Seguí estos dos pasos exactamente:

PASO 1 — GENERÁ LAS IMÁGENES (con Banana):
Generá [N] imágenes con este estilo visual: [describí el estilo]
Tema visual: [ej: "espacio de trabajo minimalista con laptop, luz natural"]
Formato: 1080x640px (mitad superior del slide portrait)

PASO 2 — GENERÁ EL HTML:
Con las imágenes generadas, creá el carrusel:
- Formato total del slide: 1080x1350px
- Cada slide: imagen arriba (640px) + área de texto abajo (710px)
- Tipografía: [elige fuente y estilo]
- Paleta del área de texto: [colores]
- Slide 1: portada (puede ser solo texto)
- Slides 2-N: split imagen + punto de contenido
- Slide final: CTA
- HTML con slides en secuencia vertical
```

---

## 11 — FULL BLEED ATMOSFÉRICO
**Tags:** Storytelling · Historia personal · Inspiración · `Banana + HTML/CSS`

Imagen de fondo total, overlay, texto encima. Cinematográfico.

**Características:**
- Imagen de Banana ocupa 100% del slide como fondo
- Overlay oscuro (rgba 40-60%) para legibilidad del texto
- Texto blanco, muy corto — la imagen hace el trabajo emocional
- Cada slide tiene imagen diferente que evoca la historia

**Prompt:**
```
Necesito un carrusel FULL BLEED ATMOSFÉRICO. Dos pasos:

PASO 1 — GENERÁ LAS IMÁGENES (con Banana):
Generá imágenes de fondo atmosféricas para cada slide:
- Slide 1 (portada): [describí la escena — ej: "amanecer sobre ciudad, tonos cálidos, cinematográfico"]
- Slide 2: [escena para ese punto]
- Slide 3: [escena siguiente]
[continuar por slide...]
Estilo: [cinematográfico / editorial / naturaleza / urbano]
Tonos: [cálido / frío / neutro / oscuro]
Formato: 1080x1350px

PASO 2 — GENERÁ EL HTML:
- Cada imagen como background-image del slide (100%, object-fit: cover)
- Overlay: rgba(0,0,0,0.45) sobre cada imagen
- Texto centrado, en blanco
- Tipografía: [Playfair Display serif / DM Sans bold]
- Máximo 2-3 líneas por slide
- Slide 1: portada con título principal
- Slides 2-N: frase corta con imagen evocadora de fondo
- Slide final: reflexión de cierre + CTA + handle
- HTML con slides en secuencia vertical
```

---

## 12 — MITOS VS REALIDAD
**Tags:** Autoridad · Educación · Desmentir creencias · `HTML/CSS`

Dos paletas opuestas alternan: oscuro (mito) vs claro (realidad).

**Características:**
- Slides MITO: fondo oscuro, badge ❌ en rojo, texto blanco
- Slides REALIDAD: fondo claro, badge ✅ en verde, texto oscuro
- Alternancia visual marcada entre tipos de slide

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo MITOS VS REALIDAD:

TEMA: [ej: "mitos sobre crear contenido en Instagram"]
PARES: [ej: 4 pares = 10 slides con portada y cierre]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: DM Sans bold titulares, DM Sans regular cuerpo — Google Fonts
- SLIDES DE MITO:
    * Fondo: gris carbón #1A1A1A o negro
    * Badge "MITO ❌" en rojo #c0392b arriba
    * Texto del mito en blanco, tamaño grande
- SLIDES DE REALIDAD:
    * Fondo: blanco o crema #FAF8F5
    * Badge "REALIDAD ✅" en verde #27ae60 arriba
    * Texto de la realidad en oscuro, mismo tamaño
- Portada impactante sobre el tema
- Alternancia: portada → Mito 1 → Realidad 1 → Mito 2 → Realidad 2... → CTA
- HTML con slides en secuencia vertical
```

---

## 13 — CHECKLIST INTERACTIVO
**Tags:** Diagnóstico · Guardar · Viralizar · `HTML/CSS`

Un ítem por slide con checkbox visual. Cierra con escala de resultado.

**Características:**
- Cada slide tiene 1 ítem con checkbox UI moderno grande
- Checkboxes marcados o vacíos según el diseño
- Slide final: escala de resultados (0-3 / 4-6 / 7+)

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo CHECKLIST INTERACTIVO:

TEMA: [ej: "señales de que tu estrategia de contenido no funciona"]
ÍTEMS: [ej: 8 ítems = 10 slides con portada y cierre]
COLOR DE ACENTO: [hex de tu color de marca]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Poppins o DM Sans — Google Fonts
- Fondo: blanco o gris muy claro #F5F5F5
- Cada slide de ítem:
    * Checkbox grande estilo UI moderno (cuadrado redondeado, 60x60px)
    * Marcado = ✓ en color de acento / vacío = borde gris
    * Badge pequeño con número del ítem
    * El ítem en tipografía grande y clara
    * 1 línea explicativa pequeña opcional
- Portada: hook + "¿cuántos de estos tienes?"
- Slides 2-N: un ítem por slide
- Slide final: escala de resultados (rangos + descripción de cada uno) + CTA
- HTML con slides en secuencia vertical
```

---

## 14 — FAQ TIPO CHAT
**Tags:** FAQ · Objeciones de venta · Conversacional · `HTML/CSS`

Burbujas de mensajería. Pregunta usuario ← → Respuesta marca.

**Características:**
- Simula interfaz de mensajería (WhatsApp/DM style)
- Burbuja pregunta: izquierda, gris, border-radius con esquina recta inferior izquierda
- Burbuja respuesta: derecha, color de marca, esquina recta inferior derecha
- Tipografía redondeada (Poppins, Nunito)

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo FAQ TIPO CHAT:

TEMA: [ej: "preguntas frecuentes sobre tu programa/producto"]
FAQs: [ej: 5 = 7 slides con portada y cierre]
COLOR DE MARCA (burbujas de respuesta): [hex]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Poppins o Nunito redondeada — Google Fonts
- Fondo: blanco o gris muy claro #F5F5F5
- Burbuja PREGUNTA:
    * Izquierda, background: #E5E5EA, texto oscuro, font-size 20px
    * border-radius: 18px 18px 18px 4px
- Burbuja RESPUESTA:
    * Derecha, background: [color de marca], texto blanco
    * border-radius: 18px 18px 4px 18px
- Portada: "Preguntas que me hacen todo el tiempo 💬"
- Slides 2-N: un par pregunta/respuesta por slide
- Slide final: invitación a preguntar más + CTA
- HTML con slides en secuencia vertical
```

---

## 15 — ANTES / DESPUÉS DRAMÁTICO
**Tags:** Testimoniales · Resultados · Ventas · `HTML/CSS`

Paleta fría/oscura (antes) vs cálida/vibrante (después). El contraste es el storytelling.

**Características:**
- Slides ANTES: fondo oscuro/frío, badge rojo, emojis de problema (😤 ❌)
- Slides DESPUÉS: fondo cálido/claro, badge verde, emojis de éxito (🚀 ✅)
- El contraste de color ES el storytelling visual
- Texto corto y directo en ambos tipos

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo ANTES/DESPUÉS DRAMÁTICO:

TEMA: [ej: "antes y después de aplicar una estrategia de contenido"]
ESTRUCTURA: [ej: 2-3 slides ANTES + 2-3 slides DESPUÉS + portada y cierre = ~8 slides]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: DM Sans bold — Google Fonts
- SLIDES "ANTES":
    * Fondo oscuro/frío: gris oscuro #1A1A2E o negro
    * Badge "ANTES" en rojo #c0392b arriba
    * Texto del problema en blanco o gris claro
    * Emojis de dificultad: 😤 😩 ❌ 😰
- SLIDES "DESPUÉS":
    * Fondo claro/cálido: blanco, crema #FFF8EE o color de marca suave
    * Badge "DESPUÉS" en verde #27ae60 arriba
    * Texto del resultado en oscuro
    * Emojis de éxito: 🚀 ✅ 🎯 💰 🙌
- Portada que anticipa: "De [punto A] a [punto B]"
- Estructura: portada → ANTES (2-3 slides) → DESPUÉS (2-3 slides) → Cómo ocurrió → CTA
- Slide final: cómo acceder al resultado
- HTML con slides en secuencia vertical
```

---

## 16 — BRUTALIST / SWISS GRID
**Tags:** Opiniones fuertes · Posicionamiento experto · `HTML/CSS`

Grilla cruda, tipografía condensada, cero adornos. Se ve hecho por diseñador, no por plantilla.

**Características:**
- Fondo blanco roto `#F4F1EA` o blanco puro, sin gradientes ni sombras
- Líneas hairline negras (1px) que dividen el slide en grilla visible
- Tipografía condensada gigante alineada a la izquierda
- Un solo bloque de color puro por slide
- Número de slide impreso enorme en una esquina

**Paletas sugeridas:**
- Blanco roto `#F4F1EA` + Negro `#111` + Naranja `#FF3B00`
- Blanco + Negro + Azul eléctrico `#0000FE`
- Blanco roto + Negro + Rojo `#E5322D`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo BRUTALIST / SWISS GRID:

TEMA: [tu tema aquí]
SLIDES: [ej: 8]
COLOR ACENTO: [naranja #FF3B00 / azul #0000FE / rojo #E5322D]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Archivo Black o Anton (condensada, gigante) + Space Mono para etiquetas — Google Fonts
- Fondo blanco roto #F4F1EA, sin sombras ni esquinas redondeadas ni gradientes
- Líneas hairline negras (1px solid #111) que forman una grilla visible
- Titular flush-left (alineado a la izquierda), nunca centrado
- Un solo bloque/rectángulo de color acento por slide
- Número de slide gigante (120px+) impreso en una esquina
- Slide 1: portada con el hook en condensada masiva
- Slides 2-N: un punto por slide, número grande + titular flush-left
- Slide final: CTA directo + handle
- HTML con slides en secuencia vertical
```

---

## 17 — RECIBO / TICKET / BOARDING PASS
**Tags:** Stack de valor · Listas · Itinerarios · `HTML/CSS`

Un objeto falso por slide: recibo, ticket o pase. Tangible y screenshot-eable.

**Características:**
- Recibo: tira monospace, divisores punteados, borde dentado (mask), código de barras CSS, línea "TOTAL"
- Boarding pass: 2 paneles con línea perforada y muescas circulares
- Fondo kraft o papel térmico apagado
- Objeto reconocible al instante = más engagement

**Paletas sugeridas:**
- Papel térmico `#FBFBF7` + Tinta `#1A1A1A` + fondo kraft `#D9CDB8`
- Blanco recibo + Negro + sello rojo `#C0392B`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo RECIBO / TICKET / BOARDING PASS:

TEMA: [tu tema — ej: "lo que incluye mi programa"]
SLIDES: [ej: 7]
OBJETO: [recibo / ticket / boarding pass]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Courier Prime o JetBrains Mono (monospace) — Google Fonts
- Fondo kraft #D9CDB8 o papel térmico apagado
- Objeto falso centrado con detalles skeuomórficos reales:
  * Recibo: divisores punteados, borde inferior DENTADO con CSS mask (triángulos repetidos), código de barras con repeating-linear-gradient, línea "TOTAL"
  * Boarding pass: 2 paneles con línea perforada punteada y muescas circulares (::before/::after)
- Slide 1: portada — objeto presentando el tema ("TU TICKET A [resultado]")
- Slides 2-N: cada ítem como línea de recibo
- Slide final: "TOTAL" = el resultado/CTA + handle
- HTML con slides en secuencia vertical
```

---

## 18 — CODE EDITOR / TERMINAL
**Tags:** IA · Tech · Prompts · `HTML/CSS`

Chrome de IDE con sintaxis de colores. Credibilidad insider para contenido de IA y tech.

**Características:**
- Ventana oscura tipo Dracula `#282A36` o Catppuccin `#1E1E2E`
- Barra de título con 3 luces de semáforo + nombre de archivo
- Gutter con números de línea + resaltado de sintaxis (keywords rosa, strings verde)
- Cursor de bloque parpadeante

**Paletas sugeridas:**
- Dracula: `#282A36` + rosa `#FF79C6` + verde `#50FA7B`
- Catppuccin: `#1E1E2E` + lila `#CBA6F7` + verde `#A6E3A1`
- Terminal: negro `#0C0C0C` + verde fósforo `#39FF14`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo CODE EDITOR / TERMINAL:

TEMA: [tu tema — ej: "5 prompts de IA que uso a diario"]
SLIDES: [ej: 8]
TEMA DE COLOR: [Dracula #282A36 / Catppuccin #1E1E2E / Terminal #0C0C0C]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: JetBrains Mono o Fira Code (monospace) — Google Fonts
- Cada slide = ventana de editor/terminal:
  * Barra de título con 3 luces (rojo #FF5F56, amarillo #FFBD2E, verde #27C93F) + nombre de archivo
  * Gutter con números de línea (#6272A4)
  * Resaltado de sintaxis: keywords rosa #FF79C6, strings verde #50FA7B, comentarios gris
  * Cursor de bloque parpadeante
- Cada punto como línea de "código" o // comentario
- Slide 1: archivo abriéndose con el título como comentario destacado
- Slides 2-N: una "función"/bloque por punto
- Slide final: salida tipo > guardado ✓ + CTA + handle como @comment
- HTML con slides en secuencia vertical
```

---

## 19 — Y2K / CHROME RETRO-FUTURISTA
**Tags:** Tendencias · Pop culture · Lanzamientos · `HTML/CSS`

Cromo líquido sobre fondo holográfico. Nostalgia de los 2000s, energía Gen-Z.

**Características:**
- Texto en cromo líquido (gradient plateado clip a texto + drop-shadow)
- Fondo holográfico iridiscente (conic/linear gradient cyan-magenta-lima)
- Sprites de estrellas y destellos (✦ ✧), blobs de glow
- Fuentes tech/bubble, energía loud

**Paletas sugeridas:**
- Cromo plata + fondo holográfico cyan/magenta/lima
- Cromo + azul eléctrico `#0066FF` con blobs rosa `#FF6EC7`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo Y2K / CHROME RETRO-FUTURISTA:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Orbitron o Chakra Petch (titulares) + Baloo 2 (texto bubble) — Google Fonts
- Titular en CROMO LÍQUIDO: linear-gradient(180deg,#fff,#c8c8c8,#888,#fff) con background-clip:text + color:transparent + drop-shadow
- Fondo HOLOGRÁFICO: conic/linear-gradient iridiscente (cyan #00FFFF, magenta #FF00FF, lima #CCFF00) + blobs difuminados
- Sprites ✦ ✧ y destellos, glow blobs (filter: blur)
- Slide 1: portada — título cromado gigante sobre holográfico
- Slides 2-N: un punto por slide, titular cromado + texto bubble
- Slide final: CTA cromado + handle con sparkles
- HTML con slides en secuencia vertical
```

---

## 20 — ACID / MAXIMALISTA
**Tags:** Hooks atrevidos · Creativo · Alta energía · `HTML/CSS`

Neón que vibra, fuentes chocando, caos organizado. Lo más ruidoso del feed.

**Características:**
- Neón de alto contraste que "vibra" (lima ácida sobre negro)
- 4-6 fuentes chocando en un mismo slide
- Tipografía rotada, superpuesta, distintos tamaños
- Layout sticker-bomb, grano/halftone opcional

**Paletas sugeridas:**
- Lima ácida `#CCFF00` + Negro `#1A1A1A` + Magenta `#FF00A8`
- Magenta `#FF00A8` + Amarillo `#FFEB00` + Negro

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo ACID / MAXIMALISTA:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]
PALETA: [lima #CCFF00 + negro / magenta #FF00A8 + amarillo #FFEB00]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías (mezcla 4-6 chocando): Anton + Bungee + Monoton + Archivo Black + un script tipo Pacifico — Google Fonts
- Colores de alto contraste que vibran (lima ácida sobre negro)
- Tipografía rotada (±5° a ±15°), superpuesta, tamaños chocando
- Layout sticker-bomb (caos organizado) + grano/halftone sutil opcional
- Slide 1: portada — hook gritado en máximo contraste y choque tipográfico
- Slides 2-N: un punto por slide manteniendo la energía
- Slide final: CTA atrevido + handle
- HTML con slides en secuencia vertical
```

---

## 21 — BENTO GRID
**Tags:** Features · Resúmenes · Stacks · `HTML/CSS`

Mosaico modular de tiles tipo keynote de Apple. Escaneable, premium, SaaS-grade.

**Características:**
- Grilla de tiles desiguales con esquinas redondeadas (CSS grid + span)
- Cada tile = una micro-idea (stat, ícono, etiqueta, mini chart)
- Fondo neutro + tiles tonales + 1 tile de acento
- Empaca mucho valor sin saturar = alto guardado

**Paletas sugeridas:**
- Fondo `#F5F5F7` + tiles blancos + acento azul `#2563EB`
- Dark: fondo `#0E0E12` + tiles `#1A1A22` + cyan `#22D3EE`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo BENTO GRID:

TEMA: [tu tema — ej: "todo lo que incluye tu programa/producto"]
SLIDES: [ej: 7]
PALETA: [claro #F5F5F7 + azul #2563EB / dark #0E0E12 + cyan]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Inter, Manrope o Geist — Google Fonts
- Cada slide = grilla CSS de tiles DESIGUALES (grid + grid-column/grid-row span), gap 12px, border-radius 20px
- Cada tile: un stat grande, un ícono/emoji, una etiqueta o un mini gráfico
- Fondo neutro + tiles tonales + 1 tile de acento por slide
- El tile más importante ocupa más espacio
- Slide 1: portada — tile grande con título + tiles preview
- Slides 2-N: agrupa 3-6 micro-ideas en bento
- Slide final: tile CTA destacado + handle
- HTML con slides en secuencia vertical
```

---

## 22 — DATA-VIZ / INFOGRAFÍA
**Tags:** Resultados · Casos de estudio · Prueba · `HTML/CSS`

Gráficos CSS reales: barras, anillos, callouts. El dato como prueba (distinto al Dato Gigante).

**Características:**
- Gráficos construidos en CSS: barras, donuts (conic-gradient), callouts con flecha
- Un color de acento + escala de grises
- Ejes, gridlines y etiquetas de datos
- Cada slide = un insight visualizado distinto

**Paletas sugeridas:**
- Blanco + grises + acento azul `#2563EB`
- Blanco + grises + acento verde `#16A34A` (crecimiento)

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo DATA-VIZ / INFOGRAFÍA:

TEMA: [tu tema — idealmente datos, resultados, estadísticas]
SLIDES: [ej: 7]
COLOR ACENTO: [azul #2563EB / verde #16A34A / cyan #22D3EE]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: IBM Plex Sans o Inter (números tabulares) — Google Fonts
- Cada slide visualiza UN insight con gráfico en CSS puro:
  * Barras (divs con height) + etiquetas de valor
  * Anillo/donut con conic-gradient + % al centro
  * Callout: número grande + flecha ▲/▼ + delta
  * Barras comparativas (antes vs después)
- Ejes y gridlines sutiles, etiquetas visibles, 1 color de acento + grises
- Slide 1: portada — el dato más fuerte graficado
- Slides 2-N: un insight visualizado por slide
- Slide final: síntesis + CTA + handle
- HTML con slides en secuencia vertical
```

---

## 23 — NEWSPAPER / PRINT
**Tags:** Anuncios · Storytelling · Thought-leadership · `HTML/CSS`

Masthead, columnas justificadas y halftone. Encuadre breaking news, creíble y nostálgico.

**Características:**
- Fondo papel envejecido `#F2EFE6`, toda tinta negra sobre crema
- Masthead con nombre + línea hairline + dateline
- Cuerpo en columnas justificadas (`column-count`)
- Foto falsa con halftone (radial-gradient de puntos) + pull-quotes

**Paletas sugeridas:**
- Papel `#F2EFE6` + Tinta negra (clásico)
- Papel + tinta negra + sello rojo `#B0271E` "EXTRA"

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo NEWSPAPER / PRINT:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]
NOMBRE DEL PERIÓDICO: [ej: "EL DIARIO"]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: Playfair Display (masthead) + PT Serif o Lora (cuerpo) + Oswald (kickers) — Google Fonts
- Fondo papel envejecido #F2EFE6, tinta negra sobre crema
- Slide 1: PRIMERA PLANA — masthead con nombre, línea hairline, titular enorme serif, dateline con fecha
- Slides 2-N: kicker mayúsculas + titular serif + cuerpo en columnas justificadas (column-count:2)
- Foto falsa con HALFTONE (radial-gradient de puntos) + un pull-quote con líneas
- Slide final: "sección de avisos" con CTA + handle como pie
- HTML con slides en secuencia vertical
```

---

## 24 — NOTES-APP / TWEET SCREENSHOT
**Tags:** Hot takes · Relatable · Quotes · `HTML/CSS`

UI nativa de Notas de iOS o de un post de X. Se siente auténtico, no "diseñado".

**Características:**
- Mock pixel-perfect de Notas iOS (crema + acento amarillo) o post de X
- Tarjeta con avatar, @handle, texto y fila de íconos
- A veces apilado como hilo
- Se ve nativo = más confianza y share

**Paletas sugeridas:**
- Notas iOS: `#FFFDF4` + texto `#1C1C1E` + amarillo `#FFD60A`
- Tweet: blanco + `#0F1419` + azul `#1D9BF0` + gris `#536471`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo NOTES-APP / TWEET SCREENSHOT:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]
FORMATO: [Notas de iOS / post de X (Twitter)]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Inter o system-ui para imitar SF Pro — Google Fonts
- Imita la UI NATIVA pixel-perfect:
  * Notas iOS: fondo crema #FFFDF4, barra con acción amarilla #FFD60A, título bold + cuerpo + timestamp gris
  * Post de X: tarjeta blanca radius 16px, avatar circular + nombre bold + @handle gris + texto + fila comentario/retweet/like/vistas en gris #536471
- Centra la tarjeta sobre fondo suave
- Texto auténtico y conversacional, no publicitario
- Slide 1: portada — la nota/tweet con el hook principal
- Slides 2-N: una nota/tweet por slide (o apilados como hilo)
- Slide final: nota/tweet de cierre con CTA + handle real
- HTML con slides en secuencia vertical
```

---

## 25 — PASO A PASO CON PROGRESS BAR
**Tags:** Tutoriales · Frameworks · Metodologías · `HTML/CSS`

Pasos numerados con barra de progreso persistente. El efecto Zeigarnik empuja al final.

**Características:**
- Indicador de progreso persistente: barra que se llena o stepper de nodos
- Número de paso en chip de color + título corto accionable
- Etiqueta "Paso N de [total]"
- Loop de finalización = más swipe-through

**Paletas sugeridas:**
- Fondo `#FAFAFA` + acento violeta `#6D28D9`
- Blanco + acento naranja `#FF6B35`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo PASO A PASO CON PROGRESS BAR:

TEMA: [tu tema — ej: "cómo crear tu primer reel viral en 5 pasos"]
PASOS: [ej: 5 pasos = 7 slides con portada y cierre]
COLOR ACENTO: [violeta #6D28D9 / naranja #FF6B35 / cyan #22D3EE]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Sora u Outfit (titulares) + Inter (cuerpo) — Google Fonts
- Indicador de progreso PERSISTENTE en cada slide de paso:
  * Opción A: barra superior que se llena (width 20% → 40% → 60% ...)
  * Opción B: stepper de nodos (completados llenos, actual con borde, siguientes vacíos) unidos por línea
- Etiqueta "Paso N de [total]" + número grande en chip del acento
- Título corto accionable + 1-2 líneas de apoyo, fondo neutro
- Slide 1: portada — promesa del resultado + "en N pasos" (barra 0%)
- Slides 2-N: un paso por slide con la barra/stepper avanzando
- Slide final: barra 100% + "lo lograste" + CTA + handle
- HTML con slides en secuencia vertical
```

---

## 26 — TIER LIST (S–F)
**Tags:** Opiniones · Rankings · Engagement · `HTML/CSS`

Rankea cualquier cosa en filas S/A/B/C. El formato más debatido y guardado del feed.

**Características:**
- Filas de colores: S rojo/rosa, A naranja, B amarillo, C verde, etc.
- Etiqueta de letra grande a la izquierda + ítems en chips a la derecha
- Tipografía condensada (Anton) para las letras, Inter para los chips
- Fondo oscuro para que los colores de tier vibren
- Invita a debatir = comentarios ('¿dónde pondrías X?')

**Paletas sugeridas:**
- Fondo `#15161B` + S `#FF4D6D` / A `#FF9F45` / B `#FFD23F` / C `#4EC2A8`
- Fondo blanco + tiers pastel para nicho bienestar/lifestyle

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo TIER LIST (S–F):

TEMA: [qué vas a rankear — ej: "formatos de contenido que más venden"]
SLIDES: [ej: 6]
NIVELES: [ej: S, A, B, C — o los que necesites]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Anton o Archivo Black (letras de tier) + Inter (chips de ítems) — Google Fonts
- Fondo oscuro #15161B para que los colores de cada tier resalten
- Cada fila: etiqueta de letra grande a la izquierda con fondo de color (S rojo #FF4D6D, A naranja #FF9F45, B amarillo #FFD23F, C verde #4EC2A8) + ítems en chips a la derecha
- Slide 1: portada — "EL RANKING DEFINITIVO DE [tema]" + tabla preview
- Slides 2-N: construye o explica un tier por slide (por qué cada cosa está donde está)
- Slide final: tu opinión + "¿en qué tier pondrías ___?" + CTA + handle
- HTML con slides en secuencia vertical
```

---

## 27 — BUSCADOR / GOOGLE
**Tags:** SEO de mente · Dolores reales · Relatable · `HTML/CSS`

La barra de Google con autocompletado. El hook ES la pregunta que tu audiencia ya escribe.

**Características:**
- Logo multicolor de buscador + barra redondeada con sombra
- Cursor parpadeante dentro de la búsqueda
- Dropdown de autocompletado con sugerencias (la fila destacada es el tema)
- Tipografía system/Inter para imitar la UI real
- El autocompletado = los pensamientos de tu cliente ideal

**Paletas sugeridas:**
- Blanco + azul `#4285F4` / rojo `#EA4335` / amarillo `#FBBC05` / verde `#34A853`
- Dark mode: fondo `#202124` + texto claro + sugerencias `#303134`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo BUSCADOR / GOOGLE:

TEMA: [la búsqueda central — ej: "cómo crear contenido que venda"]
SLIDES: [ej: 7]
MODO: [claro / dark mode]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Inter o Arial para imitar la UI real — Google Fonts
- Slide 1 (portada): logo multicolor + barra de búsqueda redondeada (border 1px #dfe1e5, sombra suave) con cursor parpadeante + dropdown de autocompletado; la sugerencia destacada (fondo gris claro) es tu tema, las otras 2-3 son variantes reales que tu audiencia busca
- Slides 2-N: cada sugerencia se convierte en un punto desarrollado (puedes mostrar una 'página de resultados' o una tarjeta de respuesta)
- Texto en negrita solo en la parte clave de cada sugerencia
- Slide final: barra con tu CTA escrito como búsqueda + handle
- HTML con slides en secuencia vertical
```

---

## 28 — SPOTIFY / NOW PLAYING
**Tags:** Mood · Branding · Lifestyle · `HTML/CSS`

La pantalla de reproducción con tu mensaje como canción. Nostálgico y altamente shareable.

**Características:**
- Carátula cuadrada con sombra + gradiente de fondo que baja a negro
- Título de 'canción' + 'artista' alineados a la izquierda
- Barra de progreso con tiempos (1:48 / -2:32)
- Controles: anterior, play circular blanco, siguiente
- Cada slide = un 'track' de una playlist temática

**Paletas sugeridas:**
- Gradiente verde `#1E6F50` → negro + texto blanco/gris `#b3b3b3`
- Gradiente de la carátula al fondo (extrae el color dominante)

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo SPOTIFY / NOW PLAYING:

TEMA: [la 'playlist' — ej: "7 hábitos para creadores constantes"]
SLIDES: [ej: 8]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Inter (semibold/bold) imitando la UI — Google Fonts
- Fondo: gradiente que arranca en un color y baja a negro (#0a0a0a)
- Cada slide = pantalla de reproducción:
  * Carátula cuadrada (gradiente o emoji grande) con sombra fuerte
  * Título de la 'canción' (tu punto) en blanco bold + 'artista' ([@handle del cliente] o subtítulo) en gris #b3b3b3
  * Barra de progreso con relleno blanco + tiempos a los lados
  * Controles ⏮ ▶/⏸ ⏭ (play en círculo blanco)
- Slide 1: portada de la playlist (título + 'N canciones')
- Slides 2-N: un track por slide con su mensaje
- Slide final: 'añade a tu biblioteca' = CTA + handle
- HTML con slides en secuencia vertical
```

---

## 29 — PINTEREST / MOODBOARD
**Tags:** Aspiracional · Nichos visuales · Inicio de año · `HTML/CSS`

Mosaico tipo masonry con barra de búsqueda. El 'vision board' que todas quieren guardar.

**Características:**
- Pill de búsqueda gris arriba con el tema del board
- Grilla masonry (columnas con alturas desiguales)
- Cada tile con gradiente/imagen + etiqueta corta abajo
- Estética suave, mucha saturación de color por tile
- Formato perfecto para vision boards y aesthetics de nicho

**Paletas sugeridas:**
- Fondo blanco + tiles con gradientes vibrantes variados
- Tonos tierra/crema para nicho lifestyle premium

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo PINTEREST / MOODBOARD:

TEMA: [el board — ej: "vision board de marca personal"]
SLIDES: [ej: 7]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Inter — Google Fonts
- Fondo blanco; arriba una pill de búsqueda gris #efefef con el tema escrito
- Grilla masonry: usa CSS columns (3 columnas) con tiles de alturas distintas (break-inside: avoid), border-radius 12px, gap 8px
- Cada tile: gradiente de color (o imagen si usas Banana) + etiqueta corta en blanco abajo
- Slide 1: portada — board completo como mosaico
- Slides 2-N: haz zoom a un 'pin' y desarrolla esa idea (1 concepto por slide)
- Slide final: 'guarda este board' = CTA + handle
- HTML con slides en secuencia vertical
- (Opcional motor Híbrido: pide las imágenes de los tiles a Banana primero)
```

---

## 30 — DICCIONARIO / DEFINICIÓN
**Tags:** Posicionamiento · Conceptos · Quotes · `HTML/CSS`

Una palabra, su definición y un ejemplo. Resignifica un concepto y suena a autoridad.

**Características:**
- Palabra gigante en serif + transcripción fonética en cursiva
- Tipo de palabra (sustantivo, verbo…) en cursiva de color acento
- Definición numerada + frase de ejemplo en cursiva
- Fondo papel crema, todo serif editorial
- Ideal para redefinir términos de tu nicho a tu favor

**Paletas sugeridas:**
- Papel `#FBF9F4` + tinta `#1a1a1a` + acento vino `#b04030`
- Blanco + negro + acento azul tinta `#1B3A6B`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo DICCIONARIO / DEFINICIÓN:

TEMA: [la palabra/concepto a redefinir — ej: "constancia"]
SLIDES: [ej: 6]
ACENTO: [vino #b04030 / azul tinta #1B3A6B]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: Playfair Display (la palabra, 900) + PT Serif o Lora (definición, cursivas) — Google Fonts
- Fondo papel crema #FBF9F4, todo en serif como una entrada de diccionario
- Estructura: palabra gigante + /transcripción fonética/ en cursiva + tipo de palabra (sustantivo/verbo) en cursiva de color acento + línea fina + definición numerada + frase de ejemplo en cursiva gris
- Slide 1: la palabra principal con tu definición resignificada
- Slides 2-N: definiciones secundarias, sinónimos, 'no confundir con…', ejemplos
- Slide final: tu marca como la definición viva del concepto + CTA + handle
- HTML con slides en secuencia vertical
```

---

## 31 — HIGHLIGHTER / NOTAS ESTÉTICAS
**Tags:** Educación · Tips · Femenino premium · `HTML/CSS`

Texto limpio con subrayados de marcador y notas a mano. El look 'studygram' que se guarda.

**Características:**
- Subrayado tipo marcador en las palabras clave (gradiente al 55% de altura)
- Mezcla Caveat (notas a mano) + Nunito (cuerpo redondeado y limpio)
- Acentos sueltos: estrellitas, flores, 'guárdalo' a mano
- Fondo casi blanco, papel suave
- Highlights de 2-3 colores pastel (amarillo, rosa, menta)

**Paletas sugeridas:**
- Fondo `#FCFBF7` + highlights amarillo `#FFE26B` / rosa `#FFC2D9` / menta `#B8EBD0`
- Crema + highlights lila y durazno para lifestyle

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo HIGHLIGHTER / NOTAS ESTÉTICAS:

TEMA: [tu tema — ej: "5 cosas que aprendí creando contenido"]
SLIDES: [ej: 7]
HIGHLIGHTS: [amarillo #FFE26B / rosa #FFC2D9 / menta #B8EBD0]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: Nunito (cuerpo y títulos, 800) + Caveat (notas a mano) — Google Fonts
- Fondo casi blanco #FCFBF7 (papel suave)
- Subrayado de marcador en las palabras CLAVE: background: linear-gradient(180deg,transparent 55%,[color] 55%); aplicado solo a esas palabras (alterna colores)
- Acentos a mano en Caveat: una 'kicker' arriba ('guárdalo para después ✦'), estrellitas/flores sueltas, rotaciones leves
- Slide 1: portada — título con 2 palabras resaltadas
- Slides 2-N: una idea por slide, resaltando solo lo esencial
- Slide final: nota a mano de cierre + CTA + handle
- HTML con slides en secuencia vertical
```

---

## 32 — CLAYMORPHISM / 3D SUAVE
**Tags:** Apps · Bienestar · Comunidad · `HTML/CSS`

Formas infladas tipo plastilina con sombras suaves. Tierno, táctil, muy actual.

**Características:**
- Elementos 'inflados' con doble sombra (clara y oscura) + inset
- Esferas/botones/badges redondeados de aspecto plástico
- Fondo neutro frío para que las sombras se lean
- Tipografía redondeada (Baloo 2, Poppins)
- Paleta dulce: lila, rosa, durazno

**Paletas sugeridas:**
- Fondo `#E0E5F2` + lila `#C8B6FF` + rosa `#FF8FAB`
- Fondo crema + menta y coral suaves

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo CLAYMORPHISM / 3D SUAVE:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]
PALETA: [lila #C8B6FF + rosa #FF8FAB sobre fondo #E0E5F2]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Baloo 2 o Poppins (redondeada) — Google Fonts
- Fondo neutro frío (#E0E5F2) para que las sombras claymorphism se lean
- Efecto clay en cada elemento (badges, esferas, botones):
    box-shadow: 8px 8px 20px [sombra-oscura], -8px -8px 20px #ffffff, inset 4px 4px 8px rgba(255,255,255,.5), inset -4px -4px 8px rgba(0,0,0,.08);
    border-radius generoso (50% en orbes, 18-24px en cards)
- Un 'orbe' o ícono inflado como elemento central por slide
- Tipografía redondeada, colores dulces (lila, rosa, durazno)
- Slide 1: portada con título + orbe grande
- Slides 2-N: un punto por slide con su elemento clay
- Slide final: botón clay de CTA + handle
- HTML con slides en secuencia vertical
```

---

## 33 — RISOGRAPH / RETRO PRINT
**Tags:** Creativo · Marca con carácter · Cultura · `HTML/CSS`

Duotono impreso con grano y tintas que se superponen. Se ve hecho a mano, de diseñador.

**Características:**
- 2-3 tintas planas que se superponen con `mix-blend-mode: multiply`
- Textura de grano/puntos sutil encima de todo
- Bloques de color con leve 'desregistro' (offset)
- Tipografía pesada (Archivo Black) + grotesque para apoyo
- Paleta limitada y saturada (azul + rosa + crema)

**Paletas sugeridas:**
- Crema `#F3ECDD` + azul riso `#2B3FE0` + rosa `#FF5C8A`
- Crema + verde riso `#00A95C` + naranja `#FF6C2F`

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo RISOGRAPH / RETRO PRINT:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]
TINTAS: [azul #2B3FE0 + rosa #FF5C8A sobre crema #F3ECDD]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: Archivo Black (titulares) + Space Grotesk (apoyo) — Google Fonts
- Fondo crema; usa 2-3 tintas planas saturadas
- Las formas/bloques de color se superponen con mix-blend-mode: multiply (donde se cruzan, mezclan)
- Textura de grano encima de todo: ::before con radial-gradient de puntos a baja opacidad (.06)
- Un bloque de color grande con titular en negativo (color crema sobre tinta) + un 'blob' que se superpone
- Slide 1: portada con titular masivo en negativo
- Slides 2-N: un punto por slide manteniendo la paleta de tintas
- Slide final: CTA en bloque de tinta + handle
- HTML con slides en secuencia vertical
```

---

## 34 — VHS / GLITCH RETRO
**Tags:** Nostalgia · Tendencias · Alta energía · `HTML/CSS`

Cinta de los 90 con scanlines, RGB split y timestamp REC. Nostalgia analógica, energía Gen-Z.

**Características:**
- Scanlines (líneas horizontales) sobre todo el slide
- Texto con efecto glitch: doble sombra magenta/cyan desplazada
- HUD de cámara: 'REC ●', timestamp, 'SP', 'PLAY ▶'
- Fondo negro azulado, tipografía pixel (VT323) en el HUD
- Estética found-footage de los 90s/2000s

**Paletas sugeridas:**
- Negro `#0a0a12` + glitch magenta `#FF00C1` / cyan `#00FFF0`
- Negro + verde fósforo para look de cámara nocturna

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo VHS / GLITCH RETRO:

TEMA: [tu tema aquí]
SLIDES: [ej: 7]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: VT323 (HUD pixel) + Space Grotesk bold (titulares) — Google Fonts
- Fondo negro azulado #0a0a12
- Scanlines en todo el slide: ::before con repeating-linear-gradient de líneas horizontales sutiles
- Titular con efecto GLITCH: text-shadow: 2px 0 #FF00C1, -2px 0 #00FFF0
- HUD superior: 'REC ●' en rojo + 'SP · 00:24' a la derecha; HUD inferior: '▶ PLAY' + año/fecha en cyan
- Slide 1: portada — título glitcheado bajo el HUD REC
- Slides 2-N: un punto por slide manteniendo el HUD y los scanlines
- Slide final: 'STOP ■' + CTA + handle
- HTML con slides en secuencia vertical
```

---

## 35 — MEME / IMPACT
**Tags:** Relatable · Humor · Alcance · `HTML/CSS`

Texto Impact arriba y abajo sobre una imagen. El formato más relatable y compartible que existe.

**Características:**
- Tipografía Impact/Anton en mayúsculas con contorno negro
- Texto arriba (setup) y abajo (remate) sobre la imagen
- Imagen central (gradiente, emoji gigante o foto de Banana)
- Cero diseño 'bonito' — la fuerza está en lo relatable
- Perfecto para hooks de humor que rompen el feed

**Paletas sugeridas:**
- Negro + texto blanco con contorno (meme clásico)
- Cualquier imagen + texto Impact blanco contorneado

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo MEME / IMPACT:

TEMA: [el ángulo de humor — ej: "las excusas que me ponía para no publicar"]
SLIDES: [ej: 7]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Anton (sustituto de Impact) en MAYÚSCULAS con contorno negro (text-shadow en 4 direcciones) — Google Fonts
- Cada slide = un meme: texto arriba (setup) + imagen central + texto abajo (remate)
- Imagen central: gradiente, emoji gigante (🗿😭💀) o foto generada por Banana
- Mantén el texto corto, hablado, relatable — nada publicitario
- Slide 1: el meme más fuerte como portada
- Slides 2-N: un meme por slide siguiendo el hilo
- Slide final: rompe el formato con el mensaje real + CTA + handle
- HTML con slides en secuencia vertical
- (Opcional Híbrido: genera las imágenes con Banana primero)
```

---

## 36 — CALENDARIO / PLANNER
**Tags:** Rutinas · Planificación · Hábitos · `HTML/CSS`

Una cuadrícula de mes o agenda semanal. Convierte tu método en un plan visual que se guarda.

**Características:**
- Cuadrícula de 7 columnas con días + encabezado de mes
- Días marcados (color acento) y puntos para 'día de acción'
- Nota al pie con la leyenda del plan
- Tipografía limpia (Sora + Inter)
- Ideal para retos, rutinas y 'planea conmigo'

**Paletas sugeridas:**
- Blanco + acento naranja `#FF6B35`
- Crema + acento verde salvia para nicho bienestar

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo CALENDARIO / PLANNER:

TEMA: [tu plan — ej: "reto de 30 días de contenido"]
SLIDES: [ej: 7]
ACENTO: [naranja #FF6B35 / verde salvia #8FAF8A]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: Sora (títulos) + Inter (números/etiquetas) — Google Fonts
- Fondo blanco; encabezado con mes + etiqueta del plan en el acento
- Cuadrícula CSS de 7 columnas (L M M J V S D): días en celdas redondeadas; días clave con fondo de acento; días con tarea con un puntito de color
- Nota al pie con la leyenda ('Mar y Jue: reel · Sáb: carrusel')
- Slide 1: portada — el calendario completo del reto
- Slides 2-N: haz zoom a una semana o a un tipo de día y explícalo
- Slide final: 'empieza hoy' + CTA + handle
- HTML con slides en secuencia vertical
```

---

## 37 — BLUEPRINT / PLANO TÉCNICO
**Tags:** Frameworks · Metodologías · Autoridad · `HTML/CSS`

Cuadrícula de plano azul con cotas y anotaciones. Hace que tu método parezca ingeniería.

**Características:**
- Fondo azul plano con grilla técnica fina blanca
- Tipografía typewriter (Special Elite) para todo el texto
- Cajas con borde punteado + anotaciones tipo 'FIG. 03'
- Cotas/medidas en una esquina ('ESCALA 1:1')
- Convierte un proceso en un 'diagrama de ingeniería'

**Paletas sugeridas:**
- Azul plano `#0B3D91` + líneas blancas + texto `#9DC3FF`
- Carbón `#102A43` + grilla cyan para look más tech

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo BLUEPRINT / PLANO TÉCNICO:

TEMA: [el sistema a diagramar — ej: "la estructura de un reel que retiene"]
SLIDES: [ej: 7]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Special Elite (typewriter) — Google Fonts
- Fondo azul plano #0B3D91; grilla técnica con ::before (dos linear-gradients que forman cuadrícula blanca fina, 22px)
- Texto en blanco/azul claro #9DC3FF; cajas con borde 1px dashed para los componentes del sistema
- Anotaciones tipo plano: 'FIG. 0X — [sección]', cotas/medidas en una esquina ('ESCALA 1:1 · 1080×1350')
- Slide 1: portada — el 'plano maestro' del método con título
- Slides 2-N: amplía un componente por slide (con su caja punteada y anotación)
- Slide final: 'construido por [@handle del cliente]' + CTA
- HTML con slides en secuencia vertical
```

---

## 38 — CINEMA / SUBTÍTULO
**Tags:** Storytelling · Frases · Emoción · `Banana + HTML/CSS`

Fotograma con barras letterbox y subtítulo de película. Cinematográfico y emocional.

**Características:**
- Barras negras arriba y abajo (letterbox 2.39:1)
- Subtítulo blanco centrado con sombra fuerte, estilo film
- Timecode en una esquina (01:14:22:08)
- Imagen/escena de Banana como fotograma central
- Cada slide = un 'frame' que cuenta la historia

**Paletas sugeridas:**
- Negro + subtítulo blanco (clásico cine)
- Imagen con grado de color cálido o teal&orange + subtítulo blanco

**Prompt:**
```
Necesito un carrusel CINEMA / SUBTÍTULO. Dos pasos:

PASO 1 — GENERÁ LAS IMÁGENES (con Banana):
Generá un fotograma por slide, estilo cinematográfico:
- Slide 1: [escena de apertura]
- Slide 2: [siguiente escena]
[continuar por slide…]
Estilo: [cine / teal&orange / cálido nostálgico]
Formato: 1080x1350px

PASO 2 — GENERÁ EL HTML:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Inter semibold (subtítulo) — Google Fonts
- Barras negras letterbox arriba y abajo (≈48px) sobre la imagen
- Subtítulo blanco centrado en la parte inferior con text-shadow fuerte y leve caja semitransparente (box-decoration-break: clone)
- Timecode en una esquina superior (estilo 01:14:22:08)
- Slide 1: fotograma + título/primera línea de la historia
- Slides 2-N: un frame + una línea de subtítulo que avanza el relato
- Slide final: frame de cierre + CTA + handle como 'créditos'
- HTML con slides en secuencia vertical
```

---

## 39 — PIZARRA / CHALKBOARD
**Tags:** Educación · Explicaciones · Listas · `HTML/CSS`

Tiza sobre pizarra verde con subrayados de color. Se siente como una mini clase.

**Características:**
- Fondo verde pizarra con leve iluminación de esquina
- Tipografía a mano (Permanent Marker / Caveat) en blanco tiza
- Subrayado grueso amarillo bajo el título
- Ítems con palomita verde + palabras clave en color
- Da sensación de clase rápida, didáctica y cercana

**Paletas sugeridas:**
- Pizarra `#2C3A31` + tiza blanca + subrayado amarillo `#FFE26B` + acentos menta/rosa
- Pizarra negra `#1d1d1d` + tiza + acento cian

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo PIZARRA / CHALKBOARD:

TEMA: [tu tema — ej: "3 errores que frenan tu alcance"]
SLIDES: [ej: 7]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografías: Permanent Marker o Caveat (a mano, tiza) — Google Fonts
- Fondo verde pizarra #2C3A31 con leve glow de esquina (::before radial-gradient blanco a baja opacidad)
- Texto en blanco tiza; título con subrayado grueso amarillo #FFE26B debajo
- Ítems con ✓ verde + palabras clave en colores tiza (menta, rosa)
- Slide 1: portada — tema escrito 'a mano' con subrayado
- Slides 2-N: un punto por slide o lista corta tipo apunte de clase
- Slide final: 'tarea para hoy' + CTA + handle
- HTML con slides en secuencia vertical
```

---

## 40 — VS / VERSUS
**Tags:** Comparativas · Debate · Decisiones · `HTML/CSS`

Dos opciones enfrentadas con un medallón VS al centro. Obliga a elegir bando = comentarios.

**Características:**
- Slide partido en dos mitades de paletas opuestas (fría vs cálida)
- Medallón circular 'VS' rojo centrado encima de la división
- Etiqueta 'Opción A / B' + frase corta en cada mitad
- Distinto de Antes/Después: aquí ambas opciones son válidas
- Hace que la gente comente su elección

**Paletas sugeridas:**
- Mitad fría `#12203A` + mitad cálida `#FBEFE6` + medallón rojo `#FF3B3B`
- Azul vs naranja, o morado vs amarillo — siempre contraste fuerte

**Prompt:**
```
Genérame un carrusel HTML/CSS estilo VS / VERSUS:

TEMA: [la comparación — ej: "publicar diario vs publicar con sistema"]
SLIDES: [ej: 7]

ESPECIFICACIONES:
- Formato: 1080x1350px (portrait 4:5)
- Tipografía: Inter bold (opciones) + Anton (medallón VS) — Google Fonts
- Cada slide partido en dos mitades verticales con paletas opuestas (una fría/oscura, otra cálida/clara)
- Medallón circular 'VS' en rojo #FF3B3B con borde blanco, centrado sobre la línea divisoria
- Cada mitad: etiqueta 'Opción A/B' + frase corta enfrentada
- A diferencia de Antes/Después, aquí presentas dos caminos para que la audiencia elija (o revelas cuál gana)
- Slide 1: portada — el dilema principal A vs B
- Slides 2-N: una comparación por slide (criterio por criterio)
- Slide final: tu veredicto + '¿tú de qué lado estás?' + CTA + handle
- HTML con slides en secuencia vertical
```

---

## Modificadores — combínalos con cualquier estilo

**SEAMLESS / PANORÁMICO** — el diseño fluye de un slide al siguiente como si fuera una
sola imagen continua.
```
MODIFICADOR SEAMLESS: Diseña el carrusel como un canvas
continuo donde los elementos fluyen de un slide al
siguiente. Usa elementos (línea, forma, gradiente,
patrón) que crucen el borde entre slides para crear
la sensación de imagen panorámica al deslizar.
```

**NUMERACIÓN PROMINENTE** — el número de cada punto ocupa el primer plano del slide.
```
MODIFICADOR NUMERACIÓN: Cada slide tiene el número
del punto muy grande y prominente (bold, color de
acento, mínimo 120px) como primer elemento visual,
antes del contenido. El número es parte del diseño,
no solo un indicador.
```

**FRASE ÚNICA POR SLIDE** — cada slide contiene solo una frase completa, nada más.
```
MODIFICADOR FRASE ÚNICA: Cada slide de contenido
tiene UNA SOLA frase o idea completa, tipografía
grande (mínimo 48px), sin subtítulos ni puntos extra.
Impacto puro, lectura instantánea.
```

**BRANDING EN TODOS LOS SLIDES** — el handle aparece en cada slide, discreto pero
siempre presente.
```
MODIFICADOR BRANDING: En todos los slides, incluye
en la esquina inferior derecha el handle [@handle del cliente]
en tipografía pequeña (14-16px), color sutil,
semi-transparente. El slide final es 100% branding:
nombre o logo grande + handle + CTA.
```

**VARIACIÓN DE FONDO POR SLIDE** — cada slide usa un color de fondo diferente dentro
de la misma paleta.
```
MODIFICADOR VARIACIÓN: Cada slide tiene un fondo
de color diferente, todos dentro de la misma paleta
definida. No todos del mismo color. La variación
da ritmo visual al carrusel.
```

---

## Prompt universal

Si no se sabe qué estilo pedir, dejar que Claude elija el más adecuado según el contenido:

```
Voy a darte información sobre el carrusel que necesito.
Elige el estilo más adecuado de tu catálogo y genérame el HTML completo:

TEMA: [tu tema]
OBJETIVO: [educar / vender / conectar / viralizarse / autoridad]
AUDIENCIA: [a quién va dirigido]
CANTIDAD DE PUNTOS: [cuántos tips, pasos, razones, etc.]
PALETA DE MARCA: [tus colores, o deja que Claude elija]
HANDLE: [@handle del cliente]
MOTOR: HTML/CSS

Antes de generarlo, dime qué estilo elegiste y por qué.
```
