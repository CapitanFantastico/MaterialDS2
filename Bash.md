.
**Bash** (Bourne Again Shell) es un **intérprete de comandos** y lenguaje de scripting utilizado principalmente en sistemas operativos basados en [[Unix]], como **[[Linux]]** y **[[macOS]]**. Es una evolución del shell original **Bourne Shell ([[sh]])**, con muchas mejoras y funcionalidades adicionales.

### Características de Bash:

1. **Intérprete de comandos**: Bash permite a los usuarios ejecutar comandos en la terminal para interactuar con el sistema operativo, como navegar por directorios, copiar archivos, y ejecutar programas.
   
2. **Lenguaje de scripting**: Además de ejecutar comandos de forma interactiva, Bash también se usa para escribir **scripts**, que son archivos que contienen secuencias de comandos que pueden automatizar tareas repetitivas.

3. **Variables**: Bash permite la creación de variables para almacenar datos y utilizarlos en comandos o scripts.

4. **Redirección de entrada/salida**: Bash soporta redireccionar la salida de un comando hacia un archivo o hacia otro comando, así como redirigir la entrada de un archivo.

5. **Pipelines**: Permite encadenar múltiples comandos usando el símbolo `|`, de manera que la salida de un comando se convierte en la entrada de otro.

6. **Control de flujo**: Como lenguaje de scripting, Bash permite estructuras de control de flujo, como bucles (`for`, `while`) y condicionales (`if`, `else`), para realizar operaciones más complejas.

### Ejemplos de comandos comunes en Bash:

- **`ls`**: Lista archivos y directorios.
- **`cd`**: Cambia el directorio de trabajo.
- **`mkdir`**: Crea un directorio.
- **`cp`**: Copia archivos o directorios.
- **`mv`**: Mueve o renombra archivos o directorios.
- **`rm`**: Elimina archivos o directorios.

### Ejemplo de un script en Bash:
```bash
#!/bin/bash

# Este es un script simple en Bash
echo "Hola, bienvenido al mundo de Bash!"

# Definir una variable
nombre="Carlos"
echo "Hola, $nombre"

# Bucle for
for i in 1 2 3; do
  echo "Número $i"
done
```

Este script imprime un saludo, luego utiliza una variable y un bucle para mostrar una secuencia de números.

### ¿Por qué es útil Bash?

- **Automatización**: Puedes crear scripts que realicen tareas repetitivas o complejas automáticamente.
- **Flexibilidad**: Bash puede combinarse con otros comandos y utilidades del sistema para manipular archivos, administrar procesos, o interactuar con redes.
- **Popularidad**: Es uno de los intérpretes de comandos más usados en sistemas Linux y macOS, por lo que aprender Bash es esencial para trabajar eficientemente en estos entornos.


---

Ver
- [[Shells cheatsheet]] <
- https://www.freecodecamp.org/espanol/news/tutorial-de-programacion-de-bash-script-de-shell-de-linux-y-linea-de-comandos-para-principiantes/
- https://youtu.be/H4ayPYcZEfI 
- https://en.wikibooks.org/wiki/Bash_Shell_Scripting
- [[Difference Between .bashrc, .bash-profile, and .profile]] 

