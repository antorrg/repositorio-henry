# Repositorio Henry/ Sobre GIT
<**https://jonmircha.com/git**>
(Toda la información que vuelco aquí fue extraida del curso y la página mencionada).

### Configurando Git por primera vez:
git --version


git config --global user.name "Jonathan MirCha"


git config --global user.email `jonmircha@gmail.com`


git config --global user.ui true


git config --global init.defaultBranch main

git config --list


### Asignando visual studio code como editor de configuración de git

git config --global core.editor "code --wait"

git config --global -e

### Para estandarizar los saltos de línea en windows

git config --global core.autocrlf true

### Para estandarizar los saltos de línea en linux/mac

git config --global core.autocrlf input

### Ver todas las opciones de la configuración en la terminal

git config -h

### Ver todas las opciones de la configuración en el navegador

git help config

<hr>

## Inicializar Git en un repositorio local.

mkdir carpeta

cd carpeta

touch README.md

touch .gitignore

git init

---

<hr>

## Flujo básico

El flujo de Git, consta de tres estados locales, es decir en la computadora donde se esta trabajando y uno más de forma remota cuando accedemos al codigo centralizado en plataformas como GitHub, Gitlab, Bitbucket, etc.

Dichos estados son modified, staged, committed y remote. A cada uno de ellos le corresponde un área de trabajo:

#### Working Directory: 
Es el área correspondiente al estado modified y es la carpeta local de tu computadora donde almacenas los archivos de tu proyecto.

#### Staging Area: 
Es el área correspondiente al estado staged también se le llama index por que es el área donde git indexa y agrega los cambios realizados en los archivos previos a comprometerlos en su registro.

#### Local Repository: 
Es el área correspondiente al estado committed, donde los cambios ya se han registrado en el repositorio de git también se le llama HEAD por que indica en qué cambio se encuentra el puntero del repositorio.

#### Remote Repository: 
Es el área correspondiente al estado remote y es el directorio remoto donde almacenamos los archivos del proyecto en alguna plataforma web como GitHub, GitLab, BitBucket. Git denomina origin al repositorio remoto.

## Fujo básico de Git/ Github:

#### git add archivo/directorio

Agregar los cambios de un archivo al staged.

#### git add .

Agregar todos los cambios de todos los archivos al staged


#### git commit -m "mensaje descriptivo del cambio"

Los cambios son comprometidos en el repositorio, debes escribir el mensaje del cambio cuando se abra el archivo de configuración. Al terminar guarda y cierra el archivo para que los cambios tengan efecto.


#### git commit

Es un shortcut del comando anterior, escribes y confirmas el mensaje del cambio en un sólo paso.


#### git remote add origin `https://github.com/usuario/repositorio.git`

Se agrega el origen remoto de tu repositorio de GitHub

#### git push -u origin master

La primera vez que vinculamos el repositorio remoto con el local.

#### git push

para las subsecuentes actualizaciones, si no cambias de rama.

#### git pull

#para descargar los cambios del repositorio remoto al local.
<hr>

## De master a main

Con los desafortunados acontecimientos del 25 de mayo de 2020 en los Estados Unidos que culminaron con el asesinato del afroamericano George Floyd a manos de policias de la ciudad de Mineápolis, se intensificó de manera global el movimiento "BlackLivesMatter".

Con dicho movimiento muchas industrias y empresas comenzaron a tomar acciones para erradicar el racismo.

En la industria de la tecnología por años se han empleado palabras como master, slave, whitelist, blacklist entre otras que actualmente no son bien vistas por el contexto y la semántica que implican.

Al respecto Microsoft empresa propietaria de GitHub decidió comenzar una campaña para reemplazar el nombre de la rama principal de los repositorios de master a main; como lo han explicado en este documento:

    "El 1 de octubre de 2020, cualquier nuevo repositorio que crees utilizará 'main' como la rama por defecto, en lugar de 'master'. Este cambio no afecta a ninguno de tus repositorios existentes: los repositorios existentes continuarán teniendo la misma rama por defecto que tienen ahora".

Este cambio implica agregar una par de líneas de comandos adicionales para crear la rama 'main' y hacerla principal en el repositorio.

Entonces el flujo básico quedaría de la siguiente manera:

### Para repositorios nuevos

#### git init

#### git add .

#### git commit -m "Primer commit"

#### git branch -M main

#### git remote add origin `https://github.com/usuario/repositorio.git`

#### git push -u origin main

### Para repositorios existentes

#### git branch -M main

#### git remote add origin `https://github.com/usuario/repositorio.git`

#### git push -u origin main

### Para reemplazar la rama master por main en GitHub

### Paso 1

Crea la rama local main y pásale el historial de la rama master

#### git branch -m master main


### Paso 2

Haz un push de la nueva rama local main en el repositorio remoto de GitHub

#### git push -u origin main


### Paso 3

Cambia el HEAD actual a la rama main

#### git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main

### Paso 4

Cambia la rama default de master a main en tu repositorio de GitHub .

Para hacerlo, sigue las instrucciones de este [**enlace.**](https://docs.github.com/en/github/administering-a-repository/setting-the-default-branch)

### Paso 5

Elimina la rama master del repositorio remoto

#### git push origin --delete master

Para reemplazar la rama master por main en Git

#### git config --global init.defaultBranch main

<hr>

## Ayuda

### Ayuda en la terminal
#### git comando -h

### Ayuda en el navegador

#### git help comando

<hr>

### Clonar repositorios

#### git clone `https://github.com/usuario/repositorio.git`

<hr>


## Ramas

Una rama nos permite aislar una nueva funcionalidad en nuestro código que después podremos añadir a la versión principal.

### Crear rama:

#### git branch nombre-rama

### Cambiar de rama:
#### git checkout nombre-rama

### Crear una rama y cambiarte a ella:
#### git checkout -b rama

### Eliminar rama:
git branch -d nombre-rama

### Eliminar ramas remotas:
#### git push origin --delete nombre-rama

### Eliminar rama (forzado):
#### git branch -D nombre-rama

### Listar todas las ramas del repositorio:
#### git branch

### Lista ramas no fusionadas a la rama actual:
#### git branch --no-merged

### Lista ramas fusionadas a la rama actual:
#### git branch --merged

### Rebasar ramas:
#### git checkout rama-secundaria
#### git rebase rama-principal

<hr>

## Fusiones

Une dos ramas. Para hacer una fusión necesitamos:

    Situarnos en la rama que se quedará con el contenido fusionado.

    Fusionar.

Cuando se fusionan ramas se pueden dar 2 resultados diferentes:

    Fast-Forward: La fusión se hace automática, no hay conflictos por resolver.


    Manual Merge: La fusión hay que hacerla manual, para resolver conflictos de duplicación de contenido.


### Nos cambiamos a la rama principal que quedará de la fusión
#### git checkout rama-principal

### Ejecutamos el comando merge con la rama secundaria a fusionar
#### git merge rama-secundaria

<hr>

## Cambios

Puedes agregar modificaciones al último cambio sin editar el mensaje del último commit:

#### git commit --amend --no-edit

Editando el mensaje del último commit:

#### git commit --amend -m "nuevo mensaje para el último commit"

### Eliminar el último commit:

#### git reset --hard HEAD~1

Podemos desplazarnos en el historial del repositorio hacia atrás o adelante en cambios o ramas, sin afectar el repositorio como tal.

### Cambiar a una rama:
#### git checkout nombre-rama

### Cambiar a un commit en particular:
#### git checkout id-commit

## Pd:
El resto de la información como por ejemplo: registro y reseteo del historial, reseteo del repositorio, colaborar con github etc., se encuentra en la página de la cual extraje esta información [**(Clic en este enlace)**](https://jonmircha.com/git)
