.
- Ver [[GIT cheat sheet]] 

## Instalación y configuración de GIT

1. **Instalar Git** (si no está instalado).

   ```bash
   sudo apt-get install git
   ```

Nota: En entornos Windows, descargar el instalador desde https://git-scm.com/ e instalarlo.  En el proceso de instalación indicar que se está usando Visual Studio Code.  Se recomienda instalar y usar "Git bash"

2. **Configurar Git** (nombre y correo del desarrollador).

   ```bash
   git config --global user.name "Tu Nombre"
   git config --global user.email "tuemail@example.com"
   git config --list
   ```


## Trabajando con GIT (sin GitHub)

```bash
# Creación de la carpeta del proyecto
mkdir TallerGit
cd TallerGit

# Inicialización del repositorio
git init

# Validación del estado del repositorio
git status

# Crea un archivo "index.html"
# El siguiente es el contendio del archivo
<!DOCTYPE html>
<html>
<head>
<title>Mi Proyecto</title>
</head>
<body>
<h1>Hola Mundo</h1>
</body>
</html>

# Nota: En este punto los archivos no están protegidos y pueden ser borrados o modificados sin posibilidad de restaurarlos

# Muestra el estado del repositorio
git status

# Marca el archivo para hacerle commit.  Si son varios puede hacerse uno a uno, o poner toda la lista en la misma lína de comando
git add index.html 

git status

# Muestra el historial de commits
git log

# Realiza el commit de los cambios
git commit -m "Añadir archivo HTML básico"

git status

git log

# En este momento el archivo index.html ya está protegido, vamos a borrarlo y recuperarlo del último commit

rm index.html
git status

# Recupera el archivo del último commit
# git checkout index.html
git restore index.html

git status

# Creemos otro archivo para pruebas
touch app.py

git status

# También podemos marcar todo el directorio para hacerles commit
git add .

# El commit sin más parámetros abre un archivo donde puedo escribir comentarios más amplios
git commit 

# Mostremos la historia de los commits de la rama actual y tomemos nota del primer y del último commit (note que primero se muestra el más reciente)
git log

# Creemos otro archivo para pruebas
touch moda.py
ls -l

# Regresemos en la línea de tiempo
git checkout <primer commit>
ls -l
git log
git status

# La historia no se pierde, el siguiente comando muestra los checkout realizados
git reflog

# Volvamos al último commit en la línea de tiempo
git checkout <último commit>
ls -l
git log
git status
git reflog

# Mostremos las ramas o líneas de tiempo existentes y en cuál estamos
git branch
ls -l

# Creemos una nueva rama (o lína de tiempo)
git checkout -b nueva-funcionalidad
git branch
ls -l

# Validemos que la historia de commits se hereda en la nueva rama
git log
git reflog

# Regresemos a la rama principal
git checkout master
ls -l
git log

# Volvamos a la rama donde vamos a hacer cambios
git checkout nueva-funcionalidad

# Realiza cambios en "index.html"
# El siguiente es el contendio del archivo
<!DOCTYPE html>
<html>
<head>
<title>Mi Proyecto</title>
</head>
<body>
<h1>Hola Mundo</h1>
</body>
</html>
<p>Nueva funcionalidad añadida</p>

# Marquemos sólo el archivo modificado para commit
git add index.html

# Mira las diferencias entre los archivos marcados para commit y los que están en el último commit relizado
git diff --staged

git commit -m "Añadir nueva fOncionalidad"

# Tomar nota de la nueva funcionalidad
git log

# Parece que escribimos mal el asunto del commit, corrijamoslo
git commit --amend

# amend también nos sirve para incluir en el último commit un nuevo archivo o modificar un archivo al que ya le hicimos commit
touch pruebamend.txt
git add pruebamend.txt
git commit --amend

# Validemos que no hayan nuevos commits
git log

# Para ver los archivos modificados en cada commit
git log --stat


# Volvamos a la rama principal y hagamos un merge (unamos las líneas temporales)
git checkout master
git log
ls -l

git merge nueva-funcionalidad
ls -l
git log

# Crear un archivo "README.md"
# El siguiente es el contenido del archivo
Primera línea del archivo README.md
Segunda línea del archivo README.md

# Crea nuevos archivos para probar
touch a b c
git status

# La siguiente opción marca para commit los archivos del directorio actual que han cambiado y que ya venían siendo manejados por GIT
# Esto me permite agregar solamente los archivos que me interesan
echo "Nueva linea" >> README.md
rm app.py
git status
git add -u
git status

# Marcamos para commit un archivo que no había sido manejado por GIT
git add README.md a b
git status

# Con el siguiente comando desmarco el archivo para commit
git restore --staged README.md
git status

# Probemos la opción git add con menú
git add --interactive
# Marquemos el archivo c para commit

git commit "Este commit incluye al archivo c"
git status

# Indiquemos que ya no queremos que git almacene información del archivo c (ej. el archivo tiene información secreta).  Esto no borra el archivo del directorio de trabajo
git rm --cached c
git commit -m "Dejé de gestionar el archivo c en el repositorio"
rm abc

# Identificar el commit donde estaba el archivo
git log --oneline 

# Restaurar el archivo abc
git checkout abc 
ls -l abc

# Note que ahora estamos en un modo "HEAD detached at ", vea el prompt.
git status

# En el modo anterior nos devolvimos a una ventana de tiempo y podemos jugar con el repositorio
# Podemos hacer pruebas y si esas pruebas nos sirven, podemos almacenar los commits de esa realidad alterna en una nueva rama 
# O simplemente descartarlos y volver a la rama donde estabamos
git checkout master
git status
ls -l

echo "Nueva línea" >> README.md

# Con la opción -a del commit, no necesitamos hacer "git add" previo 
git commit -am "Adición del archivo README.md para prueba de commit por parche"

git log --oneline

# Veamos diferencias entre dos commits distintos
git diff <commit_X> <commit_Y>

# Modificamos el index.html
# El siguiente es el contenido del archivo:
Estos cambios corresponden al requerimiento 121
Primera línea del archivo README.md
Segunda línea del archivo README.md
Estos cambios corresponden al requerimiento 300

# Diferencias encontradas en el working directory
git diff 

# Probemos la opción de marcados parciales o parches
git add -p README.md 
# Si no aparecen los cambios separados, presionar s

git status

# Veamos la diferencia entre los cambios que van a commit y los que no
git diff 

git commit -m "Probando parche 1"
git status
git add README.md
# Muestra la diferencia entre los cambios del stage y los que ya están en commit
git diff --staged 

git commit -m "Probando parche 2"
ls -l
git branch

# Pasemos a la rama nueva-funcionalidad
git checkout nueva-funcionalidad
touch nuevafuncionalidad.txt
git add nuevafuncionalidad.txt
git commit -m "Este commit tiene el nuevo archivo nuevafuncionalidad.txt"
git log --oneline

# Regresemos a la rama master
git checkout master
git branch
ls -l

# Ahora vamos a aplicar un commit particular de cualquier otra rama (Apliquemos en último commit de la rama nueva-funcionalidad, donde se creó el archivo nuevafuncionalidad.txt)
# Esto sirve si me doy cuenta que estaba en otra rama distinta a la que yo necesito
git cherry-pick <hash_del_commit>
ls -l
git status
git log --oneline

# Borremos la rama nueva-funcionalidad
git checkout nueva-funcionalidad
git branch -d nueva-funcionalidad
git checkout master
git branch -d nueva-funcionalidad
git branch -D nueva-funcionalidad

# Creemos otra rama llamada feature y probemos la resolución de conflictos
git checkout -b feature
git branch
echo "Cambio en feature" > conflicto.txt
git add conflicto.txt
git commit -m "Cambio en feature" conflicto.txt

git checkout master
git branch
echo "Cambio en master" > conflicto.txt
git add conflicto.txt
git commit -m "Cambio en master"

# Hagamos un merge y observemos que hay conflictos con el archivo conflicto.txt
git merge feature
# Note el cambio en el prompt

# El archivo en conflicto fue modificado para señalar el conflicto
# Es la oportunidad para decidir cuál cambio es el correcto o hacer una combinación de propuestas
# Hay herramientas que se pueden instalar para gestionar estos conflictos de forma gráfica
# Simplemente los vamos a ignorar y a abortar el merge
vi conflicto.txt 

git log --oneline
git merge feature
git add c
git commit -m "Adicionando un archivo después del merge fallido"

# El siguiente comando muestra mayor información con respecto a un commit
git show <commit-hash>
git show <branch-name>
git show <commit-hash> -- <nombre-del-archivo>

# Abortemos en merge pendiente
git merge --abort # Note el cambio en el prompt
cat conflicto.txt
git status
```


## Uso de GitHub

1. **Creación de la cuenta y repositorio en GitHub**

   Crear un repositorio privado en GitHub con el mismo nombre que el proyecto local.

2. **Agregar el repositorio remoto**
   
   Enlazar el repositorio remoto de GitHub con el proyecto local:

   ```bash
   git remote add origin https://github.com/tu-usuario/TallerGit.git
   git remote -v
   ```


3. **Subir cambios al repositorio remoto**
   
   Subir los cambios locales al repositorio remoto:

   ```bash
   git push -u origin master
   ```

Nota: Ahora valida que el repositorio en GitHub es igual al repositorio en tu pc

4. **Agregar colaboradores al repositorio**

   En la configuración del repositorio de GitHub, añadir a los colaboradores que trabajarán en el proyecto.

5. **Trabajando con pull requests**

   Crear ramas para cada nueva funcionalidad, luego subirlas a GitHub:


En el equipo del nuevo colaborador:

``` bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
git config --list
git remote add origin https://github.com/tu-usuario/TallerGit.git
git remote -v

# Configurar Git con tus credenciales
# Generar una clave SSH
# Es recomendable que configures una clave SSH para que puedas interactuar con GitHub sin tener que ingresar tu usuario y contraseña constantemente. Sigue estos pasos:

# Genera una clave SSH:
ssh-keygen -t ed25519 -C "tu_email@example.com"

# Presiona enter para aceptar las ubicaciones por defecto, y opcionalmente ingresa una contraseña si lo deseas.

# Agrega la clave SSH al agente de autenticación:

eval "$(ssh-agent -s)"

# Copia tu clave SSH al portapapeles

cat ~/.ssh/id_ed25519.pub

# Agrega la clave SSH a tu cuenta de GitHub:
   
# Ve a tu perfil en GitHub.
# Ve a **Settings** > **SSH and GPG keys** > **New SSH key**.
# Pega tu clave pública y guárdala.

# Clonar el repositorio

# Una vez que hayas sido invitado como colaborador, puedes clonar el repositorio en tu máquina.

# Ve al repositorio en GitHub y copia la URL SSH del proyecto.

# Clona el repositorio en tu máquina local:

git clone git@github.com:nombre_propietario/nombre_repositorio.git`

# Entra en el directorio del repositorio clonado:

cd nombre_repositorio

# Crear una rama de trabajo

# Antes de empezar a hacer cambios, es una buena práctica trabajar en una rama distinta a `main` o `master`.

git checkout -b nombre_de_tu_rama
git branch

# Realizar cambios en tu proyecto

# Ahora puedes comenzar a hacer cambios en tu código o agregar nuevos desarrollos desde tu repositorio local

touch ventas.py
git add .
git commit -m "Descripción de los cambios"
  
# Actualizar tu repositorio local (opcional)
# Si alguien más ha hecho cambios en el repositorio remoto, es una buena práctica traer esos cambios antes de hacer un push.

git pull origin main

# Si surgen conflictos durante el merge, tendrás que resolverlos antes de hacer el push.

# Subir tus cambios al repositorio remoto

# Sube tus cambios a la rama en el repositorio remoto:

git push origin nombre_de_tu_rama

# Crear un Pull Request

# Una vez que hayas subido tus cambios, ve a GitHub, abre el repositorio, y GitHub te sugerirá que crees un **Pull Request** para que tus cambios sean revisados e integrados en la rama principal del proyecto.

# Ve a la pestaña **Pull Requests** del repositorio.
# Haz clic en **New Pull Request**.
# Selecciona tu rama y crea el Pull Request con una descripción de los cambios que hiciste.

# Esperar el proceso de revisión y merge

# Tus compañeros o el propietario del proyecto revisarán tus cambios. Si todo está bien, tu Pull Request será aceptado y fusionado en el repositorio principal.

# Mantén tu repositorio sincronizado
# Es importante mantener tu repositorio local sincronizado con los cambios que se hagan en el repositorio principal. Para esto, debes:

git checkout main

# Traer los cambios más recientes del remoto:

git pull origin main

# Luego, puedes volver a tu rama de trabajo si continúas haciendo más cambios:

git checkout nombre_de_tu_rama
```


# Buenas prácticas

- git pull origin master # Siempre traer la última versión del repositorio
- Usa nombres descriptivos para las ramas y commits.
- Realiza commits pequeños y frecuentes.
- Revisa los cambios con `git diff` antes de hacer un commit.
- Usa `git pull --rebase` para evitar merges innecesarios.
- Mantén la rama `master` siempre limpia y funcional.
- Usa las revisiones de código para mejorar la calidad del proyecto.
- No olvides revisar y actualizar la documentación del proyecto.



[[Taller GIT v0]]  

> Documento completo
> ...