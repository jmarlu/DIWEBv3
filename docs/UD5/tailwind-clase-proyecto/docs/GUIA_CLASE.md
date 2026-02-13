# Guía rápida de clase (Tailwind v4.1)

## Objetivo de la sesión
- Entender el flujo de trabajo real con Tailwind v4.1.
- Construir una página con utilidades, componentes y responsive.

## Orden recomendado para explicar
1. Setup mínimo:
   - `npm install -D tailwindcss @tailwindcss/cli`
   - `@import "tailwindcss";`
   - `npm run dev`
2. Utilidades básicas (`bg-*`, `text-*`, `m-*`, `p-*`, `border-*`).
3. Tokens con `@theme`:
   - Colores personalizados (`--color-*`)
   - Sombras (`--shadow-*`)
   - Animaciones (`--animate-*` + `@keyframes`)
4. Reutilización:
   - `@layer components`
   - `@apply`
5. Responsive:
   - Prefijos `sm: md: lg:`
   - Estrategia `max-md:`

## Comandos
```bash
npm run dev
npm run build
```

## Archivos clave
- `public/index.html`: demo completa de los ejemplos.
- `src/styles.css`: `@theme`, `@layer base`, `@layer components`.
