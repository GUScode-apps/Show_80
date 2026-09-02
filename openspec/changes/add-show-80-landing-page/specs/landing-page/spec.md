## ADDED Requirements

### Requirement: Hero page

El sitio SHALL mostrar una sección hero con el título del evento "Show de los 80", un mensaje de bienvenida y un botón de llamado a la acción para registrarse.

#### Scenario: Vista de la sección hero

- **WHEN** el usuario abre la página
- **THEN** se muestra el título del evento, el mensaje de bienvenida y un botón de registro visible

### Requirement: Información del evento con video

El sitio SHALL incluir una sección con información breve del evento (fecha, lugar y categorías) y SHALL embeber un video promocional de YouTube.

#### Scenario: Sección informativa con video

- **WHEN** el usuario desplaza a la sección de información
- **THEN** se muestra el texto descriptivo del evento y un reproductor de video embebido de YouTube

### Requirement: Registro de participantes

El sitio SHALL ofrecer un botón de registro que abra el formulario de Google Forms del evento en una pestaña nueva.

#### Scenario: Clic en el botón de registro

- **WHEN** el usuario hace clic en el botón "Regístrate" en cualquier sección
- **THEN** se abre el formulario de Google Forms del evento en una pestaña nueva del navegador

#### Scenario: Datos almacenados en Google Sheets

- **WHEN** el participante completa y envía el formulario de Google Forms
- **THEN** sus datos quedan registrados en la hoja de cálculo de Google Sheets vinculada

### Requirement: Footer informativo

El sitio SHALL incluir un footer con los datos informativos del evento: fecha, hora, lugar y contacto de organización.

#### Scenario: Vista del footer

- **WHEN** el usuario desplaza al final de la página
- **THEN** se muestran la fecha, hora, lugar y contacto de organización del evento

### Requirement: Diseño responsive

El sitio SHALL ser responsivo y SHALL adaptar su maquetado a pantallas móviles y de escritorio.

#### Scenario: Navegación en pantalla móvil

- **WHEN** el usuario abre la página en un dispositivo móvil
- **THEN** las secciones se reorganizan y el contenido permanece legible sin desbordes horizontales

#### Scenario: Navegación en pantalla de escritorio

- **WHEN** el usuario abre la página en un monitor de escritorio
- **THEN** el layout utiliza el ancho completo de forma equilibrada y el contenido se centra correctamente

### Requirement: Despliegue en GitHub Pages

El sitio SHALL poder desplegarse como sitio estático mediante GitHub Pages.

#### Scenario: Publicación del sitio

- **WHEN** los archivos del sitio se publican en GitHub Pages
- **THEN** la página es accesible mediante la URL pública del sitio
