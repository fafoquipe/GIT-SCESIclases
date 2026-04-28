# TRABAJO INDIVIDUAL
Benjamin Alex Quiroga Perez
## Preguntas de examen
QUE HACE STAGED
comando ssh-keygen -t ed25519 -C "gmail"
## Clase 1

###Que es GIT?
Es un sistema de control de versiones distribuidos, creando puntos de 
guardado y tener un control de versiones
### Como nacio GIT?
Linus Tolvas revisaba a mano todos los emails y se cansaba Usa 
BitKeeper, pero quitan su repositorio
se encierra en su habitacion 2 semanas y crea GIT
### Como se instala git?
no tomare apuntes de esto porque ya lo tengo XD
### Comandos basicos de GIT
git config global suer.name "Nombre"
git config --global user.email "Correo"
git config --global core.autocrlf true
git config --list
git config --global --list
git --version
### sistema de puntuacion XD
nada tampoco
### Archivos que todo repo deberia tener
Ese Diego con el Ridmi (video) 
readme.md (Estamos ahi)
.Gitignore


## Clase 2: STATES Y COMMITS
### Estados de GIT
1. Directorio de trabajo (modificado)
 Carpeta local
2. Stage area
 Preparado (voy a guardar estas cosas)
3. Commited (confirmado)
 Git crea un punto de guardado y ya estan en el historial (Ya son accesibles)
### Directorio de trabajo
git no hace nada como tal, solo los clasifica como
Untracked : Aparecio de la nada
Modified: Git mira un cambio en un archivo creado anteriormente
git restore -> permite volver al estado anterior o elimina cambios 
git restore aplicado a un archivo borrado, este se desborra XD
touch .env (credenciales) ---> .gitignore contiene los archivos 
que no quieres subir
git add (Nombre del archivo) (.gitignore si quieres guardar)
pasas de modifies a stagged
git add . (se agrega TODO)
git restore --staged README.md   esto quita el archivo de staged 
(vuelve a modified)
git commit -m "nombre" ->  crea el punto de guardado
deshacer el ultimo commit git reset --soft HEAD~1

### Buenas prácticas:
Cada cuanto hacer commits? 
commits atomicos -> pequenios pero funcionales
commits en ingles y en maximo 50 caracteres
usar un prefijo 
fit nueva caracteristica
fix arregla un bug
perf mejora en rendimiento
build cambios en el sistema deployed
ci cambios en la integracion continua
docs para cambios en la documentacion
refactor cambio de nombre de variables 
test es un test
si auxi, usare docs :(
git add script
como darle mas contexto? 
git commit 
(abre el editor) feat: add math operations -> titulo
- add sum function
- add mult function
ctrl+o -> x

## CLASE 3
fue solo GITHUB y con la conexios por SSH del repositorio local con
es que esta ya subido en mis repos de github

## CLASE 4
### GIT REMOTE
Es el comando que nos permite gestionar conexiones con repositorios remotos
Git remote -v (url exacta donde apunta el repo)
git remote add <apodo> "URL" (vincula nuestro repo local con uno en la nube)
git remote set-url<apodo>"url" cambia la url a la que apunta nuestro repo
###GIT CHECKOUT
Ver hacia atras o probar cambios sin arruinar la rama principal
git checkout (hash)
el hash se obtiene con git log --oneline

