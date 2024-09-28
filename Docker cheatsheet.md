.
Aquí tienes un **cheatsheet de Docker** que cubre los comandos más comunes y útiles, agrupados por categoría para facilitar su uso:

### **1. Comandos Básicos de Docker**

| Comando                        | Descripción                                        |
|-------------------------------|----------------------------------------------------|
| `docker --version`            | Muestra la versión de Docker instalada.            |
| `docker info`                 | Muestra información detallada del sistema Docker.  |
| `docker help`                 | Muestra ayuda sobre los comandos de Docker.        |

### **2. Gestión de Imágenes**

| Comando                                          | Descripción                                               |
|--------------------------------------------------|-----------------------------------------------------------|
| `docker pull <imagen>`                           | Descarga una imagen desde Docker Hub.                     |
| `docker images`                                  | Lista todas las imágenes descargadas.                     |
| `docker rmi <imagen>`                            | Elimina una imagen local.                                 |
| `docker build -t <nombre>:<tag> .`               | Construye una imagen a partir de un Dockerfile.           |
| `docker tag <imagen> <nombre>:<tag>`             | Etiqueta una imagen con un nuevo nombre o tag.            |

### **3. Gestión de Contenedores**

| Comando                                          | Descripción                                               |
|--------------------------------------------------|-----------------------------------------------------------|
| `docker run <imagen>`                            | Ejecuta un contenedor desde una imagen.                   |
| `docker run -d <imagen>`                         | Ejecuta un contenedor en segundo plano (modo detached).   |
| `docker run -it <imagen> /bin/bash`              | Ejecuta un contenedor en modo interactivo con bash.       |
| `docker ps`                                      | Lista los contenedores en ejecución.                      |
| `docker ps -a`                                   | Lista todos los contenedores, incluidos los detenidos.    |
| `docker stop <id_contenedor>`                    | Detiene un contenedor en ejecución.                       |
| `docker start <id_contenedor>`                   | Inicia un contenedor detenido.                            |
| `docker restart <id_contenedor>`                 | Reinicia un contenedor.                                   |
| `docker rm <id_contenedor>`                      | Elimina un contenedor detenido.                           |
| `docker logs <id_contenedor>`                    | Muestra los registros de un contenedor.                   |
| `docker exec -it <id_contenedor> /bin/bash`      | Ejecuta un comando dentro de un contenedor en ejecución.  |

### **4. Gestión de Volúmenes**

| Comando                                          | Descripción                                               |
|--------------------------------------------------|-----------------------------------------------------------|
| `docker volume create <nombre>`                  | Crea un volumen.                                          |
| `docker volume ls`                               | Lista todos los volúmenes.                                |
| `docker volume rm <nombre>`                      | Elimina un volumen.                                       |
| `docker run -v <nombre_volumen>:/ruta <imagen>`  | Monta un volumen en un contenedor.                        |

### **5. Redes de Docker**

| Comando                                          | Descripción                                               |
|--------------------------------------------------|-----------------------------------------------------------|
| `docker network ls`                              | Lista las redes disponibles.                              |
| `docker network create <nombre_red>`             | Crea una nueva red.                                       |
| `docker network rm <nombre_red>`                 | Elimina una red.                                          |
| `docker run --network <nombre_red> <imagen>`     | Conecta un contenedor a una red específica.               |

### **6. Gestión de Docker Compose**

| Comando                                          | Descripción                                               |
|--------------------------------------------------|-----------------------------------------------------------|
| `docker-compose up`                              | Inicia los servicios definidos en `docker-compose.yml`.   |
| `docker-compose up -d`                           | Inicia los servicios en segundo plano (modo detached).    |
| `docker-compose down`                            | Detiene y elimina los contenedores y redes asociadas.     |
| `docker-compose ps`                              | Lista los servicios en ejecución.                         |
| `docker-compose logs`                            | Muestra los registros de los servicios.                   |

### **7. Comandos de Inspección y Diagnóstico**

| Comando                                          | Descripción                                               |
|--------------------------------------------------|-----------------------------------------------------------|
| `docker inspect <id_contenedor>`                 | Muestra información detallada sobre un contenedor.        |
| `docker stats`                                   | Muestra el uso de recursos (CPU, memoria) de los contenedores. |
| `docker top <id_contenedor>`                     | Muestra los procesos en ejecución dentro de un contenedor. |

### **8. Limpieza del Sistema Docker**

| Comando                                          | Descripción                                               |
|--------------------------------------------------|-----------------------------------------------------------|
| `docker system prune`                            | Elimina contenedores, redes e imágenes no utilizados.     |
| `docker image prune`                             | Elimina imágenes no utilizadas.                           |
| `docker container prune`                         | Elimina contenedores detenidos.                           |
| `docker volume prune`                            | Elimina volúmenes no utilizados.                          |

### **9. Seguridad en Docker**

| Comando                                          | Descripción                                               |
|--------------------------------------------------|-----------------------------------------------------------|
| `docker scan <imagen>`                           | Realiza un escaneo de seguridad en una imagen.            |

### **10. Gestión de Entornos Variables**

| Comando                                          | Descripción                                               |
|--------------------------------------------------|-----------------------------------------------------------|
| `docker run -e <VARIABLE=valor> <imagen>`        | Establece variables de entorno al ejecutar un contenedor. |

Otros

docker logs -f <container_id>

- Ver https://imaginaformacion.com/tutoriales/comandos-docker
