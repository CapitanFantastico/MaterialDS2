
https://www.atlassian.com/es/git/tutorials/what-is-git

Hoy en día, Git es, con diferencia, el [[Sistema de Control de Versiones]] moderno ==más utilizado del mundo==.  

Git es un proyecto de ==código abierto== maduro y con un mantenimiento activo que desarrolló originalmente [[Linus Torvalds]], el famoso creador del kernel del sistema operativo Linux, en 2005. Un asombroso número de proyectos de software dependen de Git para el control de versiones, incluidos proyectos comerciales y de código abierto. 

Los desarrolladores que han trabajado con Git cuentan con una buena representación en la base de talentos disponibles para el desarrollo de software, y este sistema funciona a la perfección en una amplia variedad de sistemas operativos e IDE (entornos de desarrollo integrados).

Git, que presenta una ==arquitectura distribuida==, es un ejemplo de [[DVCS]] ([[Sistema de Control de Versiones Distribuido]], por sus siglas en inglés). En lugar de tener un único espacio para todo el historial de versiones del software, como sucede de manera habitual en los sistemas de control de versiones antaño populares, como [[CVS]] o [[Subversion]] (también conocido como [[SVN]]), en Git, ==la copia de trabajo del código de cada desarrollador es también un repositorio que puede albergar el historial completo de todos los cambios==.

Además de contar con una arquitectura distribuida, Git se ha diseñado teniendo en cuenta el ==rendimiento, la seguridad y la flexibilidad==.


---
## Rendimiento

---

Las características básicas de rendimiento de Git son muy sólidas en comparación con muchas otras alternativas. La [[Confirmación]] de nuevos cambios, la [[Ramificación]], la [[Fusión]] y la comparación de versiones anteriores se han optimizado en favor del rendimiento. Los algoritmos implementados en Git aprovechan el profundo conocimiento sobre los atributos comunes de los auténticos árboles de archivos de código fuente, cómo suelen modificarse con el paso del tiempo y cuáles son los patrones de acceso.

A diferencia de algunos programas de software de control de versiones, ==Git no se deja engañar por los nombres de los archivos== a la hora de determinar cuál debería ser el almacenamiento y el historial de versiones del árbol de archivos; en lugar de ello, ==se centra en el contenido del propio archivo==. Al fin y al cabo, los archivos de código fuente se cambian de nombre, se dividen y se reorganizan con frecuencia. El formato de objeto de los archivos del repositorio de ==Git emplea una combinación de codificación delta== (que almacena las diferencias de contenido) y compresión, y guarda explícitamente el contenido de los directorios y los objetos de metadatos de las versiones.

==Su arquitectura distribuida también permite disfrutar de importantes ventajas en términos de rendimiento.==

Por ejemplo, supongamos que una desarrolladora, Alice, hace cambios en el código fuente (añade una función para la próxima versión 2.0) y, luego, los confirma con mensajes descriptivos. Después, trabaja en una segunda función y confirma también esos cambios. De forma natural, estos se almacenan como elementos independientes de trabajo en el historial de versiones. A continuación, Alice cambia a la rama de la versión 1.3 del mismo software para corregir un error que afecta únicamente a esa versión anterior. El objetivo es permitir al equipo de Alice lanzar una publicación de corrección de errores, la versión 1.3.1, antes de que la 2.0 esté lista. Tras ello, Alice puede volver a la rama 2.0 para seguir trabajando en las nuevas funciones de la versión. Todo esto puede tener lugar sin necesidad de acceso a la red y, por consiguiente, es un proceso rápido y fiable. Alice podría incluso hacerlo mientras viaja en avión. Cuando esté lista para enviar al repositorio remoto todos los cambios confirmados de modo individual, bastará con que utilice un solo comando.

---
## Seguridad

---

Git se ha diseñado con ==la principal prioridad de conservar la integridad del código fuente gestionado==. El contenido de los archivos y las verdaderas relaciones entre estos y los directorios, las versiones, las etiquetas y las confirmaciones, todos ellos objetos del repositorio de Git, están protegidos con un algoritmo de hash criptográficamente seguro llamado "SHA1". De este modo, se salvaguarda el código y el historial de cambios frente a las modificaciones accidentales y maliciosas, y se garantiza que el historial sea totalmente trazable.

Con Git, puedes tener la certeza de contar con un auténtico historial de contenido de tu código fuente.

Algunos otros sistemas de control de versiones carecen de protección contra las modificaciones ocultas realizadas con posterioridad, algo que puede suponer una grave vulnerabilidad de seguridad de la información para cualquier organización que se base en el desarrollo de software.

---
## Flexibilidad

---

Uno de los objetivos clave de Git en cuanto al diseño es la flexibilidad. Git es flexible en varios aspectos: ==en la capacidad para varios tipos de flujos de trabajo de desarrollo no lineal, en su eficiencia en proyectos tanto grandes como pequeños y en su compatibilidad con numerosos sistemas y protocolos.==

Git se ha ideado para posibilitar la ramificación y el etiquetado como procesos de primera importancia (a diferencia de SVN) y las operaciones que afectan a las ramas y las etiquetas (como la fusión o la reversión) también se almacenan en el historial de cambios. No todos los sistemas de control de versiones ofrecen este nivel de seguimiento.

---
## Control de versiones con Git

---

==Git es la mejor opción para la mayoría de los equipos de software actuales.== Aunque cada equipo es diferente y debería realizar su propio análisis, aquí recogemos los principales motivos por los que destaca el control de versiones de Git con respecto a otras alternativas:

### Git es una excelente herramienta

Git tiene la ==funcionalidad, el rendimiento, la seguridad y la flexibilidad== que la mayoría de los equipos y desarrolladores individuales necesitan. Estas cualidades de Git se detallan más arriba. En las comparaciones directas con gran parte de las demás alternativas, Git resulta muy ventajoso para muchos equipos.

### Git es un estándar de facto

Git ==es la herramienta con el mayor índice de adopción de su clase==, lo que la hace muy atractiva por las siguientes razones.

Un gran número de desarrolladores ya tienen experiencia con Git y una parte importante de los graduados universitarios puede que solo haya aprendido a usar dicha solución. Aunque algunas organizaciones puedan necesitar escalar la curva de aprendizaje al migrar a Git desde otro sistema de control de versiones, muchos de sus desarrolladores actuales y futuros no precisan de formación para utilizar esta herramienta.

Además de las ventajas que brinda disponer de una amplia base de talentos, el predominio de Git también implica que muchos servicios y herramientas de software de terceros ya están integrados con Git, incluidos los [[IDE]], [[VSCode]], [[Jira]] y el servicio de alojamiento de código, [[Bitbucket]].


### Git es un proyecto de código abierto de calidad

Git es un proyecto de código abierto muy bien respaldado con más de una década de gestión de gran fiabilidad. Los encargados de mantener el proyecto han demostrado un criterio equilibrado y un enfoque maduro para satisfacer las necesidades a largo plazo de sus usuarios con publicaciones periódicas que mejoran la facilidad de uso y la funcionalidad. La calidad del software de código abierto resulta sencilla de analizar y un sinnúmero de empresas dependen en gran medida de esa calidad.

==Git goza de una amplia base de usuarios ==y de un gran apoyo por parte de la comunidad. La documentación es excepcional y para nada escasa, ya que incluye libros, tutoriales y sitios web especializados, así como podcasts y tutoriales en vídeo.

El hecho de que sea de código abierto reduce el coste para los desarrolladores aficionados, puesto que pueden utilizar Git sin necesidad de pagar ninguna cuota. En lo que respecta a los proyectos de código abierto, no cabe duda de que Git es el sucesor de las anteriores generaciones de los exitosos sistemas de control de versiones de código abierto, [[SVN]] y [[CVS]].

### Críticas de Git

Para los equipos que provienen de un sistema de control de versiones no distribuido, el hecho de contar con un repositorio central puede parecer una buena funcionalidad que no quieren perder. Sin embargo, aunque Git se ha diseñado como un sistema de control de versiones distribuido (DVCS), con él puedes seguir teniendo un repositorio oficial convencional donde se almacenen todos los cambios del software. En Git, como el repositorio de cada desarrollador lo incluye todo, no es necesario que su trabajo se vea limitado por la disponibilidad y el rendimiento del servidor "central". Durante las interrupciones o la ausencia de conexión, los desarrolladores pueden continuar consultando todo el historial del proyecto. Gracias a la flexibilidad y la arquitectura distribuida de Git, puedes trabajar como de costumbre, pero disfrutando de las ventajas adicionales de Git, algunas de las cuales puede que ni siquiera supieras que necesitabas.


---
- Ver [[Tutorial de GIT]] 
- Ver [[GIT cheat sheet]] 
- Ver [[Git bash]] 
- Ver [[Taller GIT para la clase]] 





![[Pasted image 20240930213728.png]]
USB Memory

