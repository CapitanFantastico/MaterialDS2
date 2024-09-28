.
Aquí tienes un **cheatsheet de comandos básicos de Ubuntu**, que incluye los comandos más comunes para la gestión del sistema, archivos, usuarios, procesos, y redes en Ubuntu:

### **1. Comandos de Navegación y Gestión de Archivos**

| Comando               | Descripción                                               |
|-----------------------|-----------------------------------------------------------|
| `ls`                  | Lista los archivos y directorios en el directorio actual. |
| `cd <directorio>`     | Cambia al directorio especificado.                        |
| `pwd`                 | Muestra el directorio de trabajo actual.                  |
| `mkdir <nombre>`      | Crea un nuevo directorio.                                 |
| `rmdir <nombre>`      | Elimina un directorio vacío.                              |
| `rm <archivo>`        | Elimina un archivo.                                       |
| `rm -r <directorio>`  | Elimina un directorio y su contenido de forma recursiva.  |
| `cp <origen> <destino>`| Copia archivos o directorios.                           |
| `mv <origen> <destino>`| Mueve o renombra archivos o directorios.                |
| `touch <archivo>`     | Crea un archivo vacío o actualiza su fecha de modificación.|
| `cat <archivo>`       | Muestra el contenido de un archivo.                       |
| `nano <archivo>`      | Abre un archivo en el editor de texto Nano.               |
| `less <archivo>`      | Visualiza un archivo por páginas.                         |
| `find <ruta> -name <patrón>` | Busca archivos o directorios por nombre.          |

### **2. Comandos de Permisos y Propiedad**

| Comando                | Descripción                                                   |
|------------------------|---------------------------------------------------------------|
| `chmod <permisos> <archivo>` | Cambia los permisos de un archivo o directorio.       |
| `chown <usuario>:<grupo> <archivo>` | Cambia el propietario de un archivo o directorio.|
| `sudo`                 | Ejecuta un comando como superusuario.                         |

### **3. Gestión de Procesos**

| Comando                 | Descripción                                                 |
|-------------------------|-------------------------------------------------------------|
| `ps aux`                | Lista todos los procesos en ejecución.                      |
| `top`                   | Muestra los procesos en ejecución en tiempo real.           |
| `htop`                  | Muestra una interfaz mejorada de `top` (requiere instalación).|
| `kill <PID>`            | Termina un proceso por su ID de proceso (PID).              |
| `killall <nombre>`      | Termina todos los procesos con un nombre específico.        |
| `bg`                    | Envía un proceso suspendido al fondo (background).          |
| `fg`                    | Trae un proceso en el fondo al primer plano (foreground).   |

### **4. Comandos de Gestión de Usuarios y Grupos**

| Comando                | Descripción                                                     |
|------------------------|-----------------------------------------------------------------|
| `adduser <usuario>`    | Crea un nuevo usuario.                                          |
| `deluser <usuario>`    | Elimina un usuario.                                             |
| `passwd <usuario>`     | Cambia la contraseña de un usuario.                             |
| `groups <usuario>`     | Muestra los grupos a los que pertenece un usuario.              |
| `usermod -aG <grupo> <usuario>` | Añade un usuario a un grupo.                          |

### **5. Gestión de Paquetes y Actualización del Sistema**

| Comando                           | Descripción                                                     |
|-----------------------------------|-----------------------------------------------------------------|
| `sudo apt update`                 | Actualiza la lista de paquetes disponibles.                     |
| `sudo apt upgrade`                | Actualiza todos los paquetes instalados a sus versiones más recientes.|
| `sudo apt install <paquete>`      | Instala un paquete.                                             |
| `sudo apt remove <paquete>`       | Elimina un paquete.                                             |
| `sudo apt autoremove`             | Elimina paquetes no necesarios y dependencias obsoletas.        |

### **6. Comandos de Red**

| Comando                   | Descripción                                                         |
|---------------------------|---------------------------------------------------------------------|
| `ifconfig`                | Muestra la configuración de red (requiere instalación de `net-tools`).|
| `ip addr`                 | Muestra y configura la dirección IP de las interfaces de red.       |
| `ping <host>`             | Envía paquetes ICMP a un host para verificar la conectividad.       |
| `traceroute <host>`       | Muestra la ruta tomada por los paquetes hacia un destino.           |
| `curl <URL>`              | Transfiere datos desde o hacia un servidor.                         |
| `wget <URL>`              | Descarga archivos desde la web.                                     |

### **7. Comandos de Compresión y Archivos**

| Comando                            | Descripción                                                     |
|------------------------------------|-----------------------------------------------------------------|
| `tar -czvf <archivo.tar.gz> <ruta>`| Comprime archivos/directorios en formato tar.gz.               |
| `tar -xzvf <archivo.tar.gz>`       | Descomprime archivos tar.gz.                                    |
| `zip <archivo.zip> <archivo>`      | Comprime archivos en formato ZIP.                              |
| `unzip <archivo.zip>`              | Descomprime archivos ZIP.                                       |

### **8. Información del Sistema**

| Comando                 | Descripción                                                        |
|-------------------------|--------------------------------------------------------------------|
| `uname -a`              | Muestra información del sistema operativo y kernel.                |
| `df -h`                 | Muestra el espacio en disco disponible en el sistema.              |
| `free -h`               | Muestra la memoria RAM libre y usada.                              |
| `lscpu`                 | Muestra información sobre la CPU.                                  |
| `lsblk`                 | Lista todos los dispositivos de bloques (discos, particiones).     |

### **9. Comandos de Seguridad y Administración del Sistema**

| Comando                   | Descripción                                                        |
|---------------------------|--------------------------------------------------------------------|
| `sudo ufw status`         | Muestra el estado del firewall UFW (Uncomplicated Firewall).      |
| `sudo ufw enable`         | Activa el firewall UFW.                                           |
| `sudo ufw disable`        | Desactiva el firewall UFW.                                        |
| `sudo ufw allow <puerto>` | Permite tráfico en un puerto específico.                          |
| `sudo shutdown now`       | Apaga el sistema inmediatamente.                                   |
| `sudo reboot`             | Reinicia el sistema.                                               |

