.
- Ver [[Configuración IP ubuntu]] 
- Ver [[Docker cheatsheet]]  
- Ver [[Docker-compose cheatsheet]] 
- Ver [[Ubuntu cheatsheet]] 
- Ver [[Puesta a cero de docker]] 
- Ver [[Configuración Xhost]] 

```
PowerShell C:\Users\Gustavo> ssh gosorio@192.168.x.y
> sudo su -
> set -o vi
> cd ~gosorio

# Comando para mostrar los contenedores que están corriendo

docker ps

# Para ver los contenedores que han corrido 

docker ps -a

# Validamos las imágenes descargadas

docker images 

# Ejecutamos el docker hello-world, si no encuentra la imagen correspondiente, la descarga del repositorio en línea

docker run hello-world 

# Validamos que aparezca la nueva imagen

docker images

# Validamos los contenedores que han corrido en el sistema

docker ps
docker ps -a

# Para descargar repositorios en línea, sin necesidad de ejecutarlo 

docker pull alpine

# Validamos que aparezca la nueva imagen

docker images

# Validamos los contenedores que han corrido en el sistema

docker ps
docker ps -a

# Corremos (y creamos) un contenedor con la imagen descargada

grep NAME /etc/os-release
docker run -it alpine sh
> grep NAME /etc/os-release
> exit

# Validamos los contenedores que han corrido en el sistema

docker ps
docker ps -a

# Borramos una imagen que no necesitamos : No debe haber un contenedor creado con esa imagen

docker rmi alpine

# Borramos el contenedor y luego borramos la imagen correspondiente

docker ps -a
docker rm <CONTAINER_ID>
docker ps -a
docker images
docker rmi alpine
docker images

# Alpine es una versión mínima de Linux
# Si no se especifica un tag o etiqueta, se descarga la versión latest (la más reciente), pero no es buena práctica, pues esta puede ir cambiando
# Si se quiere descargar una versión concreta, lo especifico con un tag.  En el siguiente caso, se descarga la versión 3.20 del contenedor alpine

docker pull alpine:3.20
docker images

# Ahora ejecutamos el docker que ya descargamos

docker ps -a
docker run alpine:3.20 
docker ps -a
docker run alpine:3.20 
docker ps -a

# El contenedor se ejecuta, y ejecuta también los comandos que le especifiquemos e inmediatamente sale y se apaga.  Adicionalmente va dejando registro de su ejecución

grep NAME /etc/os-release # Muestra la información local
docker run alpine:3.20 grep NAME /etc/os-release



# Para que no se salga, ejecutamos un proceso que nunca termine
# También podemos establecer una conexión interactiva usando un shell del contenedor y las opciones -it (terminal interactiva)

docker run -it alpine:3.20 sh
> date > /tmp/fecha.txt
> ls -l /tmp/fecha.txt

# Desde otra terminal (#2) yo puedo monitorear la conexión anterior

docker ps

# Para mostrar que los contenedores están aislados entre ellos (isolated), corremos (creamos) un nuevo contenedor con la imágen del contenedor que ya está corriendo y verificamos que no existe el archivo /tmp/fecha.txt creado en el paso anterior.  Esto se tiene que hacer desde otra terminal (#2)

docker run -it alpine:3.20 sh
> ls -l /tmp/fecha.txt
> exit

# Desde la misma terminal #2 vamos a identificar el CONTAINER_ID del contenedor que está en ejecución en la terminal #1 para ingresar a él

docker ps
docker exec -it <CONTAINER_ID> sh
ls -l /tmp/fecha.txt
cat /tmp/fecha.txt


# Imágenes
# Cada que se apaga un contenedor, se pierden todos los datos o archivos que hayamos creado, igualmente se pierden las actualizaciones o nuevo software instalado
# Para garantizar la persistencia, debemos guardar el estado último del contenedor en una imágen (antes de apagarlo)
# Volvamos a la terminal #1, salimos del contenedor alpine y ejecutamos (creamos) un contenedor ubuntu

docker run -it ubuntu /bin/bash
> grep NAME /etc/os-release
> apt-get update
> apt-get install figlet 
> figlet "Hola"
> exit

docker run -it ubuntu /bin/bash
> figlet "Hola"
> grep NAME /etc/os-release
> apt-get update
> apt-get install figlet 
> figlet "Hola"



# Sin detener el contenedor de ubuntu de la terminal #1, donde instalamos figlet, vamos a la terminal #2 y creamos una imagen con los cambios realizados en el contenedor

docker ps
docker image ls 
docker commit <CONTAINER_ID>
docker image ls 

# Asignemos el TAG midocker a la imágen que acabamos de crear

docker image tag <IMAGE_ID> midocker
docker image ls

# Observemos que automáticamente asigna el nombre midocker al nombre de REPOSITORY, y el TAG queda como latest
# Esto lo podemos cambiar si ejecutamos 

docker image tag <IMAGE_ID> midocker:1.0
docker image ls

# Subimos nuevamente un contenedor con la imagen midocker:1.0 y probamos figlet

docker run -it midocker:1.0 /bin/bash
> figlet "Hola"
> exit

# Lo anterior nos sirve como un control de versiones, en caso de que necesitemos hacer cambios o deshacer los cambios realizados
# Todos los comandos ejecutados en el docker se van registrando y queda rastro para todos aquellos que usen dicha imágen.  

docker image history midocker:1.0

# Comparémoslo con la imágen original descargada del repositorio y veamos el incremento en el tamaño 

docker image history ubuntu


# Dockerfile
# Una buena práctica es usar Dockerfile para que no quede ese registro y para automatizar los cambios.  El archivo Dockerfile no puede ejecutar comandos interactivos

vi Dockerfile

# El siguiente es el contenido del archivo:
###
FROM ubuntu
RUN apt-get update && apt-get install figlet -y 
###

docker build -t miotrodocker:1.0 . 
docker image ls
docker run miotrodocker:1.0 figlet hola
docker image history <IMAGE_ID>

# Cada cambio afecta sólo una capa del caché correspondiente a la imágen, haciendo que las imágenes no pesen tanto y aumenta la velocidad de creación de imágenes

# Agregar al Dockerfile y comentar el RUN anterior

# El siguiente es el contenido del archivo
###
FROM miotrodocker:1.0
RUN touch /tmp/hola
###

docker build -t miotrodocker:1.1 .
docker image ls
docker image history <IMAGE_ID>
docker run miotrodocker:1.1 ls /tmp

# El comando anterior muestra el archivo /tmp/hola, si ejecutamos (creamos) un docker con la imágen miotrodocker:1.0, vemos que no está el archivo /tmp/hola

docker run miotrodocker:1.0 ls /tmp



# Volúmenes y Puertos

# Descarguemos y ejecutemos un servidor NGINX (Servidor Web) del repositorio oficial Docker Hub (https://hub.docker.com)
# La opción -d me permite ejecutar un proceso largos en background o servicios como el que ejecuta nginx

docker run -d nginx:1.27.1-alpine 
docker ps

# Ahora ingresamos al contenedor que está corriendo

docker exec -it <CONTENEDOR_ID> bash

# El comando anterior puede fallar si el binario de bash no está en la imágen usada.  Podemos usar el siguiente comando

docker exec -it <CONTENEDOR_ID> sh

# Los contenedores descargados usualmente no están actualizados a la fecha más reciente, o son versiones mínimas del sistema operativo para ahorrar espacio, por lo que es buena práctica actualizarlos e instalar lo que se vaya a necesitar

> ps fax

# El comando anterior muestra los procesos o servicios en ejecución en el contenedor, observemos el daemon de nginx

> curl localhost

# Ahora montamos volúmenes al contenedor

> exit
docker ps
docker stop <CONTAINER_ID> 
docker ps
mkdir docker
cd docker
vi index.html
#El siguiente es el contenido del archivo index.html
###
<html>
<body>
Nuestra web v 1.0
</body>
</html>
###
docker run -v ~gosorio/docker/index.html:/usr/share/nginx/html/index.html:ro -d nginx:1.27.1-alpine
docker ps
docker exec -it <CONTAINER_ID> sh
> df -k
> cd /usr/share/nginx/html
> cat index.html
> curl localhost
> exit
docker ps
docker stop <CONTAINER_ID>


# Para exponer un puerto en un contenedor usamos el parámetro -p <puerto_local>:<puerto_contenedor>

docker ps
docker stop <CONTAINER_ID>
docker run -v ~gosorio/docker:/usr/share/nginx/html:ro -p 8080:80 -d nginx:1.27.1-alpine
docker ps

# Ahora vemos el enrutamiento de puertos en la salida anterior
# El siguiente comando mostrará la página web compartida por volúmenes al contenedor

curl localhost:8080

# Ahora modifiquemos el archivo index.html local y probamos nuevamente

curl localhost:8080
docker ps
docker stop <CONTAINER_ID>


# Paso de variables
# Con el comando 
# docker run -e MYSQL_ROOT_PASSWORD=miclave -e MYSQL_DATABASE=midb -v ~gosorio/mysql-data:/var/lib/mysql -d mysql:8.0.13 
# puedo pasar variables de entorno para la configuración de la imágen y además compartir el volúmen donde va a ir la base de datos, porque cuando se baje el contenedor, todo los datos desaparecen
# Esto es especialmente útil cuando estoy configurando un ambiente de producción que no debe tener las mismas contraseñas que el ambiente de desarrollo

# Docker compose (Mysql y Wordpress)
# Pero para comandos tan extensos, es mejor usar un docker-compose.yaml, que es un archivo para configurar todos los contenedores que necesito

#El siguiente es el contenido del archivo docker-compose.yaml
###
services:
  # Configuración del contenedor de MySQL
  db:
    image: mysql:8.0.13
    container_name: mysql_container
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress_user
      MYSQL_PASSWORD: wordpress_password
    volumes:
      - db_data:/var/lib/mysql  # Volumen para persistir los datos de MySQL
    networks:
      - wp_network

  # Configuración del contenedor de WordPress
  wordpress:
    image: wordpress:php:8.1-fpm-alpine
    container_name: wordpress_container
    depends_on:
      - db
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_DB_USER: wordpress_user
      WORDPRESS_DB_PASSWORD: wordpress_password
    ports:
      - "8080:80"  # El sitio de WordPress estará disponible en el puerto 8080
    volumes:
      - wp_data:/var/www/html  # Volumen para persistir los datos de WordPress
    networks:
      - wp_network

# Definición de volúmenes para la persistencia de datos
volumes:
  db_data:
  wp_data:

# Definición de la red para la comunicación entre los servicios
networks:
  wp_network:
###

# Debo tener creado el volumen a compartir
# Validemos que no haya ningún contenedor corriendo

docker ps
docker-compose up -d
docker ps
docker-compose ps

# Ahora probamos

curl http://localhost:8080/
curl -I http://localhost:8080/

# Abrimos un navegador con la dirección http://localhost:8080/ y debería mostrar el Wordpress y la pantalla de configuración

# Docker compose está pensado para usarlo localmente, a nivel empresarial ya se usa Kubernetes o Docker Swarm 

```

Aquí tienes un archivo `docker-compose.yml` para configurar dos contenedores: uno para MySQL y otro para WordPress. Estos contenedores estarán conectados en la misma red interna de Docker, lo que permitirá a WordPress interactuar con la base de datos MySQL.

```yaml
services:
  # Configuración del contenedor de MySQL
  db:
    image: mysql:latest
    container_name: mysql_container
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress_user
      MYSQL_PASSWORD: wordpress_password
    volumes:
      - db_data:/var/lib/mysql  # Volumen para persistir los datos de MySQL
    networks:
      - wp_network

  # Configuración del contenedor de WordPress
  wordpress:
    image: wordpress:latest
    container_name: wordpress_container
    depends_on:
      - db
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_DB_USER: wordpress_user
      WORDPRESS_DB_PASSWORD: wordpress_password
    ports:
      - "8080:80"  # El sitio de WordPress estará disponible en el puerto 8080
    volumes:
      - wp_data:/var/www/html  # Volumen para persistir los datos de WordPress
    networks:
      - wp_network

# Definición de volúmenes para la persistencia de datos
volumes:
  db_data:
  wp_data:

# Definición de la red para la comunicación entre los servicios
networks:
  wp_network:
```

### **Instrucciones para Ejecutar el `docker-compose.yml`:**

1. Guarda el contenido anterior en un archivo llamado `docker-compose.yml`.

2. Abre una terminal y navega al directorio donde guardaste el archivo.

3. Ejecuta el siguiente comando para levantar los contenedores:

   ```bash
   docker-compose up -d
   ```

   Esto descargará las imágenes necesarias, creará los contenedores, y los ejecutará en segundo plano.

4. Una vez ejecutado, podrás acceder a WordPress desde tu navegador en `http://localhost:8080`.

### **Detalles de la Configuración:**

- **MySQL:**
  - La base de datos se configura con las credenciales y parámetros especificados en la sección `environment`.
  - Los datos de MySQL se persisten en el volumen `db_data`.

- **WordPress:**
  - WordPress se conecta a MySQL usando los parámetros especificados en `WORDPRESS_DB_HOST`, `WORDPRESS_DB_NAME`, `WORDPRESS_DB_USER`, y `WORDPRESS_DB_PASSWORD`.
  - Los datos del sitio se guardan en el volumen `wp_data`.
  - El servicio estará disponible en el puerto 8080 de tu máquina host.

Para detener y eliminar los contenedores, volúmenes y la red creada, utiliza:

```bash
docker-compose down -v
```

Este comando limpiará el ambiente sin dejar residuos de los datos o configuraciones.



- Ver https://aulasoftwarelibre.github.io/taller-de-docker/docker-compose/
- Ver [[Contenedor mysql]] 
- https://imaginaformacion.com/tutoriales/comandos-docker
---

Aquí tienes un instructivo detallado para crear un ambiente de desarrollo en tu equipo personal con Ubuntu que conste de contenedores para PostgreSQL y NGINX, así como todo lo necesario para desarrollar en Python con VSCode. Incluye los pasos para instalar y configurar Docker y Docker Compose, así como la creación de volúmenes para PostgreSQL, la configuración de puertos y la forma de pasar parámetros de configuración.

### **Paso 1: Instalación y Configuración de Docker y Docker Compose**

1. **Actualizar el sistema e instalar paquetes necesarios:**

   ```bash
   sudo apt update
   sudo apt upgrade -y
   sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
   ```

2. **Agregar la clave GPG oficial de Docker:**

   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   ```

3. **Agregar el repositorio de Docker:**

   ```bash
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

4. **Instalar Docker:**

   ```bash
   sudo apt update
   sudo apt install docker-ce docker-ce-cli containerd.io -y
   ```

5. **Instalar Docker Compose:**

   ```bash
   sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
   sudo chmod +x /usr/local/bin/docker-compose
   ```

6. **Verificar las instalaciones:**

   ```bash
   docker --version
   docker-compose --version
   ```

7. **Agregar tu usuario al grupo `docker` para evitar usar `sudo` en cada comando:**

   ```bash
   sudo usermod -aG docker $USER
   newgrp docker
   ```

### **Paso 2: Creación del Proyecto con Docker Compose**

1. **Crear un directorio de proyecto y navegar a él:**

   ```bash
   mkdir dev_environment
   cd dev_environment
   ```

2. **Crear un archivo `docker-compose.yml` con la siguiente configuración:**

   ```yaml
   services:
     postgres:
       image: postgres:latest
       container_name: postgres_db
       environment:
         - POSTGRES_USER=youruser
         - POSTGRES_PASSWORD=yourpassword
         - POSTGRES_DB=yourdb
       ports:
         - "5432:5432"
       volumes:
         - pg_data:/var/lib/postgresql/data

     nginx:
       image: nginx:latest
       container_name: nginx_server
       ports:
         - "80:80"
       volumes:
         - ./nginx.conf:/etc/nginx/nginx.conf:ro
       depends_on:
         - postgres

   volumes:
     pg_data:
       driver: local
   ```

3. **Crear el archivo de configuración de NGINX (`nginx.conf`):**

   Crea un archivo llamado `nginx.conf` en el mismo directorio:

   ```nginx
   events { }

   http {
       server {
           listen 80;
           location / {
               root /usr/share/nginx/html;
               index index.html index.htm;
           }
       }
   }
   ```

### **Paso 3: Configuración y Desarrollo en Python con VSCode**

1. **Instalar VSCode si aún no lo tienes:**

   ```bash
   sudo snap install --classic code
   ```

2. **Abrir el proyecto en VSCode:**

   ```bash
   code .
   ```

3. **Instalar las extensiones necesarias de Python en VSCode:**
   - Busca e instala las extensiones: Python, Docker y Remote - Containers.

4. **Crear un entorno virtual para Python en tu proyecto:**

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

5. **Instalar cualquier dependencia de tu proyecto usando `pip`:**

   ```bash
   pip install -r requirements.txt  # si tienes un archivo de requisitos
   ```

- https://medium.com/@meghasharmaa704/file-structure-of-docker-compose-yml-file-e955a2f99a1f
### **Paso 4: Iniciar los Contenedores**

1. **Levantar los contenedores con Docker Compose:**

   ```bash
   docker-compose up -d
   ```

2. **Verificar que los contenedores estén corriendo:**

   ```bash
   docker ps
   ```

### **Paso 5: Conectar y Probar**

- Conéctate a la base de datos PostgreSQL desde tu aplicación Python o desde herramientas como DBeaver usando los siguientes parámetros:
  - Host: `localhost`
  - Puerto: `5432`
  - Usuario: `youruser`
  - Contraseña: `yourpassword`
  - Base de datos: `yourdb`

- NGINX estará sirviendo en el puerto `80` de tu localhost. Puedes personalizar más la configuración de NGINX según lo necesites.

### **Paso 6: Desinstalación y Limpieza del Ambiente**

1. **Detener y borrar todos los contenedores y volúmenes:**

   ```bash
   docker-compose down -v
   ```

2. **Desinstalar Docker y Docker Compose:**

   ```bash
   sudo apt-get purge docker-ce docker-ce-cli containerd.io -y
   sudo apt-get autoremove -y --purge docker-ce docker-ce-cli containerd.io
   sudo rm -rf /var/lib/docker
   sudo rm -rf /var/lib/containerd
   sudo rm /usr/local/bin/docker-compose
   ```

3. **Eliminar el grupo de Docker:**

   ```bash
   sudo groupdel docker
   ```

Este instructivo te guía desde la instalación hasta la eliminación completa del entorno de desarrollo, garantizando que tu base de datos tenga volúmenes persistentes y que los contenedores estén configurados correctamente.

---

En Docker, se pueden especificar los recursos asignados a un contenedor, como la cantidad de CPU y memoria, utilizando opciones de configuración en el comando `docker run` o en un archivo `docker-compose.yml`. Estos recursos ayudan a controlar el rendimiento del contenedor y a garantizar que no consuma más de lo necesario del sistema anfitrión.

### **Especificación de Recursos en Docker**

#### **1. Asignar Recursos Usando el Comando `docker run`**

Puedes especificar recursos directamente cuando inicias un contenedor usando el comando `docker run`. Aquí están algunas de las opciones más comunes:

- **Asignar Memoria (`-m` o `--memory`)**: Limita la cantidad máxima de memoria que puede usar el contenedor.
- **Asignar CPU (`--cpus`)**: Limita la cantidad de CPU que puede usar el contenedor.
- **Limitar CPU Shares (`--cpu-shares`)**: Define la prioridad del contenedor para el uso de la CPU.

**Ejemplo:**

```bash
docker run -d \
  --name my_container \
  --memory="512m" \             # Limita la memoria a 512 MB
  --cpus="1.5" \                # Limita el uso de la CPU a 1.5 núcleos
  --cpu-shares="1024" \         # Prioridad de CPU (valor por defecto es 1024)
  my_image
```

#### **2. Asignar Recursos Usando Docker Compose**

En un archivo `docker-compose.yml`, puedes especificar los recursos para cada servicio bajo la clave `deploy.resources`. Esta configuración suele ser utilizada en ambientes de producción o para mayor control.

**Ejemplo: `docker-compose.yml`**

```yaml
services:
  my_service:
    image: my_image:latest
    deploy:
      resources:
        limits:
          cpus: '1.5'               # Limita el uso de CPU a 1.5 núcleos
          memory: 512M              # Limita la memoria a 512 MB
        reservations:
          cpus: '0.5'               # Reserva de 0.5 núcleos de CPU
          memory: 256M              # Reserva de 256 MB de memoria
```

### **Explicación de los Parámetros**

- **`limits`**: Define el límite máximo de recursos que el contenedor puede usar. Si se alcanza este límite, el contenedor no podrá usar más recursos.
- **`reservations`**: Especifica la cantidad de recursos garantizados para el contenedor, incluso cuando el sistema está bajo carga.

### **Otros Parámetros Útiles para Control de Recursos**

- **`--memory-swap`**: Controla la cantidad total de memoria más swap que el contenedor puede usar. Por ejemplo, `--memory="512m" --memory-swap="1g"` permite 512 MB de RAM y 512 MB de swap.
- **`--cpuset-cpus`**: Permite especificar qué núcleos de CPU puede usar el contenedor. Por ejemplo, `--cpuset-cpus="0,1"` limita el uso a los núcleos 0 y 1.
- **`--cpu-quota` y `--cpu-period`**: Controlan la cantidad de CPU que puede usar el contenedor en un período de tiempo, configurando así cuotas específicas.

### **Resumen**

- **Memoria (`-m`, `--memory`)**: Define el límite de memoria.
- **CPU (`--cpus`)**: Define la cantidad de núcleos de CPU asignados.
- **Prioridad (`--cpu-shares`)**: Asigna prioridad en el uso de la CPU.

Especificar recursos correctamente ayuda a controlar el comportamiento de los contenedores y a optimizar el uso de recursos en tu sistema anfitrión, especialmente en entornos donde varios contenedores compiten por los mismos recursos.