<!-- Autor: Daniel Benjamin Perez Morales -->
<!-- GitHub: https://github.com/DanielBenjaminPerezMoralesDev13 -->
<!-- Gitlab: https://gitlab.com/DanielBenjaminPerezMoralesDev13 -->
<!-- Correo electrónico: danielperezdev@proton.me  -->

# ***Bandido Nivel 31 → Nivel 32***

- *Meta de nivel*

- *Hay un repositorio git en ssh://bandit31-git@localhost/home/bandit31-git/repo a través del puerto 2220. La contraseña del usuario bandit31-git es la misma que la del usuario bandit31.*

- *Clona el repositorio y encuentra la contraseña para el siguiente nivel.*
- **Comandos que puedes necesitar para resolver este nivel**

- *git*

## ***1. Ver el fichero de configuración de Git***

- *Primero, mostramos el fichero `.gitconfig`, que contiene la configuración de usuario para Git. Este fichero suele incluir el nombre de usuario y el correo electrónico que se utilizarán para los commits:*

```bash
cat .gitconfig
```

- *La salida muestra que el usuario está configurado como **bandit31** con el correo electrónico **`bandit31@overthewire.org`**:*

```bash
[user]
        email = bandit31@overthewire.org
        name = bandit31
```

### ***2. Clonar el repositorio con `git clone`***

- *A continuación, creamos un directorio temporal con el comando `mktemp -d` para mantener nuestro entorno limpio y evitar interferencias con otros ficheros o directorios.*

```bash
cd $(mktemp -d)
```

- *Después, clonamos el repositorio de Git utilizando el siguiente comando. Es importante especificar el puerto correcto (2220) con la variable de entorno `GIT_SSH_COMMAND`, ya que este puerto se utiliza en este nivel para acceder al repositorio de Git:*

```bash
GIT_SSH_COMMAND="ssh -p 2220" git clone ssh://bandit31-git@localhost/home/bandit31-git/repo
```

- *Esto clona el repositorio en el directorio `repo` dentro del directorio temporal.*

### ***3. Revisar el contenido del fichero `README.md`***

- *Al ingresar al repositorio recién clonado, leemos el fichero `README.md`, que nos da instrucciones sobre la tarea que debemos realizar. El contenido del fichero es el siguiente:*

```bash
cat README.md
```

- **Salida:**

```bash
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

- *El objetivo es crear un fichero llamado **`key.txt`** con el contenido **"May I come in?"** y luego **hacer un push** de este fichero al repositorio remoto en la rama **master**.*

### ***4. Crear y agregar el fichero `key.txt`***

- *Primero, creamos el fichero `key.txt`:*

```bash
touch key.txt
```

- *Luego, agregamos el contenido al fichero con el siguiente comando:*

```bash
echo "May I come in?" > key.txt
```

- *Ahora, hemos creado el fichero con el contenido correcto. Antes de hacer un commit, debemos asegurarnos de que el fichero sea agregado al área de preparación (staging area) de Git.*

### ***5. Verificar las ramas remotas***

- *Ejecutamos el siguiente comando para ver las ramas remotas disponibles en el repositorio:*

```bash
git branch -r
```

- *La salida muestra que solo existe la rama `master` en el repositorio remoto:*

```bash
origin/HEAD -> origin/master
origin/master
```

### ***6. Problema con `.gitignore`***

- *Cuando intentamos agregar el fichero `key.txt` con el comando `git add key.txt`, Git nos advierte que este fichero está siendo ignorado debido a una configuración en el fichero `.gitignore`. El mensaje dice que el fichero `key.txt` está siendo ignorado y nos sugiere usar la opción `-f` para forzar la adición:*

```bash
git add key.txt --verbose --all .
```

- *Salida del mensaje de advertencia:*

```bash
The following paths are ignored by one of your .gitignore files:
key.txt
hint: Use -f if you really want to add them.
hint: Turn this message off by running
hint: "git config advice.addIgnoredFile false"
```

### ***7. Agregar el fichero con la opción `-f`***

- *Para solucionar este problema, podemos forzar la adición del fichero `key.txt` utilizando la opción `-f` o `--force`. Esto ignorará la configuración de `.gitignore` y permitirá agregar el fichero al área de preparación:*

```bash
git add key.txt --force
```

- *O alternativamente, podemos usar:*

```bash
git add key.txt -f
```

### ***8. Verificar el estado del repositorio***

- *Ejecutamos `git status` para verificar que el fichero ha sido agregado correctamente al área de preparación:*

```bash
git status
```

- *La salida muestra que el fichero `key.txt` está listo para ser committeado:*

```bash
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   key.txt
```

### ***9. Eliminar el fichero `.gitignore`***

- *Otra forma de resolver el problema de ignorar el fichero es eliminar el fichero `.gitignore` que está causando que Git ignore el fichero `key.txt`. Para hacerlo, usamos el comando `rm`:*

```bash
rm .gitignore
```

- *Luego, volvemos a intentar agregar el fichero `key.txt`:*

```bash
git add key.txt --verbose
```

- *Este comando muestra que el fichero `key.txt` fue agregado correctamente:*

```bash
add 'key.txt'
```

### ***10. Hacer el commit***

- *Ahora que el fichero está en el área de preparación, hacemos el commit con el mensaje correspondiente:*

```bash
git commit --message="Añadiendo file key.txt" --verbose --verify --all
```

- *La salida muestra que el commit ha sido realizado correctamente y el fichero `key.txt` ha sido añadido:*

```bash
[master f95b2e4] Añadiendo file key.txt
 2 files changed, 1 insertion(+), 1 deletion(-)
 delete mode 100644 .gitignore
 create mode 100644 key.txt
```

### ***11. Hacer push del commit***

- *Finalmente, hacemos push de los cambios al repositorio remoto usando el siguiente comando. Esto subirá el commit con el fichero `key.txt` al repositorio remoto en la rama `master`:*

```bash
GIT_SSH_COMMAND="ssh -p 2220" git push --set-upstream origin master --verbose --verify
```

```bash
bandit31@bandit:/tmp/tmp.UzSPZ0STdn/repo$ GIT_SSH_COMMAND="ssh -p 2220" git push --set-upstream origin master --verbose --verify
Pushing to ssh://localhost/home/bandit31-git/repo
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit31/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password:
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 301 bytes | 301.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
remote: Well done! Here is the password for the next level:
remote: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
To ssh://localhost/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://localhost/home/bandit31-git/repo'
```

- **Password:**

```bash
3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
```

### ***Resumen de los pasos***

1. ***Clonamos el repositorio** *y accedemos al fichero `README.md` que nos da instrucciones sobre la tarea.**
2. ***Creamos el fichero `key.txt`** *con el contenido correcto.**
3. Intentamos **agregar el fichero** *al repositorio, pero se nos advierte que está siendo ignorado por el fichero `.gitignore`.*
4. ***Forzamos la adición** *del fichero usando `git add -f` o eliminamos el fichero `.gitignore`.**
5. ***Realizamos el commit** *con el fichero `key.txt` y el mensaje correspondiente.**
6. ***Hacemos push** *del commit al repositorio remoto en la rama `master`.**

- *De esta manera, hemos completado la tarea y hemos enviado el fichero al repositorio remoto correctamente.*
