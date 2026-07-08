---
name: lf-creador-copies-carruseles
description: >
  Investiga carruseles virales reales y escribe el copy completo, slide por slide,
  de los carruseles que se le pidan — con hook, estructura narrativa y CTA
  adaptados a la marca y el avatar que el propio usuario da en el chat. Usar cuando
  alguien diga: "hazme el copy de mis carruseles", "escribe un carrusel para
  Instagram", "necesito N carruseles sobre X", "crea el copy de un carrusel",
  o cualquier variación que pida contenido de carrusel para redes sociales. No
  depende de ningún cliente ni oferta cargados de antemano — pregunta el avatar,
  la marca y el tono directamente en el chat. Antes de escribir, investiga
  carruseles virales reales con Playwright y Tavily, extrae sus estructuras
  narrativas y las adapta al contenido. Entrega todo en el chat — no guarda nada
  en Drive ni en el computador.
argument-hint: "[cuántos carruseles y de qué tema, si ya lo sabes]"
---

# lf-creador-copies-carruseles — Copy de Carruseles

Antes de escribir, investiga. El principio de este skill es el mismo que el del
periodismo: buscar lo que ya está funcionando en el mundo real, entender por qué
funciona y usarlo como base — no como copia.

El copy de cada carrusel debe sonar como la marca hablándole directamente a la
persona que más necesita ese contenido. Si podría ser de cualquier creador del
mundo, hay que reescribirlo.

---

## PASO 1 — Marca, avatar y tono

Preguntar directamente en el chat, en un solo bloque:

> "Para escribir copy que suene a ti y no genérico, necesito:
>
> 1. **Marca o negocio:** ¿cómo se llama y a qué se dedica?
> 2. **Avatar:** ¿a quién le hablas? Dolores, deseos, objeciones — lo que sepas.
> 3. **Tono de voz:** ¿cómo hablas normalmente? Si tienes un fragmento de algo
>    que ya escribiste o dijiste (200-300 palabras), pégalo — ayuda muchísimo
>    a que el copy no suene genérico.
> 4. **Handle de Instagram:** @[tu handle]
> 5. **Palabra clave para CTA** (opcional): si vas a pedir "comenta X" en algún carrusel."

Guardar esta info como contexto de marca para el resto de la sesión. No pedirla
de nuevo si ya la dio.

---

## PASO 2 — Cuántos carruseles y de qué

> "¿Cuántos carruseles quieres crear y de qué tema cada uno?
>
> Ejemplo: '3 carruseles — uno sobre [tema 1], uno sobre [tema 2], uno sobre [tema 3]'
>
> Si no tienes los temas definidos, dime solo cuántos quieres y te propongo
> temas según tu avatar y tu marca."

Si no da temas, proponer [N] temas basados en el avatar/marca del PASO 1 y
esperar confirmación antes de seguir.

Para cada carrusel, identificar (preguntando o infiriendo del tema, y
confirmando) el tipo de contenido:

- **Contrarian** — rompe una creencia del avatar
- **Conexión** — historia o emoción personal
- **Vehículo** — sistema/proceso con CTA fuerte
- **Autoridad** — momento que demuestra expertise sin declararlo

---

## PASO 3 — INVESTIGACIÓN DE CARRUSELES VIRALES

Esta es la fase más importante del skill. No se escribe nada hasta completarla.

El objetivo es construir un banco de estructuras narrativas reales — no inventadas —
basadas en carruseles que ya probaron funcionar con miles o millones de personas.

### FASE A — Búsqueda con Tavily

Realizar 3 búsquedas en paralelo:

```
Búsqueda 1: "viral carousel instagram examples structure copy"
Búsqueda 2: "best instagram carousel formats hook slide 2024 2025"
Búsqueda 3: "carrusel viral estructura copy slide hook instagram"
```

Usar `mcp__plugin_ghl-skills-fanforce_tavily__tavily_search` para cada una. Extraer de los resultados:
- URLs de ejemplos específicos de carruseles virales
- Descripciones de estructuras que funcionan
- Primeras palabras de slides que generaron engagement

### FASE B — Exploración en Instagram con Playwright

Abrir Instagram Explore y buscar carruseles de alto engagement:

```
1. mcp__plugin_ghl-skills-fanforce_playwright__browser_navigate →
   "https://www.instagram.com/explore/"

2. Tomar screenshot con browser_take_screenshot → identificar posts con
   icono de carrusel (ícono de cuadrados apilados, esquina superior derecha)

3. Hacer clic en un carrusel que tenga muchos likes/comentarios visibles

4. Por cada slide:
   → browser_take_screenshot → leer visualmente el texto del slide
   → browser_click en la flecha para avanzar
   Repetir hasta el último slide

5. Registrar:
   - Texto del slide 1 (hook)
   - Texto de slides 2-N (desarrollo)
   - Texto del slide final (CTA o cierre)
   - Número total de slides
   - Engagement visible (likes, comentarios si son visibles)
```

Analizar 4-6 carruseles de cualquier nicho. El nicho no importa —
lo que importa es la estructura narrativa.

Si Instagram requiere login: navegar a perfiles públicos con carruseles
conocidos por ser virales, o usar las URLs encontradas en Fase A.

### FASE C — Extracción con Supadata

Para carruseles encontrados en Fase A o B que tengan URL pública, usar
`mcp__plugin_ghl-skills-fanforce_supadata__supadata_scrape` para extraer el contenido del post
(caption, descripción, número de slides si es accesible).

Complementar con `mcp__plugin_ghl-skills-fanforce_tavily__tavily_extract` para las URLs encontradas
en Fase A que contengan análisis o desglose de carruseles virales.

### FASE D — Clasificar por estructura narrativa

Cada carrusel encontrado tiene una estructura subyacente. Clasificar usando
los 8 tipos de narrativa adaptados para copy:

| # | Tipo narrativo | El slide 1 dice... | El desarrollo... | El cierre... |
|---|---------------|-------------------|-----------------|-------------|
| **1. Proceso** | "Los N pasos para..." / "Cómo lograr X en N pasos" | Cada slide = un paso con acción concreta | Resultado del proceso + CTA |
| **2. Sistema** | "Las N partes de..." / "Así funciona..." | Cada slide = un componente del sistema | Visión completa + CTA |
| **3. Antes/Después** | "Esto era yo antes / Así me fue haciendo X" | Contraste entre estados | La transformación como prueba + CTA |
| **4. Espejo emocional** | Describe una situación que el avatar vive | Valida la emoción, no la juzga | Salida o reencuadre + CTA suave |
| **5. Metáfora** | Usa una imagen o analogía inesperada | Desarrolla la metáfora aplicándola | La lección que rompe el patrón + CTA |
| **6. Jerarquía** | "De menor a mayor..." / "La pirámide de..." | Capas en orden lógico o de importancia | El principio que todo lo sostiene + CTA |
| **7. Roadmap** | "Tu camino de X a Y" / "El recorrido que nadie te cuenta" | Waypoints del journey con lo que pasa en cada uno | El destino como promesa + CTA |
| **8. Historia** | Situación concreta + apertura de tensión | Giros, complicaciones, revelaciones | Resolución + reflexión + CTA |

### FASE E — Banco de estructuras

Documentar los patrones encontrados:

```
BANCO DE ESTRUCTURAS VIRALES — [Fecha de investigación]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ESTRUCTURA #1 — [Tipo narrativo]
Nicho original: [nicho del carrusel encontrado]
Hook (slide 1): "[texto exacto o paráfrasis fiel]"
Patrón de desarrollo: [cómo avanza entre slides]
Cierre: "[texto del slide final]"
Por qué funciona: [razón narrativa o psicológica]
Mejor para: [Contrarian / Conexión / Vehículo / Autoridad]

[Repetir para cada estructura encontrada]
```

Los hooks descubiertos aquí son la única fuente de hooks del skill — nunca
inventar uno ni usar un banco externo.

---

## PASO 4 — Modo de trabajo

> "Encontré [N] estructuras virales de carruseles. ¿Cómo quieres el proceso?
>
> **A) Carrusel por carrusel aquí** — muestro cada propuesta, elegimos la
>    estructura juntos y escribimos el copy antes de pasar al siguiente.
>
> **B) Todo de una vez** — elijo la mejor estructura para cada carrusel, escribo
>    todos los copies y te los muestro todos juntos aquí en el chat."

---

## PASO 5 — Asignar estructura a cada carrusel

Para cada carrusel, seleccionar la estructura del banco que mejor encaja con:

1. **Tipo de contenido** (Contrarian, Conexión, Vehículo, Autoridad)
2. **Tema específico**
3. **Lo que necesita el avatar en ese momento**
4. **Variedad** — que los carruseles no repitan el mismo tipo narrativo

Guía de compatibilidad:

| Tipo de contenido | Estructuras que mejor encajan |
|------------------|------------------------------|
| Contrarian | 5 (Metáfora) / 3 (Antes-Después invertido) / 8 (Historia con giro) |
| Conexión | 4 (Espejo emocional) / 8 (Historia) / 3 (Antes-Después personal) |
| Vehículo | 2 (Sistema) / 1 (Proceso) / 6 (Jerarquía) / 7 (Roadmap) |
| Autoridad | 7 (Roadmap) / 8 (Historia con resultado) / 2 (Sistema) |

Si el modo es B, definir todas las asignaciones sin preguntar y proceder.
Si el modo es A, proponer la estructura para el primer carrusel y esperar confirmación.

---

## PASO 6 — Escribir el copy de cada carrusel

### REGLAS GENERALES DE ESCRITURA

**Hook del carrusel:**
El slide 1 es el hook — debe detener el scroll. Tomarlo del banco de estructuras
del PASO 3. Elegir el que mejor conecta con el tipo y tema. Primeras palabras
intactas. Nunca inventado. No repetir hooks entre los carruseles de esta sesión.

**Conexión con el avatar:**
Cada slide debe hablar directamente a un dolor, anhelo, sueño u objeción del
avatar del PASO 1. Si un slide puede ser de cualquier persona, reescribirlo
hasta que se sienta escrito para esa persona específica.

**Lenguaje:**
Natural y visceral. Una persona hablándole a otra. Sin palabras de coach, sin
copy genérico, sin jerga de marketing. Basarse en el ritmo y vocabulario del
fragmento de tono que dio el usuario en el PASO 1.

**CTA:**
- Todos los carruseles llevan CTA con palabra clave excepto Conexión.
- El CTA va en el último slide, siempre.
- El CTA de Vehículo/Autoridad: "Comenta [palabra_clave]" o invitar a seguir/guardar
  si no hay palabra clave.
- El CTA de Conexión: "¿Te identificas?" o "Te leo en comentarios."

**Longitud de slides:**
- Slide 1 (hook): máximo 1-2 líneas. Que quepa completo en pantalla.
- Slides de desarrollo: máximo 3-4 líneas por slide. Si hay más, partir en dos slides.
- Slide final (CTA): máximo 2 líneas. Directo.
- Total de slides recomendado: 5-8 slides.

**No repetir palabras en frases consecutivas dentro de un slide.**

### ESTRUCTURA POR TIPO DE CONTENIDO

**CARRUSEL CONTRARIAN**
```
Slide 1 — HOOK: hook del banco de estructuras que rompe una creencia del avatar
Slide 2 — LA CREENCIA: lo que el avatar cree hoy (sin ridiculizarlo)
Slide 3 — EL PROBLEMA: por qué esa creencia no le funciona
Slide 4 — EL GIRO: lo que en realidad está pasando
Slide 5 — EL VACÍO: lo que aún no sabe (sin darlo todo)
Slide 6 — EL CIERRE: insinuación de otro camino
Slide 7 — CTA con palabra clave
```

**CARRUSEL CONEXIÓN**
```
Slide 1 — HOOK: hook del banco que abre una situación personal concreta
Slide 2 — LA SITUACIÓN: qué pasó, cuándo, dónde
Slide 3 — LO QUE SENTÍ: sin filtro, sin moraleja todavía
Slide 4 — EL GIRO: qué entendí / qué cambió
Slide 5 — EL PRINCIPIO: la lección que se desprende de forma natural
Slide 6 — CIERRE: honesto, sin moraleja de libro
Slide 7 — CTA sin palabra clave: "¿te pasó algo así?" / "te leo"
```

**CARRUSEL VEHÍCULO / CTA DIRECTO**
```
Slide 1 — HOOK: hook del banco que promete un resultado o sistema concreto
Slide 2 — EL CONTEXTO: quién eres, qué sistema tienes, para quién es
Slide 3 — COMPONENTE 1: primera parte del sistema con descripción concreta
Slide 4 — COMPONENTE 2: segunda parte con descripción concreta
Slide 5 — COMPONENTE 3 (si aplica): tercera parte
Slide 6 — PRUEBA O RESULTADO: cómo se ve en la realidad
Slide 7 — CTA con palabra clave
```

**CARRUSEL AUTORIDAD SUTIL**
```
Slide 1 — HOOK: hook del banco con resultado real o momento de impacto
Slide 2 — EL CONTEXTO: dónde fue, qué estaba pasando, quiénes estaban
Slide 3 — LO QUE PASÓ: el momento específico que muestra la autoridad
Slide 4 — EL APRENDIZAJE: sin declarar la autoridad — mostrarla
Slide 5 — EL PRINCIPIO: lo que ese momento enseñó
Slide 6 — CIERRE: que posiciona sin decir "yo soy experto"
Slide 7 — CTA suave con palabra clave
```

### FORMATO DE CADA CARRUSEL

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CARRUSEL #[N]
Tipo: [Contrarian / Conexión / Vehículo / Autoridad]
Tema: [tema]
Estructura narrativa: [tipo de los 8 — con nombre]
Estructura viral referencia: [nicho original + por qué se eligió]
Hook (slide 1): "[texto del hook]" — [cuenta de referente]
Slides totales: [N]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SLIDE 1 — HOOK
"[Texto completo del slide 1]"

SLIDE 2 — [Nombre del componente]
"[Texto del slide 2]"

[... repetir por cada slide ...]

SLIDE [N] — CTA
"[Texto del CTA]"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## FLUJO A — Carrusel por carrusel

Mostrar el primer carrusel. Esperar:

> "¿Aprobamos este carrusel o ajustamos algo?
> → Aprobado → carrusel #[N+1]
> → [corrección específica]"

Aplicar ajustes en el momento. Avanzar solo cuando se apruebe.
Al terminar todos, ir al PASO 7.

---

## FLUJO B — Todo de una vez

Escribir todos los carruseles sin interrupciones y luego ir al PASO 7.

---

## PASO 7 — Entrega en el chat

Mostrar en el chat, en un solo mensaje final:

1. El banco de estructuras virales encontrado en la investigación (PASO 3)
2. Los copies completos de todos los carruseles, con su asignación de estructura

No guardar nada en Drive ni en el computador — la entrega es este mensaje.

> "✅ Listos los [N] carruseles. Cópialos de aquí arriba cuando los necesites —
> por ejemplo, para pegarlos en `lf-diseno-carrusel` y convertirlos en slides
> visuales."

---

## REGLAS DEL SKILL

- No requiere ningún cliente ni oferta cargados de antemano — el avatar, la
  marca y el tono se piden directamente en el chat en el PASO 1.
- La investigación (PASO 3) es OBLIGATORIA — no se escribe sin ella. Aunque los
  resultados sean limitados, ejecutar la búsqueda antes de producir.
- Hooks: deben salir del banco de estructuras del PASO 3 — nunca inventados,
  primeras palabras intactas. No repetir hooks entre carruseles de la misma sesión.
- Estructuras narrativas: deben variar entre carruseles — no repetir el mismo
  tipo dos veces si hay suficientes carruseles.
- Todos los carruseles llevan CTA con palabra clave excepto Conexión.
- Cada slide habla directamente al avatar que el usuario dio en el PASO 1 — no
  a un público genérico.
- Lenguaje natural y visceral, basado en el fragmento de tono que dio el usuario.
- Todo se entrega en el chat. No se guarda nada en Drive ni en el computador.
