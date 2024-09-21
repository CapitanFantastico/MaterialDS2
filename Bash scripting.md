.
### Guía de Bash Scripting

- Ver [[Bash]] 

#### **1. Introducción a Bash Scripting**

- **¿Qué es Bash?**
  Bash (Bourne Again Shell) es un intérprete de comandos y lenguaje de scripting ampliamente utilizado en sistemas operativos tipo Unix, como Linux y macOS. Permite a los usuarios automatizar tareas repetitivas y escribir scripts para realizar operaciones complejas.

- **¿Qué es un Script?**
  Un script en Bash es un archivo de texto que contiene una serie de comandos que se ejecutan en secuencia. Estos comandos pueden incluir la manipulación de archivos, la ejecución de programas, y el procesamiento de texto.

#### **2. Configuración Inicial**

- **Crear un Archivo de Script:**
  Para crear un script en Bash, usa un editor de texto como `nano` o `vim`. Guarda el archivo con una extensión `.sh` (por ejemplo, `mi_script.sh`).

- Ver [[Comparación entre los principales editores de texto para entornos unix]] 

- **Hacer un Script Ejecutable:**
  Una vez creado, debes hacer el script ejecutable usando el siguiente comando:
  ```bash
  chmod +x mi_script.sh
  ```
  Para ejecutarlo, usa:
  ```bash
  ./mi_script.sh
  ```

#### **3. Estructura Básica de un Script**

- **Shebang:**
  La primera línea de un script Bash debe ser:
  ```bash
  #!/bin/bash
  ```
  Esto indica al sistema que debe usar el intérprete de Bash para ejecutar el script.

- **Comentarios:**
  Puedes añadir comentarios en un script para explicar lo que hace cada parte:
  ```bash
  # Esto es un comentario
  echo "Hola, mundo"
  ```

- **Comandos Básicos:**
  Bash incluye comandos básicos como `echo`, `ls`, `cd`, `cp`, `mv`, y `rm` para interactuar con el sistema de archivos y realizar tareas básicas.

#### **4. Variables y Tipos de Datos**

- **Declaración de Variables:**
  Las variables se declaran sin la palabra clave `var` o `let`:
  ```bash
  nombre="Juan"
  ```
  Para acceder al valor de una variable, usa el símbolo `$`:
  ```bash
  echo $nombre
  ```

- **Tipos de Datos:**
  Bash solo maneja cadenas de texto y números, no hay tipos de datos estrictos como en otros lenguajes. 

#### **5. Estructuras de Control**

- **Condicionales (if-else):**
  ```bash
  if [ $nombre == "Juan" ]; then
      echo "Hola, Juan"
  else
      echo "Hola, desconocido"
  fi
  ```

- **Bucles:**

  - **For loop:**
    ```bash
    for i in 1 2 3 4 5; do
        echo "Número $i"
    done
    ```
  
  - **While loop:**
    ```bash
    count=1
    while [ $count -le 5 ]; do
        echo "Este es el intento número $count"
        ((count++))
    done
    ```

#### **6. Funciones en Bash**

- **Definición de Funciones:**
  ```bash
  funcion_hola() {
      echo "Hola, $1"
  }
  ```
  Llama a la función con:
  ```bash
  funcion_hola "Juan"
  ```

#### **7. Gestión de Archivos y Directorios**

- **Crear Directorios y Archivos:**
  ```bash
  mkdir mi_directorio
  touch mi_archivo.txt
  ```

- **Mover y Copiar Archivos:**
  ```bash
  mv mi_archivo.txt mi_directorio/
  cp mi_archivo.txt copia_archivo.txt
  ```

- **Eliminar Archivos y Directorios:**
  ```bash
  rm mi_archivo.txt
  rmdir mi_directorio
  ```

#### **8. Entrada y Salida Estándar**

- **Redirección de Salida:**

  Para redirigir la salida de un comando a un archivo:
  ```bash
  echo "Hola, archivo" > archivo.txt
  ```
  Para agregar contenido a un archivo existente:
  ```bash
  echo "Más texto" >> archivo.txt
  ```

- **Redirección de Entrada:**

  Para leer la entrada de un archivo:
  ```bash
  while read linea; do
      echo $linea
  done < archivo.txt
  ```

#### **9. Ejemplos de Scripts Útiles**

- **Script para realizar un respaldo de archivos:**
  ```bash
  #!/bin/bash
  tar -czvf backup.tar.gz /ruta/al/directorio
  echo "Respaldo completado."
  ```

- **Script para monitorear el uso de espacio en disco:**
  ```bash
  #!/bin/bash
  df -h > uso_disco.txt
  echo "Reporte de uso de disco guardado en uso_disco.txt"
  ```

#### **10. Buenas Prácticas**

- **Uso de Comentarios:** Comenta tu código para que sea más fácil de entender y mantener.
- **Validación de Entradas:** Verifica que las entradas sean válidas antes de procesarlas.
- **Pruebas:** Prueba tus scripts en entornos controlados antes de ejecutarlos en producción.
- **Modularidad:** Divide tu script en funciones para mejorar la legibilidad y reutilización del código.

### **Recursos Adicionales**

- **Documentación de Bash:** [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html)
- **Tutorial de Bash Scripting:** [Shell Scripting Tutorial](https://www.shellscript.sh/)

Esta guía proporciona una base sólida para comenzar a escribir scripts en Bash. Practicar y experimentar con ejemplos reales es clave para dominar Bash scripting.

---

Ver
 - [[Overthewire]] <
 - https://overthewire.org/wargames/bandit/ 
 - [[getopts]] <
- https://www.youtube.com/watch?v=Z7S6Mvl9hHA&list=PLf8XMtbjh0dX0Go7CNxaoCOufOB446NNA Bash scripting
- https://www.gnu.org/software/bash/manual/html_node/Shell-Builtin-Commands.html
