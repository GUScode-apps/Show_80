# Informe de Revisión CSS - SHOW DE LOS 80

**Fecha:** 2025-09-09  
**Archivo analizado:** `css/styles.css` (14.6 KB, ~480 líneas)

---

## 🔴 Issues Críticos / Bugs

| Archivo/Línea | Problema |
|---|---|
| L164, L276 | **Duplicado**: `.crt::after` definido dos veces (línea 164 y 276) |
| L231 | `pointer-events: none` en `.scattered-photos` pero `pointer-events: auto` en hijos - confuso, mejor en contenedor |
| L258 | `@media (max-width: 640px)` duplica reglas que ya están en `@media (min-width: 768px)` - ordenar mobile-first |

---

## 🟡 Mejoras de Mantenibilidad

| Área | Sugerencia |
|---|---|
| **Variables CSS** | Extraer valores mágicos repetidos: `0.55` (opacidad triángulos), `0.18` (scanlines), `8px` (blur header), `4px` (blur footer/registro), `12px` / `18px` / `24px` / `30px` (sombras) |
| **Selectores complejos** | `.neon-word` usa `-webkit-text-stroke` + `background-clip: text` + `filter` - considerar `@supports` fallback o simplificar |
| **Organización** | Agrupar por: 1) Reset/variables 2) Layout 3) Componentes (botones, cards, CRT) 4) Secciones 5) Responsive - ahora está mezclado |
| **Nombrado** | `.scattered-photo--1`...`--4` → usar `nth-child` con `--rotation` / `--position` vars para reducir duplicación |

---

## 🟢 Optimizaciones de Rendimiento

| Tema | Detalle |
|---|---|
| **`filter: drop-shadow` múltiple** | En `.neon-word-*` (3 sombras cada uno) + `.hero__eyebrow` + `.hero__tagline` + `.spark` - costoso en móvil; considerar `will-change: filter` solo en hover/animación |
| **`backdrop-filter`** | Usado en header, footer, registro, organizers - OK pero testear en móviles bajos |
| **`background-attachment: fixed`** | En `body` - puede causar jank en scroll móvil; considerar `@media (hover: hover)` o `prefers-reduced-motion` |
| **Animaciones** | `arrow-bounce` infinita - agregar `prefers-reduced-motion: reduce` para pausar |

---

## 🔵 Accesibilidad / UX

| Falta | Acción |
|---|---|
| **Focus visible** | Ningún `:focus-visible` en botones, enlaces, cards - crítico para teclado |
| **Reduced motion** | Sin `@media (prefers-reduced-motion: reduce)` para `arrow-bounce`, `scroll-behavior: smooth`, transiciones |
| **Contraste** | `--text-dim: #4a3a63` sobre fondos claros/gradientes - verificar WCAG AA |
| **Skip link** | No hay "Saltar al contenido" para navegación por teclado |

---

## 📝 Limpieza Menor (Slop/Verbosity)

- **L12-14**: Reset `margin: 0; padding: 0;` en `*` + `::before` + `::after` - `box-sizing` basta, márgenes/paddings se heredan
- **L89**: `.hero__line { display: block; margin-block: -0.18em; }` - `margin-block` solo afecta si hay siblings, podría ser `line-height`
- **L198**: `.btn` define `transition` en 3 propiedades - agrupar `transition: transform .15s, box-shadow .15s, background .15s;`
- **L295**: `.organizers__grid { max-width: 720px; margin: 0 auto; }` - duplicado de `.container` lógica

---

## 🎯 Prioridad Sugerida

1. **Fix duplicado `.crt::after`** (bug real)
2. **Añadir `:focus-visible` global** (accesibilidad)
3. **Mobile-first responsive** (reordenar media queries)
4. **Variables para magic numbers** (mantenibilidad)
5. **`prefers-reduced-motion`** (respeto usuario)
6. **Consolidar selectores scattered photos** (DRY)

---

## Próximos Pasos

¿Quieres que implemente alguna de estas mejoras? Indica cuáles (por número o área) y procedo.