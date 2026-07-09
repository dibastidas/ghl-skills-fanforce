# 🔌 MCPs — Las "súper-conexiones" de tus skills

> **¿Qué es un MCP en cristiano?**
> Es una **conexión** que le da a Claude poderes extra: publicar en GoHighLevel, abrir un navegador logueado, generar imágenes con IA, buscar en la web, etc.
>
> Sin MCPs, las skills funcionan, pero a medias. Es como tener Netflix sin internet — la app está, pero no puedes ver nada.

---

## 📊 Resumen rápido

| Nivel | Cuántos | ¿Qué se rompe sin esto? |
|---|---|---|
| 🔥 **ESENCIALES** (2) | Necesitas estos sí o sí | Nada de GHL ni de carruseles funciona |
| ⭐ **RECOMENDADOS** (3) | Súbete cuando puedas | Los carruseles pierden features |

Los 5 vienen **declarados** en `.mcp.json` — Playwright y Supadata se conectan solos (OAuth), Nanobanana y Tavily solo piden que exportes su API key. Nanobanana es el único que **no tiene tier gratis** — es opcional, el resto del plugin funciona sin él.

**Costo total mínimo (esenciales):** $0/mes (usas tu cuenta GHL que ya pagas)
**Costo total si activas todo excepto Nanobanana:** ~$0-30/mes (Tavily/Supadata tienen tier gratis)
**Nanobanana (si lo activas):** variable según uso, ≈$0.04 por imagen — no es una cuota fija

---

## 🔥 ESENCIALES (sin estos no arrancas)

### 1. HighLevel (GHL)
**¿Para qué?** Le permite a Claude leer y escribir directamente en tu cuenta de GoHighLevel — canales conectados, posts programados, workflows de automatización.

**Skills que dependen de esto:**
- `ghl-publicar`
- `ghl-automatizar-comentarios`

**Costo:** **Incluido en tu cuenta GHL** — no es un costo aparte.
**Cómo activarlo:**
1. En GHL: **Configuración → Private Integrations** → crea un token con scope de Workflows/Conversations según el skill.
2. En Claude Code CLI: conecta vía `mcp-remote` al endpoint `https://services.leadconnectorhq.com/mcp/anthropic/v2` con tu Private Integration Token + `locationId`.
   En Claude.ai (web): **Settings → Connectors → Add custom connector** con OAuth.
3. Reinicia Claude Code.

---

### 2. Playwright
**¿Para qué?** Le permite a Claude **abrir un navegador como una persona** — navega la interfaz de GHL cuando un flujo no tiene endpoint de API, y explora Instagram para traer referencias reales de carruseles virales.

**Skills que dependen de esto:**
- `ghl-automatizar-comentarios` (navega la UI de GHL para configurar el workflow)
- `lf-diseno-carrusel` (navega la biblioteca de estilos y hace fallback de export por screenshot)
- `lf-creador-copies-carruseles` (explora Instagram buscando carruseles virales de referencia)

**Costo:** **Gratis** ✨
**Cómo instalarlo:** Ya viene incluido en el repo (`.mcp.json`). Se instala solo cuando corres `/plugin install ghl-skills-fanforce@ghl-skills-fanforce`. No requiere nada más.

*Nota: `ghl-automatizar-comentarios-chrome` es la variante que NO usa este MCP — en su lugar genera un prompt para la extensión [Claude for Chrome](https://claude.com/claude-for-chrome).*

---

## ⭐ RECOMENDADOS (solo si usas los skills de carrusel)

### 3. Nanobanana (Google Gemini 2.5 Flash Image)
**¿Para qué?** Genera y edita **imágenes con IA**. Es el motor visual de los slides de carrusel que lo requieren.

**Skills que dependen de esto:**
- `lf-diseno-carrusel` — pero es **opcional**: sin Nanobanana, el skill sigue funcionando con estilos 100% HTML/CSS y fotos reales, solo pierde la opción de generar imágenes con IA.

**Costo:** ⚠️ **NO tiene tier gratuito** — a diferencia de los otros MCP de esta lista, este modelo cobra por imagen desde la primera llamada: **≈$0.04 por imagen** (más barato que casi cualquier alternativa, pero no es gratis). Requiere que tu cuenta de Google tenga **facturación habilitada** (tarjeta vinculada) — sin eso, la key se crea pero las llamadas fallan.

**Cómo activarlo (5 minutos):**
1. Ve a [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
2. Click en **"Get API key"** → crea una nueva
3. Si te pide vincular una tarjeta o habilitar facturación, es esperado — este modelo específico no tiene modo gratis
4. Copia el código que empieza con `AIza...`
5. Pégasela directamente a `lf-diseno-carrusel` cuando te la pida — el skill la
   configura por ti (detecta tu sistema operativo y la deja guardada, sin que
   tengas que tocar terminal ni archivos). El skill también te ofrece seguir
   sin ella si prefieres no pagar por esto — puedes usar fotos reales en su lugar.

   O manualmente, si prefieres:
   - **macOS / Linux** — abre tu terminal y corre:
     ```bash
     echo 'export GOOGLE_AI_API_KEY="TU_KEY_AQUI"' >> ~/.zshrc
     source ~/.zshrc
     ```
   - **Windows** — abre PowerShell y corre:
     ```powershell
     setx GOOGLE_AI_API_KEY "TU_KEY_AQUI"
     ```
6. Reinicia Claude Code/Desktop por completo. ¡Listo! (Ya viene declarado en `.mcp.json`, solo falta la key.)

---

### 4. Tavily
**¿Para qué?** Búsqueda web inteligente — encuentra carruseles virales de referencia por palabra clave antes de escribir el copy.

**Skills que dependen de esto:**
- `lf-creador-copies-carruseles`

**Costo:** **Gratis (1000 búsquedas/mes)** o de pago para uso intensivo.
**Cómo activarlo (2 minutos):**
1. Ve a [tavily.com](https://tavily.com) → crea cuenta gratis → copia tu API key (empieza con `tvly-...`)
2. Configúrala:
   - **macOS / Linux** — abre tu terminal y corre:
     ```bash
     echo 'export TAVILY_API_KEY="TU_KEY_AQUI"' >> ~/.zshrc
     source ~/.zshrc
     ```
   - **Windows** — abre PowerShell y corre:
     ```powershell
     setx TAVILY_API_KEY "TU_KEY_AQUI"
     ```
3. Reinicia Claude Code/Desktop por completo. ¡Listo! (Ya viene declarado en `.mcp.json`, solo falta la key.)

*Nota: nunca pongas tu key directamente en `.mcp.json` — este repo es público. Siempre usa la variable de entorno `TAVILY_API_KEY`.*

---

### 5. Supadata
**¿Para qué?** Extrae contenido de posts públicos (caption, descripción, número de slides) a partir de una URL, como respaldo cuando Playwright no puede leer el post directamente.

**Skills que dependen de esto:**
- `lf-creador-copies-carruseles`

**Costo:** **Gratis (100 transcripciones/mes)** o de pago para uso intensivo.
**Cómo activarlo:**
1. Ya viene declarado en `.mcp.json` — no necesita API key en texto, se conecta por OAuth.
2. Corre `/mcp` en Claude Code, selecciona **supadata** y autoriza con tu cuenta.
3. Listo — no hay nada que exportar en `~/.zshrc`.

---

## 🎯 Plan recomendado por etapa

### 👶 ETAPA 1 — Solo publicación y automatización GHL ($0/mes extra)
- HighLevel (ya pagas tu cuenta GHL)
- Playwright (gratis)

**Skills que funcionan:** `ghl-publicar`, `ghl-automatizar-comentarios`, `ghl-automatizar-comentarios-chrome`

### 🚀 ETAPA 2 — Sumas diseño y copy de carruseles ($0/mes extra)
Suma:
- Tavily tier free (gratis)
- Supadata tier free (gratis)

**Skills que funcionan:** 100% del plugin usando estilos HTML/CSS y fotos reales — sin gastar nada.

### 💎 ETAPA 3 (opcional) — Imágenes generadas con IA (variable según uso)
Suma:
- Nanobanana (≈$0.04 por imagen, requiere facturación habilitada — no tiene tier gratis)

**Para qué sirve:** solo si quieres que `lf-diseno-carrusel` genere imágenes con IA en vez de usar únicamente fotos reales o estilos tipográficos. El resto del plugin funciona igual sin esto.

---

## ❓ Preguntas frecuentes

### "¿Tengo que activar todos los MCPs antes de usar las skills?"
**No.** Activa HighLevel y Playwright y arranca con los skills de GHL. Suma Tavily y Supadata cuando llegues a los skills de carrusel — ambos son gratis. Nanobanana es aparte y de pago: actívalo solo si de verdad quieres generar imágenes con IA.

### "¿Las skills me avisan si me falta un MCP?"
**Sí.** Cada skill detecta qué MCPs tiene disponibles y te avisa si uno está faltando, explicándote cómo activarlo.

### "Activé un MCP pero Claude dice que no lo ve."
1. Cierra Claude Code completamente
2. Vuélvelo a abrir
3. Si sigue, corre `/mcp` en Claude Code para ver el estado de tus MCPs

---

## 🆘 Si algo no funciona

1. **Revisa Claude.ai → Settings → Integrations** — ¿está conectado y verde?
2. **Reinicia Claude Code** completamente (no solo cerrar la ventana)
3. **Corre `/mcp`** en Claude Code para ver qué tiene activo

---

**Fanforce © 2026**
