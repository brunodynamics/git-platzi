# GIT Y GITHUB

Git es el sistema más famoso y poderoso de control de versiones. Creado por Linus Torvalds.

## Iniciar un repositorio

Para iniciar un repositorio de Git, debemos abrir una terminal o línea de comandos en la ruta de la carpeta a la que deseamos gestionar sus versiones y colocar el siguiente comando:

> git init

Esto creará una carpeta **.git**, la cual contenerá las configuraciones necesarias para manejar el repositorio.

## Ciclo de vida o estados en los archivos de Git

Los archivos de una directorio que contenga la carpeta **.git** pueden tener 4 estados distintos:

- Achivos Tracked: Archivos que pertenecen al repositorio cuya última versión fue guardada por medio de un commit.

- Archivos Staged: Archivos que están registrados en Git a la espera de ser guardados definitivamente en el repositorio.

- Archivos Unstaged: Archivos que están siendo trackeados por Git, pero cuyas últimas modificaciones solo están en el disco duro, pues no han pasado al estado de staging.

- Archivos Untracked: Archivos que solo viven en el disco duro y no son trackeados por Git.

### Comandos Importantes

- **git status**: Nos permite ver el estado de todos nuestros archivos y carpetas.
- **git add**: Conviente archivos Untracked y Unstaged a Staged.

  > git add \<filename\> **(Un solo archivo)**

  > git add . **(Todos los archivos)**

- **git reset HEAD**: Nos ayuda a devolver los archivos que se encuentren en el estado Staged a su estado estado anterior.
- **git commit**: Permite convertir archivos staged a tracked. Al ejecutar este comando se nos solicitará un mensaje a ser guardado en el repositorio, para futuras consultas.

  > git commit -m "mensaje interesante"

  > git commit -am "mensaje interesante"

  <small>Psdt: El comando **git commit -am** solo aplicará para archivos unstaged. No tendrá efecto en archivos untracked.</small>

- **git rm**: Este comando tiene dos formas de funcionar.

  > git rm --cached \<filename\> > <small>Mueve los archivos que se le indique al estado untracked</small>

  > git rm --force \<filename\> > <small>Elimina los archivos de Git y del disco duro. Es posible luego recuperarlos, pero se deben utilizar comando más avanzados. Utilízalo con precaución.</small>

- **git log**: Sirve para mostrar todos los commits de una rama.

  > git log

  > git log --oneline

## Analizar cambios en el repositorio

El propósito de contar con un sistema de control de versiones es el poder de regresar en el tiempo, si algo se rompió, ver qu;e cambió para romper el código y así hacer los cambios necesarios.

Git cuenta con varias maneras de revisar los cambios en un documento:

> git show \<filename\>

<small>Muestra los útlimos cambios de un archivo</small>

Si deseáramos ver las diferencias entre un commit y otro, podemos usar el comando **git diff**

> git diff \<commitID1\> \<commitID2\>

## "Volver en el tiempo" con Git

En git tenemos más de una forma para regresar en el tiempo y estas se diferencian por la "rudeza" de la acción.

**git checkout**: Nos permite volver atrás a un commit específico, pero también regresar al HEAD, no elimina nada, solo oculta o muestra según el commit al que se viaje.

> git checkout \<commitID\>

**git reset**: Con este comando no solo volvemos en el tiempo, sino que también borramos los cambios que hicimos después del commit indicado. Este commando tiene dos versiones:

> git reset --soft \<commitID\>

<small>Borra los commits posteriores al indicado, pero mantiene los archivos que fueron puesto en el área de staging, tal como estaban.</small>

> git reset --hard \<commitID\>

<small>Borra los commits posteriores al indicado y toda la información en staging.</small>

## Ramas o Branches

Una de las funcionalidades más interesantes de Git, es que brinda la posibilidad de crear ramificaciones del proyecto principal.
¿Esto qué quiere decir?
Supongamos que tenemos una página web, la cual ya fue terminada y está en producción. Llega diciembre y queremos hacerle algunos cambios a esta página para darle un tema navideño.
Lo más lógico sería dejar trabajar en los cambios sin afectar a la página que ya está en producción hasta que estemos seguro de que lo nuevo que hicimos nos gusta. Para este caso sería muy útil crear una rama "Navidad" al proyecto y trabajarlo en paralelo, para cuando hayamos acabado, unir ambas ramas y reflejar los cambios a nuestros clientes.

![Ejemplo Ramas](img/Branches.PNG)

Para crear una rama en Git es muy simple, se puede usar el siguiente comando:

> git branch \<branchname\>

Luego, es necesario hacer un checkout a esta rama:

> git checkout \<branchname\>

Para simplificar esto y crear la rama y cambiarse a ella en un solo comando se puede hacer lo siguiente:

> git checkout -b \<branchname\>

Luego de crear ramas, llegará un momento en el que querremos fusionarlas a la rama principal como se comentó en el ejemplo.
Para esto, debemos hacer checkout a la rama en la que queremos crear un nuevo commit para la fusión:

> git checkout \<branchname1\>

Y luego ejectura el comando merge:

> git merge \<branchname2\>

### Resolución de Conflictos

Muchas veces pueden ocurrir conflictos al momento de hacer merging, esto debido a que no siempre sabemos qué archivos están modificando nuestros compañeros del proyecto.
Cuando esto ocurra, Git nos pintará en el documento marcas mostrando dónde está el o los conflictos.
No entremos en pánico cuando suceda esto, lo mejor que podemos hacer es hablar con el desarrollador involucrado y definir qué lineas se quedan y cuales no.

### Comandos útiles:

> git branch -a

<small>Muestra todas las ramas del repositorio</small>

> git branch -d \<branchname\>

<small>Elimina la rama indicada</small>

## Github
