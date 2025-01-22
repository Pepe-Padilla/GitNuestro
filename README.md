# GitNuestro
### **Práctica Git &amp; GitHub** - Ejercicio de Bootcamp Inteligencia Artificial Full Stack Edición III

Este proyecto es un entregable para la práctica del Master Bootcamp Inteligencia Artificial Full Stack Edición III realizado por el centro de formación [@Keepcoding](https://github.com/KeepCoding)

---

Preguntas de la práctica

- ¿Qué comando utilizaste en el paso 11? ¿Por qué?
``` sh
git reset --hard HEAD~1
# --hard asegura dejar el WA limpio sobre lo que había en el commit
```

- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?
``` sh
git reflog
# busqueda del commit afectado 0d1627a
git reset --hard 0d1627a
# reflog para ver el historial y sacar el commit perdido (log no lo mostraría)
# git reset --hard <commit perdido> para decir aqui no pasó nada
```

- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?
``` sh
git merge main
# No, Already up to date. No pasa nada porque main es predecesor de styled
```

- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?
``` sh
git checkout styled
git merge --no-ff --no-commit htmlify
# aunque espero confilctos cuando tengo dudas del merge prefiero usar --no-commit para asegurarme a mano
#
# Como era de esperar más conflictos imposible, solo me quedé con la única fila que no tenía stye de markdown
```

- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?
``` sh
git checkout main
git merge styled
# No todo bien, de hecho fue un fast-foward, 
# antes tuve que desactivar el --no-ff por defecto de mi git (lo puse hace mucho), que es una mala practica especialmente contra main/master.
```

- ¿Qué comando o comandos utilizaste en el paso 25?
``` sh
git log --graph --decorate --pretty=oneline
# tan importante es esta combinación que la tengo en alias:
# git config --global alias.graph "log --graph --decorate --pretty=oneline"
```

- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
``` sh
git checkout main
git merge --no-ff title
# Es un predecesor, si no fuera por el --no-ff lo habría 
```

- ¿Qué comando o comandos utilizaste en el paso 27?
``` sh
git reset HEAD~1
# esta vez sin hard, que si no no hay paso 28
```

- ¿Qué comando o comandos utilizaste en el paso 28?
``` sh
git restore ./git-nuestro.md
# así se resuelve
```

- ¿Qué comando o comandos utilizaste en el paso 29?
``` sh
git branch -D title
git branch 
# para comprobar
```

- ¿Qué comando o comandos utilizaste en el paso 30?
``` sh
git reflog
# buscar el commit
git merge --no-ff 26880ea
# también se hubiera podido rehaciendo la rama title pero me gustó así
```

- ¿Qué comando o comandos usaste en el paso 32?
``` sh
git graph
# buscar el commit
git reset --hard e92d4cbc54a91d83b2b4f0bf9fd8a5e1a92f4a44
```

- ¿Qué comando o comandos usaste en el punto 33?
``` sh
# Ya tenía el commit del git graph anterior
git reset --hard 2ada5069dd4e2b13f37e9602b921ee420a2859b4
```


---

### Historial completo Practica 1
``` sh
# 1) Crear un repositorio en GitHub y clónalo en tu equipo
# Creación de la repo desde GitHub
git clone https://github.com/Pepe-Padilla/GitNuestro.git
cd .\GitNuestro\
# Edición del README.md desde editor de texto

# 2) Crear un archivo git-nuestro.md con el contenido:
New-Item -Path '.\git-nuestro.md' -ItemType File
# Modificación del fichero desde editor de texto

# 3) Añadir git-nuestro.md al staging area
git add .

# 4) Mover lo que hay en el staging area al repositorio
git commit -m "Git nuestro base"

# 5) Crear una rama llamada “styled”
git branch styled

# 6) Listar las ramas que hay en el repositorio
git branch

# 7) Moverse a la rama “styled”
git checkout styled

# 8) Comprobar que se está en la rama correcta
git status

# 9) Modificar en el archivo git-nuestro.md:
# Modificación del fichero desde editor de texto

# 10) Añadir los cambios al staging area y luego pasarlos al repositorio
git commit -a -m "cambios styled con amor a git"

# 11) Deshacer el último commit (perdiendo los cambios realizados en el working copy)
git reset --hard HEAD~1
# --hard asegura dejar el WA limpio sobre lo que había en el commit

# 12) Rehacer el último commit (el que acabamos de deshacer)
git reflog
# busqueda del commit afectado 0d1627a
git reset --hard 0d1627a
# reflog para ver el historial y sacar el commit perdido (log no lo mostraría)
# git reset --hard <commit perdido> para decir aqui no pasó nada

# 13) Hacer un merge con ‘main’ (styled absorbe a main)
git merge main
# No, Already up to date. No pasa nada porque main es predecesor de styled

# 14) Volver a la rama main
git checkout main

# 15) Crear una nueva rama llamada “htmlify”
git branch htmlify

# 16) Cambiar a la rama htmlify
git checkout htmlify

# 17) Modificar en el archivo git-nuestro.md:
# Modificación del fichero desde editor de texto

# 18) Hacer un commit
git commit -a -m "htmlizado - markdown vs html - who wins??? who is next??"

# 19) Hacer un merge de “htmlify” en “styled” (styled absorbe a htmlify)
git checkout styled
git merge --no-ff --no-commit htmlify
# aunque espero confilctos cuando tengo dudas del merge prefiero usar --no-commit para asegurarme a mano
# Como era de esperar más conflictos imposible, solo me quedé con la única fila que no tenía stye de markdown

# 20) Si hay conflictos, deberemos resolverlos quedándonos con el contenido de la rama “styled”.
# Modificación del fichero desde editor de texto
git add .
git commit
# acepto el mensaje por defecto

# 21) Desde “main”, hacer un merge con “styled” ## No me gusta el Fast Foward pero tú mandas
git checkout main
git merge styled
# No todo bien, de hecho fue un fast-foward, antes tuve que desactivar el --no-ff por defecto de mi git (lo puse hace mucho), que es una mala practica especialmente contra main/master.

# 22) Crear una rama “title” y cambiarse a esa rama
git branch title

# 23) Añadir un título (a tu gusto) al archivo git-nuestro.md y hacer un commit.
git checkout title
# Modificación del fichero desde editor de texto
git commit -a -m "Un titulo mono para un buen final"

# 24) Volver a la rama main
git checkout main

# 25) Dibujar el diagrama
git log --graph --decorate --pretty=oneline
# tan importante es esta combinación que la tengo en alias:
# git config --global alias.graph "log --graph --decorate --pretty=oneline"

# 26) Hacer un merge “no fast-forward” de “title” en “main” (main absorbe a title)
git checkout main
git merge --no-ff title
# Es un predecesor, si no fuera por el --no-ff lo habría 

# 27) Deshacer el merge (sin perder los cambios del working copy)
git reset HEAD~1
# esta vez sin hard, que si no no hay paso 28

# 28) Descartar los cambios
git restore ./git-nuestro.md
# así se resuelve

# 29) Eliminar la rama “title”
git branch -D title
git branch 
# para comprobar

# 30) Rehacer el merge que hemos deshecho
git reflog
# buscar el commit
git merge --no-ff 26880ea
# también se hubiera podido rehaciendo la rama title pero me gustó así

# 31) Volver a main y eliminar el resto de ramas
git branch
# listado de ramas
git branch -D htmlify
git branch -D styled

# 32) Volver al commit inicial cuando se creó el poema
git graph
# buscar el commit
git reset --hard e92d4cbc54a91d83b2b4f0bf9fd8a5e1a92f4a44

# 33) Volver al estado final, cuando pusimos título al poema
git reset --hard 2ada5069dd4e2b13f37e9602b921ee420a2859b4

# 34) Crear los siguientes tags:
git reflog
# Para ver los commit
# inicial: en el primer commit
git tag -a inicial -m inicial e92d4cb
# styled: modificación del paso 10
git tag -a styled -m styled 0d1627a
# htmlify: modificación del paso 17-18
git tag -a htmlify -m htmlify b212e42
# title: modificación del paso 30
git tag -a title -m title 26880ea

# 35) Ir al tag htmlify
git checkout tags/htmlify
# estamos en "detached HEAD" ahhh algo esta fallando en la oración del git nuestro "No nos dejes caer en <em>detached HEAD</em>"

# 36) Vuelve a la rama main
git checkout main
# Uff todo bien XD

# 37) Sube a GitHub todas las ramas y todos los tags
git push --follow-tags

```
