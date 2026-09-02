## MODIFIED Requirements

### Requirement: Hero page

El sitio SHALL mostrar una sección hero con el título del evento "SHOW DE LOS 80s" en estilo letrero neón, un mensaje de bienvenida y un botón de llamado a la acción para registrarse.

El título SHALL mostrar "SHOW DE LOS 80s" en mayúsculas y SHALL asignar un color neón por palabra: "SHOW" fucsia, "DE" amarillo, "LOS" turquesa y "80s" morado. Todas las letras SHALL tener borde blanco simulando neón y un gradiente claro arriba. El título SHALL incluir sombra exterior suave, organizarse en dos líneas ("SHOW DE" arriba, "LOS 80s" abajo), llevar una inclinación suave hacia arriba y presentar chispas de brillo decorativas.

#### Scenario: Vista del título con colores por palabra

- **WHEN** el usuario abre la página
- **THEN** el título muestra "SHOW DE LOS 80s" en mayúsculas con "SHOW" en fucsia, "DE" en amarillo, "LOS" en turquesa y "80s" en morado

#### Scenario: Borde, gradiente y sombra del título

- **WHEN** el usuario visualiza el título del hero
- **THEN** las letras tienen borde blanco estilo neón, gradiente claro arriba y sombra exterior suave

#### Scenario: Disposición del título en dos líneas

- **WHEN** el usuario visualiza el título del hero
- **THEN** "SHOW DE" aparece en la primera línea y "LOS 80s" en la segunda línea

#### Scenario: Inclinación del título

- **WHEN** el usuario visualiza el título del hero
- **THEN** el título presenta una inclinación suave hacia arriba

#### Scenario: Chispas de brillo del título

- **WHEN** el usuario visualiza el título del hero
- **THEN** se muestran chispas de brillo decorativas alrededor del título
