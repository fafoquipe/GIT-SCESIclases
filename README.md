# APUNTES GIT - BENJAMIN QUIROGA

## PREGUNTAS DE EXAMEN
* Que es un commit? Un punto de guardado en el historial con un ID unico (hash)[cite: 5].
* Para que sirve el .gitignore? Para evitar trackear archivos sensibles (.env) o basura (node_modules)[cite: 5].
* Diferencia entre git restore y git restore --staged? El primero borra cambios en el working directory, el segundo solo saca el archivo de staging[cite: 5].
* Como ver el historial simplificado? git log --oneline[cite: 5].
* Que hace el git reset --soft? Borra el commit pero mantiene tus cambios en los archivos[cite: 5].

---

## Clase 1: CONFIGURACION INICIAL
* Configurar identidad: 
  git config --global user.name "Benjamin Quiroga"[cite: 5]
  git config --global user.email "tu@correo.com"[cite: 5]
  git config --global core.autocrlf true[cite: 5]
* Inicializar repo: git init (crea la carpeta oculta .git)[cite: 5].
* Archivos clave: README.md (documentacion) y .gitignore (para lo que no quieres que suba a la nube)[cite: 5].

---

## Clase 2: STATES Y COMMITS
### Estados de GIT
1. Directorio de trabajo: Carpeta local (modificado)[cite: 5].
2. Stage area: Preparado (limbo antes de guardar)[cite: 5].
3. Commited: Confirmado (ya esta en el historial y es accesible)[cite: 5].
### Comandos y Practica
* Untracked: Archivo nuevo que git no conoce[cite: 5].
* Modified: Archivo viejo con cambios nuevos[cite: 5].
* git restore <archivo> -> Vuelve al estado anterior o desborra archivos (XDD)[cite: 5].
* git add . -> Pasas todo de modified a staged (al limbo)[cite: 5].
* git restore --staged README.md -> Quita el archivo del staged y lo devuelve a modified[cite: 5].
* git commit -m "prefijo: mensaje" -> Crea el punto de guardado oficial[cite: 5].
* git reset --soft HEAD~1 -> Borra el ultimo commit pero te deja los archivos como estaban para corregir algo[cite: 5].
### Commits Atomicos (Prefijos)
* feat: nueva feature; fix: arregla bug; docs: documentacion; refactor: limpieza de codigo[cite: 5].
* Maximo 50 caracteres y en ingles si se puede[cite: 5].
* git commit (a secas) -> Abre editor para poner titulo y descripcion con mas detalle[cite: 5].

---

## Clase 3: GITHUB Y SSH
* Para no poner contraseña cada vez que haces push se usa SSH[cite: 5].
* Generas la llave en tu PC y la pegas en la config de GitHub[cite: 5].
* Esto vincula tu maquina con tu cuenta de forma segura[cite: 5].

---

## Clase 4: REMOTES Y CHECKOUT
### GIT REMOTE
* Para volver al presente: git checkout main[cite: 5].
* Sirve para viajar en el tiempo o probar cosas sin romper la rama main[cite: 5].
* git log --oneline -> Sacas el hash corto (ej: a1b2c3d)[cite: 5].
* git checkout <hash> -> Te mueve a ese estado especifico del pasado para revisar codigo[cite: 5].
* Permite gestionar conexiones con servidores en la nube[cite: 5].
* git remote -v -> Te da la URL exacta (fetch y push) a donde apunta tu repo[cite: 5].
* git remote add origin <URL> -> Vincula tu carpeta local con el repositorio vacio de GitHub[cite: 5].

