<!-- Autor: Daniel Benjamin Perez Morales -->
<!-- GitHub: https://github.com/DanielBenjaminPerezMoralesDev13 -->
<!-- Gitlab: https://gitlab.com/DanielBenjaminPerezMoralesDev13 -->
<!-- Correo electrónico: danielperezdev@proton.me -->

# ***Bandido Nivel 4 → Nivel 5***

- **Meta de nivel**
- *La contraseña para el siguiente nivel se almacena en el único fichero legible por humanos en el directorio inhere. Consejo: si tu terminal está estropeada, prueba el comando «reset».*
- **Comandos que puede necesitar para resolver este nivel**
- *ls, cd, cat, file, du, find*

## ***1. Comando `whoami`***

```bash
whoami
```

- **Descripción:** *Este comando muestra el usuario actualmente autenticado en el sistema.*
- **Salida:**

  ```bash
  root
  ```

  **Análisis de la salida:**
  - **`root`:** *Indica que el usuario activo en la terminal es `root`, el superusuario del sistema.*

---

### ***2. Comando `touch file.txt`***

```bash
touch file.txt
```

- **Descripción:** *Crea un fichero vacío llamado `file.txt` en el directorio actual si no existe.*
- **Salida:** *Sin salida.*
- **Efecto en el sistema:**
  - *Se genera un fichero vacío `file.txt` en `/tmp`.*

---

### ***3. Comando `echo "My name is Daniel" >> file.txt`***

```bash
echo "My name is Daniel" >> file.txt
```

- **Descripción:** *Añade el texto "My name is Daniel" al fichero `file.txt`.*
- **Salida:** *Sin salida.*
- **Efecto en el sistema:**
  - *El fichero `file.txt` ahora contiene el texto `My name is Daniel`.*

---

### ***4. Comando `chmod o-r file.txt`***

```bash
chmod o-r file.txt
```

- **Descripción:** *Revoca el permiso de lectura para "otros" usuarios en el fichero `file.txt`.*
- **Salida:** *Sin salida.*
- **Efecto en el sistema:**
  - *El fichero `file.txt` ahora tiene permisos `rw-r-----`, limitando la lectura solo al propietario y grupo.*

---

### ***5. Comando `su d4nitrix13` y `cat file.txt`***

```bash
su d4nitrix13
cat file.txt
```

- **Descripción:** *Cambia al usuario `d4nitrix13` e intenta leer el fichero `file.txt`.*
- **Salida:**

  ```bash
  cat: file.txt: Permiso denegado
  ```

  **Análisis de la salida:**
  - **`Permiso denegado`:** *Indica que el usuario `d4nitrix13` no tiene permiso de lectura en `file.txt`.*

---

### ***6. Comando `chmod o+rw file.txt`***

```bash
chmod o+rw file.txt
```

- **Descripción:** *Otorga permisos de lectura y escritura para "otros" usuarios en el fichero `file.txt`.*
- **Salida:** *Sin salida.*
- **Efecto en el sistema:**
  - *El fichero `file.txt` ahora tiene permisos `rw-r--rw-`, permitiendo a cualquier usuario leer y escribir en él.*

---

### ***7. Comando `chgrp d4nitrix13 file.txt`***

```bash
chgrp d4nitrix13 file.txt
```

- **Descripción:** *Cambia el grupo propietario de `file.txt` al grupo `d4nitrix13`.*
- **Salida:** *Sin salida.*
- **Efecto en el sistema:**
  - *El grupo propietario de `file.txt` ahora es `d4nitrix13`.*

---

### ***8. Comando `chattr +i -V file.txt`***

```bash
chattr +i -V file.txt
```

- **Descripción:** *Configura el fichero `file.txt` como inmutable, lo que significa que no puede ser*modificado, eliminado ni renombrado.
- **Salida:**

  ```bash
  Las banderas de file.txt están puestas como ----i---------e-------
  ```

  **Análisis de la salida:**
  - **`i`:** *La bandera de inmutabilidad está activa.
  - **`e`:** *El fichero utiliza un sistema de extensión.

---

### ***9. Comando `rm file.txt`***

```bash
rm file.txt
```

- **Descripción:** *Intenta eliminar el fichero `file.txt`.*
- **Salida:**

  ```bash
  rm: no se puede borrar 'file.txt': Operación no permitida
  ```

  **Análisis de la salida:**
  - **`Operación no permitida`:** *El fichero está protegido por la bandera `i`.

---

### ***10. Comando `chattr -i -V file.txt`***

```bash
chattr -i -V file.txt
```

- **Descripción:** *Elimina la inmutabilidad del fichero `file.txt`.*
- **Salida:**

  ```bash
  Las banderas de file.txt están puestas como --------------e-------
  ```

  **Análisis de la salida:**
  - **`i` eliminada:** *El fichero ya no es inmutable.*

---

### ***11. Comando `find` para buscar y filtrar ficheros***

```bash
find ./inhere/ -type f -name *file* | xargs file | grep -iF "text"
```

- **Descripción:** *Busca ficheros cuyo nombre contenga `file` en el directorio `inhere` y filtra aquellos*que son de tipo texto ASCII.
- **Salida:**

  ```bash
  ./inhere/-file07: ASCII text
  ```

  **Análisis de la salida:**
  - **`-file07`:** *Fichero identificado como texto ASCII.*
  - **`ASCII text`:** *Especifica el tipo del contenido.*

---

### ***Resumen***

1. **`whoami`:** *Muestra el usuario actual.*
2. **`touch`:** *Crea un fichero vacío.*
3. **`chmod`:** *Gestiona permisos de usuarios y grupos.*
4. **`chattr`:** *Configura atributos especiales como inmutabilidad.*
5. **`find`:** *Busca ficheros con filtros avanzados.*

## ***1. Comando: Buscar y filtrar ficheros por contenido***

```bash
find ./inhere/ -type f -name *file* | xargs file | grep -iF "text" | awk '{print $1}' | tr -d ':' | xargs cat
```

- **Descripción:**  
  *Este comando busca ficheros en el directorio `./inhere/` cuyo nombre contiene `file`. Luego:*  
  1. *Identifica los ficheros mediante el comando `file`.*  
  2. *Filtra aquellos cuyo contenido sea de texto (`ASCII text`) usando `grep`.*  
  3. *Extrae solo el nombre del fichero con `awk`.*  
  4. *Limpia los caracteres `:` con `tr`.*  
  5. *Finalmente, muestra el contenido del fichero con `cat`.*  

- **Salida:**

  ```bash
  4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
  ```

  **Análisis de la salida:**  
  - **`4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`:** *Este es el contenido del fichero de texto identificado, probablemente el fichero `./inhere/-file07`.*  

---

## ***2. Comando: Identificar el fichero sin leer su contenido***

```bash
find ./inhere/ -type f -name *file* | xargs file | grep -iF "text" | awk '{print $1}' | tr -d ':'
```

- **Descripción:**  
  *Similar al anterior, pero aquí solo muestra el nombre del fichero que contiene texto (`ASCII text`).*

- **Salida:**

  ```bash
  ./inhere/-file07
  ```

  **Análisis de la salida:**  
  - **`./inhere/-file07`:** *Nombre del fichero que contiene texto ASCII.*  

---

## ***3. Comando: Identificar fichero mostrando formato original***

```bash
find ./inhere/ -type f -name *file* | xargs file | grep -iF "text" | awk '{print $1}'
```

- **Descripción:**  
  *Similar al comando anterior, pero conserva los dos puntos (`:`) al final del nombre del fichero.*

- **Salida:**

  ```bash
  ./inhere/-file07:
  ```

  **Análisis de la salida:**  
  - **`./inhere/-file07:`** *Fichero encontrado, incluyendo el separador `:`.*  

---

## ***4. Comando: Ver detalles del tipo de fichero***

```bash
find ./inhere/ -type f -name *file* | xargs file | grep -iF "text" --color=always
```

- **Descripción:**  
  *Busca ficheros cuyo contenido sea texto (`ASCII text`) y resalta el resultado con colores para una mejor visualización.*

- **Salida:**

  ```bash
  ./inhere/-file07: ASCII text
  ```

  **Análisis de la salida:**  
  - **`ASCII text`:** *Identifica que el fichero contiene texto en formato ASCII.*  
  - **`--color=always`:** *Añade color a las coincidencias encontradas.*  

---

## ***5. Comando: Mostrar todos los ficheros y sus tipos***

```bash
find ./inhere/ -type f -name *file* | xargs file
```

- **Descripción:**  
  *Lista todos los ficheros que contienen `file` en su nombre y muestra el tipo de cada fichero.*

- **Salida:**

  ```bash
  ./inhere/-file08: data
  ./inhere/-file02: data
  ./inhere/-file09: data
  ./inhere/-file01: data
  ./inhere/-file00: data
  ./inhere/-file05: data
  ./inhere/-file07: ASCII text
  ./inhere/-file03: data
  ./inhere/-file06: data
  ./inhere/-file04: data
  ```

  **Análisis de la salida:**  
  - **`ASCII text`:** *Solo el fichero `-file07` contiene texto.*  
  - **`data`:** *Los demás ficheros no contienen texto legible.*  

---

## ***6. Comando: Mostrar únicamente nombres de ficheros***

```bash
find ./inhere/ -type f -name *file*
```

- **Descripción:**  
  *Busca y lista todos los ficheros cuyo nombre contiene `file` en el directorio `./inhere/`.*

- **Salida:**

  ```bash
  ./inhere/-file08
  ./inhere/-file02
  ./inhere/-file09
  ./inhere/-file01
  ./inhere/-file00
  ./inhere/-file05
  ./inhere/-file07
  ./inhere/-file03
  ./inhere/-file06
  ./inhere/-file04
  ```

  **Análisis de la salida:**  
  - **Lista completa de ficheros:** *Identifica todos los ficheros en `inhere` que coinciden con el patrón `*file*`.*  

1. **`find` con filtros:** *Busca ficheros por nombre o tipo.*  
2. **`file`:** *Identifica el contenido de cada fichero.*  
3. **`grep`:** *Filtra resultados con coincidencias específicas.*  
4. **`awk` y `tr`:** *Procesan y limpian los resultados.*  
5. **`xargs`:** *Permite ejecutar comandos como `cat` para múltiples resultados.*  
