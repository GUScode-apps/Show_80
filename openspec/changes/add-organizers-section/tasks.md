## 1. Estructura y contenido HTML

- [x] 1.1 Crear carpeta `assets/organizers/` para las fotos
- [x] 1.2 Añadir `<section id="organizers">` antes de `<footer>` en `index.html` con grid de 3 cards
- [x] 1.3 Cada card: `<img>` circular (placeholder o foto real), `<h3>` nombre, `<p>` reseña
- [x] 1.4 Nombres en orden: Geissel Colmenares, Zulma Corrales, [tercer organizador placeholder]
- [x] 1.5 Añadir atributos `alt` descriptivos en imágenes

## 2. Estilos CSS

- [x] 2.1 Definir grid responsive en `#organizers` (3 cols desktop, 1 col móvil <640px)
- [x] 2.2 Estilizar `.organizer-card`: fondo semitransparente, borde neón, radio, padding
- [x] 2.3 Estilizar foto circular: `aspect-ratio: 1/1`, `border-radius: 50%`, `object-fit: cover`, borde neón
- [x] 2.4 Estilizar nombre: `var(--font-retro)`, colores alternados (pink/cyan/yellow)
- [x] 2.5 Estilizar reseña: `var(--font-body)`, color `--text-dim`, tamaño legible
- [x] 2.6 Añadir hover en card: cambio de borde + glow neón
- [x] 2.7 Media query móvil (<640px): grid 1 columna, gap reducido

## 3. Assets y placeholders

- [x] 3.1 Preparar/colocar fotos reales en `assets/organizers/` (geissel.jpg, zulma.jpg, org3.jpg) 200x200px cuadradas
- [x] 3.2 Crear SVG placeholder genérico si faltan fotos (iniciales en círculo neón)

## 4. Verificación

- [x] 4.1 Verificar en navegador: 3 cards horizontales en desktop, apiladas en móvil
- [x] 4.2 Confirmar fotos circulares, nombres en fuente retro, reseñas legibles
- [x] 4.3 Verificar hover en cards (borde + glow)
- [x] 4.4 Confirmar que la sección queda justo antes del footer sin solapamientos
- [x] 4.5 Probar responsive en DevTools (320px, 768px, 1280px)