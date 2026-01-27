# Examen de primera evaluacion

## Ejercicio 1 (6 puntos)

Crea una pagina web **responsiva** con una seccion `section-gallery` que contenga una **galeria** de tarjetas con imagen, titulo y descripcion. La composicion debe recordar a una galeria tipo mosaico (varias columnas que se adaptan al ancho disponible).

**Especificaciones:**

- Obligatorio usar **Grid** con `auto-fit` y `minmax()` para la galeria.
- Cada tarjeta debe tener un **ancho minimo** de `16rem` para que el contenido se vea bien.
- Las imagenes deben cubrir el espacio (usa `object-fit: cover`).
- La galeria debe estar centrada y ocupar como maximo el `90%` del ancho.
- Debe reordenarse correctamente al reducir el ancho de pantalla.

## Ejercicio 2 (4 puntos)

Dentro del mismo proyecto crea una **carta** (card) con la clase `profile-card`. Debe incluir una imagen redondeada, un titulo, un subtitulo y un boton. La imagen debe tener una **animacion** suave al pasar el raton.

**Especificaciones:**

- Obligatorio usar **Flex** para alinear el contenido interno de la carta.
- La imagen debe ser circular (`border-radius: 50%`) y mantener su proporcion.
- La animacion puede ser `scale`/`rotate` y debe activarse en `:hover`.
- La carta debe tener un **ancho minimo** de `18rem` y ajustarse en pantallas pequenas.
- La carta debe centrarse en la pagina y mantener una lectura correcta en movil.

**Notas:**

> > No se permite SASS. Usa solo HTML y CSS.
> > Calcula `1rem` como `10px`.
> > Los colores pueden variar, no tienen que ser iguales a los de ejemplos anteriores.
