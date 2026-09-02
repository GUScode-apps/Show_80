## Why

El evento "Show de los 80" necesita dar visibilidad a sus organizadores para generar confianza y cercanía con los participantes. Actualmente no hay una sección que presente al equipo detrás del evento, lo que reduce la credibilidad y el sentido de comunidad.

## What Changes

- Agregar una nueva sección "Organizadores" ubicada justo antes del footer.
- La sección contendrá 3 tarjetas (cards) en fila horizontal, una por organizador.
- Cada tarjeta mostrará: foto circular, nombre completo y una breve reseña/bio.
- Orden de izquierda a derecha: Geissel Colmenares, Zulma Corrales, [tercer organizador por definir].
- Estilo visual coherente con la estética neón/ochentera del sitio (tarjetas con borde neón suave, foto circular con borde, tipografía retro para nombres).

## Capabilities

### New Capabilities
- `organizers-section`: Nueva sección de tarjetas de organizadores con foto circular, nombre y reseña breve, ubicada sobre el footer.

### Modified Capabilities
- `landing-page`: Se modifica el requisito "Footer informativo" para agregar la sección de organizadores inmediatamente antes del footer.

## Impact

- `index.html`: Nueva sección `<section id="organizers">` con 3 cards antes del `<footer>`.
- `css/styles.css`: Estilos para grid de 3 tarjetas responsive, fotos circulares, nombres con fuente retro, bordes neón, animaciones sutiles.
- Sin cambios en backend, formularios ni despliegue.
- Requiere 3 imágenes de fotos (circulares, idealmente 200x200px) en `assets/`.