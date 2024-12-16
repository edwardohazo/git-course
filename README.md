# GIT & GITHUB

## GIT 

Software de control de versiones distribuido y descentralizado que permite a un equipo de desarrolladores trabajar sobre el mismo código

## GITHUB

Plataforma social que le permite a los usuarios compartir repositorios gestionados con Git.

Conceptos:
Estado del proyecto .- Estructura conformada por los directorios, archivos incluidos y el contenido de estos archivos en cada confirmación (commit).
Estado actual del proyecto .- Estructura conformada por los directorios, archivos incluidos y el contenido de estos archivos en la confirmación activa (commit).
Puntero .- Variable que almacena la referencia a otra variable.
Head .- Es un puntero que apunta o bien a la rama activa (indirectamente al último commit de la rama activa en el caso más común) o a un commit específico (en el caso de un estado "detached HEAD"). En ambos casos, el commit al que apunta HEAD contiene el árbol de nodos que representa el estado actual del proyecto, estado con base en el cual se forma inicialmente el directorio de trabajo (working directory).
Repositorio .- Unidad conformada por la carpeta .git dentro del working directory y los archivos dentro del working directory confirmados mediante commits.
Trackear/rastrear .- Git reconoce los archivos y empieza a gestionar los cambios de un archivo de manera activa, lo cual implica que impondrá ciertas restricciones en su flujo de trabajo.

Git - Es un sistema de control de versiones distribuido y descentralizado que permite a un equipo de desarrolladores trabajar 
sobre el mismo código. Se denomina "distribuido" porque cada miembro del equipo dispone de una copia completa del código.
GitHub - Es una plataforma social puesta a disposición por la nube (sistema virtual) que interactúa con GIT para compartir proyectos versionados y administrados con GIT.

Flujo básico del versionado en git (Se divide en 4 estados):
* Working directory (modified) - Es la carpeta local de la computadora donde se almacenan los directorios y archivos de un proyecto creada con base en un commit específico. Los archivos en este directorio pueden estar modificados o eliminados en comparación con el commit actual al que HEAD está apuntando. El estado no está asociado a una rama en específico.
* Staging Area o Index (staged): Es un estado intermedio entre el directorio de trabajo y el repositorio, donde los archivos modificados están preparados para ser incluidos en la siguiente confirmación, pero aún no se han guardado en la historia del repositorio permitiendo observaciones y aún modificaciones. El estado no está asociado a una rama en específico.
* Git local directory / repository (commited) - En este estado, los archivos han sido confirmados y guardados en el repositorio local de Git como último commit de la rama activa. Cada confirmación crea un nuevo punto en la historia del repositorio, lo que permite la recuperación de versiones anteriores si es necesario. El estado si está asociado a una rama en específico.

                            A continuación una descripción detallada del proceso de un commit:

                            1. Se crea un nuevo archivo en el working directory o se modifica un archivo existente que ya está siendo trackeado por Git.
                            2. Al ejecutar el comando git add, Git crea un blob que representa el contenido del archivo creado o modificado en su estado actual. Luego, se agrega una referencia a ese blob en el staging area
                            3. Cuando se realiza un commit se crea un objeto que incluye las referencias del staging area y las de otros objetos que incluyen a su vez más referencias, representando así el estado actual del proyecto.

                            Commit .- Es una entidad u objeto en Git que incluye: 
                                      * Un ID hash SHA-1 asignado.
                                      * Metadatos (como la fecha, el autor y el mensaje del commit).
                                      * Una referencia al commit padre (si existe).
                                      * Una referencia a un objeto tree que representa el directorio del proyecto en ese momento. El tree incluye referencias a los blobs (contenidos de archivos) y a otros objetos tree (subdirectorios).
      
* Git remote directory / repository (saved remotly) - Es el área correspondiente al estado remote y es el directorio remoto donde almacenamos los archivos del proyecto en alguna plataforma web como GitHub, GitLab, BitBucket. Git denomina origin al repositorio remoto.

.git - Carpeta oculta que se crea en la raíz de un repositorio Git. Esta carpeta contiene todos los archivos y metadatos necesarios para gestionar el repositorio y su historial de versiones.

Estados locales:
Working directory - Archivos que no están preparados para ser registrados en el historial del repositorio (Modificaciones constantes sin ser rastreadas por git)
Staging Area - Archivos que ya están preparados para ser registrados en el historial del repositorio.
git local directory - Archivos que quedan registrado con su estado actual en el historial del repositorio (Inmodificables una vez registrado)

Estado remoto:
git remote directory - Archivos que se envían a la plataforma social

Configuración inicial:
git --version
git config --global user.name "Jonathan MirCha"
git config --global user.email jonmircha@gmail.com
git config --global user.ui true
git config --global init.defaultBranch main
git config --list
# asignando visual studio code como el editor nucleo quie realiza la configuración de git
git config --global core.editor "code --wait"
git config --global -e
# para estandarizar los saltos de línea en windows
git config --global core.autocrlf true
En sistemas Windows:
Al realizar commit - Git realizará la conversión automática de las secuencias de escape que representan los saltos de línea de CRLF -> LF antes de almacenar los archivos en el repositorio.
Al realizar clone - Git realizará la conversión automática de las secuencias de escape de LF -> CRLF en los archivos de trabajo.
Al realizar checkout - Git realizará la conversión automática de las secuencias de escape de LF -> CRLF en los archivos de trabajo.
# para estandarizar los saltos de línea en linux/mac
git config --global core.autocrlf input
En sistemas Unix:
Al realizar commit - Git convierte automáticamente las secuencias de escape que representan los saltos de línea de CRLF → LF antes de almacenar los archivos en el repositorio.
Al realizar clone - Git no realiza ninguna conversión de saltos de línea al clonar el repositorio, ya que los sistemas Unix esperan LF como el formato estándar de salto de línea.
Al realizar checkout - Git no realiza ninguna conversión de saltos de línea al hacer checkout, dejando los saltos de línea en formato LF en los archivos de trabajo.
# ver todas las opciones (banderas) de la configuración de git en la terminal
git config -h
# ver todas las opciones (banderas) de la configuración de git en el navegador
git help config

-------- INICIO de los comandos del flujo básico de Git --------

Comandos principales:
# Inicializar un repositorio
git init

# agregar todos los cambios de todos los archivos al staged
git add archivo/directorio
git add .

# los cambios son comprometidos en el repositorio
# debes escribir el mensaje del cambio cuando se abra el archivo de configuración
# al terminar guarda y cierra el archivo para que los cambios tengan efecto
git commit
# es un shortcut del comando anterior
# escribes y confirmas el mensaje del cambio en un sólo paso
git commit -m "mensaje descriptivo del cambio"


# se agrega el origen remoto de tu repositorio de GitHub
git remote add origin https://github.com/usuario/repositorio.git
# empujamos la rama local master al repositorio remoto sin establecer una vinculación entre la rama remota master recien creada y la rama local master
git push origin master (master refiere a la rama local)
# -u / --set-upstream-to= 
La opción --set-upstream-to= en Git se utiliza para establecer la rama upstream para tu rama local activa, lo que significa que vincula tu rama local activa a una rama remota específica
# la primera vez que vinculamos a la rama remota recien creada master con la rama master local y empujamos los cambios
git push -u origin master (master refiere a la rama local)
# abreviaciones para las subsecuentes actualizaciones si los nombres de la rama remota y local coinciden
git push / git pull
# no vinculamos a la rama remota master con la rama local second-branch y simplemente empujamos los cambios
git push origin second-branch:master
# simplemente vinculamos la rama remota master con la rama local second branch
git push --set-upstream-to=origin/master second-branch
# la primera vez que vinculamos a la rama remota master con la rama local second-branch y empujamos los cambios
git push -u origin second-branch:master
# para las subsecuentes actualizaciones si las ramas vinculadas tienen distinto nombre no se puede utilizar la abreviatura 'git push'
git push origin second-branch:master

# Descargar repositorios a local con cambios
git pull

-------- FIN de los comandos del flujo básico de Git --------

DE master A main

Para repositorios nuevos
git init
git add .
git commit -m "Primer commit"
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main

Para repositorios existentes
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main

--------- Iniciativa Black Lives Matter ---------

Para reemplazar la rama master por main en GitHub
# Paso 1
# Crea la rama local main y pásale el historial de la rama master
git branch -m master main


# Paso 2
# Haz un push de la nueva rama local main en el repositorio remoto de GitHub
git push -u origin main


# Paso 3
# Cambia el HEAD actual a la rama main | Especifica qué rama del repositorio remoto es la rama por defecto en el repositorio local
git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main

Nota: Al cambiar la rama por defecto en un repositorio (por ejemplo, en GitHub o GitLab), lo que realmente se hacie es cambiar a qué rama apunta el HEAD de ese repositorio de forma predeterminada

--------- Fin de la iniciativa Black Lives Matter ---------

ARCHIVOS IGNORADOS

# Los archivos ignorados se determinan por medio del archivo .gitignore
Que un archivo sea ignorado significa que no será trackkeado por git

# esto es un comentario
archivo.ext
carpeta
/archivo_desde_raiz.ext

# ignorar todos los archivos que terminen en .log
*.log

# excepto production.log
!production.log

# ignorar los archivos terminados en .txt dentro de la carpeta doc,
# pero no en sus subcarpetas
doc/*.txt

# ignorar todos los archivos terminados en .txt dentro de la carpeta doc
# y también en sus subcarpetas
doc/**/*.txt

RAMAS (Branch)

Rama (branch) - Es una línea secundaria de commits secuenciales.

Comando de las ramas

# crear rama
git branch nombre-rama

# cambiar de rama
git checkout nombre-rama

# crear una rama y cambiarte a ella
git checkout -b rama

# eliminar rama
git branch -d nombre-rama

# eliminar ramas remotas
git push origin --delete nombre-rama

#eliminar rama (forzado)
git branch -D nombre-rama

# listar todas las ramas del repositorio
git branch

# lista ramas no fusionadas a la rama actual
git branch --no-merged

# lista ramas fusionadas a la rama actual
git branch --merged

# rebasar ramas
git checkout rama-secundaria
git rebase rama-principal

# Traer todas las ramas de un repositorio remoto a local
git branch -r | grep -v '\->' | sed 's/origin\///' | while read branch; do git checkout --track origin/$branch; done

FUSIONES

Une dos ramas. Para hacer una fusión necesitamos:

1. Situarnos en la rama que se quedará con el contenido fusionado.

# nos cambiamos a la rama principal que quedará de la fusión
git checkout rama-principal

2. Cuando se fusionan ramas se pueden dar 2 resultados diferentes:

# ejecutamos el comando merge con la rama secundaria a fusionar
git merge rama-secundaria

Fast-Forward: La fusión se hace automática, no hay conflictos por resolver.
Manual Merge: La fusión hay que hacerla manual, para resolver conflictos de duplicación de contenido.

CAMBIOS

Puedes agregar modificaciones al último cambio (commit)

# sin editar el mensaje del último commit
git commit --amend --no-edit

# editando el mensaje del último commit
git commit --amend -m "nuevo mensaje para el último commit"

# eliminar el último commit
git reset --hard HEAD~1
Podemos cambiar de rama o desplazarnos en el historial del repositorio hacia atrás o adelante en cambios (commits), sin afectar el repositorio como tal.

# cambiar a una rama
git checkout nombre-rama

# cambiar a un commit en particular
git checkout id-commit

REGISTRO DEL HISTORIAL 

git log nos permite conocer todo el historial de un proyecto, con la información de la fecha, el autor y id de cada cambio.

git log

# muestra en una sola línea por cambio
git log --oneline

# guarda el log en la ruta y archivo que especifiquemos
git log > commits.txt

# muestra el historial con el formato que indicamos
git log --pretty=format:"%h - %an, %ar : %s"

# cambiamos la n por cualquier número entero y mostrará los n cambios recientes
git log -n

# muestra los cambios realizados después de la fecha especificada
git log --after="2019-07-07 00:00:00"

# muestra los cambios realizados antes de la fecha especificada
git log --before="2019-07-08 00:00:00"

# muestra los cambios realizados en el rango de fecha especificado
git log --after="2019-07-07 00:00:00" --before="2019-07-08 00:00:00"

# muestra una gráfica del historial de cambios, rama y fusiones
git log --oneline --graph --all

# muestra todo el registro de acciones del log
# incluyendo inserciones, cambios, eliminaciones, fusiones, etc.
git reflog

# diferencias entre el Working Directory y el Staging Area
git diff

# grafica el historial de commits en diversas ramas junto con resolucines de conflictos
git log --online --graph -all

Ejemplo:

*   76716b2 (HEAD -> main) Fourth commit merge main/branch2
|\
| * 6539a9b (branch2) First commit branch2
* | 48cedae Third commit update
|/
* 44d482a Second Commit

RESETEO DEL HISTORIAL

Podemos eliminar el historial de cambios del proyecto hacia adelante con respecto de un punto de referencia.

#nos muestra el listado de archivos nuevos (untracked), borrados o editados
git status

# borra HEAD
git reset --soft

# borra HEAD y Staging
git reset --mixed id

# borra HEAD, Staging y Working Directory
git reset --hard id

# deshace todos los cambios después del commit indicado, preservando los cambios localmente
git reset id-commit

# desecha todo el historial y regresa al commit especificado
git reset --hard id-commit


RESETAR REPOSITORIO
Si en algún momento tienes la necesidad de resetear el historial de cambios de un repositorio para que quede como si lo acabarás de crear ejecuta esta serie de comandos:

cd carpeta-repositorio
mv .git/config ~/saved_git_config
rm -rf .git
git init
git branch -M main
git add .
git commit -m "Commit inicial"
mv ~/saved_git_config .git/config
git push --force origin main


REMOTOS

# muestra los orígenes remotos del repositorio
git remote

# muestra los orígenes remotos con detalle
git remote -v

# agregar un orígen remoto
git remote add nombre-orígen https://github.com/usuario/repositorio.git

# renombrar un orígen remoto
git remote rename nombre-viejo nombre-nuevo

# eliminar un orígen remoto
git remote remove nombre-orígen

# descargar una rama remota a local diferente a la principal
git checkout --track -b rama-remota origin/rama-remota


ETIQUETAS

Con esta opción git nos permite versionar nuestro código, librería o proyecto.

# listar etiquetas
git tag

# crea una etiqueta
git tag numero-versión

# eliminar una etiqueta
git tag -d numero-versión

# mostrar información de una etiqueta
git show numero-versión

# sincronizando la etiqueta del repositorio local al remoto
git add .
git commit -m "v1.0.0"
git  tag v1.0.0
git push origin numero-versión

# generando una etiqueta anotada (con mensaje de commit)
git add .
git tag -a "v1.0.0" -m "Mensaje de la etiqueta"
git push --tags


GITHUB PAGES

gh-pages es una rama especial para crear un sitio web a tu proyecto alojado directamente en tu repositorio de GitHub.

URL del repositorio: https://github.com/usuario/repositorio
URL del sitio: https://usuario.github.io/repositorio 
       Ej. https://edwardohazo.github.io/git-course
Para crear esta rama especial en GitHub ejecutamos los siguientes comandos:

git branch gh-pages
git checkout gh-pages

git remote add origin https://github.com/usuario/repositorio.git
git push origin gh-pages

# para descargar los cambios del repositorio remoto al local
git pull origin gh-pages


COLABORACIÓN EN GITHUB

Para poder colaborar en proyectos alojados en GitHub necesitamos hacer uso de los forks y pull requests, herramientas que nos ofrece la plataforma para dicho objetivo.

A continuación describo el proceso de colaboración en GitHub.

Forkea el repositorio en el que quieras colaborar, para hacerlo, sigue las instrucciones de este enlace.
Una vez forkeado el repositorio en tu cuenta de GitHub, clónalo en tu equipo de cómputo.
En el repositorio local hay que configurar los orígenes remotos de tu nueva copía para tener ambos remotos, los originales (origin) y los de tu copia, para hacerlo, sigue las instrucciones de este enlace.
Crea una rama nueva en tu fork local para hacer tu colaboración, y sincrónizala con tu repositorio remoto, para hacerlo, sigue las instrucciones de este enlace.
Configura tu repositorio para que acepté cambios (pull requests), para hacerlo, sigue las instrucciones de este enlace.
Crea una pull request, para hacerlo, sigue las instrucciones de este enlace.
Espera a que el dueño del repositorio original, acepte tus cambios.
Una vez que acepten tu pull request, es recomendable que borres la rama en la que trabajaste el cambio y actualices tu repositorio forkeado, con los cambios del repositorio original.
Anexo un resumen de los comandos a ejecutar para colaborar en un repositorio de GitHub:

# forkear repositorio
git clone https://github.com/usuario/repositorio.git
git remote -v
git remote rename origin fork
git remote add origin https://github.com/usuario/repositorio.git
git checkout -b rama-nueva
git push fork rama-nueva
# solicitar el pull request
# aceptar el pull request
git checkout main
git pull origin main
git push fork main
git branch -d rama-nueva
git push fork --delete rama-nueva




