- [Manejo de Selectores](#manejo-de-selectores)
  - [Ejercicio 1](#ejercicio-1)
  - [Ejercicio 2](#ejercicio-2)
  - [Ejercicio 3](#ejercicio-3)
  - [Ejercicio 4](#ejercicio-4)
  - [Ejercicio 5](#ejercicio-5)
  - [Ejercicio 6](#ejercicio-6)
  - [Ejercicio 7](#ejercicio-7)

# Manejo de Selectores

## Ejercicio 1

```html
<h1>Monumentos de Palencia</h1>
<p name"palencia" >
  Palencia dispone de numerosos monumentos interesantes. Debido a su importante
  actividad medieval posee una gran cantidad de edificios religiosos entre los
  que destaca la <strong>Catedral de Palencia</strong> así como la iglesia de
  San Miguel con su peculiar torre de defensa y el monumento más conocido de la
  ciudad: El Cristo del Otero
</p>
<p name="siglo">
  A finales del siglo <em>XIX</em> y principios del <em>XX</em> aparecieron
  edificios suntuosos y civiles que han embellecido una buena parte de la
  ciudad, en especial la transitada <u>Calle Mayor</u>.
</p>
<h2>Edificios religiosos</h2>
<ul>
  <li>Cristo del Otero</li>
  <li>Catedral Mayor</li>
  <li>Iglesia de San Miguel</li>
  <li>Iglesia de San Lázaro</li>
  <li></li>
  <li>" "</li>
  <li>Convento de San Pablo</li>
  <li>Iglesia de la Compañía</li>
</ul>
```

A partir del siguiente código html asigna los estilos correspondientes a los elementos que te marcan en el comentario:

```css
/*Todos los elementos de la pagina */
 {
  font: 1em/1.3 Arial, Helvetica, sans-serif;
}
/* Todos los parrafos de la pagina */
 {
  color: #555;
}
/* Todos los párrafos contenidos en #primero */
 {
  color: #336699;
}
/* Todos los enlaces la pagina */
 {
  color: #cc3300;
}
/* Los elementos "em" contenidos en #primero */
 {
  background: #ffffcc;
  padding: 0.1em;
}
/* Todos los elementos "em" de clase "especial" en toda la
pagina */
 {
  background: #ffcc99;
  border: 1px solid #ff9900;
  padding: 0.1em;
}
/* Elementos "span" contenidos en .normal */
 {
  font-weight: bold;
}
/* Elementos primeros de la lista li */
 {
  color: #ffffff;
}
/* Primeras lineas de los Párrafos */
 {
  color: #000000;
}
/* Elementos strong únicos */
 {
  color: pink;
}
/* Cada 3 elementos del listado */
 {
  color: red;
}
/* Aquellos elementos de p que no sean u*
 {
  color: gold;
}
/* El primer y el último elemento de la lista li*/
 {
  color: #111;
}
>
/*El hermano adyacente a h1*/ {
  border: 2px solid #fff;
}
/*Todos los hermanos de h1*/
 {
  border: 5px solid #333;
}
/* Todo elemento que contenga un atributo name con un valor que comience en "si"*/
 {
  border: 5px solid #333;
}
/* Todo elemento que contenga un atributo name con un valor que contenga en "l"*/
 {
  color: red;
  border: 5px solid #333;
}
/* Aquellos li que estén vacíos */
 {
  color: red;
}
```

## Ejercicio 2

A partir del código html anterior, crea dos contadores personalizados, uno para la lista que no tenga orden y otro para cada uno de los `p` que si que estén ordenados.

## Ejercicio 3

Establece los siguientes estilos para la página **proyectos.html** de la **Actividad 2 del anterior tema**.

- Un título en la parte de abajo.
- La celda se debe ajustar según el texto introducido.
- La tabla debe ocupar el 100% del contenedor padre.
- Utiliza la propiedad `border-collapse:collapse`.
- Dale estilos a los borders y margenes de la tabla.
- Centra el texto.
- Utiliza el pseudo-elemento para darle un color de fondo a la primera línea.
- Usa la pseudo-clase para dar un fondo diferente a las filas pares e impares.
- Define las siguientes pseudo-clases para los estados de los enlaces de la página principal (no la de **proyectos.html**) :link :visited :hover :active.

## Ejercicio 4

Utiliza la regla `@import` para utilizar el conjunto de reglas de resteo de Josh W. Comeau, que está en la teoría en la web de la **Actividad 2 del anterior tema**. ¿Ha tenido algún efecto?.
¿La regla `@import` es ampliamente aceptada por todos los navegadores?.

## Ejercicio 5

Dentro de la **Actividad 4 del anterior tema**, añade la fuente que te aparecen en la carpeta fonts. Como vemos la fuente la disponemos en diferentes ficheros con diferentes formatos. Genera el archivo woff2 para la fuente a partir del archivo ttf. ¿Cuál de los archivos es menos pesado?

## Ejercicio 6

En la página **contacto.html de la Actividad 2 del tema anterior**, tenéis que añadir:

- Un campo para subir ficheros que permita seleccionar multiples ficheros.
- **Una expresión regular** para validar el email.
- **Una expresión regular** para validar el número de teléfono.
- **Una expresión regular** Para validar la edad.

**_He modificado el pdf de html5 e incluido el tema de Formularios y expresiones regulares._**

## Ejercicio 7

Contesta a las siguientes preguntas:

1. ¿Qué hace la siguiente pseudoclase `a:has(> img)`?
