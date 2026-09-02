## Context

El sitio actual tiene hero, info+video, registro, footer. Se requiere insertar una sección "Organizadores" entre el registro y el footer, con 3 tarjetas estilo neón/retro. Stack: HTML + CSS puro, sin JS, despliegue estático en GitHub Pages.

## Goals / Non-Goals

**Goals:**
- Sección con 3 cards horizontales (desktop) / apiladas (móvil).
- Cada card: foto circular (200x200px ideal), nombre en fuente retro (Press Start 2P), reseña breve.
- Bordes neón suaves en cards y fotos, hover sutil.
- Coherente con paleta actual (--neon-pink, --neon-cyan, --neon-yellow, --neon-purple).
- Responsive: una columna en <640px.

**Non-Goals:**
- No carrusel ni slider (solo grid estático).
- No lightbox ni modal al clic en fotos.
- No CMS ni datos dinámicos (HTML estático con placeholders de imágenes).

## Decisions

**D1: HTML semántico `<section id="organizers">` con grid CSS**
`display: grid; grid-template-columns: repeat(3, 1fr); gap: 2rem;` y media query a 1 columna en móvil. Simple, sin flexbox wrap que rompe alineación.
*Alternativa:* flexbox con wrap — descartado por control preciso de 3 columnas iguales.

**D2: Fotos circulares con `aspect-ratio: 1/1; border-radius: 50%; object-fit: cover;`**
Imágenes en `assets/organizers/` (geissel.jpg, zulma.jpg, organizador3.jpg). Placeholder SVG si faltan.
*Alternativa:* fondo `background-image` — descartado por semántica y accesibilidad (alt text).

**D3: Nombres en `var(--font-retro)` (Press Start 2P), reseña en `var(--font-body)` (Rubik)**
Coherente con hero__eyebrow y hero__tagline. Color nombre: `--neon-pink` / `--neon-cyan` / `--neon-yellow` alternados para variedad visual.

**D4: Cards con fondo semitransparente y borde neón animado en hover**
`background: rgba(255,255,255,0.08); border: 1px solid var(--neon-pink); transition: border-color, box-shadow`. Hover: `border-color: var(--neon-cyan); box-shadow: 0 0 16px rgba(0,240,255,0.4)`.

**D5: Placeholders de imágenes**
Si no hay foto real, se usa un SVG circular con iniciales (nombre) generado inline o placeholder genérico.

## Risks / Trade-offs

- [Fotos de distinto aspecto recortadas por `object-fit: cover`] → Comunicar a organizadores que suban fotos cuadradas 1:1; fallback SVG si no.
- [Texto de reseña de longitud variable rompe altura de cards] → `min-height` en card + `text-overflow: ellipsis` opcional en reseña; o aceptar altura variable (grid alinea inicio).
- [Tercer organizador no definido aún] → Placeholder "Próximamente" con foto genérica; se actualiza HTML cuando se sepa.

## Migration Plan

1. Añadir `<section id="organizers">` en `index.html` antes de `<footer>`.
2. Crear estilos en `css/styles.css` (variables de color por card si se desea, grid, responsive).
3. Añadir 3 fotos en `assets/organizers/` (o placeholders).
4. Verificar en móvil y escritorio.
5. Rollback: eliminar sección HTML y reglas CSS asociadas.

## Open Questions

- ¿Cuál es el tercer organizador? (Nombre, foto, reseña).
- ¿Colores de borde distintos por card (pink/cyan/yellow) o todos iguales?
- ¿Longitud máxima de reseña? (Sugerido: máx 2 líneas / ~160 chars).