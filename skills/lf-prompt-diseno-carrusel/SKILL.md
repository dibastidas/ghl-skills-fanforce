---
name: lf-prompt-diseno-carrusel
description: >
  Construye un prompt de diseño de carrusel personalizado cuando ninguno de los
  40 estilos de la biblioteca de `lf-diseno-carrusel` convence — a partir de una
  referencia visual que el usuario describe o pega, más sus colores de marca,
  handle y preferencias de fotos. Usar cuando alguien diga: "quiero un estilo
  propio para mi carrusel", "no me gusta ninguno de los 40 estilos", "crea un
  prompt de diseño personalizado", o cuando `lf-diseno-carrusel` redirija aquí
  porque ningún estilo del catálogo convence. No depende de ningún cliente
  cargado de antemano — pide colores, handle y referencia directamente en el
  chat. Entrega el prompt completo en el chat, listo para pegar de vuelta en
  `lf-diseno-carrusel` — no guarda nada en Drive ni en el computador.
argument-hint: "[describe el estilo que quieres, si ya lo tienes en mente]"
---

# lf-prompt-diseno-carrusel — Prompt de Diseño Personalizado

Este skill es para cuando ninguno de los 40 estilos de la biblioteca de
`lf-diseno-carrusel` encaja. Construye un prompt de diseño desde cero, a partir
de una referencia visual y los datos de marca del usuario, y lo entrega en el
chat para usarlo directamente.

---

## PASO 1 — La referencia visual

> "Cuéntame el estilo que tienes en mente. Puede ser:
>
> **A) Una descripción** — colores, sensación, referencias (ej. "minimalista,
>    mucho blanco, tipografía serif elegante, como una revista de moda")
> **B) Una captura o carrusel que viste** — descríbeme lo que recuerdas: colores,
>    tipografía, cómo se distribuye el texto, elementos decorativos
> **C) Partir de uno de los 40 estilos base** — dime el nombre o número y lo
>    tomamos como punto de partida para modificarlo"

Si elige C y no sabe el nombre o número, ofrecer la biblioteca visual:

> "Si quieres ver cada estilo con su imagen de ejemplo antes de elegir uno como base:
> 🔗 **https://lanzafacil.com/biblioteca-de-carruseles** · Contraseña: `lanzafacil2026`
>
> Cuando tengas el nombre o número, dímelo y seguimos aquí."

**En cuanto el usuario diga un nombre o número** (haya visto la web o no), ir
directo a `../lf-diseno-carrusel/references/biblioteca-estilos.md` y leer el
prompt completo de ese estilo desde ahí — nunca desde la web — y usarlo como
base para las modificaciones que pida.

Hacer las preguntas necesarias hasta tener claro: paleta general, tipografías
(serif/sans/handwriting/display), nivel de contraste, y elementos decorativos
distintivos (líneas, formas, texturas, íconos).

---

## PASO 2 — Colores y handle

> "Dame:
> - **Color principal** (hex o descripción): ej. #1A3A5C o "azul marino"
> - **Color secundario / acento**: ej. #FF6B35 o "naranja"
> - **Handle de Instagram**: @[tu handle]
>
> Si no tienes los hex exactos, con una descripción del color elijo los más cercanos."

---

## PASO 3 — Fotos (opcional)

> "¿Quieres incluir fotos reales en los carruseles con este estilo?
>
> **A) Sí** — algunos slides usarán fotos reales (fondos, retratos, momentos).
>    Dame la ruta de la carpeta local, o dime que la cargas después.
> **B) No** — el diseño será 100% tipográfico y de color."

Si dice sí y da una ruta local, listar con `ls "[ruta]"` y confirmar cuántas
fotos hay disponibles.

Preguntar la disposición:

> "¿Cómo quieres usar las fotos?
>
> **A) Hero de fondo** — la foto ocupa todo el slide, texto encima con overlay
> **B) Split** — foto en la mitad superior, texto en la mitad inferior
> **C) Circular** — foto en un círculo con texto alrededor
> **D) Polaroid** — foto con borde blanco rotada como recorte de álbum
> **E) Mezcla** — algunos slides con foto, otros tipográficos puros"

Guardar la elección como `modo_foto`.

---

## PASO 4 — Modificadores (opcional)

> "¿Quieres agregar algún modificador al estilo? (opcionales, máximo 2)
>
> **Seamless** — el diseño fluye de un slide al siguiente como panorámica
> **Numeración prominente** — el número de cada slide es un elemento de diseño enorme
> **Frase única** — un solo mensaje por slide, tipografía grande, impacto puro
> **Branding en todos** — tu handle en cada slide, último slide 100% de marca
> **Variación de fondo** — cada slide tiene un tono diferente de la paleta
>
> Si no quieres ninguno, di 'ninguno' y continuamos."

---

## PASO 5 — Construir el prompt

Combinar todo en un prompt completo y autocontenido:

1. Descripción del estilo (de la referencia del PASO 1, o el prompt base del
   estilo elegido en la opción C)
2. Colores reales del usuario (reemplazar cualquier placeholder de color)
3. Handle real: `[@handle del cliente]` → sustituido por el handle real dado
4. Formato siempre 1080×1350px (4:5 portrait) — **obligatorio, sin excepción**
5. Instrucciones de fotos si aplica (modo de disposición, sin depender de Drive)
6. Modificadores elegidos al final

### Sección de fotos en el prompt (si aplica):

```
FOTOS REALES:
- Carpeta local: [ruta_fotos]
- Modo: [Hero de fondo / Split / Circular / Polaroid / Mezcla]
- Para cada slide que incluya foto:
  · Listar archivos de la carpeta con `ls`
  · Elegir la foto que mejor encaje por composición y tono del slide
  · Si el slide es tipo "resultado" o "autoridad" → foto profesional/formal
  · Si el slide es tipo "conexión" → foto más cercana, casual
  · Si el slide es tipo "proceso" → foto trabajando o en acción
  · Copiar al scratchpad y referenciar en el HTML con ruta relativa
  · Para modo Hero: agregar overlay rgba([R,G,B],0.5) para legibilidad
  · Para modo Split: imagen arriba (560px) + área de texto abajo (520px)
  · Para modo Circular: clip-path: circle(50%) + sombra suave
  · Para modo Polaroid: border blanco 20px + sombra + rotate(±3deg)
```

Formato del prompt final:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PROMPT DE DISEÑO PERSONALIZADO
Fotos: [Sí — carpeta: X — modo: Y / No]
Modificadores: [lista o Ninguno]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[PROMPT COMPLETO CON COLORES, HANDLE, FORMATO 1080x1350px Y FOTOS YA INCORPORADOS]

[SECCIÓN DE FOTOS si aplica]

[MODIFICADORES si aplica]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PARA USAR:
Pega este prompt completo en `lf-diseno-carrusel`, opción C del PASO 2
("Ninguno me convence") — el copy que tengas cargado se inserta en el diseño.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Mostrar el prompt completo en el chat y preguntar:

> "¿Este prompt queda bien o ajustamos algo?"

Iterar hasta que el usuario lo apruebe. La entrega final es este mensaje del
chat — no se guarda en ningún otro lugar.

---

## REGLAS DEL SKILL

- No requiere ningún cliente cargado de antemano. Colores, handle y referencia
  se piden directamente en el chat.
- Siempre confirmar la referencia visual antes de construir el prompt — nunca
  asumir un estilo sin que el usuario lo describa o elija uno base.
- Formato siempre 1080×1350px (4:5) — sin excepción, igual que en `lf-diseno-carrusel`.
- Los modificadores son opcionales. Si el usuario dice "ninguno", continuar sin ellos.
- El resultado se entrega completo en el chat — no se guarda en Drive ni en el
  computador. El usuario es quien decide si lo reutiliza pegándolo de nuevo la
  próxima vez.
- Este skill solo construye el prompt personalizado. El diseño y la
  exportación a PNG los hace `lf-diseno-carrusel`.
