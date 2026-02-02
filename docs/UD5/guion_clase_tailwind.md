# Guion de Clase: Tailwind CSS

## 📋 Información General
- **Tema**: Introducción y práctica con Tailwind CSS
- **Duración**: 3 sesiones de 2 horas (6 horas totales)
- **Nivel**: Intermedio
- **Prerequisitos**: Conocimientos sólidos de HTML y CSS

---

## 🎯 Objetivos de Aprendizaje

Al finalizar estas sesiones, el alumnado será capaz de:

1. Comprender qué es Tailwind CSS y sus diferencias con otros frameworks
2. Instalar y configurar Tailwind CSS en un proyecto desde cero
3. Utilizar clases de utilidad para estilizar elementos HTML
4. Crear componentes reutilizables con `@layer` y `@apply`
5. Personalizar el tema de Tailwind (colores, fuentes, animaciones, sombras)
6. Implementar diseño responsive con breakpoints personalizados
7. Crear animaciones y transiciones personalizadas
8. Construir layouts completos con Flexbox y Grid
9. Dominar el flujo de trabajo con el **Laboratorio Proyectable**

---

# 🧪 EL LABORATORIO PROYECTABLE (Novedad)

Para facilitar las explicaciones en clase, disponemos de una carpeta `/lab` configurada para proyectar ejemplos en directo.

### Estructura del Lab:
- `index.html`: Tu lienzo en blanco para codificar en vivo.
- `src/styles.css`: Base de Tailwind lista para usar.
- `examples/`: Ficheros HTML aislados con demos técnicas (proyectar directamente).
- `package.json`: Scripts listos (`npm run dev`).

### Cómo usarlo en clase:
1. Abre una terminal en la carpeta `/lab`.
2. Ejecuta `npm install` (solo la primera vez).
3. Ejecuta `npm run dev` para activar el "watch mode".
4. Abre `index.html` en el navegador y edita el código durante la sesión.

---

# 📅 SESIÓN 1: Fundamentos y Configuración (2 horas)

## ⏱️ Bloque 1: Introducción Teórica (20 min)

### ¿Qué es Tailwind CSS?

**Definición:**
- Framework CSS basado en **clases de utilidad** (utility-first)
- Desarrollo ágil con clases predefinidas que mapean propiedades CSS
- Optimización automática mediante PostCSS
- Solo incluye en producción las clases que realmente usas

**Comparación con otros frameworks:**

| Característica | Tailwind | Bootstrap |
|----------------|----------|-----------|
| Enfoque | Clases de utilidad | Componentes preconstruidos |
| Personalización | Total libertad | Limitada (requiere override) |
| Tamaño CSS | Solo lo que usas | Todo el framework |
| Curva aprendizaje | Requiere conocer CSS | Más rápido al inicio |

**Ventajas:**
- ✅ Desarrollo rápido y ágil
- ✅ Altamente personalizable
- ✅ CSS optimizado (tree-shaking automático)
- ✅ Flujo de trabajo moderno con PostCSS
- ✅ No hay conflictos de nombres de clases
- ✅ Diseños únicos (no se ve "Bootstrap-like")

**Desventajas:**
- ❌ Requiere conocimiento sólido de CSS
- ❌ No trae componentes listos para usar
- ❌ HTML con muchas clases (puede parecer "inline styles")
- ❌ Curva de aprendizaje inicial empinada

> **💡 Pregunta para reflexión**: ¿En qué tipo de proyectos usarías Tailwind vs Bootstrap?

**Respuesta esperada:** Tailwind para proyectos personalizados, aplicaciones web modernas, cuando se necesita diseño único. Bootstrap para prototipos rápidos, proyectos con diseño estándar.

---

## ⏱️ Bloque 2: Instalación y Configuración (30 min)

### Paso 1: Preparar el entorno

```bash
# Crear directorio del proyecto
mkdir proyecto-tailwind
cd proyecto-tailwind

# Inicializar proyecto npm
npm init -y
```

> **📝 Explicar**: `npm init -y` crea `package.json` con valores por defecto

---

### Paso 2: Instalar dependencias

```bash
npm install -D tailwindcss@latest @tailwindcss/cli@latest
```

**Explicar cada paquete:**
- `tailwindcss`: El framework principal
- `@tailwindcss/cli`: CLI oficial para compilar en local
- `-D` (alias de `--save-dev`): Dependencia de desarrollo

---

### Paso 3: Estructura de carpetas

```
proyecto-tailwind/
├── src/
│   └── styles.css          # CSS fuente (sin compilar)
├── css/
│   └── styles.css          # CSS compilado (generado automáticamente)
├── img/                    # Imágenes del proyecto
├── index.html              # Página principal
├── package.json            # Configuración npm
└── package-lock.json        # Dependencias bloqueadas (auto)
```

**Crear carpetas:**
```bash
mkdir src css img
```

---

### Paso 4: Crear archivo fuente CSS

Crear `src/styles.css`:

```css
@import "tailwindcss";
```

**Explicar la directiva moderna:**
- `@import "tailwindcss"`: Carga Preflight + utilidades + variantes
- En Tailwind v4 la configuración principal se hace en CSS (`@theme`, `@utility`)

---

### Paso 5: Compilar CSS (sin `tailwind.config.js`)

```bash
npx @tailwindcss/cli -i ./src/styles.css -o ./css/styles.css --watch
```

**Explicar:**
- En Tailwind v4 no es obligatorio crear `tailwind.config.js`
- El CLI detecta automáticamente clases en tus plantillas
- Si necesitas forzar rutas, se usa `@source` dentro del CSS

---

### Paso 6: Entender el comando de compilación

**Explicar opciones:**
- `-i`: Input (archivo fuente)
- `-o`: Output (archivo compilado)
- `--watch`: Recompila automáticamente al detectar cambios

---

### Paso 7: Ejecutar en modo desarrollo

Editar `package.json`:

```json
{
  "scripts": {
    "dev": "tailwindcss -i ./src/styles.css -o ./css/styles.css --watch",
    "build": "tailwindcss -i ./src/styles.css -o ./css/styles.css --minify"
  }
}
```

**Ahora ejecutar:**
```bash
npm run dev
```

> **💡 Consejo**: Dejar esta terminal abierta durante el desarrollo

---

## ⏱️ Bloque 3: Primeros Pasos (40 min)

### Crear HTML básico

Crear `index.html`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mi Proyecto Tailwind</title>
  <link rel="stylesheet" href="./css/styles.css">
</head>
<body>
  <h1>Hola Mundo</h1>
  <ul>
    <li>Manzana</li>
    <li>Pera</li>
    <li>Limón</li>
  </ul>
</body>
</html>
```

**Abrir en navegador y observar:**
- Tailwind aplica un **reset CSS** automático
- Fuente sans-serif por defecto
- Sin márgenes ni estilos predeterminados

---

### Aplicar primeras clases de utilidad

```html
<h1 class="text-2xl">Hola Mundo</h1>
```

**Mostrar en DevTools:** `font-size: 1.5rem; /* 24px */`

**Añadir más clases:**

```html
<h1 class="text-2xl bg-black text-white m-5 p-5 border-8 border-yellow-900 text-center">
  Hola Mundo
</h1>
```

**Explicar cada clase paso a paso:**

| Clase | Propiedad CSS | Valor |
|-------|---------------|-------|
| `text-2xl` | `font-size` | `1.5rem` (24px) |
| `bg-black` | `background-color` | `#000000` |
| `text-white` | `color` | `#ffffff` |
| `m-5` | `margin` | `1.25rem` (20px) |
| `p-5` | `padding` | `1.25rem` (20px) |
| `border-8` | `border-width` | `8px` |
| `border-yellow-900` | `border-color` | `#713f12` |
| `text-center` | `text-align` | `center` |

---

### Explorar la paleta de colores

**Mostrar documentación de colores:** [https://tailwindcss.com/docs/customizing-colors](https://tailwindcss.com/docs/customizing-colors)

**Explicar sistema de intensidades:**
- `50`: Muy claro
- `100-400`: Tonos claros
- `500`: Tono base
- `600-900`: Tonos oscuros
- `950`: Muy oscuro (en algunos colores)

**Ejemplos:**
```html
<div class="bg-blue-100">Azul muy claro</div>
<div class="bg-blue-500">Azul base</div>
<div class="bg-blue-900">Azul muy oscuro</div>
```

**Opacidad:**
```html
<div class="bg-blue-500/50">Azul al 50% de opacidad</div>
<div class="bg-blue-500/75">Azul al 75% de opacidad</div>
```

---

### Ejercicio Práctico 1: Tarjeta Básica (15 min)

**Objetivo:** Crear una tarjeta de presentación personal

**Requisitos:**
- Fondo de color
- Borde redondeado
- Sombra
- Padding interno
- Título y descripción con diferentes tamaños

**Solución:**

```html
<div class="bg-white border-2 border-gray-300 rounded-lg shadow-lg p-6 m-5 max-w-sm">
  <h2 class="text-3xl font-bold text-blue-600 mb-3">Juan Pérez</h2>
  <p class="text-gray-700 text-base">
    Desarrollador Full Stack apasionado por crear experiencias web increíbles.
  </p>
  <button class="mt-4 bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">
    Contactar
  </button>
</div>
```

**Clases nuevas explicadas:**
- `rounded-lg`: Bordes redondeados grandes
- `shadow-lg`: Sombra grande
- `max-w-sm`: Ancho máximo pequeño (24rem)
- `font-bold`: Negrita
- `mb-3`: Margen inferior de 0.75rem
- `px-4`: Padding horizontal de 1rem
- `py-2`: Padding vertical de 0.5rem
- `hover:bg-blue-600`: Cambiar fondo al hacer hover

---

## ⏱️ Bloque 4: Flexbox con Tailwind (30 min)

### Conceptos básicos de Flex

```html
<div class="flex">
  <div class="bg-red-500 p-4">Item 1</div>
  <div class="bg-blue-500 p-4">Item 2</div>
  <div class="bg-green-500 p-4">Item 3</div>
</div>
```

**Clases de dirección:**
- `flex-row`: Horizontal (por defecto)
- `flex-col`: Vertical
- `flex-row-reverse`: Horizontal invertido
- `flex-col-reverse`: Vertical invertido

**Clases de alineación:**
- `justify-start`: Inicio (horizontal)
- `justify-center`: Centro (horizontal)
- `justify-end`: Final (horizontal)
- `justify-between`: Espacio entre elementos
- `items-start`: Inicio (vertical)
- `items-center`: Centro (vertical)
- `items-end`: Final (vertical)

**Clases de crecimiento:**
- `flex-1`: Crece y se encoge según espacio disponible
- `flex-none`: No crece ni se encoge
- `flex-auto`: Crece según contenido

---

### Ejercicio Práctico 2: Barra de Navegación (15 min)

**Objetivo:** Crear una barra de navegación horizontal

```html
<nav class="bg-gray-800 text-white">
  <div class="container mx-auto flex justify-between items-center p-4">
    <div class="text-2xl font-bold">MiLogo</div>
    <ul class="flex space-x-6">
      <li><a href="#" class="hover:text-blue-400">Inicio</a></li>
      <li><a href="#" class="hover:text-blue-400">Servicios</a></li>
      <li><a href="#" class="hover:text-blue-400">Contacto</a></li>
    </ul>
  </div>
</nav>
```

**Clases nuevas:**
- `container`: Ancho máximo según breakpoint
- `mx-auto`: Centrar horizontalmente (margin-left y margin-right auto)
- `justify-between`: Espacio entre logo y menú
- `space-x-6`: Espacio horizontal entre elementos hijos

---

# 📅 SESIÓN 2: Personalización y Componentes (2 horas)

## ⏱️ Bloque 1: Personalización del Tema (40 min)

### A. Añadir imagen de fondo personalizada

**Opción 1: CSS personalizado en `src/styles.css`**

```css
@import "tailwindcss";

@utility bg-pattern {
  background-image: url("../img/pattern.png");
}
```

Usar: `<body class="bg-pattern">`

---

**Opción 2: Usar `@layer base`** (recomendado para estilos globales)

```css
@layer base {
  body {
    background-image: url("../img/pattern.png");
    background-repeat: repeat;
  }
}
```

---

**Opción 3: Token de tema con `@theme`** (recomendado en Tailwind v4)

En `src/styles.css`:

```css
@theme {
  --background-image-body-pattern: url("../img/pattern.png");
  --background-image-hero-pattern: url("../img/hero.jpg");
}
```

Usar: `<body class="bg-body-pattern">`

---

### B. Crear colores personalizados

En `src/styles.css` con `@theme`:

```css
@theme {
  --color-azul-claro: #84b6f4;
  --color-azul-oscuro: #005187;
  --color-brand-50: #f0f9ff;
  --color-brand-100: #e0f2fe;
  --color-brand-500: #0ea5e9;
  --color-brand-900: #0c4a6e;
}
```

**Usar en cualquier clase de color:**
- `bg-azul-claro`
- `text-azul-oscuro`
- `border-brand-500`
- `hover:bg-brand-900`

---

### C. Incrustar fuentes personalizadas

**Paso 1:** Crear carpeta `css/fonts/` y copiar archivos de fuentes

**Paso 2:** En `src/styles.css`:

```css
@layer base {
  @font-face {
    font-family: "BebasNeue";
    src: url("fonts/BebasNeue.otf");
    font-weight: normal;
    font-style: normal;
  }

  @font-face {
    font-family: "TrebuchetMS";
    src: url("fonts/TrebuchetMS.ttf");
    font-weight: normal;
    font-style: normal;
  }

  @font-face {
    font-family: "WebSymbolsRegular";
    src: url("fonts/websymbols-regular-webfont.woff") format("woff"),
         url("fonts/websymbols-regular-webfont.ttf") format("truetype");
    font-weight: normal;
    font-style: normal;
  }

  .bebas {
    font-family: "BebasNeue", sans-serif;
  }
  
  .trebuchet {
    font-family: "TrebuchetMS", sans-serif;
  }
  
  .symbol {
    font-family: "WebSymbolsRegular";
  }
}
```

**Usar:**
```html
<h1 class="bebas text-4xl">TÍTULO GRANDE</h1>
<span class="symbol text-2xl">S</span>
```

---

### D. Crear sombras personalizadas

En `src/styles.css` con `@theme`:

```css
@theme {
  --shadow-header3D: 0px 1px #393d3f, 1px 2px 0px #393d3f, 2px 3px 0px #393d3f, 3px 4px 0px #393d3f;
  --shadow-box: 0px 0px 1px rgba(0,0,0,0.3), 0px 3px 7px rgba(0,0,0,0.3), 0px 1px white inset, 0px -3px 1px rgba(0,0,0,0.3) inset;
}
```

**Usar:**
```html
<h2 class="shadow-header3D">Título con efecto 3D</h2>
<div class="shadow-box">Caja con sombra compleja</div>
```

---

## ⏱️ Bloque 2: Crear Componentes Reutilizables (30 min)

### Problema: Repetición de clases

**HTML repetitivo:**
```html
<button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">Guardar</button>
<button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">Enviar</button>
<button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">Continuar</button>
```

---

### Solución: Componentes con `@utility` (enfoque recomendado en v4)

En `src/styles.css`:

```css
@utility btn-primary {
  @apply bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition duration-200;
}

@utility btn-secondary {
  @apply bg-gray-500 text-white px-4 py-2 rounded hover:bg-gray-600 transition duration-200;
}

@utility btn-danger {
  @apply bg-red-500 text-white px-4 py-2 rounded hover:bg-red-600 transition duration-200;
}
```

**Usar:**
```html
<button class="btn-primary">Guardar</button>
<button class="btn-secondary">Cancelar</button>
<button class="btn-danger">Eliminar</button>
```

---

### Crear componente de menú

En `src/styles.css`:

```css
@utility menu-item {
  @apply mr-5 ml-5 tracking-wider;
}

@utility menu-item-a {
  @apply block transition duration-200 hover:text-azul-oscuro transform hover:scale-125;
}
```

**Usar:**
```html
<nav>
  <ul class="flex flex-row h-20 items-center justify-end text-2xl">
    <li class="menu-item">
      <a class="menu-item-a" href="#">INICIO</a>
    </li>
    <li class="menu-item">
      <a class="menu-item-a" href="#">CONTACTO</a>
    </li>
    <li class="menu-item">
      <a class="menu-item-a" href="#">PERFIL</a>
    </li>
  </ul>
</nav>
```

---

## ⏱️ Bloque 3: Ejemplo Completo - Header (40 min)

### HTML del Header

```html
<header class="bg-black text-white bebas">
  <div class="container w-11/12 mx-auto flex flex-row items-center">
    <!-- Logo -->
    <div class="flex-1" id="logo">
      <div class="overflow-hidden w-72 pt-0.5 pb-0.5 text-center tracking-wider transition duration-100 rounded-sm bg-azul-claro hover:text-black hover:bg-white">
        <span class="symbol block float-left text-3xl mt-1 ml-11">S</span>
        <h3 class="block float-right text-4xl mt-1.5 mr-14">INFORMÁTICA</h3>
      </div>
    </div>
    
    <!-- Menú -->
    <nav class="flex-1">
      <ul class="flex flex-row h-20 items-center justify-end text-2xl text-center mr-6">
        <li class="menu-item">
          <a class="menu-item-a" href="#">INICIO</a>
        </li>
        <li class="menu-item">
          <a class="menu-item-a" href="#">CONTACTO</a>
        </li>
        <li class="menu-item">
          <a class="menu-item-a" href="#">PERFIL</a>
        </li>
      </ul>
    </nav>
  </div>
</header>
```

---

### Clases importantes explicadas

| Clase | Función |
|-------|---------|
| `container` | Ancho fijo según breakpoint |
| `w-11/12` | 91.67% de ancho |
| `mx-auto` | Centrar horizontalmente |
| `flex flex-row` | Flexbox horizontal |
| `flex-1` | Crecer/encoger según espacio |
| `items-center` | Alinear verticalmente al centro |
| `tracking-wider` | Espaciado entre letras |
| `transition duration-100` | Transición de 100ms |
| `rounded-sm` | Bordes ligeramente redondeados |
| `overflow-hidden` | Ocultar contenido desbordado |
| `float-left` / `float-right` | Flotación |

---

### Ejercicio Práctico 3: Personalizar el Header (10 min)

**Modificar el header para:**
1. Cambiar los colores personalizados
2. Añadir un efecto de sombra al hacer hover
3. Cambiar el símbolo del logo
4. Añadir un cuarto elemento al menú

---

# 📅 SESIÓN 3: Animaciones y Responsive (2 horas)

## ⏱️ Bloque 1: Animaciones (40 min)

### A. Animaciones predefinidas

Tailwind incluye 4 animaciones básicas:

```html
<div class="animate-spin">Girando</div>
<div class="animate-ping">Ping</div>
<div class="animate-pulse">Pulsando</div>
<div class="animate-bounce">Rebotando</div>
```

**Ejemplo práctico:**
```html
<span class="animate-spin symbol text-3xl">S</span>
```

---

### B. Modificar animación existente

**Problema:** La animación `spin` es muy rápida

**Solución:** Crear variantes en `@theme`

En `src/styles.css`:

```css
@theme {
  --animate-spin-slow: spin 3s linear infinite;
  --animate-spin-slower: spin 5s linear infinite;
}
```

**Usar:**
```html
<span class="animate-spin-slow symbol">S</span>
```

---

### C. Crear animación personalizada

En `src/styles.css`:

```css
@theme {
  --animate-wiggle: wiggle 2s linear infinite;
  --animate-fade-in: fadeIn 1s ease-in;
  --animate-slide-in: slideIn 0.5s ease-out;

  @keyframes wiggle {
    0%, 100% { transform: rotate(-3deg); }
    50% { transform: rotate(3deg); }
  }

  @keyframes fadeIn {
    0% { opacity: 0; }
    100% { opacity: 1; }
  }

  @keyframes slideIn {
    0% { transform: translateX(-100%); }
    100% { transform: translateX(0); }
  }
}
```

**Usar:**
```html
<h3 class="animate-wiggle">INFORMÁTICA</h3>
<div class="animate-fade-in">Apareciendo...</div>
<div class="animate-slide-in">Deslizándose...</div>
```

---

### D. Modificadores de grupo (`group` y `group-hover`)

**Problema:** Quiero que al hacer hover en el padre, los hijos cambien

**Solución:** Usar `group` y `group-hover:`

```html
<div class="group bg-azul-claro hover:bg-white p-4">
  <span class="animate-spin-slow group-hover:animate-none symbol">S</span>
  <div class="invisible group-hover:visible">¡Estoy aquí!</div>
  <h3 class="text-black group-hover:animate-wiggle">INFORMÁTICA</h3>
</div>
```

**Explicación:**
1. `group`: Marca el elemento padre
2. `group-hover:animate-none`: Detiene animación al hover en padre
3. `invisible` / `group-hover:visible`: Muestra elemento oculto

---

### Ejercicio Práctico 4: Tarjeta Animada (15 min)

**Crear una tarjeta que:**
- Tenga una imagen
- Al hacer hover, la imagen haga zoom
- El texto cambie de color
- Aparezca un botón desde abajo

**Solución:**

```html
<div class="group max-w-sm rounded-lg overflow-hidden shadow-lg hover:shadow-2xl transition-shadow duration-300">
  <div class="overflow-hidden">
    <img 
      class="w-full transform group-hover:scale-110 transition-transform duration-500" 
      src="img/producto.jpg" 
      alt="Producto"
    >
  </div>
  <div class="p-6">
    <h3 class="text-2xl font-bold mb-2 group-hover:text-blue-600 transition-colors">
      Producto Increíble
    </h3>
    <p class="text-gray-700 mb-4">
      Descripción del producto que cambia al hacer hover.
    </p>
    <button class="opacity-0 group-hover:opacity-100 transform translate-y-4 group-hover:translate-y-0 transition-all duration-300 bg-blue-500 text-white px-4 py-2 rounded">
      Comprar Ahora
    </button>
  </div>
</div>
```

---

## ⏱️ Bloque 2: Diseño Responsive (50 min)

### Breakpoints predefinidos

Tailwind usa **mobile-first** (min-width por defecto):

| Prefijo | Tamaño | Equivalente CSS |
|---------|--------|-----------------|
| (sin prefijo) | 0px+ | Móvil |
| `sm:` | 640px+ | `@media (min-width: 640px)` |
| `md:` | 768px+ | `@media (min-width: 768px)` |
| `lg:` | 1024px+ | `@media (min-width: 1024px)` |
| `xl:` | 1280px+ | `@media (min-width: 1280px)` |
| `2xl:` | 1536px+ | `@media (min-width: 1536px)` |

---

### Ejemplo visual: Bordes de colores

```html
<header class="
  border-8 
  border-red-600 
  sm:border-yellow-400 
  md:border-green-600 
  lg:border-blue-600 
  xl:border-indigo-900 
  2xl:border-purple-600
">
  Cambia el tamaño de la ventana
</header>
```

**Comportamiento:**
- 0-639px: Borde rojo
- 640-767px: Borde amarillo
- 768-1023px: Borde verde
- 1024-1279px: Borde azul
- 1280-1535px: Borde índigo
- 1536px+: Borde morado

---

### Personalizar breakpoints

En `src/styles.css`:

```css
@theme {
  --breakpoint-xs: 30rem;   /* 480px */
  --breakpoint-3xl: 120rem; /* 1920px */
}
```

**Uso:**
- `xs:` activa desde 480px
- `3xl:` activa desde 1920px
- `max-md:` aplica hasta 767px

---

### Ejemplo: Grid Responsive

```html
<div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
  <div class="bg-blue-500 p-4">Item 1</div>
  <div class="bg-blue-500 p-4">Item 2</div>
  <div class="bg-blue-500 p-4">Item 3</div>
  <div class="bg-blue-500 p-4">Item 4</div>
  <div class="bg-blue-500 p-4">Item 5</div>
  <div class="bg-blue-500 p-4">Item 6</div>
</div>
```

**Comportamiento:**
- Móvil: 1 columna
- Tablet pequeña (640px+): 2 columnas
- Tablet grande (768px+): 3 columnas
- Desktop (1024px+): 4 columnas

---

### Ejemplo: Menú Responsive

```html
<div class="container w-11/12 mx-auto flex flex-col md:flex-row items-center">
  <div class="w-full md:w-auto md:flex-1">
    <div class="bg-azul-claro text-center md:text-left p-4">
      <span class="symbol">S</span>
      <h3>INFORMÁTICA</h3>
    </div>
  </div>
  
  <nav class="w-full md:w-auto md:flex-1">
    <ul class="flex flex-col md:flex-row items-center justify-center md:justify-end space-y-2 md:space-y-0 md:space-x-6">
      <li class="w-full md:w-auto text-center">
        <a href="#">INICIO</a>
      </li>
      <li class="w-full md:w-auto text-center">
        <a href="#">CONTACTO</a>
      </li>
      <li class="w-full md:w-auto text-center">
        <a href="#">PERFIL</a>
      </li>
    </ul>
  </nav>
</div>
```

**Comportamiento:**
- Móvil: Logo y menú en columna, menú vertical
- Desktop (768px+): Logo y menú en fila, menú horizontal

---

### Incluir responsive en componentes

En `src/styles.css`:

```css
@layer components {
  .menu-item {
    @apply mr-5 ml-5 tracking-wider max-md:flex-1 max-md:text-center;
  }
}
```

---

## ⏱️ Bloque 3: Layout Completo (30 min)

### Estructura Main con Aside y Section

```html
<main class="container w-11/12 mx-auto mt-5 flex flex-col lg:flex-row gap-6">
  <!-- Aside (Sidebar) -->
  <aside class="w-full lg:w-1/4 lg:order-2">
    <h3 class="bg-gray-800 text-white text-center p-3 rounded-t-lg">
      Buscar
    </h3>
    <div class="bg-white p-4 rounded-b-lg shadow">
      <form>
        <input 
          class="w-full p-2 border border-gray-300 rounded focus:outline-none focus:border-blue-500" 
          type="text" 
          placeholder="Buscar..."
        >
      </form>
    </div>
    
    <h3 class="bg-gray-800 text-white text-center p-3 rounded-t-lg mt-6">
      LOGIN
    </h3>
    <div class="bg-white p-4 rounded-b-lg shadow">
      <form class="space-y-4">
        <input 
          class="w-full p-2 border border-gray-300 rounded" 
          type="email" 
          placeholder="Email"
        >
        <input 
          class="w-full p-2 border border-gray-300 rounded" 
          type="password" 
          placeholder="Contraseña"
        >
        <button class="w-full bg-blue-500 text-white p-2 rounded hover:bg-blue-600">
          Entrar
        </button>
      </form>
    </div>
  </aside>
  
  <!-- Section (Artículos) -->
  <section class="w-full lg:w-3/4">
    <h2 class="articles-header">Últimos artículos</h2>
    
    <article class="bg-white rounded-lg shadow-lg p-6 mb-6">
      <div class="flex gap-4 text-sm text-gray-600 mb-3">
        <span>📅 Fecha: 30/01/2026</span>
        <span>📂 Categoría: Tecnología</span>
      </div>
      <h4 class="text-2xl font-bold mb-4">
        <a href="#" class="hover:text-blue-600">Título del artículo</a>
      </h4>
      <figure class="mb-4">
        <img 
          class="w-full h-64 object-cover rounded" 
          src="./img/articulo1.jpg" 
          alt="Imagen del artículo"
        >
      </figure>
      <p class="text-gray-700">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. 
        Est, obcaecati accusamus facilis libero eveniet nemo architecto 
        recusandae excepturi optio explicabo dolore voluptate quasi numquam 
        dolorem repudiandae expedita similique saepe deserunt?
      </p>
    </article>
    
    <!-- Más artículos... -->
  </section>
</main>
```

**Clases importantes:**
- `lg:w-1/4`: 25% de ancho en desktop
- `lg:w-3/4`: 75% de ancho en desktop
- `lg:order-2`: Cambiar orden visual en desktop
- `gap-6`: Espacio entre elementos flex/grid
- `object-cover`: Imagen cubre contenedor sin distorsión

---

### Componente de artículo

En `src/styles.css`:

```css
@layer components {
  .articles-header {
    font-family: "BebasNeue";
    @apply w-full h-16 text-center text-5xl tracking-widest pt-4 bg-slate-50 shadow-header3D font-medium mb-6;
  }
  
  .article-item {
    @apply bg-white rounded-lg shadow-lg p-6 mb-6 hover:shadow-2xl transition-shadow duration-300;
  }
  
  .article-title {
    @apply text-2xl font-bold mb-4 hover:text-blue-600 transition-colors;
  }
  
  .article-figure {
    @apply mb-4 overflow-hidden rounded;
  }
  
  .article-figure img {
    @apply w-full h-64 object-cover transform hover:scale-105 transition-transform duration-500;
  }
}
```

---

## ⏱️ Bloque 4: Ejercicio Final (30 min)

### Proyecto: Landing Page Completa

**Requisitos:**

1. **Header:**
   - Logo personalizado
   - Menú responsive (hamburguesa en móvil)
   - Fondo degradado

2. **Hero Section:**
   - Imagen de fondo
   - Título grande con animación
   - Botón call-to-action

3. **Sección de Características:**
   - Grid de 3 columnas (responsive)
   - Iconos o imágenes
   - Hover effects

4. **Footer:**
   - Información de contacto
   - Redes sociales
   - Copyright

**Tiempo:** 25 minutos de trabajo + 5 minutos de presentación

---

# 📖 Recursos Adicionales

## Documentación y Herramientas

- **Documentación oficial**: [https://tailwindcss.com/docs](https://tailwindcss.com/docs)
- **Tailwind Play**: [https://play.tailwindcss.com/](https://play.tailwindcss.com/) - Editor online
- **Cheat Sheet**: [https://nerdcave.com/tailwind-cheat-sheet](https://nerdcave.com/tailwind-cheat-sheet)
- **Tailwind UI**: [https://tailwindui.com/](https://tailwindui.com/) - Componentes premium
- **Headless UI**: [https://headlessui.com/](https://headlessui.com/) - Componentes accesibles

## Extensiones VS Code

- **Tailwind CSS IntelliSense**: Autocompletado de clases
- **Tailwind Docs**: Documentación integrada
- **Headwind**: Ordena clases automáticamente

## Inspiración

- **Tailwind Components**: [https://tailwindcomponents.com/](https://tailwindcomponents.com/)
- **Tailwind Toolbox**: [https://www.tailwindtoolbox.com/](https://www.tailwindtoolbox.com/)

---

# ✅ Evaluación

## Criterios de Evaluación

| Criterio | Peso | Descripción |
|----------|------|-------------|
| Instalación y configuración | 15% | Correcta instalación de Tailwind, configuración de archivos |
| Uso de clases de utilidad | 25% | Aplicación apropiada de clases, conocimiento de la documentación |
| Personalización del tema | 20% | Colores, fuentes, animaciones, sombras personalizadas |
| Componentes reutilizables | 20% | Uso de `@layer` y `@apply`, organización del código |
| Diseño responsive | 20% | Implementación correcta de breakpoints, adaptación móvil/desktop |

## Rúbrica Detallada

### Excelente (9-10)
- Instalación perfecta y configuración optimizada
- Uso avanzado de clases con modificadores complejos
- Personalización completa del tema
- Componentes bien estructurados y reutilizables
- Diseño totalmente responsive con breakpoints personalizados

### Notable (7-8)
- Instalación correcta con configuración funcional
- Uso correcto de clases básicas y algunos modificadores
- Personalización de colores y fuentes
- Algunos componentes reutilizables
- Diseño responsive básico

### Aprobado (5-6)
- Instalación funcional
- Uso básico de clases de utilidad
- Personalización mínima
- Pocos componentes reutilizables
- Responsive limitado

### Suspenso (0-4)
- Errores en instalación
- Uso incorrecto de clases
- Sin personalización
- Sin componentes
- Sin responsive

---

# 💡 Consejos para el Profesor

## Metodología

1. **Mostrar siempre la documentación**: Tailwind tiene excelente documentación visual
2. **Comparar con CSS vanilla**: Mostrar equivalencia entre clases y CSS
3. **Usar Live Server**: Ver cambios en tiempo real
4. **Inspeccionar en DevTools**: Mostrar CSS generado
5. **Práctica guiada**: Construir componentes paso a paso
6. **Pair programming**: Que trabajen en parejas

## Errores Comunes del Alumnado

### Error 1: No se detectan clases nuevas
**Síntoma:** Escribes clases en HTML pero no aparecen en el CSS
**Solución:** Verificar que el HTML está dentro del proyecto y añadir `@source` en `src/styles.css` si hace falta (ejemplo: `@source "./**/*.{html,js}";`)

### Error 2: No ejecutar `npm run dev`
**Síntoma:** Los cambios no se reflejan
**Solución:** Asegurarse de que el proceso de compilación está corriendo

### Error 3: Enlazar CSS incorrecto
**Síntoma:** No se aplican estilos
**Solución:** Verificar `<link href="./css/styles.css">` (archivo compilado, no fuente)

### Error 4: Usar clases que no existen
**Síntoma:** Estilos no se aplican
**Solución:** Consultar documentación, verificar sintaxis exacta

### Error 5: Definir tokens fuera de `@theme`
**Síntoma:** No se generan utilidades como `bg-mi-color` o `shadow-mi-sombra`
**Solución:** Declarar tokens dentro de `@theme` usando namespaces correctos (`--color-*`, `--shadow-*`, `--animate-*`)

---

# 🔄 Flujo de Trabajo Recomendado

```
1. Planificar diseño (wireframe/mockup)
   ↓
2. Crear estructura HTML semántica
   ↓
3. Aplicar clases de utilidad de Tailwind
   ↓
4. Identificar patrones repetitivos
   ↓
5. Crear utilidades/componentes con `@utility` (o `@layer` cuando convenga)
   ↓
6. Personalizar tema según necesidades
   ↓
7. Implementar responsive design
   ↓
8. Añadir animaciones y detalles finales
   ↓
9. Optimizar para producción (npm run build)
```

---

# ❓ Preguntas Frecuentes

**P: ¿No es malo tener tantas clases en el HTML?**
R: Aunque parece "inline styles", Tailwind ofrece ventajas: reutilización mediante componentes, optimización automática, y mantenibilidad al tener estilos junto al markup. Además, en producción solo se incluyen las clases usadas.

**P: ¿Cuándo usar Tailwind vs CSS personalizado?**
R: Tailwind para desarrollo rápido, prototipos, y proyectos con diseños personalizados. CSS personalizado para animaciones muy específicas o cuando el equipo prefiere separación estricta de estilos.

**P: ¿Cómo memorizar todas las clases?**
R: No es necesario memorizarlas todas. Con la práctica se aprenden las más comunes. La documentación y el autocompletado de VS Code son tus mejores aliados.

**P: ¿Funciona con React, Vue, Angular?**
R: Sí, Tailwind se integra perfectamente con cualquier framework JavaScript moderno. Hay guías específicas en la documentación oficial.

**P: ¿Qué pasa con el tamaño del CSS final?**
R: En desarrollo, el CSS es grande (incluye todas las clases). En producción, Tailwind elimina automáticamente las clases no usadas (tree-shaking), resultando en archivos muy pequeños (típicamente < 10KB comprimido).

**P: ¿Puedo usar Tailwind con Bootstrap?**
R: Técnicamente sí, pero no es recomendable. Ambos frameworks tienen estilos base que pueden entrar en conflicto. Es mejor elegir uno u otro.

---

# 📝 Tareas para Casa

## Tarea 1: Blog Personal (Básico)
Crear una página de blog con:
- Header con navegación
- 3 artículos con imagen, título y descripción
- Sidebar con categorías
- Footer
- Diseño responsive

## Tarea 2: Portfolio (Intermedio)
Crear un portfolio personal con:
- Hero section con foto y presentación
- Sección "Sobre mí"
- Grid de proyectos (6 proyectos)
- Formulario de contacto
- Animaciones en hover
- Totalmente responsive

## Tarea 3: Dashboard (Avanzado)
Crear un dashboard administrativo con:
- Sidebar con menú
- Header con búsqueda y perfil
- Cards con estadísticas
- Tabla de datos
- Gráficos (pueden ser imágenes)
- Modo oscuro (dark mode)
- Responsive con menú hamburguesa

---

# 🎓 Conclusión

Tailwind CSS es una herramienta poderosa que, aunque requiere un cambio de mentalidad, permite crear diseños únicos y personalizados de forma rápida y eficiente. La clave está en:

1. **Conocer bien CSS**: Tailwind es un atajo, no un reemplazo
2. **Consultar la documentación**: Es tu mejor recurso
3. **Practicar constantemente**: La fluidez viene con la práctica
4. **Crear componentes**: Evita repetición y mejora mantenibilidad
5. **Pensar en responsive desde el inicio**: Mobile-first

¡Ahora a practicar! 🚀

---

# 🚀 ANEXO: EXAMPLES & LABORATORY WORKOUTS

Sección pensada para ser proyectada y comentada en el **Laboratorio**.

### 💡 Ejemplo Avanzado 1: Formulario Moderno (Floating Labels)
*Concepto: Peer-siblings y modificadores de foco.*

```html
<div class="relative">
  <input type="text" id="name" class="peer h-10 w-full border-b-2 border-gray-300 text-gray-900 placeholder-transparent focus:outline-none focus:border-blue-500" placeholder="Nombre">
  <label for="name" class="absolute left-0 -top-3.5 text-gray-600 text-sm transition-all peer-placeholder-shown:text-base peer-placeholder-shown:text-gray-440 peer-placeholder-shown:top-2 peer-focus:-top-3.5 peer-focus:text-gray-600 peer-focus:text-sm">Nombre Completo</label>
</div>
```

---

### 🧩 Ejercicio Intermedio A: "The Social Card"
*Objetivo: Combinar flex, rounded-full, y hover escalado.*

**Requisitos:**
1. Imagen circular de perfil.
2. Badge de "Verificado" con color personalizado.
3. Botón que al hacer hover se "eleve" (shadow-xl + translate-y).

**Solución sugerida (Proyectar en Lab):**
```html
<div class="bg-white p-6 rounded-3xl shadow-lg border border-gray-100 max-w-xs text-center group hover:shadow-2xl transition-all">
  <div class="relative inline-block">
    <img src="img/avatar.jpg" class="w-24 h-24 rounded-full mx-auto border-4 border-blue-50">
    <span class="absolute bottom-0 right-0 w-6 h-6 bg-blue-500 border-2 border-white rounded-full"></span>
  </div>
  <h3 class="mt-4 font-bold text-xl">Andrés González</h3>
  <p class="text-gray-400 text-sm">UI Designer @ DIWEB</p>
  <div class="mt-6 flex justify-around border-t pt-4">
    <div><span class="block font-bold">1.2k</span><span class="text-xs text-gray-400">Seguidores</span></div>
    <div><span class="block font-bold">450</span><span class="text-xs text-gray-400">Posts</span></div>
  </div>
</div>
```

---

### 🌑 Ejemplo Avanzado 2: El Interruptor de Modo Oscuro
*Concepto: Combinar `dark:`, transiciones de color y JS mínimo.*

**Paso en configuración (v4):**
Si quieres control manual del modo oscuro, define la variante en CSS:

```css
@custom-variant dark (&:where(.dark, .dark *));
```

**Estructura:**
```html
<body class="bg-white dark:bg-slate-950 transition-colors">
  <button onclick="toggleDark()" class="p-2 bg-slate-200 dark:bg-slate-800 rounded-lg">
    <span class="block dark:hidden">☀️ Modo Claro</span>
    <span class="hidden dark:block">🌙 Modo Oscuro</span>
  </button>
</body>
```

---

### 🏗️ Ejercicio Intermedio B: "Pricing Table"
*Objetivo: Estilizar elementos con Grid y destacar el plan central.*

```html
<div class="grid grid-cols-1 md:grid-cols-3 gap-8 p-10">
  <div class="p-8 border rounded-xl">Básico</div>
  <div class="p-8 bg-blue-600 text-white rounded-xl shadow-2xl scale-110">Pro (Recomendado)</div>
  <div class="p-8 border rounded-xl">Empresa</div>
</div>
```
*(Pedir a los alumnos que completen el contenido con precios y botones).*
