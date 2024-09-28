.
Aquí tienes un **cheatsheet para Docker Compose** que incluye los comandos más importantes y algunas configuraciones básicas para manejar aplicaciones multi-contenedor de manera eficiente:

### **1. Comandos Básicos de Docker Compose**

| Comando                                    | Descripción                                                         |
| ------------------------------------------ | ------------------------------------------------------------------- |
| `docker-compose --version`                 | Muestra la versión instalada de Docker Compose.                     |
| `docker-compose up`                        | Inicia y ejecuta los servicios definidos en `docker-compose.yml`.   |
| `docker-compose up -d`                     | Inicia los servicios en segundo plano (modo detached).              |
| `docker-compose down`                      | Detiene y elimina los contenedores, redes y volúmenes creados.      |
| `docker-compose start`                     | Inicia servicios detenidos previamente.                             |
| `docker-compose stop`                      | Detiene los servicios en ejecución.                                 |
| `docker-compose restart`                   | Reinicia los servicios.                                             |
| `docker-compose ps`                        | Lista los servicios definidos y su estado actual.                   |
| `docker-compose logs`                      | Muestra los logs de todos los servicios.                            |
| `docker-compose logs -f`                   | Muestra los logs en tiempo real.                                    |
| `docker-compose exec <servicio> <comando>` | Ejecuta un comando dentro de un servicio en ejecución.              |
| `docker-compose build`                     | Construye o reconstruye los servicios desde los Dockerfiles.        |
| `docker-compose pull`                      | Descarga las imágenes de los servicios definidos.                   |
| `docker-compose config`                    | Valida y muestra la configuración del archivo `docker-compose.yml`. |

### **2. Definición Básica de `docker-compose.yml`**

Un archivo básico `docker-compose.yml` para tres servicios: una base de datos PostgreSQL, un servidor NGINX y una aplicación Python.

```yaml
version: '3.9'

services:
  db:
    image: postgres:latest
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydatabase
    volumes:
      - db_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"

  web:
    image: nginx:latest
    ports:
      - "8080:80"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf

  app:
    build:
      context: .
      dockerfile: Dockerfile
    volumes:
      - .:/usr/src/app
    depends_on:
      - db

volumes:
  db_data:
```

### **3. Variables y Entornos**

| Comando                                | Descripción                                                               |
|----------------------------------------|---------------------------------------------------------------------------|
| `docker-compose up --build`            | Fuerza la reconstrucción de los servicios antes de iniciarlos.            |
| `docker-compose run --rm <servicio>`   | Ejecuta un servicio temporalmente y lo elimina al salir.                  |
| `docker-compose up -e <VARIABLE=valor>`| Establece variables de entorno desde la línea de comandos.                |

### **4. Escalado de Servicios**

| Comando                                | Descripción                                                               |
|----------------------------------------|---------------------------------------------------------------------------|
| `docker-compose up --scale <servicio>=<n>` | Escala un servicio a `n` contenedores.                                |

### **5. Limpieza y Eliminación de Recursos**

| Comando                                | Descripción                                                          |
| -------------------------------------- | -------------------------------------------------------------------- |
| `docker-compose down --volumes`        | Elimina los volúmenes asociados al stack.                            |
| `docker-compose down --rmi all`        | Elimina todas las imágenes construidas para los servicios.           |
| `docker-compose down --remove-orphans` | Elimina contenedores huérfanos que no están definidos en el archivo. |

### **6. Gestión de Redes**

| Comando                                | Descripción                                                               |
|----------------------------------------|---------------------------------------------------------------------------|
| `docker-compose network ls`            | Lista las redes creadas por Docker Compose.                              |
| `docker-compose network rm <red>`      | Elimina una red específica.                                              |

### **7. Debugging y Diagnóstico**

| Comando                                | Descripción                                                               |
|----------------------------------------|---------------------------------------------------------------------------|
| `docker-compose top`                   | Muestra los procesos activos dentro de los servicios.                    |
| `docker-compose events`                | Muestra eventos en tiempo real para los servicios en ejecución.          |

### **8. Definición de Variables en `.env`**

Puedes definir variables en un archivo `.env` que serán automáticamente cargadas:

```
# Archivo .env
POSTGRES_USER=user
POSTGRES_PASSWORD=password
POSTGRES_DB=mydatabase
```

Referencias en `docker-compose.yml`:

```yaml
environment:
  - POSTGRES_USER=${POSTGRES_USER}
  - POSTGRES_PASSWORD=${POSTGRES_PASSWORD}
```

