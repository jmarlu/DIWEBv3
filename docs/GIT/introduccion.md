# Manejo básico de Git

## Referencias

- [Libro de Git](https://git-scm.com/book/es/v2/)
- [Hoja de referencia de Git](https://training.github.com/)
- [Hoja de referencia de Git (PDF)](https://training.github.com/downloads/es**ES/github-git-cheat-sheet.pdf)

## Contenidos & Instalación

- [https://git-scm.com/download](https://git-scm.com/download)

```bash title="Configuración"


# Opciones obligatorias (nombre y correo)

git config --global user.name "Nombre y apellido"
git config --global user.email CORREO@ELECTRONICO

# Editor de preferencia. Visual Studio Code

# Referencia: https://stackoverflow.com/questions/30024353/how-to-use-visual-studio-code-as-default-editor-for-git

git config --global core.editor "code --wait"

```

Si no se indica un editor de preferencia `git` utilizará el editor `vim` cuando tenga que solicitar la intervención del usuario (al hacer un `merge`, o si el usuario ejecuta `git commit` sin indicar el mensaje). Este editor es complicado de utilizar para alguien no iniciado, por lo que es muy recomendable cambiar el editor por defecto.

## Creación de repositorios

Para crear un repositorio hay que situarse en la carpeta deseada y ejecutar:

```bash
git init
```

## Ciclo de vida.

![alt text](img/lifecycle.png)

## Revisando el estado

```bash
git status
```

Esquema de colores:

-**Rojo** - Identifica los archivos **modificados o nuevos**. Si se crean archivos dentro de carpetas nuevas,`git status` solo mostrará el nombre de la carpeta, no su contenido. Si se desea ver el contenido de las carpetas nuevas se deberá ejecutar `git status -u`.

- **Verde** - Identifica los archivos en el **área de preparación**.

## Visualizar cambios

```bash
git diff
git diff <archivo**o**ruta>
```

Este es uno de los comandos más utilizados en `git`. Nos permite ver los cambios en los archivos del repositorio o en una ruta específica.

## Añadir archivos al área de preparación (stage)

```bash
git add <archivo> # Añadir archivos individuales
git add . # Añadir todos los archivos nuevos o modificados
```

El **área de preparación** contiene los **cambios que se añadirán a la nueva versión** cuando ejecutemos un `commit`. Es posible la siguiente situación:

- Modificar un fichero (aparecerá en color rojo al hacer un `git status`)
- Añadir el fichero al área de preparación mediante `git add FICHERO`
- El fichero aparecerá en color **verde** al hacer un `git status`
- Volver a modificar el fichero
- El fichero aparecerá **dos veces** al hacer un `git status`:
  - En color **verde**, indicando que se ha añadido el **primer cambio** al área de preparación
  - En color **rojo**, indicando que hay un **segundo cambio** posterior que **no se ha incluido** en el área de preparación
- Si se ejecuta un `git commit` en este momento **solamente se incorporará el primer cambio** al repositorio como nueva versión. El segundo cambio seguirá existiendo (el archivo no habrá cambiado), pero no estará guardado en el commit
- Si se desea agregar el segundo cambio se deberá ejecutar nuevamente `git add` para añadirlo al área de preparación

## Visualizar cambios de los archivos en el área de preparación

```bash
git diff --staged
git diff --staged <archivo>
```

Este comando muestra los cambios que se han agregado al área de preparación (diferencia entre la última versión guardada en el repositorio y el área de preparación).

## Confirmar cambios (commit)

```bash
git commit -m "MENSAJE"
```

Un commit equivale a una nueva **versión** en el repositorio. Cada commit tiene un **identificador único**, denominado ~hash~. Los commits están relacionados entre sí mediante una **red de tipo grafo**.

En la siguiente sesión estudiaremos como volver atrás en la historia para acceder a una versión anterior del repositorio si se desea.

## Ignorar archivos

- Archivo `.gitignore`
- [Plantillas de archivos](https://github.com/github/gitignore)

Las rutas y nombres de archivo que aparezcan en el fichero `.gitignore` serán ignoradas por `git` **siempre que no hayan sido añadidas previamente al área de preparación o al repositorio**. Por ejemplo, si añadimos un archivo al área de preparación mediante `git add` y a continuación lo añadimos al fichero `.gitignore`, `git` lo seguirá manteniendo en el área de preparación, por lo que será incluido en el repositorio si ejecutamos un `git commit`.

De igual manera, si previamente hemos guardado un archivo en el repositorio mediante `git commit` y a continuación lo incluimos en el fichero `.gitignore`, git no lo borrará: será necesario borrarlo del sistema de ficheros (a través de la consola o el navegador de archivos) y añadir los cambios (`git add` y `git commit`) para que se borre del repositorio. Una vez borrado, si lo volvemos a crear veremos que `git` sí que lo ignora si está incluido en el fichero `.gitignore`.

## Historial de cambios

```bash
git log
git log --graph
```

Este comando muestra el histórico de los commits del repositorio. Se puede navegar en el listado mediante los cursores y la barra espaciadora. Para salir hay que pulsar la tecla `q`.

Ver cambios realizados en anteriores commits

```bash
git show <commit>
```

Este comando nos permite mostrar los cambios que se introdujeron en un determinado commit. En primer lugar se puede ejecutar `git log` para buscar el hash del commit que nos interese y a continuación ejecutar `git show` indicando después el hash del commit correspondiente.

Los hash de los commits tienen 40 caracteres, pero no es necesario copiarlos enteros: basta con indicar entre los [[http://git-scm.com/book/en/v2/Git-Tools-Revision-Selection#Short-SHA-1][8 y 10 primeros caracteres]] para identificar un commit correctamente.

## Quitar archivo del área de preparación

```bash
git reset <archivo>
```

En ocasiones nos encontramos con que hemos añadido cambios al área de preparación que no queremos incorporar al commit. Para ello podemos utilizar este comando, que elimina los cambios del fichero correspondiente del área de preparación. **Los cambios no se pierden** en ningún caso.

## Eliminar las modificaciones con respecto al último commit

```bash
#¡PELIGRO! Todos los cambios que se hayan hecho al archivo desde el último commit se eliminarán

git checkout -- <archivo>
```

Este comando es peligroso, ya que **elimina todos los cambios del archivo** que no hayan sido guardados en el repositorio. Es decir, si el archivo tiene cambios y está en color **rojo**, se perderán dichos cambios. Este comando puede ser útil para dejar un archivo tal como estaba en la última versión guardada del repositorio.

## Etiquetado

```bash
git tag NOMBRE**TAG
```

Este comando crea un `tag` en el commit en que nos encontremos en este momento. Un `tag` es un **alias** que se utiliza para **hacer referencia a un commit** sin necesidad de saber su hash. Normalmente se utiliza para **indicar números o nombres de versiones** asociadas a un determinado commit. De esta manera podemos **identificar una versión de una manera más amable**.

El nombre de los `tag` se puede utilizar con los comandos de git: por ejemplo, `git show`.

## Guardado temporal

```bash

# Guardado temporal de cambios no añadidos al área de preparación

git stash

# Restaurar cambios guardados mediante git stash

git stash pop
```

En ocasiones se hacen cambios que se desea preservar para más adelante: por ejemplo, trabajamos en una modificación de un fichero y de repente nos avisan de que hay un bug en otro fichero que tiene que ser resuelto inmediatamente. Para no trabajar en ambas tareas a la vez podemos ejecutar `git stash`: los cambios que tenemos en ese momento y que no están en el área de preparación (es decir, los cambios que están en color rojo) se guardan en un área temporal; al ejecutar `git status` veremos que no hay ninguna modificación, el directorio de trabajo está limpio.

A continuación trabajamos en el bug, hacemos cambios y al terminar ejecutamos `git add` y `git commit` para resolverlo. Una vez resuelto, ejecutamos `git stash pop` y recuperamos los cambios que estábamos realizando antes de ser interrumpidos: veremos que `git status` nos muestra en color rojo los archivos que habíamos modificado al principio.
