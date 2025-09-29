# Tutorial Completo: Creando Componentes en Figma

## 📋 Introducción
En este documento aprenderás a crear componentes reutilizables en Figma, basándonos en el diseño de la landing page "DesignPro". Los componentes son elementos clave para mantener la consistencia y eficiencia en tus diseños.

**¿Qué vamos a crear?**
- Componentes básicos: Botones, tarjetas, y encabezados.
- Variantes de componentes.
- Organización de componentes en un sistema de diseño.

**Tiempo estimado:** 2-3 horas  
**Herramienta:** Figma (web o app de escritorio)

---

## 🚀 Creando Componentes Básicos

### Paso 1: Crear un botón como componente

1. Dibuja un rectángulo de 140x40px.
2. Aplica un relleno con el color "Primary" (#030213).
3. Redondea las esquinas a 8px.
4. Añade un texto centrado: "Botón Principal".
   - Fuente: Inter, 16px, Medium, color blanco.
5. Selecciona el rectángulo y el texto.
6. Agrúpalos (Ctrl/Cmd + G).
7. Con el grupo seleccionado, haz clic derecho y selecciona "Create Component".
8. Nombra el componente: "Botón/Primario".

### Paso 2: Crear variantes del botón

1. Selecciona el componente "Botón/Primario".
2. Haz clic en "+" en la sección de variantes del panel derecho.
3. Crea las siguientes variantes:
   - **Secundario:** Sin relleno, borde de 1px color "Border" (#e5e5e5), texto en color "Primary".
   - **Deshabilitado:** Relleno gris claro (#ececf0), texto gris medio (#717182).
4. Organiza las variantes en un contenedor de variantes.

---

## 🎨 Creando Tarjetas como Componentes

### Paso 3: Crear una tarjeta base

1. Dibuja un rectángulo de 360x200px.
2. Aplica un relleno blanco.
3. Redondea las esquinas a 12px.
4. Añade una sombra: X: 0, Y: 4, Blur: 20, Color: rgba(0,0,0,0.1).
5. Añade un título: "Título de la Tarjeta".
   - Fuente: Inter, 18px, SemiBold, color "Primary".
6. Añade un texto descriptivo: "Descripción breve de la tarjeta.".
   - Fuente: Inter, 14px, Regular, color "Muted Foreground".
7. Agrupa todos los elementos y crea un componente: "Tarjeta/Base".

### Paso 4: Crear variantes de la tarjeta

1. Selecciona el componente "Tarjeta/Base".
2. Crea las siguientes variantes:
   - **Con ícono:** Añade un círculo de 48x48px con un ícono dentro.
   - **Con imagen:** Sustituye el fondo por una imagen.
3. Organiza las variantes en un contenedor de variantes.

---

## 🖼️ Creando Encabezados como Componentes

### Paso 5: Crear un encabezado

1. Dibuja un rectángulo que cubra todo el ancho (1440px) y altura de 80px.
2. Aplica un relleno blanco.
3. Añade un texto: "Encabezado Principal".
   - Fuente: Inter, 24px, Bold, color "Primary".
4. Agrupa los elementos y crea un componente: "Encabezado/Principal".

### Paso 6: Crear variantes del encabezado

1. Selecciona el componente "Encabezado/Principal".
2. Crea las siguientes variantes:
   - **Con logo:** Añade un logo a la izquierda.
   - **Con navegación:** Añade un menú de navegación centrado.
3. Organiza las variantes en un contenedor de variantes.

---

## 🎥 Añadiendo Animaciones a los Componentes

### Paso 9: Crear transiciones básicas

1. Selecciona un componente (por ejemplo, "Botón/Primario").
2. Ve a la pestaña "Prototype" en el panel derecho.
3. Haz clic en el componente y arrastra una flecha hacia otro frame o variante.
4. Configura la interacción:
   - **Trigger:** On Click.
   - **Action:** Navigate To (o Swap With para variantes).
   - **Animation:** Smart Animate.
   - **Easing:** Ease In and Out.
   - **Duration:** 300ms.

### Paso 10: Crear microinteracciones

1. Selecciona un componente (por ejemplo, "Botón/Primario").
2. Crea una variante adicional para el estado "Hover".
   - Cambia el color de fondo o el tamaño del texto.
3. Ve a la pestaña "Prototype" y conecta el estado base con el estado "Hover".
4. Configura la interacción:
   - **Trigger:** While Hovering.
   - **Animation:** Smart Animate.
   - **Easing:** Linear.
   - **Duration:** 200ms.

### Paso 11: Crear animaciones complejas

1. Diseña dos frames con diferentes estados de un componente (por ejemplo, un menú desplegable abierto y cerrado).
2. Ve a la pestaña "Prototype" y conecta los frames.
3. Configura la interacción:
   - **Trigger:** On Click.
   - **Animation:** Smart Animate.
   - **Easing:** Spring.
   - **Duration:** 500ms.

### Paso 12: Exportar animaciones

1. Selecciona el frame o componente animado.
2. Ve a "Export" en el panel derecho.
3. Elige formato GIF o MP4.
4. Ajusta la calidad y exporta.

---

## ✅ Finalización y Consejos

### Paso 7: Organizar los componentes

1. Crea una página en Figma llamada "Componentes".
2. Organiza los componentes en secciones: Botones, Tarjetas, Encabezados.
3. Asegúrate de nombrar todos los componentes y variantes de forma clara.

### Paso 8: Reutilizar los componentes

1. Usa los componentes en tus diseños para mantener la consistencia.
2. Si necesitas personalizar un componente, crea una instancia y realiza los cambios necesarios.

---

## 🎓 Conceptos Aprendidos

- ✅ Crear componentes básicos en Figma.
- ✅ Crear variantes de componentes.
- ✅ Organizar componentes en un sistema de diseño.
- ✅ Reutilizar componentes para mantener la consistencia.
- ✅ Crear transiciones básicas entre componentes.
- ✅ Diseñar microinteracciones para mejorar la experiencia del usuario.
- ✅ Implementar animaciones complejas con Smart Animate.
- ✅ Exportar animaciones para compartir o presentar.

---

¡Felicidades! Ahora tienes una base sólida para trabajar con componentes en Figma. Esto te permitirá ahorrar tiempo y mantener la coherencia en tus diseños.