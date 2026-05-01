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
