## Context

Proyecto "Show de los 80": página web one-page para un show de talentos. Actualmente no existe sitio web; se requiere una landing page estática de bajo mantenimiento. El registro de participantes se delega a Google Forms (sin backend propio) y los datos se almacenan en Google Sheets. El despliegue es estático vía GitHub Pages.

El proyecto se limita a HTML y CSS puros, sin JavaScript ni frameworks.

## Goals / Non-Goals

**Goals:**
- Página one-page estática con estética ochentera (neón, retro).
- Cero backend: registro por Google Forms, datos en Google Sheets.
- Despliegue estático con GitHub Pages.
- Responsive mobile-first, accesible y de carga rápida.
- Mantenible: HTML semántico y CSS con variables.

**Non-Goals:**
- No implementar formulario propio ni validación server-side.
- No usar frameworks (React, Bootstrap, Tailwind).
- No incluir JavaScript (ni menús animados con JS).
- No construir panel de administración ni visualización de datos.

## Decisions

**D1: Página one-page vs multi-page**
Se usa una sola página (`index.html`) con scroll. Es el patrón habitual para eventos y reduce el mantenimiento.
*Alternativa:* multi-page — descartada por más archivos sin beneficio real.

**D2: HTML semántico + CSS con variables**
`index.html` con etiquetas semánticas (`header`, `main`, `section`, `footer`). `css/styles.css` con variables CSS para la paleta de colores neón y tipografías, facilitando cambios de tema.
*Alternativa:* CSS precompilado (Sass) — descartado por añadir tooling innecesario.

**D3: Estética ochentera**
Fondo oscuro, acentos neón (fucsia/cian/amarillo), degradados y tipografía retro vía Google Fonts (p. ej., Orbitron / Press Start 2P para títulos, fuente sans-serif legible para cuerpo).
*Alternativa:* estilo sobrio — descartado porque el evento pide identidad temática.

**D4: Registro por enlace a Google Forms**
Botón "Regístrate" (`<a href="..." target="_blank" rel="noopener">`) que abre el formulario de Google. La hoja de Google Sheets se llena sola al enviar; sin integración adicional.

**D5: Video embebido de YouTube**
`<iframe>` con el video promocional del evento dentro de un marco decorativo tipo TV/CRT.

**D6: Despliegue GitHub Pages**
Archivos servidos desde la raíz del repo (`index.html` en la raíz). GitHub Pages publica el sitio sin pasos extra de build.

## Risks / Trade-offs

- [El embed de YouTube depende de terceros para cargar] → Usar `loading="lazy"` y fallback de texto en el caso de bloqueo.
- [Las fuentes de Google Fonts requieren conexión] → Definir fallbacks seguros (sans-serif) en `font-family`.
- [El link del Google Form es un valor externo] → Centralizar la URL en un solo lugar (atributo del botón) para facilitar su actualización.
- [Estética recargada puede afectar legibilidad] → Contraste alto entre texto y fondo y tamaños de fuente adecuados.
