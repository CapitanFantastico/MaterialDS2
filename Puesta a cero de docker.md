.
- Ver [[Configuración IP ubuntu]] 

Para desinstalar Docker en tu sistema Ubuntu y volver a instalarlo sin perder las imágenes que ya has descargado, puedes seguir los pasos detallados a continuación:

### **Paso 1: Detener los Contenedores Actuales**

Antes de desinstalar Docker, detén todos los contenedores que estén en ejecución:

```bash
docker stop $(docker ps -q)
```

Esto detiene todos los contenedores en ejecución.

### **Paso 2: Desinstalar Docker Manteniendo las Imágenes**

1. **Eliminar Docker pero conservar los datos**: Desinstala Docker sin eliminar los directorios de configuración y las imágenes. Usa el siguiente comando para desinstalar los paquetes de Docker:

   ```bash
   sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```

   Este comando elimina los binarios y dependencias, pero no toca los volúmenes o las imágenes que están almacenados en tu sistema.

2. **Verificar que los datos están intactos**: Docker almacena imágenes, contenedores y volúmenes en `/var/lib/docker`. Este directorio no se eliminará con los comandos de desinstalación anteriores, por lo que tus imágenes permanecerán en tu sistema.

   Puedes verificar su existencia con:

   ```bash
   ls /var/lib/docker
   ```

### **Paso 3: Reinstalar Docker**

1. **Actualizar los paquetes del sistema**:

   ```bash
   sudo apt-get update
   ```

2. **Instalar los paquetes necesarios para usar Docker desde el repositorio oficial**:

   ```bash
   sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
   ```

3. **Añadir la clave GPG oficial de Docker**:

   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   ```

4. **Añadir el repositorio oficial de Docker**:

   ```bash
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

5. **Instalar Docker**:

   ```bash
   sudo apt-get update
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```

6. **Verificar que Docker esté instalado correctamente**:

   ```bash
   sudo docker --version
   ```



### **Paso 4: Verificar que las Imágenes y Contenedores Persisten**

Después de reinstalar Docker, las imágenes y los contenedores previos deben seguir estando disponibles. Verifica esto ejecutando:

```bash
docker images
```

Esto debería mostrar todas las imágenes que ya habías descargado antes de desinstalar Docker.

### **Paso 5: (Opcional) Mover las Imágenes o Directorio Docker a Otro Lugar**

Si tienes limitaciones de espacio o prefieres tener un respaldo adicional de las imágenes, puedes mover el directorio `/var/lib/docker` a otro lugar temporalmente, desinstalar Docker y luego restaurarlo antes de reinstalar Docker.

Para mover las imágenes a otro lugar, puedes hacer lo siguiente:

1. Mover las imágenes y volúmenes a una ubicación temporal:
   ```bash
   sudo mv /var/lib/docker /path/to/backup/docker
   ```

2. Luego de reinstalar Docker, puedes restaurar el directorio:
   ```bash
   sudo mv /path/to/backup/docker /var/lib/docker
   ```

De esta manera, reinstalarás Docker sin perder tus imágenes.


---

Para instalar Docker Compose en Ubuntu, sigue estos pasos:

### **Paso 1: Actualizar los Paquetes Existentes**

Primero, actualiza el índice de paquetes del sistema:

```bash
sudo apt update
```

### **Paso 2: Instalar Docker (si no lo tienes ya)**

Si Docker no está instalado en tu sistema, instálalo con los siguientes comandos:

1. **Instalar los paquetes necesarios**:

   ```bash
   sudo apt install apt-transport-https ca-certificates curl software-properties-common
   ```

2. **Agregar la clave GPG del repositorio de Docker**:

   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   ```

3. **Agregar el repositorio oficial de Docker**:

   ```bash
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

4. **Instalar Docker**:

   ```bash
   sudo apt update
   sudo apt install docker-ce docker-ce-cli containerd.io
   ```

5. **Verificar la instalación de Docker**:

   ```bash
   sudo docker --version
   ```

   Esto debería mostrar la versión instalada de Docker.

### **Paso 3: Descargar e Instalar Docker Compose**

1. **Descargar la última versión de Docker Compose**:

   Verifica la última versión disponible en la [página de versiones de Docker Compose](https://github.com/docker/compose/releases), o puedes usar este comando para descargar directamente la última versión estable (en este caso, reemplaza la versión por la más reciente disponible, aquí utilizamos la `v2.22.0` como ejemplo):

   ```bash
   sudo curl -L "https://github.com/docker/compose/releases/download/v2.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
   ```

2. **Aplicar permisos de ejecución**:

   Haz que el binario sea ejecutable:

   ```bash
   sudo chmod +x /usr/local/bin/docker-compose
   ```

3. **Verificar la instalación de Docker Compose**:

   Ejecuta el siguiente comando para verificar que Docker Compose se haya instalado correctamente:

   ```bash
   docker-compose --version
   ```

   Esto debería mostrar algo como:

   ```
   docker-compose version 2.22.0, build e7cf4db2
   ```

### **Paso 4: Configuración Opcional**

Si quieres que Docker Compose sea accesible para todos los usuarios sin necesidad de permisos `sudo`, puedes crear un enlace simbólico en `/usr/bin`:

```bash
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

### **Paso 5: Uso Básico de Docker Compose**

Ahora ya puedes crear archivos `docker-compose.yml` y ejecutar servicios con el comando:

```bash
docker-compose up
```

### **Paso 6: Actualización de Docker Compose (Opcional)**

Si en el futuro necesitas actualizar Docker Compose, simplemente repite el proceso de descarga con la nueva versión disponible y sobrescribe el binario existente:

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/vX.XX.X/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

### **Paso 7: Desinstalar Docker Compose**

Para desinstalar Docker Compose, simplemente elimina el binario:

```bash
sudo rm /usr/local/bin/docker-compose
```

