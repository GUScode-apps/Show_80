## ADDED Requirements

### Requirement: Sección de organizadores

El sitio SHALL mostrar una sección de organizadores ubicada inmediatamente antes del footer, con 3 tarjetas en fila horizontal (una por organizador). Cada tarjeta SHALL contener: fotografía en forma circular, nombre completo del organizador y una breve reseña biográfica.

#### Scenario: Vista de la sección de organizadores

- **WHEN** el usuario desplaza hacia la parte inferior de la página
- **THEN** se muestra la sección con 3 tarjetas horizontales, cada una con foto circular, nombre y reseña

#### Scenario: Orden de los organizadores

- **WHEN** se renderiza la sección
- **THEN** las tarjetas aparecen en orden: Geissel Colmenares (izquierda), Zulma Corrales (centro), tercer organizador (derecha)

#### Scenario: Estructura de cada tarjeta

- **WHEN** se visualiza una tarjeta
- **THEN** contiene: imagen circular con borde neón, nombre en fuente retro, reseña en texto legible

#### Scenario: Responsividad de la sección

- **WHEN** el usuario visualiza en móvil (< 640px)
- **THEN** las 3 tarjetas se apilan verticalmente en una columna

## MODIFIED Requirements

### Requirement: Footer informativo

El sitio SHALL incluir un footer con los datos informativos del evento: fecha, hora, lugar y contacto de organización. Inmediatamente antes del footer, SHALL mostrarse la sección de organizadores con 3 tarjetas (foto circular, nombre, reseña).

#### Scenario: Vista del footer y organizadores

- **WHEN** el usuario desplaza al final de la página
- **THEN** se muestra primero la sección de organizadores (3 tarjetas) y luego el footer con fecha, hora, lugar y contacto