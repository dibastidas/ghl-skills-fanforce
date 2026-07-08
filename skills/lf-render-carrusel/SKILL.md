---
name: lf-render-carrusel
description: >
  Exporta un HTML de carrusel (con divs `.slide`) a slides PNG individuales en
  resolución retina 2x, usando el Chrome instalado en la máquina. Es el motor de
  render que usa `lf-diseno-carrusel` en su Opción A de captura — no genera diseño
  ni copy, solo convierte HTML ya armado en PNGs. Activar cuando alguien diga
  "exporta este HTML a PNG", "renderiza estos slides", "convierte el carrusel a
  imágenes", o cuando `lf-diseno-carrusel` necesite capturar los slides que acaba
  de generar. NO usar para diseñar el carrusel (eso es `lf-diseno-carrusel`) ni
  para escribir el copy (eso es `lf-creador-copies-carruseles`).
---

# lf-render-carrusel — Motor de Render HTML → PNG

Toma un archivo HTML con uno o más `<div class="slide">...</div>` y exporta cada
uno como PNG individual, en la misma carpeta del HTML.

---

## CÓMO SE USA

Recibe una sola entrada: la ruta al HTML ya armado (con los divs `.slide` listos,
uno por slide, todos del mismo tamaño). No escribe HTML ni aplica ningún estilo —
solo captura lo que ya existe.

### Paso 1 — Verificar dependencias

El script es self-contained: usa `puppeteer-core` (no descarga Chromium propio,
controla el Chrome/Chromium/Brave/Edge que ya tengas instalado). Detecta solo el
navegador según el sistema operativo — macOS (`/Applications`), Windows
(`Program Files` / `Local AppData`) o Linux (`/usr/bin`) — sin que el usuario
tenga que indicar nada.

```bash
ls "$(dirname "$0")/node_modules/puppeteer-core" 2>/dev/null
```

En la práctica, reemplaza `$(dirname "$0")` por la carpeta de este mismo `SKILL.md`
(la ruta absoluta que usaste para leerlo). Si no existe `node_modules/puppeteer-core`,
instalar una sola vez:

```bash
cd "[carpeta_de_este_skill]" && npm install
```

### Paso 2 — Exportar

```bash
node "[carpeta_de_este_skill]/export.js" "[ruta-al-html]" --width 1080 --height 1350 --scale 2
```

Parámetros opcionales (default: 1080×1350 @ 2x si no se pasan):
- `--width N` — ancho del slide en px
- `--height N` — alto del slide en px
- `--scale N` — factor de escala (2 = retina)

El script:
- Abre el HTML con Chrome headless
- Espera `document.fonts.ready` + 1.5s (Google Fonts renderizadas antes de capturar)
- Detecta automáticamente todos los `.slide`
- Exporta cada uno como `slide-01.png`, `slide-02.png`, ... en la misma carpeta del HTML

### Paso 3 — Verificar resultado

```bash
ls "[carpeta_del_html]" | grep "slide-.*\.png" | wc -l
```

Confirmar que el número de PNGs coincide con el número de `.slide` esperados.
Si `export.js` no encuentra Chrome/Chromium/Brave/Edge instalado, avisa con el
error y sugiere instalar Google Chrome — no hay fallback automático dentro de
este skill (el que llama a este skill, como `lf-diseno-carrusel`, tiene su propia
Opción B vía Playwright MCP si esto falla).

---

## REGLAS

- Nunca modificar el HTML de entrada — este skill solo captura, no diseña.
- Instalar `node_modules` una sola vez; en corridas siguientes ya está disponible.
- Si el HTML no tiene ningún `.slide`, el script falla explícitamente en vez de
  producir un PNG vacío — reportar el error tal cual.
- Requiere Chrome, Chromium, Brave o Edge instalado — funciona igual en macOS,
  Windows y Linux, el script detecta el navegador según el sistema operativo.

---

## ARCHIVOS DE ESTE SKILL

- `export.js` — script de Puppeteer que exporta los PNGs
- `package.json` / `package-lock.json` — dependencia `puppeteer-core`
