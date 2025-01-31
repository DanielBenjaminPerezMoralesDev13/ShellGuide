<!-- Autor: Daniel Benjamin Perez Morales -->
<!-- GitHub: https://github.com/DanielBenjaminPerezMoralesDev13 -->
<!-- Gitlab: https://gitlab.com/DanielBenjaminPerezMoralesDev13 -->
<!-- Correo electrónico: danielperezdev@proton.me -->

# ***Bandido Nivel 2 → Nivel 3***

- **Meta de nivel**
- *La contraseña para el siguiente nivel se almacena en un fichero llamado espacios en este nombre de fichero ubicado en el directorio home*
- *Comandos que puedes necesitar para resolver este nivel*
- *ls, cd, cat, file, du, find*

- **Material de lectura útil**
*[spaces in filename](https://stackoverflow.com/questions/23019471/how-can-i-go-to-a-directory-whose-file-name-has-spaces-between-them-in-the-linux "https://stackoverflow.com/questions/23019471/how-can-i-go-to-a-directory-whose-file-name-has-spaces-between-them-in-the-linux")*

## ***1. Comando `ls -l`***

```bash
bandit2@bandit:~$ ls -l
```

- **`ls -l`:** *Lista el contenido del directorio actual en un formato largo, mostrando detalles de cada fichero como permisos, propietario, grupo, tamaño, y fecha de modificación.*
  
  **Salida:**

  ```bash
  total 4
  -rw-r----- 1 bandit3 bandit2 33 Sep 19 07:08 spaces in this filename
  ```

  **Análisis de la salida:**
  - `-rw-r-----`: Los permisos del fichero (solo lectura y escritura para el propietario, lectura para el grupo, y nada para otros usuarios).
  - `1`: Número de enlaces.
  - `bandit3`: Propietario del fichero.
  - `bandit2`: Grupo del fichero.
  - `33`: Tamaño del fichero en bytes.
  - `Sep 19 07:08`: Fecha y hora de modificación del fichero.
  - **`spaces in this filename`:** *El nombre del fichero. Contiene espacios, lo cual puede complicar su manipulación.*

---

### 2. **Comando para leer el fichero con caracteres especiales**

```bash
bandit2@bandit:~$ cat spaces\ in\ this\ filename
```

- **`cat`:** *Muestra el contenido de un fichero.*
- **`spaces\ in\ this\ filename`:**
  - *Los espacios en el nombre del fichero se **escapan** con una barra invertida (`\`) para que la terminal interprete el nombre completo como una sola unidad.*
  - *Sin los caracteres de escape, la terminal interpretaría los espacios como separadores de argumentos, causando un error.*

  **Salida:**

  ```bash
  MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
  ```

  - *Este es el contenido del fichero (probablemente la contraseña para el siguiente nivel).*

---

### ***3. Otra forma de manejar nombres con espacios***

```bash
bandit2@bandit:~$ cat "spaces in this filename"
```

- *Aquí, el nombre del fichero se pone entre **comillas dobles** (`"`) para manejar los espacios como parte del nombre.*
- *Las comillas dobles agrupan todo lo que contienen como un único argumento, por lo que no es necesario escapar los espacios.*

  **Salida:**

  ```bash
  MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
  ```

  - *Nuevamente, se muestra el contenido del fichero.*

---

### ***Resumen***

1. *Los nombres de ficheros con espacios necesitan un manejo especial en la terminal.*
2. *Dos soluciones comunes son:*
   - *Escapar los espacios con barras invertidas (`\`).*
   - *Encerrar el nombre completo entre comillas dobles (`"`) o simples (`'`).*
3. *En ambos casos, el comando funciona correctamente y muestra el contenido del fichero.*
