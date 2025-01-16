<!-- Autor: Daniel Benjamin Perez Morales -->
<!-- GitHub: https://github.com/DanielBenjaminPerezMoralesDev13 -->
<!-- Gitlab: https://gitlab.com/DanielBenjaminPerezMoralesDev13 -->
<!-- Correo electrónico: danielperezdev@proton.me  -->

# ***Bandido Nivel 33 → Nivel 34***

- *En este momento, el nivel 34 aún no existe.*
Lo que estás viendo es el resultado del último nivel en el juego **Bandit** de **OverTheWire**. A continuación te explico lo que está pasando:

## ***1. `ls -l`***

- *Cuando ejecutas el comando `ls -l`, estás listando los ficheros en tu directorio actual con detalles sobre sus permisos, propietario, tamaño, fecha de modificación, etc. El resultado muestra el fichero **`README.txt`**.*

```bash
-rw------- 1 bandit33 bandit33 430 Sep 19 07:08 README.txt
```

- **`-rw-------`:** *Los permisos del fichero indican que solo el propietario (**bandit33**) tiene permisos de lectura y escritura. Ningún otro usuario tiene acceso a este fichero.*
- **`1 bandit33 bandit33`:** *Esto indica que el fichero es propiedad del usuario **bandit33** y del grupo **bandit33**.*
- **`430`:** *El tamaño del fichero en bytes.*
- **`Sep 19 07:08`:** *La fecha y hora de la última modificación del fichero.*
- **`README.txt`:** *El nombre del fichero.*

### ***2. `whoami`***

- *El comando `whoami` muestra el nombre del usuario que está ejecutando el comando. En este caso, el resultado es **`bandit33`**, lo que indica que actualmente estás logueado como **bandit33**.*

### ***3. `cat README.txt`***

- *El comando `cat` se usa para mostrar el contenido de un fichero. Al ejecutar `cat README.txt`, ves el contenido del fichero **`README.txt`**. Este fichero es un mensaje que te felicita por haber resuelto todos los niveles del juego **Bandit**.*

- *El mensaje en **`README.txt`** es el siguiente:*

```bash
Congratulations on solving the last level of this game!

At this moment, there are no more levels to play in this game. However, we are constantly working
on new levels and will most likely expand this game with more levels soon.
Keep an eye out for an announcement on our usual communication channels!
In the meantime, you could play some of our other wargames.

If you have an idea for an awesome new level, please let us know!
```

- *Este mensaje te indica que has completado el último nivel y que, por el momento, no hay más niveles disponibles en el juego. Sin embargo, te invitan a estar atento a futuros anuncios, ya que podrían añadir más niveles. También mencionan la posibilidad de que juegues otros juegos de guerra (**wargames**) de **OverTheWire** o que propongas ideas para nuevos niveles.*

- **`ls -l`** *te mostró los detalles del fichero **`README.txt`**.*
- **`whoami`** *confirmó que estás logueado como **bandit33**.*
- **`cat README.txt`** *mostró el mensaje de felicitación que indica que has terminado el juego **Bandit**.*
