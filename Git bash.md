.
- https://www.atlassian.com/es/git/tutorials/git-bash

En esencia, Git es un conjunto de programas de utilidades de líneas de comandos que están diseñados para ejecutarse en un entorno de líneas de comandos de estilo Unix. Los sistemas operativos modernos como Linux y macOS incluyen terminales de líneas de comandos Unix integrados. Esto convierte a Linux y a macOS en sistemas operativos complementarios cuando se trabaja con Git. En cambio, Microsoft Windows utiliza el símbolo del sistema de Windows, un entorno de terminal que no es Unix.

En entornos de Windows, Git normalmente se incluye en un paquete como parte de aplicaciones de interfaz gráfica de usuario de nivel superior. Las interfaces gráficas de usuario para Git podrían intentar abstraer y ocultar los lenguajes primitivos del sistema de control de versiones subyacente. Esto puede ser una ayuda excepcional para que los principiantes en Git contribuyan rápidamente a un proyecto. Una vez que los requisitos de colaboración de un proyecto aumentan con otros miembros del equipo, es fundamental ser consciente de cómo funcionan los métodos de Git de verdad sin procesar. En ese momento, puede ser beneficioso disponer de una versión de interfaz gráfica de usuario para las herramientas de líneas de comandos. Se ofrece Git Bash para proporcionar una experiencia de Git en el terminal.

---

## ¿Qué es Git Bash?

---

Git Bash es una aplicación para entornos de Microsoft Windows que ofrece una capa de emulación para una experiencia de líneas de comandos de Git. Bash es el acrónimo en inglés de Bourne Again Shell. Una shell es una aplicación de terminal que se utiliza como interfaz con un sistema operativo mediante comandos escritos. Bash es una shell predeterminada popular en Linux y macOS. Git Bash es un paquete que instala Bash, algunas utilidades comunes de bash y Git en un sistema operativo Windows.

## Cómo instalar Git Bash

---

Git Bash viene incluido en el paquete [Git para Windows](https://gitforwindows.org/). Descárgate e instala Git para Windows como el resto de las aplicaciones de Windows. Una vez descargado, busca el archivo `.exe` incluido y ábrelo para ejecutar Git Bash.

## Cómo utilizar Git Bash

---

Git Bash tiene las mismas operaciones que una experiencia de Bash estándar. Será útil revisar el uso básico de Bash. El uso avanzado de Bash está fuera del alcance de este documento centrado en Git.

## Cómo navegar por las carpetas

---

El comando de Bash `pwd` sirve para imprimir el "directorio de trabajo actual". `pwd` equivale a ejecutar cd en un terminal DOS (host de consola de Windows). Es la carpeta o ruta en la que reside la sesión de Bash actual.

El comando de Bash `ls` sirve para "enumerar" el contenido del directorio de trabajo actual. `ls` equivale a ejecutar `DIR` en un terminal de host de consola de Windows.

Tanto el host de la consola de Bash como el de Windows tienen un comando cd. cd es la sigla en inglés de "cambiar de directorio". Se invoca cd con el nombre de un directorio adjunto. Si se ejecuta cd, se cambiará el directorio de trabajo actual de las sesiones del terminal al argumento del directorio que se ha especificado.

## Comandos de Git Bash

---

En el paquete Git Bash se incluyen otros comandos adicionales que se pueden encontrar en el directorio `/usr/bin` de la emulación de Git Bash. De hecho, Git Bash puede ofrecer una experiencia de shell bastante sólida en Windows. Git Bash incluye en el paquete los siguientes comandos de shell que están fuera del alcance de este documento: [Ssh](https://man.openbsd.org/ssh.1), [scp](https://linux.die.net/man/1/scp), [cat](http://man7.org/linux/man-pages/man1/cat.1.html) y [find](https://linux.die.net/man/1/find).

Además del conjunto de comandos de Bash que hemos mencionado anteriormente, Git Bash incluye el conjunto completo de comandos fundamentales de Git que se explican en este sitio. Obtén más información en las páginas de documentación correspondientes de [git clone](https://www.atlassian.com/es/git/tutorials/setting-up-a-repository/git-clone), [git commit](https://www.atlassian.com/es/git/tutorials/saving-changes/git-commit), [git checkout](https://www.atlassian.com/es/git/tutorials/using-branches/git-checkout) y [git push](https://www.atlassian.com/es/git/tutorials/syncing/git-push), entre otras.