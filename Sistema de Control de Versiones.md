.
https://www.atlassian.com/es/git/tutorials/what-is-version-control

También conocido como "control de código fuente", es la práctica de ==rastrear y gestionar los cambios en el código de software==. 

Los sistemas de control de versiones son herramientas de software que ayudan a los equipos de software a gestionar los cambios en el código fuente a lo largo del tiempo. 

A medida que los entornos de desarrollo se aceleran, los sistemas de control de versiones ayudan a los equipos de software a trabajar de forma más rápida e inteligente. Son especialmente útiles para los equipos de [[DevOps]], ya que les ayudan a reducir el tiempo de desarrollo y a aumentar las implementaciones exitosas.

El software de control de versiones realiza un ==seguimiento de todas las modificaciones en el código en un tipo especial de base de datos==. Si se comete un error, los desarrolladores pueden ir hacia atrás en el tiempo y comparar las versiones anteriores del código para ayudar a resolver el error, al tiempo que se minimizan las interrupciones para todos los miembros del equipo.

Para casi todos los proyectos de software, el código fuente es como las ==joyas de la corona==, un activo valioso cuyo valor debe protegerse. 

Para la mayoría de equipos de software, el código fuente es un repositorio del conocimiento de valor incalculable y de la comprensión sobre el dominio del problema que los desarrolladores han recopilado y perfeccionado con un esfuerzo cuidadoso. 

El control de versiones protege el código fuente tanto de las catástrofes como del deterioro casual de los errores humanos y las consecuencias accidentales.

Los desarrolladores de software que trabajan en equipos están escribiendo continuamente nuevo código fuente y cambiando el que ya existe. El código de un proyecto, una aplicación o un componente de software normalmente se organiza en una estructura de carpetas o "árbol de archivos". Un desarrollador del equipo podría estar trabajando en una nueva función mientras otro desarrollador soluciona un error no relacionado cambiando código. Cada desarrollador podría hacer sus cambios en varias partes del árbol de archivos.

El control de versiones ayuda a los equipos a resolver este tipo de problemas al realizar un ==seguimiento de todos los cambios individuales de cada colaborador== y al contribuir a evitar que el trabajo concurrente entre en conflicto. Los cambios realizados en una parte del software pueden ser incompatibles con los que ha hecho otro desarrollador que está trabajando al mismo tiempo.  Este problema debería detectarse y solucionarse de manera ordenada sin bloquear el trabajo del resto del equipo. Además, en todo el desarrollo de software, cualquier cambio puede introducir nuevos errores por sí mismo y el nuevo software no es fiable hasta que se prueba. De este modo, las pruebas y el desarrollo van de la mano hasta que está lista una nueva versión.

Un buen software de control de versiones soporta el flujo de trabajo preferido de un desarrollador sin imponer una forma determinada de trabajar. Idealmente, también funciona en cualquier plataforma, en vez de ordenar qué sistema operativo o cadena de herramientas deben utilizar los desarrolladores. Los sistemas de control de versiones excepcionales facilitan un flujo sencillo y continuo de cambios en el código en vez del mecanismo frustrante y burdo del bloqueo de archivos, que da luz verde a un desarrollador a expensas de bloquear el progreso de los demás.

Los equipos de software que no utilizan ninguna forma de control de versiones a menudo se encuentran con problemas como no saber qué cambios que se han hecho están disponibles para los usuarios o la creación de cambios incompatibles entre dos partes no relacionadas que tienen que desvincularse y revisarse exhaustivamente. 

Si eres un desarrollador que nunca ha utilizado el control de versiones, puede que hayas añadido versiones a tus archivos, quizás con sufijos como =="final" o "más reciente"==, y que después hayas tenido que enfrentarte con una nueva versión final. 

Quizás ==has convertido en comentarios bloques de código==, porque quieres desactivar una determinada función sin eliminar el código, con el miedo de que pueda utilizarse más adelante. El control de versiones es una forma de solucionar estos problemas.

El software de control de versiones es una parte esencial del día a día de las prácticas profesionales del equipo de software moderno. Los desarrolladores de software individuales que están acostumbrados a trabajar con un sistema de control de versiones potente en sus equipos suelen reconocer el increíble valor que el control de versiones también les da incluso en los proyectos pequeños en los que trabajan solos. Una vez acostumbrados a las potentes ventajas de los sistemas de control de versiones, ==muchos desarrolladores no se plantearían trabajar sin ellos incluso para los proyectos que no son de software==.

## Ventajas de los sistemas de control de versiones

---

Utilizar un software de control de versiones es una práctica recomendada para los equipos de software y de [[DevOps]] de ==alto rendimiento==. El control de versiones también ayuda a los desarrolladores a moverse más rápido y permite que los equipos de software mantengan la eficiencia y la agilidad a medida que el equipo se ==escala== para incluir más desarrolladores.

Los sistemas de control de versiones (**VCS**) han experimentado grandes mejoras en las últimas décadas y algunos son mejores que otros. 

Los **VCS** a veces se conocen como herramientas de **SCM** (Gestión del código fuente) o **RCS** (Sistema de control de revisiones). Una de las herramientas de VCS más populares hoy en día se llama [[GIT]]. 

Git es un VCS _distribuido_, una categoría conocida como **DVCS**, que explicaremos con más detalle después. Al igual que muchos de los sistemas de VCS más populares disponibles hoy en día, Git es gratuito y de código abierto. Independientemente del nombre que tengan, o del sistema que se utilice, las principales ventajas que deberías esperar del control de versiones son las siguientes.

1. <u>Un completo historial de cambios a largo plazo de todos los archivos</u>. Esto quiere decir todos los cambios realizados por muchas personas a lo largo de los años. Los cambios incluyen la creación y la eliminación de los archivos, así como los cambios de sus contenidos. Las diferentes herramientas de VCS difieren en lo bien que gestionan el cambio de nombre y el movimiento de los archivos. Este historial también debería incluir el autor, la fecha y notas escritas sobre el propósito de cada cambio. Tener el historial completo permite volver a las versiones anteriores para ayudar a analizar la causa raíz de los errores y es crucial cuando se tiene que solucionar problemas en las versiones anteriores del software. Si se está trabajando de forma activa en el software, casi todo puede considerarse una "versión anterior" del software.

2. <u>Creación de ramas y fusiones</u>. Si se tiene a miembros del equipo trabajando al mismo tiempo, es algo evidente; pero incluso las personas que trabajan solas pueden beneficiarse de la capacidad de trabajar en flujos independientes de cambios. La creación de una "rama" en las herramientas de VCS mantiene múltiples flujos de trabajo independientes los unos de los otros al tiempo que ofrece la facilidad de volver a fusionar ese trabajo, lo que permite que los desarrolladores verifiquen que los cambios de cada rama no entran en conflicto. Muchos equipos de software adoptan la práctica de crear ramas para cada función o quizás para cada publicación, o ambas. Existen muchos flujos de trabajo diferentes que los equipos pueden elegir cuando deciden cómo utilizar la creación de las ramas y las fusiones en VCS.

3. <u>Trazabilidad</u>. Ser capaz de trazar cada cambio que se hace en el software y conectarlo con un software de gestión de proyectos y seguimiento de errores como [Jira](https://www.atlassian.com/es/software/jira), además de ser capaz de anotar cada cambio con un mensaje que describa el propósito y el objetivo del cambio, no solo te ayuda con el análisis de la causa raíz y la recopilación de información. Tener el historial anotado del código a tu alcance cuando estás leyendo el código, intentando entender lo que hace y por qué se ha diseñado así, puede permitir a los desarrolladores hacer cambios correctos y que estén en línea con el diseño previsto a largo plazo del sistema. Esto puede ser especialmente importante para trabajar de manera eficaz con código heredado y es esencial para que los desarrolladores puedan calcular el trabajo futuro con precisión.

==Aunque se puede desarrollar software sin utilizar ningún control de versiones, hacerlo somete al proyecto a un gran riesgo que ningún equipo profesional debería aceptar. Así que la pregunta no es si utilizar el control de versiones, sino qué sistema de control de versiones usar.==

Hay muchas opciones, pero aquí vamos a centrarnos solo en una, [[GIT]] . Obtén más información sobre otros tipos de [[Software de control de versiones]]. 

- Ver [[GIT]] 