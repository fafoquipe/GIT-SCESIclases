# APUNTES GIT - BENJAMIN QUIROGA

## PREGUNTAS DE EXAMEN (CUIDADO)
* Que es un commit? Un punto de guardado en el historial con un ID unico (hash).
* Para que sirve el .gitignore? Para evitar trackear archivos sensibles (.env) o basura (node_modules).
* Diferencia entre git restore y git restore --staged? El primero borra cambios en el working directory, el segundo solo saca el archivo de staging.
* Como ver el historial simplificado? git log --oneline.
* Que hace el git reset --soft? Borra el commit pero mantiene tus cambios en los archivos.
* Que es una rama (branch)? Una linea de tiempo independiente para experimentar sin arruinar la main.
* El puntero HEAD: Es el indicador que te dice en que rama o commit estas parado actualmente.

---

## Clase 1: CONFIGURACION INICIAL
* Configurar identidad: 
  git config --global user.name "Benjamin Quiroga"
  git config --global user.email "tu@correo.com"
  git config --global core.autocrlf true
* Inicializar repo: git init (crea la carpeta oculta .git).
* Archivos clave: README.md (documentacion) y .gitignore (para lo que no quieres que suba a la nube).

---

## Clase 2: STATES Y COMMITS
### Estados de GIT
1. Directorio de trabajo: Carpeta local (modificado).
2. Stage area: Preparado (limbo antes de guardar).
3. Commited: Confirmado (ya esta en el historial y es accesible).
### Comandos y Practica
* Untracked: Archivo nuevo que git no conoce.
* Modified: Archivo viejo con cambios nuevos.
* git restore <archivo> -> Vuelve al estado anterior o desborra archivos (XDD).
* git add . -> Pasas todo de modified a staged (al limbo).
* git restore --staged README.md -> Quita el archivo del staged y lo devuelve a modified.
* git commit -m "prefijo: mensaje" -> Crea el punto de guardado oficial.
* git reset --soft HEAD~1 -> Borra el ultimo commit pero te deja los archivos como estaban para corregir algo.
### Commits Atomicos (Prefijos)
* feat: nueva feature; fix: arregla bug; docs: documentacion; refactor: limpieza de codigo.
* Maximo 50 caracteres y en ingles si se puede.
* git commit (a secas) -> Abre el editor (como nano) para poner titulo y descripcion con mas detalle.

---

## Clase 3: GITHUB Y SSH
* Para no poner contraseña cada vez que haces push se usa SSH.
* Generas la llave en tu PC y la pegas en la config de GitHub.
* Esto vincula tu maquina con tu cuenta de forma segura.

---

## Clase 4: REMOTES Y CHECKOUT
### GIT REMOTE
* Permite gestionar conexiones con servidores en la nube.
* git remote -v -> Te da la URL exacta (fetch y push) a donde apunta tu repo.
* git remote add origin <URL> -> Vincula tu carpeta local con el repositorio vacio de GitHub.
### GIT CHECKOUT
* Sirve para viajar en el tiempo o probar cosas sin romper la rama main.
* git log --oneline -> Sacas el hash corto (ej: a1b2c3d).
* git checkout <hash> -> Te mueve a ese estado especifico del pasado para revisar codigo.
* Para volver al presente: git checkout main.

---

## Clase 5: BRANCHES (RAMAS)
### Conceptos de la Clase
* Una rama es una linea de tiempo independiente.
* Por que usarlas? Permiten el trabajo en paralelo y protegen el codigo estable de produccion.
* HEAD -> Puntero que indica donde estas parado.
### Comandos de Terminal
* git branch -> Lista todas las ramas locales (la que tiene el * es donde estas).
* git branch <nombre> -> Crea una rama nueva pero no te mueve a ella.
* git switch <nombre> -> Te mueve a la rama indicada (mueve el HEAD).
* git switch -c <nombre> -> Atajo para crear la rama y saltar a ella de una sola vez.
* git branch -d <nombre> -> Borra la rama (solo si ya fusionaste los cambios).
* git branch -D <nombre> -> Borrado forzado (borra la rama aunque tenga cambios no guardados).
* git merge <nombre-rama> -> Trae los cambios de la rama indicada hacia la rama donde estas parado.

---

## Clase 6: FUSIONES (MERGE) Y CONFLICTOS
### El Proceso de Merge
* Que es un Merge? Es unir dos lineas de tiempo (ramas). Traes los cambios de una rama a la que tienes activa.
* Fast-Forward: Si la rama main no se movio, Git solo "mueve el puntero" hacia adelante. Es el merge mas limpio.
* Merge Commit: Si ambas ramas avanzaron, Git crea un nuevo commit de union para juntar las dos historias.

### Comandos de Terminal
* git merge <nombre-rama> -> Fusiona la rama indicada en la rama donde estas parado actualmente.
* git merge --abort -> Si el merge se pone muy feo y quieres cancelar todo para volver a como estabas antes.

### Conflictos (Cuando todo explota)
* Por que pasa? Cuando dos personas (o tu mismo en dos ramas) tocan la misma linea del mismo archivo.
* Como arreglarlo:
  1. Git detiene el merge y te dice que archivos fallaron.
  2. Abres el archivo en nano y veras las marcas:

     <<<<<<< HEAD (lo que tu tienes)

     ======= (separador)

     >>>>>>> rama-colaborador (lo que viene de afuera)

  3. Borras las marcas y dejas solo el codigo que sirve.
  4. git add . y git commit -> Para confirmar que ya arreglaste el choque.

---

## Clase 7: REMOTOS Y PULL REQUESTS (PR)
### Flujo de Trabajo en la Nube
* Que es un Pull Request (PR)? No es un comando de git, es una herramienta de GitHub para pedir permiso antes de meter tus cambios a la rama principal.
* Para que sirve el PR? Para que otros revisen tu codigo, comenten y den el "visto bueno" antes del merge final.

### Comandos de Sincronizacion
* git push origin <nombre-rama> -> Sube tus commits locales al repositorio en GitHub.
* git fetch -> Descarga la informacion de la nube pero NO toca tus archivos locales. Sirve para ver que hicieron los demas.
* git pull -> Es un git fetch + git merge. Descarga todo y lo intenta unir a tus archivos de una. Cuidado con los conflictos aqui.
* git remote prune origin -> Limpia las referencias locales de ramas que ya fueron borradas en GitHub.

### Buenas Practicas
* Siempre hacer un git pull antes de empezar a trabajar para tener lo ultimo del equipo.
* No pushear directo a main; siempre usar ramas y Pull Requests para mantener el codigo limpio.

---

## Clase 8: COMANDOS AVANZADOS Y LIMPIEZA
### Git Stash (Cajon de sastre)
* Para que sirve? Para guardar cambios temporalmente sin hacer commit porque tienes que cambiar de rama rapido.
* git stash -> Guarda tus cambios actuales en un "limbo" y deja el working directory limpio.
* git stash list -> Muestra la lista de cosas que tienes guardadas.
* git stash pop -> Recupera los cambios guardados y los borra del stash.

### Git Rebase (La alternativa al Merge)
* Que es? Es otra forma de integrar cambios. En lugar de crear un commit de fusion, "reescribe" la historia para que parezca que todo paso en una sola linea.
* git rebase main -> Pone tus cambios por encima de lo ultimo que haya en main. Queda mucho mas limpio pero es peligroso en ramas compartidas.

### Limpieza y Tags
* git clean -f -> Borra archivos que NO estan trackeados (cuidado, esto no se recupera).
* git tag -a v1.0 -m "Version final" -> Le pone una "etiqueta" a un commit importante (como un lanzamiento).
* git commit --amend -> Para editar el mensaje del ultimo commit si te equivocaste al escribirlo.

---
