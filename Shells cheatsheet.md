.
[[Tabla comparativa entre distintos shell]] 

Aquí tienes un **cheat sheet** que compara algunos comandos comunes entre **Bash**, **Bourne Shell (sh)**, **KornShell (ksh)** y **Bourne Again Shell (bsh)**. Los cuatro son **intérpretes de comandos** usados principalmente en sistemas Unix y Linux, y aunque tienen muchas similitudes, existen algunas diferencias en cuanto a sintaxis y características.

### **1. Navegación del sistema de archivos**
| Acción                     | Bash          | sh (Bourne Shell) | ksh (KornShell) |
| -------------------------- | ------------- | ----------------- | --------------- |
| Cambiar directorio         | `cd`          | `cd`              | `cd`            |
| Listar archivos            | `ls`          | `ls`              | `ls`            |
| Imprimir directorio actual | `pwd`         | `pwd`             | `pwd`           |
| Crear un directorio        | `mkdir <dir>` | `mkdir <dir>`     | `mkdir <dir>`   |

### **2. Gestión de archivos y directorios**
| Acción               | Bash                    | sh (Bourne Shell)       | ksh (KornShell)         |
| -------------------- | ----------------------- | ----------------------- | ----------------------- |
| Copiar archivos      | `cp <origen> <destino>` | `cp <origen> <destino>` | `cp <origen> <destino>` |
| Mover archivos       | `mv <origen> <destino>` | `mv <origen> <destino>` | `mv <origen> <destino>` |
| Eliminar archivos    | `rm <archivo>`          | `rm <archivo>`          | `rm <archivo>`          |
| Eliminar directorios | `rm -r <dir>`           | `rm -r <dir>`           | `rm -r <dir>`           |

### **3. Redirección de entrada/salida**
| Acción                    | Bash                     | sh (Bourne Shell)        | ksh (KornShell)          |
| ------------------------- | ------------------------ | ------------------------ | ------------------------ |
| Redirigir salida          | `command > archivo`      | `command > archivo`      | `command > archivo`      |
| Redirigir entrada         | `command < archivo`      | `command < archivo`      | `command < archivo`      |
| Redirigir y añadir salida | `command >> archivo`     | `command >> archivo`     | `command >> archivo`     |
| Canalización (pipe)       | `command1` \| `command2` | `command1` \| `command2` | `command1` \| `command2` |

### **4. Gestión de procesos**
| Acción                    | Bash         | sh (Bourne Shell) | ksh (KornShell) |
| ------------------------- | ------------ | ----------------- | --------------- |
| Listar procesos           | `ps`         | `ps`              | `ps`            |
| Matar un proceso          | `kill <PID>` | `kill <PID>`      | `kill <PID>`    |
| Ejecutar en segundo plano | `command &`  | `command &`       | `command &`     |
| Traer proceso al frente   | `fg <job>`   | `fg <job>`        | `fg <job>`      |

### **5. Variables y alias**
| Acción           | Bash                     | sh (Bourne Shell) | ksh (KornShell)          |
| ---------------- | ------------------------ | ----------------- | ------------------------ |
| Definir variable | `VAR=value`              | `VAR=value`       | `VAR=value`              |
| Mostrar variable | `echo $VAR`              | `echo $VAR`       | `echo $VAR`              |
| Definir alias    | `alias nombre='comando'` | No soportado      | `alias nombre='comando'` |

### **6. Estructuras de control**
| Acción           | Bash                      | sh (Bourne Shell)         | ksh (KornShell)           |
| ---------------- | ------------------------- | ------------------------- | ------------------------- |
| Condicional `if` | `if [ condición ]; then`  | `if [ condición ]; then`  | `if [ condición ]; then`  |
| Bucle `for`      | `for var in lista; do`    | `for var in lista; do`    | `for var in lista; do`    |
| Bucle `while`    | `while [ condición ]; do` | `while [ condición ]; do` | `while [ condición ]; do` |
| Casos `case`     | `case $var in`            | `case $var in`            | `case $var in`            |

### **7. Información del sistema**
| Acción                 | Bash       | sh (Bourne Shell) | ksh (KornShell) |
| ---------------------- | ---------- | ----------------- | --------------- |
| Mostrar uso de disco   | `df -h`    | `df -h`           | `df -h`         |
| Mostrar memoria libre  | `free -h`  | No soportado      | `free -h`       |
| Información del kernel | `uname -r` | `uname -r`        | `uname -r`      |

### **8. Gestión de scripts**
| Acción              | Bash          | sh (Bourne Shell) | ksh (KornShell) |
| ------------------- | ------------- | ----------------- | --------------- |
| Ejecutar script     | `./script.sh` | `./script.sh`     | `./script.sh`   |
| Declarar intérprete | `#!/bin/bash` | `#!/bin/sh`       | `#!/bin/ksh`    |

### **9. Diferencias principales**

- **Bash**: Es el shell más común en Linux y ofrece numerosas mejoras y características avanzadas, como historial de comandos y autocompletado.
- **sh (Bourne Shell)**: Es el shell original de Unix. Es más limitado y carece de algunas características modernas.
- **ksh (KornShell)**: Incluye muchas características avanzadas como programación orientada a objetos y más control de flujo.

### Conclusión:
- **Bash** y **Ksh** son más avanzados y ricos en características que **sh** y **bsh**, y son preferidos para la mayoría de tareas en sistemas modernos.
- **sh** es más limitado, pero útil si necesitas compatibilidad máxima con sistemas Unix más antiguos.

---
- [[ssh]]
- https://unix.stackexchange.com/questions/16357/usage-of-dash-in-place-of-a-filename
- https://www.computerworld.com/article/1482272/unix-tip-filename-completion.html
- https://usuariodebian.blogspot.com/2023/12/editor-nano-personalizado.html
- https://rimuhosting.com/knowledgebase/linux/misc/trapping-ctrl-c-in-bash
- https://linuxcommand.org/lc3_adv_tput.php
- https://www.gnu.org/software/termutils/manual/termutils-2.0/html_chapter/tput_1.html
- https://kodekloud.com/blog/bash-getopts/