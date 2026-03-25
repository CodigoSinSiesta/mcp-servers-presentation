# MCP Servers Presentation

Presentación sobre **MCP Servers** — qué son, cómo construirlos, comparativa TypeScript vs Python FastMCP.

## Stack

- **Framework**: Astro 4.16.19 (static site)
- **Components**: Svelte 5.x
- **Styling**: Tailwind CSS 4.x
- **Animations**: GSAP 3.x
- **Runtime**: pnpm + Node 25.x

## Arquitectura de la Presentación

```
src/
├── components/
│   ├── Navigation.svelte       # Control de slides + keyboard nav
│   └── slides/                 # 10 slides individuales
│       ├── Slide01Hero.svelte
│       ├── Slide02TheProblem.svelte
│       ├── Slide03WhatIsMCP.svelte
│       ├── Slide04MCPPrimitives.svelte
│       ├── Slide05ServerAnatomy.svelte
│       ├── Slide06FastMCPComparison.svelte
│       ├── Slide07Ecosystem.svelte
│       ├── Slide08UseCases.svelte
│       ├── Slide09BestPractices.svelte
│       └── Slide10Closing.svelte
├── layouts/
│   └── PresentationLayout.astro
├── styles/
│   ├── global.css              # Design system tokens + reset
│   └── animations.css          # GSAP animation classes
├── utils/
│   └── animations.ts           # GSAP helpers
└── pages/
    └── index.astro             # Entry point
```

## Design System

### Colors (CSS Custom Properties)
```css
--color-base-dark: #0A1628      /* Fondo oscuro */
--color-primary-cobalt: #1E3A8A  /* Azul cobalto */
--color-accent-bright: #3B82F6   /* Azul brillante */
--color-electric: #60A5FA        /* Azul eléctrico */
--color-neutral-light: #FAF9F6   /* Blanco hueso */
```

### Typography
- **Display**: Space Grotesk (títulos principales)
- **Subheader**: Bricolage Grotesque (subtítulos)
- **Body**: IBM Plex Sans (cuerpo)
- **Mono**: JetBrains Mono (código)

## Slide Structure Pattern

Cada slide sigue este patrón:
```svelte
<div class="swiper-slide">
  <div class="slide-content">
    <!-- header eyebrow + title + subtitle -->
    <!-- main content grid/layout -->
  </div>
</div>
```

El sistema de navegación se basa en CSS (opacity + visibility) + GSAP para las transiciones. NO usar Swiper JS.

## Navegación

- **Teclado**: `←` / `→` para navegar entre slides
- **Botones**: prev/next en los laterales
- **Hash URLs**: `#/slide-name` para enlazar directamente a un slide
- **Contador**: muestra "N/10" en la esquina inferior derecha

## Slide Names (para hash navigation)

```
hero, the-problem, what-is-mcp, mcp-primitives, server-anatomy,
fastmcp-comparison, ecosystem, use-cases, best-practices, closing
```

## Dev Commands

```bash
pnpm dev     # Inicia en http://localhost:4325
pnpm build   # Build para producción
pnpm preview # Preview del build
```

## Deploy

GitHub Pages en: `https://codigosinsiesta.github.io/mcp-servers-presentation`

Base configurada en `astro.config.mjs`: `/mcp-servers-presentation`

## Notas Importantes

- **NO usar `lucide-svelte`** para iconos en los slides — usar inline SVGs en su lugar. La versión instalada tiene un bug de resolución de módulos con Vite.
- **Svelte 5 syntax**: usar `$state()`, `$effect()`, `onclick` (sin `on:click`) para código nuevo. Los slides existentes usan sintaxis de compatibilidad.
- **Tailwind 4**: no usar `tailwind.config.js` para temas — usar CSS custom properties directamente en `global.css`.
