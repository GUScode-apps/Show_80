## Context

El hero de la landing page actual muestra el título "Show de los 80" con la fuente grafiti Bangers y solo el "80" resaltado en neón cian. Se requiere transformar el título en un letrero neón completo con colores por palabra, borde blanco, gradiente, inclinación y brillos, conservando el stack HTML + CSS puro sin JavaScript.

## Goals / Non-Goals

**Goals:**
- Título "SHOW DE LOS 80s" con un color neón distinto por palabra.
- Efecto letrero neón con borde blanco en todas las letras.
- Gradiente vertical claro arriba en todas las palabras.
- Sombra exterior suave de brillo.
- Dos líneas: "SHOW DE" / "LOS 80s", con inclinación suave hacia arriba.
- Chispas de brillo decorativas alrededor del título.
- Mantener CSS puro, sin JS ni imágenes externas.

**Non-Goals:**
- No animar las chispas ni el título (estático por simplicidad y rendimiento).
- No agregar dependencias ni fuentes adicionales.
- No modificar otras secciones de la página.

## Decisions

**D1: Colores por palabra con spans**
El HTML del título se estructura como `<h1 class="hero__title"><span class="neon-word neon-word--pink">SHOW</span> <span class="neon-word neon-word--yellow">DE</span> ...</h1>`. Cada palabra usa su propia clase de color. Se conserva Bangers como fuente grafiti.
*Alternativa:* colores vía CSS `nth-child` sin spans — descartada por requerir spans para separar líneas y aplicar clases claras.

**D2: Borde blanco con `-webkit-text-stroke`**
Se usa `-webkit-text-stroke: 1px #fff` combinado con `paint-order: stroke fill` (si el navegador lo soporta) para que el trazo blanco se dibuje por debajo del relleno y no lo tape. Es el mecanismo estándar para letreros neón en CSS.
*Alternativa:* `text-shadow` blanco multi-direccional — más frágil y con peor resultado visual.

**D3: Gradiente claro arriba con `background-clip: text`**
Cada palabra usa un fondo `linear-gradient(180deg, color-claro, color)` con `-webkit-background-clip: text; -webkit-text-fill-color: transparent`. Como el gradiente cubre el texto, el color "base" por palabra se define dentro del gradiente.
*Alternativa:* color plano — no cumple el requisito de gradiente.

**D4: Sombra exterior suave**
`filter: drop-shadow(0 0 6px color)` (y versiones del color por palabra) para un glow uniforme que sigue el contorno de las letras, incluyendo el trazo blanco.
*Alternativa:* `text-shadow` — descartada porque con `background-clip: text` el `text-shadow` puede quedar oculto.

**D5: Dos líneas con `display: block`**
"SHOW DE" y "LOS 80s" se agrupan cada uno en un `<span class="hero__line">` con `display: block`, garantizando el salto de línea independientemente del ancho.

**D6: Inclinación con `transform: rotate`**
`.hero__title { transform: rotate(-2deg) }` para una inclinación suave hacia arriba (el título sube de izquierda a derecha).

**D7: Chispas con elementos decorativos**
Varias `<span class="spark">` posicionadas alrededor del título, con un pequeño rombo (✧/◆) en color blanco/dorado y glow suave, sin animación.
*Alternativa:* pseudo-elementos `::before`/`::after` — insuficiente para varias chispas en posiciones variadas.

## Risks / Trade-offs

- [`-webkit-text-stroke` / `background-clip: text` dependen de prefijos] → Todos los navegadores modernos (Chrome, Firefox, Edge, Safari) los soportan; se incluyen ambos prefijos `-webkit-` y el estándar.
- [El trazo blanco grueso puede reducir la legibilidad del relleno] → Trazo de 1px y gradiente con tonos suficientemente oscuros en la base.
- [`paint-order` no se aplica en todos los motores] → El trazo se dibuja tras el relleno con `paint-order` donde exista; en el resto el impacto es mínimo con trazo de 1px.
- [`filter: drop-shadow` sobre varias palabras puede ser costoso] → Solo se aplica al título (elemento pequeño), impacto de rendimiento despreciable.
- [Inclinación puede cortar texto en móviles] → Mantener `rotate(-2deg)` sutil y margen/padding en el hero para evitar recortes.

## Migration Plan

Los cambios son aditivos sobre el CSS existente: se añaden nuevas clases sin eliminar las actuales de `.hero__title`. El HTML del `<h1>` se reemplaza por completo. Rollback: revertir el HTML del título y quitar las reglas nuevas.

## Open Questions

- Ninguna pendiente; el usuario definió los colores y disposición.
