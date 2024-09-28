.
- Ver https://youtu.be/362sHaO5eGU <
- Ver https://openwebinars.net/blog/contenedores-de-software-que-son-y-que-ventajas-ofrecen/

## Qué son los contenedores?

Los contenedores, en esencia, son <u>procesos</u> que corren dentro del sistema operativo los cuáles cumplen con algunas características que los hacen “especiales”. Comparten el ecosistema junto con procesos “comunes” y es gracias al [[KERNEL]] de Linux que, mediante algunas características de este, brinda a estos procesos, capacidades notables.

Un contenedor es un proceso que corre aislado de otros contenedores, incluso también se ejecuta aislado de otros procesos “comunes”, y es por medio de una estructura del KERNEL llamada [[Namespaces]] que proporciona esta capacidad. Además, cuando es deseable limitar y controlar el acceso a recursos de cómputo tales como CPU o memoria, el KERNEL de Linux proporciona una característica llamado [[controlGroups]] o [[cgroups]] que brinda esta posibilidad.

En su expresión más básica, un contenedor no es más que **cgroups** y **namespaces** junto con otras estructuras como [[seccomp]] para limitar algunas llamadas al sistema y controles de acceso mandatorios, tales como [[SELinux]] o [[AppArmor]].


## Historia de los contenedores

Si bien los contenedores se han vuelto populares en los últimos años, lo cierto es que no es una tecnología nueva, de hecho, la estrategia de aislar y segmentar procesos viene desde hace muchos años. Este es el timeline de eventos que derivaron en lo que hoy conocemos como “Contenedores”.

- En **1999** FreeBSD incorpora el término “**Jails**” que es un mecanismo para crear “mini sistemas” que comparten el mismo KERNEL.

- En **2001** Linux-VServer se desarrolla y proporciona un mecanismo para **virtualizar** a nivel del Sistema Operativo.

- En **2004** Solaris introduce el concepto de **snapshots** con “Solaris Zones”.

- En **2006** Google introduce el término conocido como “[[cgroups]]” o “[[controlGroups]]”.

- En **2008** Red Hat introdujo a los “**Namespaces**”.

- En **2008** además, IBM crea el proyecto LxC, también conocido como “**Linux Containers**”, que provee una serie de herramientas para trabajar con “cgroups” y “namespaces”.

- En **2013**, finalmente, **Docker** introduce herramientas que simplifican y masifican la creación de Contenedores y aparece un nuevo término; el de “**Imagen**”.


Como verán, los contenedores no son una tecnología “nueva” sino por el contrario, es el resultado de varios años de experiencia en la segmentación de cargas de trabajo, separación y aislación de aplicaciones.

- Ver [[Virtualización]] 

## Ventajas de los contenedores

No cabe duda que los contenedores han revolucionado la forma en que se empaqueta y entrega el software y que muchas son las ventajas respecto al modelo tradicional de despliegue de aplicaciones basados en máquinas virtuales, desde la simplicidad hasta la portabilidad.

Para mencionar algunas de las ventajas más notables, tenemos:

- Los contenedores son **livianos** puesto que solo involucra al proceso de la aplicación y nada más.

- Se dice que los contenedores son más **densos**, en el sentido de cantidad, por cada Máquina Virtual, podemos tener N contenedores.

- Son **portables** entre ambientes. El código usado para desplegar un contenedor puede ser replicado N veces.

- Los contenedores son **inmutables**. Es decir, que perderemos todo cambio realizado directamente sobre el contenedor luego de que el proceso finaliza abruptamente o por orden del usuario. De esta forma, se mejora notablemente la estabilidad del servicio prestado.

- Son **escalables**. Podemos tener N cantidad de réplicas del mismo servicio creando más contenedores, con muy bajo esfuerzo.

- Son **seguros**. Si se siguen las buenas prácticas, brindan un entorno de ejecución limitado, por lo que si la aplicación o servicio que ejecuta ese contenedor se ve comprometido, el sistema subyacente no se vería afectado.

## Contenedores vs Máquinas Virtuales

Las máquinas virtuales y los contenedores difieren en muchos aspectos. El primero y quizás el más notorio, es que ==las máquinas virtuales son creadas con un subconjunto de recursos de cómputo del hardware físico, es decir, por cada máquina virtual obtenemos un pool de recursos como RAM, CPU, Disco, etc. El hipervisor es el encargado de gestionar tanto los recursos físicos como los recursos virtuales provistos.==

Cada máquina virtual se despliega con un sistema operativo con sus librerías y dependencias necesarias para luego poder instalar las aplicaciones que dicha máquina va a servir.

![[Pasted image 20240922195749.png]]


Los contenedores, en cambio, como ya lo hemos mencionado, están a un nivel de abstracción mucho más alto, por lo que el concepto de hardware virtual es desconocido para estos procesos especiales. ==Los contenedores pueden correr en servidores virtuales o físicos indistintamente==, obteniendo el mismo resultado, lo único que necesitan es un entorno de ejecución y un KERNEL de Linux.  
Si se siguen las buenas prácticas, un contenedor solo debería estar compuesto por el proceso de la aplicación y las dependencias necesarias, nada más.

Mientras que el [[Hipervisor]] es el encargado de gestionar las máquinas virtuales, junto a los contenedores existe un gestor llamado “[[Container Engine]]” que se encarga de dialogar con las estructuras del KERNEL correspondientes.

![[Pasted image 20240922195808.png]]

## Uso de los contenedores

Los contenedores han sido una de las piezas de tecnología más importantes en los últimos tiempos gracias al movimiento [[DevOps]] y a las distintas estrategias de arquitectura de software para ensamblar aplicaciones **cloud** nativas, en gran medida por su versatilidad y practicidad, aunque cualquiera sea la necesidad, es posible que podamos emplear contenedores.

Entre los casos más destacados, tenemos:

- **Aplicaciones basadas en microservicios:** Cada microservicio se ejecuta como una unidad lógica de negocio independiente de otros microservicios. Los contenedores son la mejor pieza de infraestructura para alojar a estos microservicios y lograr esa independencia.
    
- **Ambientes de desarrollo basados en ciclos de [[CI]]/[[CD]]:** Los ciclos de integración continua y despliegue / delivery continuo, son uno de los procesos emblema del movimiento [[DevOps]]. El uso de contenedores en este proceso, ==habilita a los equipos DevOps en la creación de ambientes homogéneos y repetibles, a prueba de errores e integrados con herramientas para complementar el ecosistema.==
    
- **Escalabilidad horizontal manual o automática:** Una propiedad embebida del software encargado de gestionar contenedores, es la posibilidad de ==crearlos bajo demanda ==y con las mismas prestaciones. Esta característica es de las más explotadas en [[Aplicaciones cloud]] nativas donde la elasticidad es requerida para aumentar la cantidad de contenedores para soportar los picos de consumo y bajar la cantidad cuando el consumo se estabiliza.
    
- **Inmutabilidad en la infraestructura desplegada:** Los contenedores se crean a partir de unos binarios llamados **imágenes**. El ensamblado de estos binarios es, probablemente, la tarea más importante del [[SRE]] o [[DevOps]] y gracias a cómo están diseñadas las imágenes, los contenedores que se crean son efímeros, es decir, los cambios que hagamos dentro se perderán junto con este, por lo que, cualquier cambio que queramos hacer, debemos de efectuarlo a nivel de la imagen.
    
- **[[Ambientes de sandbox]] y controlados:** Los equipos de SRE, DevOps e incluso de Desarrollo, a menudo necesitan desplegar ==ambientes descartables de forma rápida==. Los contenedores habilitan la creación de estos ambientes. Existen repositorios de imágenes oficiales y de terceros, con un ==vasto catálogo de productos y software que podemos usar como base==, y de ser necesario, también podemos armar nuestro propio binario.
    
- **Refactorización y/o modernización de las [[Aplicaciones legacy]]:** Ya sea que estemos estudiando y analizando cómo modernizar una aplicación desarrollada sobre tecnologías obsoletas o iniciando el camino hacia la adopción de tecnologías de Cloud, los contenedores son una pieza de software que articulan el cambio. Su versatilidad aporta al proceso la posibilidad de dividir en etapas el proyecto, donde cada incremento puede ser por componente o funcionalidad, de hecho, podemos acoplar componentes refactorizados a componentes legacy. Un ejemplo son las aplicaciones del sector bancario, donde por un lado tenemos al **core** desarrollado en lenguajes con bastantes años y funcionando sobre hardware que ya casi no se fabrica y por el otro, el **home banking** desarrollado en tecnologías y frameworks más modernos y corriendo sobre infraestructura de cloud.
    
- **Automatización de los despliegues de infraestructura:** Los contenedores son emblema en el mundo de la “Infraestructura como Código” [[IaC]], y en parte esto es porque creamos y desplegamos contenedores de forma automatizada y usando código en distintas herramientas como [[Terraform]] o [[Ansible]]. Lo cierto es que, no importa cuál es el ambiente que deseamos ensamblar, con la elección de las herramientas correctas, podemos desplegar infraestructura rápidamente usando código. Este grado de flexibilidad permite responder rápidamente frente a cambios en el negocio.
    

## Orquestación de contenedores

Antes de hablar sobre cómo orquestar contenedores, debemos de hablar de qué tareas están involucradas en la gestión de éstos. A menudo las organizaciones que están comenzando a transitar el camino hacia el uso de tecnologías basadas en contenedores, el punto de partida es lo que se conoce como un ¨Container host¨ que no es más que una máquina virtual o física con el software instalado para trabajar con contenedores.

La gestión de estos está delegada en un componente de software llamado **[[Container Engine]]** cuya función es la de recibir las peticiones del usuario y delegar a las distintas primitivas las operaciones que se pueden efectuar, tales como crear y detener contenedores, descargar imágenes, pushear imágenes al catálogo, etc.

Gracias a este motor, la complejidad que supone trabajar con las estructuras del KERNEL, pasa a ser una tarea accesible para desarrolladores y equipos DevOps. En parte, el éxito de la tecnología se debe a esto.

Existen varios motores de contenedores, con distintas características y prestaciones, entre los más populares tenemos:

- [[Docker]] 
- [[Podman]] 
- [[CRI-O]] 
- [[LxC]] 

Internamente, y a modo de ejemplificar, el **Container Engine** tiene esta arquitectura:

![[Pasted image 20240922195836.png]]

- El usuario ejecuta la orden de operación, por ejemplo, `crear un contenedor`.
- El `container engine` recibe la petición.
- El `container engine`, mediante librerías y binarios se fija si la imagen existe localmente.
- Si no existe, va al `catálogo de imágenes` y hace un **pull** de la misma.
- Luego va contra al KERNEL para instanciar el proceso
- El proceso dentro del contenedor se inicia.

Por supuesto que el flujo, a bajo nivel, es un poco más complejo, sobre todo si hacemos “doble click” en los componentes que hacen al motor de contenedores y además de que depende del motor que usemos, ya que no es lo mismo usar Docker que Podman, pero sin duda que sirve para ilustrar como es el proceso desde que el usuario ingresa la orden y se crea el contenedor.

Ahora que ya hemos definido que es un **Container Engine**, podemos hacernos la siguiente pregunta. ¿Es suficiente con un **[[Motor de Contenedores]]**? La respuesta correcta es: Tal vez, si tenemos pocos contenedores. Depende del grado de madurez en la tecnología, 10 contenedores pueden ser pocos o muchísimos.

Lo cierto es que, cuando empezamos a hacernos algunas de las siguientes preguntas, estamos evidenciando la necesidad de evaluar herramientas que complementen al motor de contenedores.

- ¿Cómo escala mi aplicación?
- ¿Cómo evitamos conflictos de puertos en un host?
- ¿Cómo distribuimos cargas de trabajo en varios hosts?
- ¿Cómo garantizamos que un contenedor va a estar en ejecución?
- ¿Cómo gestionamos el ciclo de vida del contenedor?
- ¿Cómo encuentro un contenedor en un grupo de hosts?

A medida que las aplicaciones van creciendo y la adopción de contenedores se hace más fuerte se hacen necesarias herramientas para automatizar el mantenimiento: reemplazo de contenedores fallidos o auto-recuperación de los mismos, cambios en las configuraciones, updates periódicos, manejo de escalamiento horizontal y vertical bajo demanda, y mucho más.

Este software se le conoce como [[Orquestador de Contenedores]]. Ejemplos de orquestadores pueden ser:

- [[Kubernetes]] (a.k.a [[k8s]] o simplemente [[Kube]])
- [[Docker Swarm]] 
- [[Mesos]] 

De los mencionados, sin duda el más popular es **_Kubernetes_** al punto de convertirse en el estándar de facto de la industria en lo que manejo de contenedores a gran escala se refiere. Tan es así que los principales proveedores de Cloud Pública tienen servicios gestionados basados en Kubernetes.

Kubernetes es un proyecto Open Source liberado a la comunidad por Google en el año 2014 y derivado del proyecto Borg, ampliamente probado en el manejo de cargas de trabajo contenerizadas y desde entonces varias comunidades del ecosistema Open Source han puesto mucho foco en soportar esta plataforma, adaptando o incluso re-diseñando aplicaciones para que corran sobre Kubernetes.


- [[Taller Docker]] <

---









---
- Ver https://www.ibm.com/es-es/topics/containers

**Publicado:** 9 de mayo de 2024  
**Colaboradores:** Stephanie Susnjara, Ian Smalley

¿Qué son los contenedores?

Los contenedores son unidades ejecutables de software que empaquetan el código de la aplicación junto con sus bibliotecas y dependencias. Permiten que el código se ejecute en cualquier entorno informático, ya sea de sobremesa, TI tradicional o infraestructura en la nube.

Los contenedores se benefician de una forma de virtualización del sistema operativo (SO) en la que se pueden utilizar características del núcleo del SO (por ejemplo, los espacios de nombres y cgroups de Linux, los silos y objetos de trabajo de Windows) para aislar procesos y controlar la cantidad de CPU, memoria y disco a la que pueden acceder dichos procesos.

Más portátil y eficiente de recursos que [las máquinas virtuales (VM)](https://www.ibm.com/es-es/topics/virtual-machines), los contenedores se han convertido en las unidades de computación de facto modernas de las aplicaciones modernas. Además, los contenedores son fundamentales para la [infraestructura de TI](https://www.ibm.com/es-es/topics/infrastructure) subyacente que impulsa los entornos híbridos multinube: la combinación de instalaciones locales, [nube privada](https://www.ibm.com/es-es/topics/private-cloud), [nube pública](https://www.ibm.com/es-es/topics/public-cloud) y más de un servicio en la nube de más de un proveedor de nubes.

Según un informe de Business Research Insights1, el mercado mundial de tecnología de contenedores se valoró en 496,4 millones de dólares en 2021 y se espera que alcance los 3123,42 millones de dólares en 2031, con una tasa de crecimiento anual compuesta (CAGR) del 19,8 %.

GuíaLa modernización estratégica de las aplicaciones impulsa la transformación digital

La modernización estratégica de las aplicaciones es una de las claves del éxito de la transformación capaz de aumentar los ingresos anuales y reducir los costes de mantenimiento y funcionamiento.

Contenedores frente a Virtual Machines

Una forma de comprender mejor un contenedor es examinar en qué se diferencia de una [máquina virtual (VM)](https://www.ibm.com/es-es/topics/virtual-machines) tradicional, que es una representación virtual o emulación de un ordenador físico. Una máquina virtual suele denominarse invitado, mientras que la máquina física en la que se ejecuta se llama host.

La tecnología de [virtualización](https://www.ibm.com/es-es/topics/virtualization) hace posible las VM. Un [hipervisor,](https://www.ibm.com/es-es/topics/hypervisors) una pequeña capa de software, asigna recursos informáticos físicos (por ejemplo, procesadores, memoria, almacenamiento) a cada VM. Mantiene cada máquina virtual separada de las demás para que no interfieran entre sí. A continuación, cada VM contiene un sistema operativo invitado y una copia virtual del hardware que el sistema operativo necesita para ejecutarse, junto con una aplicación y sus bibliotecas y dependencias asociadas. [VMware](https://www.ibm.com/es-es/topics/vmware) fue uno de los primeros en desarrollar y comercializar la tecnología de virtualización basada en hipervisores.  

En lugar de virtualizar el hardware subyacente, la tecnología de contenedores virtualiza el sistema operativo (normalmente Linux) para que cada contenedor contenga _solo_ la aplicación y sus bibliotecas, archivos de configuración y dependencias. Precisamente por la ausencia del sistema operativo invitado, los contenedores son tan ligeros y, por tanto, más rápidos y portátiles que las VM.

Los contenedores y las máquinas virtuales no se excluyen mutuamente. Por ejemplo, una organización podría aprovechar ambas tecnologías ejecutando contenedores en máquinas virtuales para aumentar el aislamiento y la seguridad y aprovechar las herramientas ya instaladas para la [automatización](https://www.ibm.com/es-es/topics/automation), las copias de seguridad y la monitorización. 

Para obtener una visión más profunda de esta comparación, consulte "[Contenedores versus máquinas virtuales: ¿cuál es la diferencia?](https://www.ibm.com/es-es/think/topics/containers-vs-vms)" y mire el vídeo:

![Containers vs VMs: What’s the difference?](https://cdnsecakmi.kaltura.com/p/1773841/thumbnail/entry_id/1_uxewadch/width/640)

Containers vs VMs: What’s the difference? (7:59)

Principales beneficios de los contenedores

La principal ventaja de los contenedores, especialmente en comparación con una máquina virtual, es que proporcionan un nivel de abstracción que los hace ligeros y portátiles. Entre sus principales beneficios se incluyen estos:

#### Ligero

Los contenedores comparten el núcleo del sistema operativo de la máquina, lo que elimina la necesidad de una instancia completa del sistema operativo por aplicación y hace que los archivos de los contenedores sean pequeños y consuman pocos recursos. El reducido tamaño de un contenedor, especialmente en comparación con una máquina virtual, significa que puede iniciarse rápidamente y soportar mejor [aplicaciones nativa en la nube](https://www.ibm.com/es-es/topics/cloud-native) que escalan horizontalmente.

#### Portátil e independiente de la plataforma

Los contenedores llevan consigo todas sus dependencias, lo que significa que el software puede escribirse una vez y luego ejecutarse sin necesidad de reconfigurarlo en distintos entornos informáticos (por ejemplo, portátiles, nube y en las instalaciones).

#### Apoyo al desarrollo y la arquitectura modernos

Gracias a su portabilidad y coherencia de despliegue en distintas plataformas y a su reducido tamaño, los contenedores son ideales para el desarrollo moderno y los patrones de aplicación, como [DevOps](https://www.ibm.com/es-es/topics/devops), [serverless](https://www.ibm.com/es-es/topics/serverless) y [microservicios](https://www.ibm.com/es-es/topics/microservices), que se construyen gracias a implementaciones incrementales y regulares de pequeñas porciones de código.

#### Utilización mejorada

Al igual que las máquinas virtuales, los contenedores permiten a los desarrolladores y operadores mejorar el uso de la CPU y la memoria de las máquinas físicas. Los contenedores van incluso más allá porque permiten [una arquitectura de microservicios](https://www.ibm.com/es-es/products/cloud-pak-for-applications) para que los componentes de la aplicación puedan implementarse y escalarse de forma más granular.Es una alternativa atractiva a la ampliación de toda una aplicación monolítica, ya que un solo componente tiene problemas con su carga.

#### Plazos de comercialización más cortos

Los contenedores dependen menos de los recursos del sistema, lo que los hace más rápidos de administrar e implementar que las máquinas virtuales. Esta función ayuda a ahorrar dinero y tiempo en la implementación de aplicaciones y optimiza el tiempo de comercialización. 

En una encuesta de IBM, los desarrolladores y ejecutivos de TI informaron de muchos otros beneficios de los contenedores. Consulte el informe completo: [Containers in the enterprise](https://www.ibm.com/downloads/cas/VG8KRPRM).

¿Qué es la contenerización?

Los contenedores dependen de la [contenerización](https://www.ibm.com/es-es/topics/containerization), el empaquetado del código de software con solo el sistema operativo (SO) y sus variables de entorno relevantes, archivos de configuración, bibliotecas y dependencias de software.

El resultado es una imagen de contenedor que se ejecuta en una plataforma de contenedor. Una imagen de contenedor representa datos binarios que encapsulan una aplicación y todas sus dependencias de software. 

La contenerización permite que las aplicaciones se "escriban una vez y se ejecuten en cualquier lugar", lo que proporciona portabilidad, acelera el proceso de desarrollo, evita la dependencia de un proveedor de la nube, etc. 

### La evolución de la contenerización

La contenerización y el aislamiento de procesos existen desde hace décadas2. Un momento histórico en el desarrollo de contenedores se produjo en 1979 con el desarrollo de chroot, parte de la versión 7 del sistema operativo Unix. Chroot introdujo el concepto de aislamiento de procesos al restringir el acceso a los archivos de una aplicación a un directorio específico (la raíz) y sus hijos (o subprocesos).

Otro hito importante ocurrió en 2008, cuando se implementaron contenedores de Linux (LXC) en el kernel de Linux, lo que permitió completamente la virtualización para una sola instancia de Linux. A lo largo de los años, tecnologías como las cárceles de FreeBSD y las particiones de carga de trabajo de AIX han ofrecido una virtualización similar a nivel de sistema operativo.

Aunque LXC sigue siendo un motor de tiempo de ejecución muy conocido y forma parte del proyecto3, independiente de la distribución y el proveedor de Linux, existen tecnologías del núcleo de Linux más recientes. Ubuntu, un moderno sistema operativo Linux de código abierto, también ofrece esta posibilidad. 

Vea el vídeo para profundizar en la contenerización:

![Containerization Explained](https://cdnsecakmi.kaltura.com/p/1773841/thumbnail/entry_id/1_89e49wds/width/648)

Containerization Explained (8:08)

### Docker y la era moderna de los contenedores

La mayoría de los desarrolladores buscan 2013 como el comienzo de la era moderna de los contenedores con la introducción de [Docker](https://www.ibm.com/es-es/topics/docker). Una plataforma de software de contenerización de código abierto que funciona como [plataforma como servicio (PaaS)](https://www.ibm.com/es-es/topics/paas), Docker permite a los desarrolladores crear, implementar, ejecutar, actualizar y gestionar contenedores.  

Docker utiliza el kernel de Linux (el componente base del sistema operativo) y las características del kernel (como Cgroups y espacios de nombres) para separar los procesos y que puedan ejecutarse de forma independiente. Docker esencialmente toma una aplicación y sus dependencias y las convierte en un contenedor virtual que puede ejecutarse en cualquier sistema informático que ejecute Windows, macOS o Linux.

Docker se basa en una arquitectura cliente-servidor, con Docker Engine como tecnología subyacente. Docker proporciona un modelo de implementación basado en imágenes, lo que simplifica el uso compartido de aplicaciones en entornos informáticos. 

Para aclarar cualquier confusión, el nombre de la plataforma de contenedores Docker también se refiere a Docker, Inc.4, que desarrolla herramientas de productividad creadas en torno a su plataforma de contenerización de código abierto y al ecosistema y comunidad de código abierto Docker5.

En 2015, Docker y otros líderes del sector de los contenedores crearon The Open Container Initiative6 , que forma parte de la Fundación Linux, una estructura de gobierno abierta con el propósito expreso de crear estándares industriales abiertos en torno a los formatos de contenedores y los entornos de ejecución.

Docker es la herramienta de contenerización más utilizada, con una cuota de mercado del 82,84 %7.

[[Orquestación de contenedores]] 

---


- Ver https://www.redhat.com/es/topics/containers
- Ver https://azure.microsoft.com/es-mx/resources/cloud-computing-dictionary/what-is-a-container
- Ver https://www.hpe.com/lamerica/es/what-is/containers.html

---

- Ver https://www.netapp.com/es/devops-solutions/what-are-containers/

Los contenedores son una forma de virtualización del sistema operativo. Un solo contenedor se puede usar para ejecutar cualquier cosa, desde un microservicio o un proceso de software a una aplicación de mayor tamaño. Dentro de un contenedor se encuentran todos los ejecutables, el código binario, las bibliotecas y los archivos de configuración necesarios. Sin embargo, en comparación con los métodos de virtualización de máquinas o servidores, los contenedores no contienen imágenes del sistema operativo. Esto los hace más ligeros y portátiles, con una sobrecarga significativamente menor. En implementaciones de aplicaciones de mayor tamaño, se pueden poner en marcha varios contenedores como uno o varios clústeres de contenedores. Estos clústeres se pueden gestionar mediante un orquestador de contenedores, como Kubernetes.

## Beneficios de los contenedores

Los contenedores son una forma optimizada de crear, probar, poner en marcha y volver a poner en marcha aplicaciones en varios entornos, desde un portátil local de un desarrollador hasta un centro de datos on-premises e incluso en la nube. Algunos de los beneficios de los contenedores son:

- **Menos sobrecarga  
    **Los contenedores requieren menos recursos del sistema que los entornos de máquinas virtuales tradicionales o de hardware porque no incluyen imágenes del sistema operativo.  
    
- **Mayor portabilidad  
    **Las aplicaciones que se ejecutan en contenedores se pueden poner en marcha fácilmente en sistemas operativos y plataformas de hardware diferentes.  
    
- **Operativa más consistente  
    **Los equipos de DevOps saben que las aplicaciones en contenedores van a ejecutarse igual, independientemente de dónde se pongan en marcha.

- **Mayor eficiencia  
    **Los contenedores permiten poner en marcha, aplicar parches o escalar las aplicaciones con mayor rapidez.

- **Mejor desarrollo de aplicaciones  
    **Los contenedores respaldan los esfuerzos ágiles y de DevOps para acelerar los ciclos de desarrollo, prueba y producción.

## Casos de uso de contenedores

Estas son algunas de las formas más habituales en las que las organizaciones usan los contenedores:

- **Rehospedaje de las aplicaciones existentes en arquitecturas de nube modernas  
    **Algunas organizaciones utilizan contenedores para migrar las aplicaciones existentes a entornos más modernos. Aunque esta práctica ofrece algunos de los beneficios básicos de la virtualización de sistemas operativos, no ofrece todas las ventajas de una arquitectura de aplicaciones modular basada en contenedores.
- **Refactorización de las aplicaciones existentes para contenedores  
    **Aunque la refactorización requiere mucho más que la migración del rehospedaje, ofrece todos los beneficios de un entorno de contenedores.
- **Desarrollo de nuevas aplicaciones nativas del contenedor  
    **Al igual que la refactorización, este método permite disfrutar de todos los beneficios de los contenedores.
- **Más compatibilidad con las arquitecturas de microservicios  
    **Las aplicaciones distribuidas y los microservicios se pueden aislar, poner en marcha y escalar más fácilmente utilizando elementos básicos de contenedores individuales.
- **Soporte de DevOps para la integración y la puesta en marcha continuas (CI/CD)  
    **La tecnología de contenedores permite la creación, la prueba y la puesta en marcha optimizadas a partir de las mismas imágenes de contenedores.
- **Una puesta en marcha más sencilla de tareas y trabajos repetitivos  
    **Los contenedores se ponen en marcha para dar soporte a uno o varios procesos parecidos que, a menudo, se ejecutan en segundo plano, como las funciones ETL o los lotes de tareas.

## ¿Qué relación tienen Docker y Kubernetes con los contenedores?

Probablemente, los usuarios que trabajen en entornos de contenedores conozcan dos herramientas y plataformas muy conocidas que se utilizan para crear y gestionar contenedores. Estas herramientas son Docker y Kubernetes.

Docker es un popular entorno en tiempo de ejecución que se usa para crear y construir software dentro de contenedores. Usa imágenes de Docker (instantáneas de copia en escritura) para poner en marcha aplicaciones o software en contenedores en varios entornos, desde el desarrollo hasta las pruebas y la producción. Docker se basa en estándares abiertos y funciona en la mayoría de los entornos operativos más comunes, incluidos Linux, Microsoft Windows y otras infraestructuras locales o basadas en la nube.

Sin embargo, las aplicaciones en contenedores pueden ser complicadas. Durante la producción, muchas pueden requerir cientos o miles de contenedores independientes. Es en este punto donde los entornos en tiempo de ejecución de contenedores, como Docker, se benefician del uso de otras herramientas para orquestar o gestionar todos los contenedores en funcionamiento.

Una de las herramientas más populares para este fin es Kubernetes, un orquestador de contenedores que reconoce varios entornos en tiempo de ejecución de contenedores, incluido Docker.

Kubernetes orquesta el funcionamiento de varios contenedores juntos de forma armónica. Gestiona áreas como el uso de recursos de infraestructura subyacentes para aplicaciones en contenedores (por ejemplo, la cantidad de recursos de computación, red y almacenamiento necesarios). Las herramientas de orquestación como Kubernetes facilitan la automatización y el escalado de cargas de trabajo basadas en contenedores para entornos de producción activos.

## Contenedores frente a máquinas virtuales (VM)

En ocasiones, las personas confunden la tecnología de contenedores con máquinas virtuales (VM) o con la tecnología de virtualización de servidores. Aunque existen algunas similitudes básicas, los contenedores son muy diferentes de las máquinas VM.

Las VM se ejecutan en un entorno de hipervisor en el que cada máquina virtual debe incluir su propio sistema operativo invitado dentro del mismo, junto con sus archivos binarios, bibliotecas y archivos de aplicaciones correspondientes. Esto consume una gran cantidad de recursos y genera mucha sobrecarga, especialmente cuando se ejecutan varias VM en el mismo servidor físico, cada una con su propio sistema operativo invitado.

Por el contrario, cada contenedor comparte el mismo sistema operativo host o kernel del sistema y tiene un tamaño mucho menor, a menudo de solo unos megabytes. Esto suele implicar que un contenedor puede tardar unos segundos en iniciarse (en comparación con los gigabytes y los minutos necesarios que requiere una VM típica).

- [Sigue leyendo las diferencias entre contenedores y máquinas virtuales](https://www.netapp.com/blog/containers-vs-vms/ "Sigue leyendo las diferencias entre contenedores y máquinas virtuales")

## NetApp y contenedores

En NetApp, creemos en la conveniencia de la tecnología de contenedores y trabajamos en herramientas demostradas e innovaciones que ofrezcan y gestionen el almacenamiento persistente de todo tipo de aplicaciones sea cual sea su ubicación. Un ejemplo clave de este trabajo es el desarrollo de Trident. Gracias a Trident, las aplicaciones en contenedores pueden consumir almacenamiento persistente bajo demanda más fácilmente que nunca antes.

Trabajamos activamente en diferentes formas de acelerar DevOps ofreciendo aún más velocidad y agilidad en el desarrollo de software. Debería ser fácil utilizar los recursos de la infraestructura, como almacenamiento. Esto es una prioridad para NetApp, que ofrece soluciones de gestión de contenedores y otras soluciones que ayudan a las aplicaciones a escalar y abarcar una gran variedad de plataformas más fácilmente.

---

- Ver https://docs.docker.com/get-started/workshop/

# Overview of the Docker workshop

This 45-minute workshop contains step-by-step instructions on how to get started with Docker. This workshop shows you how to:

- Build and run an image as a container.
- Share images using Docker Hub.
- Deploy Docker applications using multiple containers with a database.
- Run applications using Docker Compose.

> **Note**
> 
> For a quick introduction to Docker and the benefits of containerizing your applications, see [Getting started](https://docs.docker.com/get-started/introduction/).

## [What is a container?](https://docs.docker.com/get-started/workshop/#what-is-a-container)

A container is a sandboxed process running on a host machine that is isolated from all other processes running on that host machine. That isolation leverages [kernel namespaces and cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), features that have been in Linux for a long time. Docker makes these capabilities approachable and easy to use. To summarize, a container:

- Is a runnable instance of an image. You can create, start, stop, move, or delete a container using the Docker API or CLI.
- Can be run on local machines, virtual machines, or deployed to the cloud.
- Is portable (and can be run on any OS).
- Is isolated from other containers and runs its own software, binaries, configurations, etc.

If you're familiar with `chroot`, then think of a container as an extended version of `chroot`. The filesystem comes from the image. However, a container adds additional isolation not available when using chroot.

## [What is an image?](https://docs.docker.com/get-started/workshop/#what-is-an-image)

A running container uses an isolated filesystem. This isolated filesystem is provided by an image, and the image must contain everything needed to run an application - all dependencies, configurations, scripts, binaries, etc. The image also contains other configurations for the container, such as environment variables, a default command to run, and other metadata.

## [Next steps](https://docs.docker.com/get-started/workshop/#next-steps)

In this section, you learned about containers and images.

Next, you'll containerize a simple application and get hands-on with the concepts.

[Containerize an application](https://docs.docker.com/get-started/workshop/02_our_app/)

# Containerize an application

For the rest of this guide, you'll be working with a simple todo list manager that runs on Node.js. If you're not familiar with Node.js, don't worry. This guide doesn't require any prior experience with JavaScript.

## [Prerequisites](https://docs.docker.com/get-started/workshop/02_our_app/#prerequisites)

- You have installed the latest version of [Docker Desktop](https://docs.docker.com/get-started/get-docker/).
- You have installed a [Git client](https://git-scm.com/downloads).
- You have an IDE or a text editor to edit files. Docker recommends using [Visual Studio Code](https://code.visualstudio.com/).

## [Get the app](https://docs.docker.com/get-started/workshop/02_our_app/#get-the-app)

Before you can run the application, you need to get the application source code onto your machine.

1. Clone the [getting-started-app repository](https://github.com/docker/getting-started-app/tree/main) using the following command:
    
    ```console
    $ git clone https://github.com/docker/getting-started-app.git
    ```
    
2. View the contents of the cloned repository. You should see the following files and sub-directories.
    
    Explain
    
    `├── getting-started-app/ │ ├── .dockerignore │ ├── package.json │ ├── README.md │ ├── spec/ │ ├── src/ │ └── yarn.lock`
    

## [Build the app's image](https://docs.docker.com/get-started/workshop/02_our_app/#build-the-apps-image)

To build the image, you'll need to use a Dockerfile. A Dockerfile is simply a text-based file with no file extension that contains a script of instructions. Docker uses this script to build a container image.

1. In the `getting-started-app` directory, the same location as the `package.json` file, create a file named `Dockerfile`. You can use the following commands to create a Dockerfile based on your operating system.
    
    Mac / Linux / Windows (Git Bash) Windows (Command Prompt) Windows (PowerShell)
    
    ---
    
    In the terminal, run the following commands.
    
    Make sure you're in the `getting-started-app` directory. Replace `/path/to/getting-started-app` with the path to your `getting-started-app` directory.
    
    ```console
    $ cd /path/to/getting-started-app
    ```
    
    Create an empty file named `Dockerfile`.
    
    ```console
    $ touch Dockerfile
    ```
    
    ---
    
2. Using a text editor or code editor, add the following contents to the Dockerfile:
    
    Explain
    
    `# syntax=docker/dockerfile:1 [FROM](https://docs.docker.com/reference/dockerfile/#from "Learn more about the FROM instruction") node:18-alpine [WORKDIR](https://docs.docker.com/reference/dockerfile/#workdir "Learn more about the WORKDIR instruction") /app [COPY](https://docs.docker.com/reference/dockerfile/#copy "Learn more about the COPY instruction") . . [RUN](https://docs.docker.com/reference/dockerfile/#run "Learn more about the RUN instruction") yarn install --production [CMD](https://docs.docker.com/reference/dockerfile/#cmd "Learn more about the CMD instruction") ["node", "src/index.js"] [EXPOSE](https://docs.docker.com/reference/dockerfile/#expose "Learn more about the EXPOSE instruction") 3000`
    
3. Build the image using the following commands:
    
    In the terminal, make sure you're in the `getting-started-app` directory. Replace `/path/to/getting-started-app` with the path to your `getting-started-app` directory.
    
    ```console
    $ cd /path/to/getting-started-app
    ```
    
    Build the image.
    
    ```console
    $ docker build -t getting-started .
    ```
    
    The `docker build` command uses the Dockerfile to build a new image. You might have noticed that Docker downloaded a lot of "layers". This is because you instructed the builder that you wanted to start from the `node:18-alpine` image. But, since you didn't have that on your machine, Docker needed to download the image.
    
    After Docker downloaded the image, the instructions from the Dockerfile copied in your application and used `yarn` to install your application's dependencies. The `CMD` directive specifies the default command to run when starting a container from this image.
    
    Finally, the `-t` flag tags your image. Think of this as a human-readable name for the final image. Since you named the image `getting-started`, you can refer to that image when you run a container.
    
    The `.` at the end of the `docker build` command tells Docker that it should look for the `Dockerfile` in the current directory.
    

## [Start an app container](https://docs.docker.com/get-started/workshop/02_our_app/#start-an-app-container)

Now that you have an image, you can run the application in a container using the `docker run` command.

1. Run your container using the `docker run` command and specify the name of the image you just created:
    
    ```console
    $ docker run -dp 127.0.0.1:3000:3000 getting-started
    ```
    
    The `-d` flag (short for `--detach`) runs the container in the background. This means that Docker starts your container and returns you to the terminal prompt. You can verify that a container is running by viewing it in Docker Dashboard under **Containers**, or by running `docker ps` in the terminal.
    
    The `-p` flag (short for `--publish`) creates a port mapping between the host and the container. The `-p` flag takes a string value in the format of `HOST:CONTAINER`, where `HOST` is the address on the host, and `CONTAINER` is the port on the container. The command publishes the container's port 3000 to `127.0.0.1:3000` (`localhost:3000`) on the host. Without the port mapping, you wouldn't be able to access the application from the host.
    
2. After a few seconds, open your web browser to [http://localhost:3000](http://localhost:3000/). You should see your app.

	
3. Add an item or two and see that it works as you expect. You can mark items as complete and remove them. Your frontend is successfully storing items in the backend.
    

At this point, you have a running todo list manager with a few items.

If you take a quick look at your containers, you should see at least one container running that's using the `getting-started` image and on port `3000`. To see your containers, you can use the CLI or Docker Desktop's graphical interface.

CLI Docker Desktop

---

Run the following `docker ps` command in a terminal to list your containers.

```console
$ docker ps
```

Output similar to the following should appear.

```console
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                      NAMES
df784548666d        getting-started     "docker-entrypoint.s…"   2 minutes ago       Up 2 minutes        127.0.0.1:3000->3000/tcp   priceless_mcclintock
```

---

## [Summary](https://docs.docker.com/get-started/workshop/02_our_app/#summary)

In this section, you learned the basics about creating a Dockerfile to build an image. Once you built an image, you started a container and saw the running app.

Related information:

- [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
- [docker CLI reference](https://docs.docker.com/reference/cli/docker/)

## [Next steps](https://docs.docker.com/get-started/workshop/02_our_app/#next-steps)

Next, you're going to make a modification to your app and learn how to update your running application with a new image. Along the way, you'll learn a few other useful commands.

[Update the application](https://docs.docker.com/get-started/workshop/03_updating_app/)

# Update the application

In [part 1](https://docs.docker.com/get-started/workshop/02_our_app/), you containerized a todo application. In this part, you'll update the application and image. You'll also learn how to stop and remove a container.

## [Update the source code](https://docs.docker.com/get-started/workshop/03_updating_app/#update-the-source-code)

In the following steps, you'll change the "empty text" when you don't have any todo list items to "You have no todo items yet! Add one above!"

1. In the `src/static/js/app.js` file, update line 56 to use the new empty text.
    
    ```diff
    - <p className="text-center">No items yet! Add one above!</p>
    + <p className="text-center">You have no todo items yet! Add one above!</p>
    ```
    
2. Build your updated version of the image, using the `docker build` command.
    
    ```console
    $ docker build -t getting-started .
    ```
    
3. Start a new container using the updated code.
    
    ```console
    $ docker run -dp 127.0.0.1:3000:3000 getting-started
    ```
    

You probably saw an error like this:

```console
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 127.0.0.1:3000 failed: port is already allocated.
```

The error occurred because you aren't able to start the new container while your old container is still running. The reason is that the old container is already using the host's port 3000 and only one process on the machine (containers included) can listen to a specific port. To fix this, you need to remove the old container.

## [Remove the old container](https://docs.docker.com/get-started/workshop/03_updating_app/#remove-the-old-container)

To remove a container, you first need to stop it. Once it has stopped, you can remove it. You can remove the old container using the CLI or Docker Desktop's graphical interface. Choose the option that you're most comfortable with.

CLI Docker Desktop

---

### [Remove a container using the CLI](https://docs.docker.com/get-started/workshop/03_updating_app/#remove-a-container-using-the-cli)

1. Get the ID of the container by using the `docker ps` command.
    
    ```console
    $ docker ps
    ```
    
2. Use the `docker stop` command to stop the container. Replace `<the-container-id>` with the ID from `docker ps`.
    
    ```console
    $ docker stop <the-container-id>
    ```
    
3. Once the container has stopped, you can remove it by using the `docker rm` command.
    
    ```console
    $ docker rm <the-container-id>
    ```
    

> **Note**
> 
> You can stop and remove a container in a single command by adding the `force` flag to the `docker rm` command. For example: `docker rm -f <the-container-id>`

---

### [Start the updated app container](https://docs.docker.com/get-started/workshop/03_updating_app/#start-the-updated-app-container)

1. Now, start your updated app using the `docker run` command.
    
    ```console
    $ docker run -dp 127.0.0.1:3000:3000 getting-started
    ```
    
2. Refresh your browser on [http://localhost:3000](http://localhost:3000/) and you should see your updated help text.
    

## [Summary](https://docs.docker.com/get-started/workshop/03_updating_app/#summary)

In this section, you learned how to update and rebuild a container, as well as how to stop and remove a container.

Related information:

- [docker CLI reference](https://docs.docker.com/reference/cli/docker/)

## [Next steps](https://docs.docker.com/get-started/workshop/03_updating_app/#next-steps)

Next, you'll learn how to share images with others.

[Share the application](https://docs.docker.com/get-started/workshop/04_sharing_app/)

# Share the application

Now that you've built an image, you can share it. To share Docker images, you have to use a Docker registry. The default registry is Docker Hub and is where all of the images you've used have come from.

> **Docker ID**
> 
> A Docker ID lets you access Docker Hub, which is the world's largest library and community for container images. Create a [Docker ID](https://hub.docker.com/signup) for free if you don't have one.

## [Create a repository](https://docs.docker.com/get-started/workshop/04_sharing_app/#create-a-repository)

To push an image, you first need to create a repository on Docker Hub.

1. [Sign up](https://www.docker.com/pricing?utm_source=docker&utm_medium=webreferral&utm_campaign=docs_driven_upgrade) or Sign in to [Docker Hub](https://hub.docker.com/).
    
2. Select the **Create Repository** button.
    
3. For the repository name, use `getting-started`. Make sure the **Visibility** is **Public**.
    
4. Select **Create**.
    

In the following image, you can see an example Docker command from Docker Hub. This command will push to this repository.


## [Push the image](https://docs.docker.com/get-started/workshop/04_sharing_app/#push-the-image)

1. In the command line, run the `docker push` command that you see on Docker Hub. Note that your command will have your Docker ID, not "docker". For example, `docker push YOUR-USER-NAME/getting-started`.
    
    ```console
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```
    
    Why did it fail? The push command was looking for an image named `docker/getting-started`, but didn't find one. If you run `docker image ls`, you won't see one either.
    
    To fix this, you need to tag your existing image you've built to give it another name.
    
2. Sign in to Docker Hub using the command `docker login -u YOUR-USER-NAME`.
    
3. Use the `docker tag` command to give the `getting-started` image a new name. Replace `YOUR-USER-NAME` with your Docker ID.
    
    ```console
    $ docker tag getting-started YOUR-USER-NAME/getting-started
    ```
    
4. Now run the `docker push` command again. If you're copying the value from Docker Hub, you can drop the `tagname` part, as you didn't add a tag to the image name. If you don't specify a tag, Docker uses a tag called `latest`.
    
    ```console
    $ docker push YOUR-USER-NAME/getting-started
    ```
    

## [Run the image on a new instance](https://docs.docker.com/get-started/workshop/04_sharing_app/#run-the-image-on-a-new-instance)

Now that your image has been built and pushed into a registry, try running your app on a brand new instance that has never seen this container image. To do this, you will use Play with Docker.

> **Note**
> 
> Play with Docker uses the amd64 platform. If you are using an ARM based Mac with Apple silicon, you will need to rebuild the image to be compatible with Play with Docker and push the new image to your repository.
> 
> To build an image for the amd64 platform, use the `--platform` flag.
> 
> ```console
> $ docker build --platform linux/amd64 -t YOUR-USER-NAME/getting-started .
> ```
> 
> Docker buildx also supports building multi-platform images. To learn more, see [Multi-platform images](https://docs.docker.com/build/building/multi-platform/).

1. Open your browser to [Play with Docker](https://labs.play-with-docker.com/).
    
2. Select **Login** and then select **docker** from the drop-down list.
    
3. Sign in with your Docker Hub account and then select **Start**.
    
4. Select the **ADD NEW INSTANCE** option on the left side bar. If you don't see it, make your browser a little wider. After a few seconds, a terminal window opens in your browser.
    
    ![Play with Docker add new instance](https://docs.docker.com/get-started/workshop/images/pwd-add-new-instance.webp)
    
5. In the terminal, start your freshly pushed app.
    
    ```console
    $ docker run -dp 0.0.0.0:3000:3000 YOUR-USER-NAME/getting-started
    ```
    
    You should see the image get pulled down and eventually start up.
    
    > **Tip**
    > 
    > You may have noticed that this command binds the port mapping to a different IP address. Previous `docker run` commands published ports to `127.0.0.1:3000` on the host. This time, you're using `0.0.0.0`.
    > 
    > Binding to `127.0.0.1` only exposes a container's ports to the loopback interface. Binding to `0.0.0.0`, however, exposes the container's port on all interfaces of the host, making it available to the outside world.
    > 
    > For more information about how port mapping works, see [Networking](https://docs.docker.com/engine/network/#published-ports).
    
6. Select the 3000 badge when it appears.
    
    If the 3000 badge doesn't appear, you can select **Open Port** and specify `3000`.
    

## [Summary](https://docs.docker.com/get-started/workshop/04_sharing_app/#summary)

In this section, you learned how to share your images by pushing them to a registry. You then went to a brand new instance and were able to run the freshly pushed image. This is quite common in CI pipelines, where the pipeline will create the image and push it to a registry and then the production environment can use the latest version of the image.

Related information:

- [docker CLI reference](https://docs.docker.com/reference/cli/docker/)
- [Multi-platform images](https://docs.docker.com/build/building/multi-platform/)
- [Docker Hub overview](https://docs.docker.com/docker-hub/)

## [Next steps](https://docs.docker.com/get-started/workshop/04_sharing_app/#next-steps)

In the next section, you'll learn how to persist data in your containerized application.

[Persist the DB](https://docs.docker.com/get-started/workshop/05_persisting_data/)

# Persist the DB

In case you didn't notice, your todo list is empty every single time you launch the container. Why is this? In this part, you'll dive into how the container is working.

## [The container's filesystem](https://docs.docker.com/get-started/workshop/05_persisting_data/#the-containers-filesystem)

When a container runs, it uses the various layers from an image for its filesystem. Each container also gets its own "scratch space" to create/update/remove files. Any changes won't be seen in another container, even if they're using the same image.

### [See this in practice](https://docs.docker.com/get-started/workshop/05_persisting_data/#see-this-in-practice)

To see this in action, you're going to start two containers. In one container, you'll create a file. In the other container, you'll verify the file exists. What you'll see is that the file created in one container isn't available in another.

1. Start an Alpine container and access its shell.
    
    ```console
    $ docker run -ti --name=mytest alpine
    ```
    
2. In the container, create a `greeting.txt` file with `hello` inside.
    
    ```console
    / # echo "hello" > greeting.txt
    ```
    
3. Exit the container.
    
    ```console
    / # exit
    ```
    
4. Run a new Alpine container and use the `cat` command to verify that the file does not exist.
    
    ```console
    $ docker run alpine cat greeting.txt
    ```
    
    You should see output similar to the following that indicates the file does not exist in the new container.
    
    ```console
    cat: can't open 'greeting.txt': No such file or directory
    ```
    
5. Go ahead and remove the containers using `docker ps --all` to get the IDs, and then `docker rm -f <container-id>` to remove the containers.
    

## [Container volumes](https://docs.docker.com/get-started/workshop/05_persisting_data/#container-volumes)

With the previous experiment, you saw that each container starts from the image definition each time it starts. While containers can create, update, and delete files, those changes are lost when you remove the container and Docker isolates all changes to that container. With volumes, you can change all of this.

[Volumes](https://docs.docker.com/engine/storage/volumes/) provide the ability to connect specific filesystem paths of the container back to the host machine. If you mount a directory in the container, changes in that directory are also seen on the host machine. If you mount that same directory across container restarts, you'd see the same files.

There are two main types of volumes. You'll eventually use both, but you'll start with volume mounts.

## [Persist the todo data](https://docs.docker.com/get-started/workshop/05_persisting_data/#persist-the-todo-data)

By default, the todo app stores its data in a SQLite database at `/etc/todos/todo.db` in the container's filesystem. If you're not familiar with SQLite, no worries! It's simply a relational database that stores all the data in a single file. While this isn't the best for large-scale applications, it works for small demos. You'll learn how to switch this to a different database engine later.

With the database being a single file, if you can persist that file on the host and make it available to the next container, it should be able to pick up where the last one left off. By creating a volume and attaching (often called "mounting") it to the directory where you stored the data, you can persist the data. As your container writes to the `todo.db` file, it will persist the data to the host in the volume.

As mentioned, you're going to use a volume mount. Think of a volume mount as an opaque bucket of data. Docker fully manages the volume, including the storage location on disk. You only need to remember the name of the volume.

### [Create a volume and start the container](https://docs.docker.com/get-started/workshop/05_persisting_data/#create-a-volume-and-start-the-container)

You can create the volume and start the container using the CLI or Docker Desktop's graphical interface.

CLI Docker Desktop

---

1. Create a volume by using the `docker volume create` command.
    
    ```console
    $ docker volume create todo-db
    ```
    
2. Stop and remove the todo app container once again with `docker rm -f <id>`, as it is still running without using the persistent volume.
    
3. Start the todo app container, but add the `--mount` option to specify a volume mount. Give the volume a name, and mount it to `/etc/todos` in the container, which captures all files created at the path.
    
    ```console
    $ docker run -dp 127.0.0.1:3000:3000 --mount type=volume,src=todo-db,target=/etc/todos getting-started
    ```
    
    > **Note**
    > 
    > If you're using Git Bash, you must use different syntax for this command.
    > 
    > ```console
    > $ docker run -dp 127.0.0.1:3000:3000 --mount type=volume,src=todo-db,target=//etc/todos getting-started
    > ```
    > 
    > For more details about Git Bash's syntax differences, see [Working with Git Bash](https://docs.docker.com/desktop/troubleshoot/topics/#working-with-git-bash).
    

---

### [Verify that the data persists](https://docs.docker.com/get-started/workshop/05_persisting_data/#verify-that-the-data-persists)

1. Once the container starts up, open the app and add a few items to your todo list.
    
    ![Items added to todo list](https://docs.docker.com/get-started/workshop/images/items-added.webp)
    
2. Stop and remove the container for the todo app. Use Docker Desktop or `docker ps` to get the ID and then `docker rm -f <id>` to remove it.
    
3. Start a new container using the previous steps.
    
4. Open the app. You should see your items still in your list.
    
5. Go ahead and remove the container when you're done checking out your list.
    

You've now learned how to persist data.

## [Dive into the volume](https://docs.docker.com/get-started/workshop/05_persisting_data/#dive-into-the-volume)

A lot of people frequently ask "Where is Docker storing my data when I use a volume?" If you want to know, you can use the `docker volume inspect` command.

```console
$ docker volume inspect todo-db
```

You should see output like the following:

Explain

`[     {        "CreatedAt": "2019-09-26T02:18:36Z",        "Driver": "local",        "Labels": {},        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",        "Name": "todo-db",        "Options": {},        "Scope": "local"    } ]`

The `Mountpoint` is the actual location of the data on the disk. Note that on most machines, you will need to have root access to access this directory from the host.

## [Summary](https://docs.docker.com/get-started/workshop/05_persisting_data/#summary)

In this section, you learned how to persist container data.

Related information:

- [docker CLI reference](https://docs.docker.com/reference/cli/docker/)
- [Volumes](https://docs.docker.com/engine/storage/volumes/)

## [Next steps](https://docs.docker.com/get-started/workshop/05_persisting_data/#next-steps)

Next, you'll learn how you can develop your app more efficiently using bind mounts.

[Use bind mounts](https://docs.docker.com/get-started/workshop/06_bind_mounts/)

# Use bind mounts

In [part 4](https://docs.docker.com/get-started/workshop/05_persisting_data/), you used a volume mount to persist the data in your database. A volume mount is a great choice when you need somewhere persistent to store your application data.

A bind mount is another type of mount, which lets you share a directory from the host's filesystem into the container. When working on an application, you can use a bind mount to mount source code into the container. The container sees the changes you make to the code immediately, as soon as you save a file. This means that you can run processes in the container that watch for filesystem changes and respond to them.

In this chapter, you'll see how you can use bind mounts and a tool called [nodemon](https://npmjs.com/package/nodemon) to watch for file changes, and then restart the application automatically. There are equivalent tools in most other languages and frameworks.

## [Quick volume type comparisons](https://docs.docker.com/get-started/workshop/06_bind_mounts/#quick-volume-type-comparisons)

The following are examples of a named volume and a bind mount using `--mount`:

- Named volume: `type=volume,src=my-volume,target=/usr/local/data`
- Bind mount: `type=bind,src=/path/to/data,target=/usr/local/data`

The following table outlines the main differences between volume mounts and bind mounts.

||Named volumes|Bind mounts|
|---|---|---|
|Host location|Docker chooses|You decide|
|Populates new volume with container contents|Yes|No|
|Supports Volume Drivers|Yes|No|

## [Trying out bind mounts](https://docs.docker.com/get-started/workshop/06_bind_mounts/#trying-out-bind-mounts)

Before looking at how you can use bind mounts for developing your application, you can run a quick experiment to get a practical understanding of how bind mounts work.

1. Verify that your `getting-started-app` directory is in a directory defined in Docker Desktop's file sharing setting. This setting defines which parts of your filesystem you can share with containers. For details about accessing the setting, see [File sharing](https://docs.docker.com/desktop/settings/#file-sharing).
    
2. Open a terminal and change directory to the `getting-started-app` directory.
    
3. Run the following command to start `bash` in an `ubuntu` container with a bind mount.
    
    Mac / Linux / PowerShell Command Prompt Git Bash
    
    ---
    
    ```console
    $ docker run -it --mount type=bind,src="$(pwd)",target=/src ubuntu bash
    ```
    
    ---
    
    The `--mount type=bind` option tells Docker to create a bind mount, where `src` is the current working directory on your host machine (`getting-started-app`), and `target` is where that directory should appear inside the container (`/src`).
    
4. After running the command, Docker starts an interactive `bash` session in the root directory of the container's filesystem.
    
    Explain
    
    `root@ac1237fad8db:/# pwd / root@ac1237fad8db:/# ls bin   dev  home  media  opt   root  sbin  srv  tmp  var boot  etc  lib   mnt    proc  run   src   sys  usr`
    
5. Change directory to the `src` directory.
    
    This is the directory that you mounted when starting the container. Listing the contents of this directory displays the same files as in the `getting-started-app` directory on your host machine.
    
    ```console
    root@ac1237fad8db:/# cd src
    root@ac1237fad8db:/src# ls
    Dockerfile  node_modules  package.json  spec  src  yarn.lock
    ```
    
6. Create a new file named `myfile.txt`.
    
    ```console
    root@ac1237fad8db:/src# touch myfile.txt
    root@ac1237fad8db:/src# ls
    Dockerfile  myfile.txt  node_modules  package.json  spec  src  yarn.lock
    ```
    
7. Open the `getting-started-app` directory on the host and observe that the `myfile.txt` file is in the directory.
    
    Explain
    
    `├── getting-started-app/ │ ├── Dockerfile │ ├── myfile.txt │ ├── node_modules/ │ ├── package.json │ ├── spec/ │ ├── src/ │ └── yarn.lock`
    
8. From the host, delete the `myfile.txt` file.
    
9. In the container, list the contents of the `app` directory once more. Observe that the file is now gone.
    
    ```console
    root@ac1237fad8db:/src# ls
    Dockerfile  node_modules  package.json  spec  src  yarn.lock
    ```
    
10. Stop the interactive container session with `Ctrl` + `D`.
    

That's all for a brief introduction to bind mounts. This procedure demonstrated how files are shared between the host and the container, and how changes are immediately reflected on both sides. Now you can use bind mounts to develop software.

## [Development containers](https://docs.docker.com/get-started/workshop/06_bind_mounts/#development-containers)

Using bind mounts is common for local development setups. The advantage is that the development machine doesn’t need to have all of the build tools and environments installed. With a single docker run command, Docker pulls dependencies and tools.

### [Run your app in a development container](https://docs.docker.com/get-started/workshop/06_bind_mounts/#run-your-app-in-a-development-container)

The following steps describe how to run a development container with a bind mount that does the following:

- Mount your source code into the container
- Install all dependencies
- Start `nodemon` to watch for filesystem changes

You can use the CLI or Docker Desktop to run your container with a bind mount.

Mac / Linux CLI PowerShell CLI Command Prompt CLI Git Bash CLI Docker Desktop

---

1. Make sure you don't have any `getting-started` containers currently running.
    
2. Run the following command from the `getting-started-app` directory.
    
    Explain
    
    `$ docker run -dp 127.0.0.1:3000:3000 \     -w /app --mount type=bind,src="$(pwd)",target=/app \    node:18-alpine \    sh -c "yarn install && yarn run dev"`
    
    The following is a breakdown of the command:
    
    - `-dp 127.0.0.1:3000:3000` - same as before. Run in detached (background) mode and create a port mapping
    - `-w /app` - sets the "working directory" or the current directory that the command will run from
    - `--mount type=bind,src="$(pwd)",target=/app` - bind mount the current directory from the host into the `/app` directory in the container
    - `node:18-alpine` - the image to use. Note that this is the base image for your app from the Dockerfile
    - `sh -c "yarn install && yarn run dev"` - the command. You're starting a shell using `sh` (alpine doesn't have `bash`) and running `yarn install` to install packages and then running `yarn run dev` to start the development server. If you look in the `package.json`, you'll see that the `dev` script starts `nodemon`.
3. You can watch the logs using `docker logs <container-id>`. You'll know you're ready to go when you see this:
    
    Explain
    
    ``$ docker logs -f <container-id> nodemon -L src/index.js [nodemon] 2.0.20 [nodemon] to restart at any time, enter `rs` [nodemon] watching path(s): *.* [nodemon] watching extensions: js,mjs,json [nodemon] starting `node src/index.js` Using sqlite database at /etc/todos/todo.db Listening on port 3000``
    
    When you're done watching the logs, exit out by hitting `Ctrl`+`C`.
    

---

### [Develop your app with the development container](https://docs.docker.com/get-started/workshop/06_bind_mounts/#develop-your-app-with-the-development-container)

Update your app on your host machine and see the changes reflected in the container.

1. In the `src/static/js/app.js` file, on line 109, change the "Add Item" button to simply say "Add":

```diff
    - {submitting ? 'Adding...' : 'Add Item'}
    + {submitting ? 'Adding...' : 'Add'}
```
    
    Save the file.
    
2. Refresh the page in your web browser, and you should see the change reflected almost immediately because of the bind mount. Nodemon detects the change and restarts the server. It might take a few seconds for the Node server to restart. If you get an error, try refreshing after a few seconds.
    
    ![Screenshot of updated label for Add button](https://docs.docker.com/get-started/workshop/images/updated-add-button.webp)
    
3. Feel free to make any other changes you'd like to make. Each time you make a change and save a file, the change is reflected in the container because of the bind mount. When Nodemon detects a change, it restarts the app inside the container automatically. When you're done, stop the container and build your new image using:
    
    ```console
    $ docker build -t getting-started .
    ```
    

## [Summary](https://docs.docker.com/get-started/workshop/06_bind_mounts/#summary)

At this point, you can persist your database and see changes in your app as you develop without rebuilding the image.

In addition to volume mounts and bind mounts, Docker also supports other mount types and storage drivers for handling more complex and specialized use cases.

Related information:

- [docker CLI reference](https://docs.docker.com/reference/cli/docker/)
- [Manage data in Docker](https://docs.docker.com/storage/)

## [Next steps](https://docs.docker.com/get-started/workshop/06_bind_mounts/#next-steps)

In order to prepare your app for production, you need to migrate your database from working in SQLite to something that can scale a little better. For simplicity, you'll keep using a relational database and switch your application to use MySQL. But, how should you run MySQL? How do you allow the containers to talk to each other? You'll learn about that in the next section.

[Multi container apps](https://docs.docker.com/get-started/workshop/07_multi_container/)

# Multi container apps

Up to this point, you've been working with single container apps. But, now you will add MySQL to the application stack. The following question often arises - "Where will MySQL run? Install it in the same container or run it separately?" In general, each container should do one thing and do it well. The following are a few reasons to run the container separately:

- There's a good chance you'd have to scale APIs and front-ends differently than databases.
- Separate containers let you version and update versions in isolation.
- While you may use a container for the database locally, you may want to use a managed service for the database in production. You don't want to ship your database engine with your app then.
- Running multiple processes will require a process manager (the container only starts one process), which adds complexity to container startup/shutdown.

And there are more reasons. So, like the following diagram, it's best to run your app in multiple containers.

![Todo App connected to MySQL container](https://docs.docker.com/get-started/workshop/images/multi-container.webp)

## [Container networking](https://docs.docker.com/get-started/workshop/07_multi_container/#container-networking)

Remember that containers, by default, run in isolation and don't know anything about other processes or containers on the same machine. So, how do you allow one container to talk to another? The answer is networking. If you place the two containers on the same network, they can talk to each other.

## [Start MySQL](https://docs.docker.com/get-started/workshop/07_multi_container/#start-mysql)

There are two ways to put a container on a network:

- Assign the network when starting the container.
- Connect an already running container to a network.

In the following steps, you'll create the network first and then attach the MySQL container at startup.

1. Create the network.
    
    ```console
    $ docker network create todo-app
    ```
    
2. Start a MySQL container and attach it to the network. You're also going to define a few environment variables that the database will use to initialize the database. To learn more about the MySQL environment variables, see the "Environment Variables" section in the [MySQL Docker Hub listing](https://hub.docker.com/_/mysql/).
    
    Mac / Linux / Git Bash PowerShell Command Prompt
    
    ---
    
    Explain
    
    `$ docker run -d \     --network todo-app --network-alias mysql \    -v todo-mysql-data:/var/lib/mysql \    -e MYSQL_ROOT_PASSWORD=secret \    -e MYSQL_DATABASE=todos \    mysql:8.0`
    
    ---
    
    In the previous command, you can see the `--network-alias` flag. In a later section, you'll learn more about this flag.
    
    > **Tip**
    > 
    > You'll notice a volume named `todo-mysql-data` in the above command that is mounted at `/var/lib/mysql`, which is where MySQL stores its data. However, you never ran a `docker volume create` command. Docker recognizes you want to use a named volume and creates one automatically for you.
    
3. To confirm you have the database up and running, connect to the database and verify that it connects.
    
    ```console
    $ docker exec -it <mysql-container-id> mysql -u root -p
    ```
    
    When the password prompt comes up, type in `secret`. In the MySQL shell, list the databases and verify you see the `todos` database.
    
    ```console
    mysql> SHOW DATABASES;
    ```
    
    You should see output that looks like this:
    
    Explain
    
    `+--------------------+ | Database           | +--------------------+ | information_schema | | mysql              | | performance_schema | | sys                | | todos              | +--------------------+ 5 rows in set (0.00 sec)`
    
4. Exit the MySQL shell to return to the shell on your machine.
    
    ```console
    mysql> exit
    ```
    
    You now have a `todos` database and it's ready for you to use.
    

## [Connect to MySQL](https://docs.docker.com/get-started/workshop/07_multi_container/#connect-to-mysql)

Now that you know MySQL is up and running, you can use it. But, how do you use it? If you run another container on the same network, how do you find the container? Remember that each container has its own IP address.

To answer the questions above and better understand container networking, you're going to make use of the [nicolaka/netshoot](https://github.com/nicolaka/netshoot) container, which ships with a lot of tools that are useful for troubleshooting or debugging networking issues.

1. Start a new container using the nicolaka/netshoot image. Make sure to connect it to the same network.
    
    ```console
    $ docker run -it --network todo-app nicolaka/netshoot
    ```
    
2. Inside the container, you're going to use the `dig` command, which is a useful DNS tool. You're going to look up the IP address for the hostname `mysql`.
    
    ```console
    $ dig mysql
    ```
    
    You should get output like the following.
    
    Explain
    
    `; <<>> DiG 9.18.8 <<>> mysql ;; global options: +cmd ;; Got answer: ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162 ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0 ;; QUESTION SECTION: ;mysql.				IN	A ;; ANSWER SECTION: mysql.			600	IN	A	172.23.0.2 ;; Query time: 0 msec ;; SERVER: 127.0.0.11#53(127.0.0.11) ;; WHEN: Tue Oct 01 23:47:24 UTC 2019 ;; MSG SIZE  rcvd: 44`
    
    In the "ANSWER SECTION", you will see an `A` record for `mysql` that resolves to `172.23.0.2` (your IP address will most likely have a different value). While `mysql` isn't normally a valid hostname, Docker was able to resolve it to the IP address of the container that had that network alias. Remember, you used the `--network-alias` earlier.
    
    What this means is that your app only simply needs to connect to a host named `mysql` and it'll talk to the database.
    

## [Run your app with MySQL](https://docs.docker.com/get-started/workshop/07_multi_container/#run-your-app-with-mysql)

The todo app supports the setting of a few environment variables to specify MySQL connection settings. They are:

- `MYSQL_HOST` - the hostname for the running MySQL server
- `MYSQL_USER` - the username to use for the connection
- `MYSQL_PASSWORD` - the password to use for the connection
- `MYSQL_DB` - the database to use once connected

> **Note**
> 
> While using env vars to set connection settings is generally accepted for development, it's highly discouraged when running applications in production. Diogo Monica, a former lead of security at Docker, [wrote a fantastic blog post](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/) explaining why.
> 
> A more secure mechanism is to use the secret support provided by your container orchestration framework. In most cases, these secrets are mounted as files in the running container. You'll see many apps (including the MySQL image and the todo app) also support env vars with a `_FILE` suffix to point to a file containing the variable.
> 
> As an example, setting the `MYSQL_PASSWORD_FILE` var will cause the app to use the contents of the referenced file as the connection password. Docker doesn't do anything to support these env vars. Your app will need to know to look for the variable and get the file contents.

You can now start your dev-ready container.

1. Specify each of the previous environment variables, as well as connect the container to your app network. Make sure that you are in the `getting-started-app` directory when you run this command.
    
    Mac / Linux PowerShell Command Prompt Git Bash
    
    ---
    
    Explain
    
    `$ docker run -dp 127.0.0.1:3000:3000 \   -w /app -v "$(pwd):/app" \  --network todo-app \  -e MYSQL_HOST=mysql \  -e MYSQL_USER=root \  -e MYSQL_PASSWORD=secret \  -e MYSQL_DB=todos \  node:18-alpine \  sh -c "yarn install && yarn run dev"`
    
    ---
    
2. If you look at the logs for the container (`docker logs -f <container-id>`), you should see a message similar to the following, which indicates it's using the mysql database.
    
    Explain
    
    ``$ nodemon src/index.js [nodemon] 2.0.20 [nodemon] to restart at any time, enter `rs` [nodemon] watching dir(s): *.* [nodemon] starting `node src/index.js` Connected to mysql db at host mysql Listening on port 3000``
    
3. Open the app in your browser and add a few items to your todo list.
    
4. Connect to the mysql database and prove that the items are being written to the database. Remember, the password is `secret`.
    
    ```console
    $ docker exec -it <mysql-container-id> mysql -p todos
    ```
    
    And in the mysql shell, run the following:
    
    Explain
    
    `mysql> select * from todo_items; +--------------------------------------+--------------------+-----------+ | id                                   | name               | completed | +--------------------------------------+--------------------+-----------+ | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 | | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 | +--------------------------------------+--------------------+-----------+`
    
    Your table will look different because it has your items. But, you should see them stored there.
    

## [Summary](https://docs.docker.com/get-started/workshop/07_multi_container/#summary)

At this point, you have an application that now stores its data in an external database running in a separate container. You learned a little bit about container networking and service discovery using DNS.

Related information:

- [docker CLI reference](https://docs.docker.com/reference/cli/docker/)
- [Networking overview](https://docs.docker.com/engine/network/)

## [Next steps](https://docs.docker.com/get-started/workshop/07_multi_container/#next-steps)

There's a good chance you are starting to feel a little overwhelmed with everything you need to do to start up this application. You have to create a network, start containers, specify all of the environment variables, expose ports, and more. That's a lot to remember and it's certainly making things harder to pass along to someone else.

In the next section, you'll learn about Docker Compose. With Docker Compose, you can share your application stacks in a much easier way and let others spin them up with a single, simple command.

[Use Docker Compose](https://docs.docker.com/get-started/workshop/08_using_compose/)

# Use Docker Compose

[Docker Compose](https://docs.docker.com/compose/) is a tool that helps you define and share multi-container applications. With Compose, you can create a YAML file to define the services and with a single command, you can spin everything up or tear it all down.

The big advantage of using Compose is you can define your application stack in a file, keep it at the root of your project repository (it's now version controlled), and easily enable someone else to contribute to your project. Someone would only need to clone your repository and start the app using Compose. In fact, you might see quite a few projects on GitHub/GitLab doing exactly this now.

## [Create the Compose file](https://docs.docker.com/get-started/workshop/08_using_compose/#create-the-compose-file)

In the `getting-started-app` directory, create a file named `compose.yaml`.

Explain

`├── getting-started-app/ │ ├── Dockerfile │ ├── compose.yaml │ ├── node_modules/ │ ├── package.json │ ├── spec/ │ ├── src/ │ └── yarn.lock`

## [Define the app service](https://docs.docker.com/get-started/workshop/08_using_compose/#define-the-app-service)

In [part 7](https://docs.docker.com/get-started/workshop/07_multi_container/), you used the following command to start the application service.

Explain

`$ docker run -dp 127.0.0.1:3000:3000 \   -w /app -v "$(pwd):/app" \  --network todo-app \  -e MYSQL_HOST=mysql \  -e MYSQL_USER=root \  -e MYSQL_PASSWORD=secret \  -e MYSQL_DB=todos \  node:18-alpine \  sh -c "yarn install && yarn run dev"`

You'll now define this service in the `compose.yaml` file.

1. Open `compose.yaml` in a text or code editor, and start by defining the name and image of the first service (or container) you want to run as part of your application. The name will automatically become a network alias, which will be useful when defining your MySQL service.
    
    ```yaml
    services:
      app:
        image: node:18-alpine
    ```
    
2. Typically, you will see `command` close to the `image` definition, although there is no requirement on ordering. Add the `command` to your `compose.yaml` file.
    
    Explain
    
    `services:   app:    image: node:18-alpine    command: sh -c "yarn install && yarn run dev"`
    
3. Now migrate the `-p 127.0.0.1:3000:3000` part of the command by defining the `ports` for the service.
    
    Explain
    
    `services:   app:    image: node:18-alpine    command: sh -c "yarn install && yarn run dev"    ports:      - 127.0.0.1:3000:3000`
    
4. Next, migrate both the working directory (`-w /app`) and the volume mapping (`-v "$(pwd):/app"`) by using the `working_dir` and `volumes` definitions.
    
    One advantage of Docker Compose volume definitions is you can use relative paths from the current directory.
    
    Explain
    
    `services:   app:    image: node:18-alpine    command: sh -c "yarn install && yarn run dev"    ports:      - 127.0.0.1:3000:3000    working_dir: /app    volumes:      - ./:/app`
    
5. Finally, you need to migrate the environment variable definitions using the `environment` key.
    
    Explain
    
    `services:   app:    image: node:18-alpine    command: sh -c "yarn install && yarn run dev"    ports:      - 127.0.0.1:3000:3000    working_dir: /app    volumes:      - ./:/app    environment:      MYSQL_HOST: mysql      MYSQL_USER: root      MYSQL_PASSWORD: secret      MYSQL_DB: todos`
    

### [Define the MySQL service](https://docs.docker.com/get-started/workshop/08_using_compose/#define-the-mysql-service)

Now, it's time to define the MySQL service. The command that you used for that container was the following:

Explain

`$ docker run -d \   --network todo-app --network-alias mysql \  -v todo-mysql-data:/var/lib/mysql \  -e MYSQL_ROOT_PASSWORD=secret \  -e MYSQL_DATABASE=todos \  mysql:8.0`

1. First define the new service and name it `mysql` so it automatically gets the network alias. Also specify the image to use as well.
    
    Explain
    
    `services:   app:    # The app service definition  mysql:    image: mysql:8.0`
    
2. Next, define the volume mapping. When you ran the container with `docker run`, Docker created the named volume automatically. However, that doesn't happen when running with Compose. You need to define the volume in the top-level `volumes:` section and then specify the mountpoint in the service config. By simply providing only the volume name, the default options are used.
    
    Explain
    
    `services:   app:    # The app service definition  mysql:    image: mysql:8.0    volumes:      - todo-mysql-data:/var/lib/mysql volumes:   todo-mysql-data:`
    
3. Finally, you need to specify the environment variables.
    
    Explain
    
    `services:   app:    # The app service definition  mysql:    image: mysql:8.0    volumes:      - todo-mysql-data:/var/lib/mysql    environment:      MYSQL_ROOT_PASSWORD: secret      MYSQL_DATABASE: todos volumes:   todo-mysql-data:`
    

At this point, your complete `compose.yaml` should look like this:

Explain

`services:   app:    image: node:18-alpine    command: sh -c "yarn install && yarn run dev"    ports:      - 127.0.0.1:3000:3000    working_dir: /app    volumes:      - ./:/app    environment:      MYSQL_HOST: mysql      MYSQL_USER: root      MYSQL_PASSWORD: secret      MYSQL_DB: todos   mysql:    image: mysql:8.0    volumes:      - todo-mysql-data:/var/lib/mysql    environment:      MYSQL_ROOT_PASSWORD: secret      MYSQL_DATABASE: todos volumes:   todo-mysql-data:`

## [Run the application stack](https://docs.docker.com/get-started/workshop/08_using_compose/#run-the-application-stack)

Now that you have your `compose.yaml` file, you can start your application.

1. Make sure no other copies of the containers are running first. Use `docker ps` to list the containers and `docker rm -f <ids>` to remove them.
    
2. Start up the application stack using the `docker compose up` command. Add the `-d` flag to run everything in the background.
    
    ```console
    $ docker compose up -d
    ```
    
    When you run the previous command, you should see output like the following:
    
    Explain
    
    `Creating network "app_default" with the default driver Creating volume "app_todo-mysql-data" with default driver Creating app_app_1   ... done Creating app_mysql_1 ... done`
    
    You'll notice that Docker Compose created the volume as well as a network. By default, Docker Compose automatically creates a network specifically for the application stack (which is why you didn't define one in the Compose file).
    
3. Look at the logs using the `docker compose logs -f` command. You'll see the logs from each of the services interleaved into a single stream. This is incredibly useful when you want to watch for timing-related issues. The `-f` flag follows the log, so will give you live output as it's generated.
    
    If you have run the command already, you'll see output that looks like this:
    
    Explain
    
    `mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections. mysql_1  | Version: '8.0.31'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL) app_1    | Connected to mysql db at host mysql app_1    | Listening on port 3000`
    
    The service name is displayed at the beginning of the line (often colored) to help distinguish messages. If you want to view the logs for a specific service, you can add the service name to the end of the logs command (for example, `docker compose logs -f app`).
    
4. At this point, you should be able to open your app in your browser on [http://localhost:3000](http://localhost:3000/) and see it running.
    

## [See the app stack in Docker Dashboard](https://docs.docker.com/get-started/workshop/08_using_compose/#see-the-app-stack-in-docker-dashboard)

If you look at the Docker Dashboard, you'll see that there is a group named **getting-started-app**. This is the project name from Docker Compose and used to group the containers together. By default, the project name is simply the name of the directory that the `compose.yaml` was located in.

If you expand the stack, you'll see the two containers you defined in the Compose file. The names are also a little more descriptive, as they follow the pattern of `<service-name>-<replica-number>`. So, it's very easy to quickly see what container is your app and which container is the mysql database.

## [Tear it all down](https://docs.docker.com/get-started/workshop/08_using_compose/#tear-it-all-down)

When you're ready to tear it all down, simply run `docker compose down` or hit the trash can on the Docker Dashboard for the entire app. The containers will stop and the network will be removed.

> **Warning**
> 
> By default, named volumes in your compose file are not removed when you run `docker compose down`. If you want to remove the volumes, you need to add the `--volumes` flag.
> 
> The Docker Dashboard does not remove volumes when you delete the app stack.

## [Summary](https://docs.docker.com/get-started/workshop/08_using_compose/#summary)

In this section, you learned about Docker Compose and how it helps you simplify the way you define and share multi-service applications.

Related information:

- [Compose overview](https://docs.docker.com/compose/)
- [Compose file reference](https://docs.docker.com/reference/compose-file/)
- [Compose CLI reference](https://docs.docker.com/reference/cli/docker/compose/)

## [Next steps](https://docs.docker.com/get-started/workshop/08_using_compose/#next-steps)

Next, you'll learn about a few best practices you can use to improve your Dockerfile.

[Image-building best practices](https://docs.docker.com/get-started/workshop/09_image_best/)

# Image-building best practices

## [Image layering](https://docs.docker.com/get-started/workshop/09_image_best/#image-layering)

Using the `docker image history` command, you can see the command that was used to create each layer within an image.

1. Use the `docker image history` command to see the layers in the `getting-started` image you created.
    
    ```console
    $ docker image history getting-started
    ```
    
    You should get output that looks something like the following.
    


| ```<br>IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT<br>a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "src/index.j…    0B                  <br>f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              <br>a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               <br>9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  <br>b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  <br><missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  <br><missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                <br><missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              <br><missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  <br><missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              <br><missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  <br><missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  <br><missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   <br>``` |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

    Each of the lines represents a layer in the image. The display here shows the base at the bottom with the newest layer at the top. Using this, you can also quickly see the size of each layer, helping diagnose large images.
    
2. You'll notice that several of the lines are truncated. If you add the `--no-trunc` flag, you'll get the full output.
    
    ```console
    $ docker image history --no-trunc getting-started
    ```
    

## [Layer caching](https://docs.docker.com/get-started/workshop/09_image_best/#layer-caching)

Now that you've seen the layering in action, there's an important lesson to learn to help decrease build times for your container images. Once a layer changes, all downstream layers have to be recreated as well.

Look at the following Dockerfile you created for the getting started app.

Explain

`# syntax=docker/dockerfile:1 [FROM](https://docs.docker.com/reference/dockerfile/#from "Learn more about the FROM instruction") node:18-alpine [WORKDIR](https://docs.docker.com/reference/dockerfile/#workdir "Learn more about the WORKDIR instruction") /app [COPY](https://docs.docker.com/reference/dockerfile/#copy "Learn more about the COPY instruction") . . [RUN](https://docs.docker.com/reference/dockerfile/#run "Learn more about the RUN instruction") yarn install --production [CMD](https://docs.docker.com/reference/dockerfile/#cmd "Learn more about the CMD instruction") ["node", "src/index.js"]`

Going back to the image history output, you see that each command in the Dockerfile becomes a new layer in the image. You might remember that when you made a change to the image, the yarn dependencies had to be reinstalled. It doesn't make much sense to ship around the same dependencies every time you build.

To fix it, you need to restructure your Dockerfile to help support the caching of the dependencies. For Node-based applications, those dependencies are defined in the `package.json` file. You can copy only that file in first, install the dependencies, and then copy in everything else. Then, you only recreate the yarn dependencies if there was a change to the `package.json`.

1. Update the Dockerfile to copy in the `package.json` first, install dependencies, and then copy everything else in.
    
    Explain
    
    `# syntax=docker/dockerfile:1 [FROM](https://docs.docker.com/reference/dockerfile/#from "Learn more about the FROM instruction") node:18-alpine [WORKDIR](https://docs.docker.com/reference/dockerfile/#workdir "Learn more about the WORKDIR instruction") /app [COPY](https://docs.docker.com/reference/dockerfile/#copy "Learn more about the COPY instruction") package.json yarn.lock ./ [RUN](https://docs.docker.com/reference/dockerfile/#run "Learn more about the RUN instruction") yarn install --production [COPY](https://docs.docker.com/reference/dockerfile/#copy "Learn more about the COPY instruction") . . [CMD](https://docs.docker.com/reference/dockerfile/#cmd "Learn more about the CMD instruction") ["node", "src/index.js"]`
    
2. Build a new image using `docker build`.
    
    ```console
    $ docker build -t getting-started .
    ```
    
    You should see output like the following.
    
    Explain
    
    `[+] Building 16.1s (10/10) FINISHED => [internal] load build definition from Dockerfile => => transferring dockerfile: 175B => [internal] load .dockerignore => => transferring context: 2B => [internal] load metadata for docker.io/library/node:18-alpine => [internal] load build context => => transferring context: 53.37MB => [1/5] FROM docker.io/library/node:18-alpine => CACHED [2/5] WORKDIR /app => [3/5] COPY package.json yarn.lock ./ => [4/5] RUN yarn install --production => [5/5] COPY . . => exporting to image => => exporting layers => => writing image     sha256:d6f819013566c54c50124ed94d5e66c452325327217f4f04399b45f94e37d25 => => naming to docker.io/library/getting-started`
    
3. Now, make a change to the `src/static/index.html` file. For example, change the `<title>` to "The Awesome Todo App".
    
4. Build the Docker image now using `docker build -t getting-started .` again. This time, your output should look a little different.
    
    Explain
    
    `[+] Building 1.2s (10/10) FINISHED => [internal] load build definition from Dockerfile => => transferring dockerfile: 37B => [internal] load .dockerignore => => transferring context: 2B => [internal] load metadata for docker.io/library/node:18-alpine => [internal] load build context => => transferring context: 450.43kB => [1/5] FROM docker.io/library/node:18-alpine => CACHED [2/5] WORKDIR /app => CACHED [3/5] COPY package.json yarn.lock ./ => CACHED [4/5] RUN yarn install --production => [5/5] COPY . . => exporting to image => => exporting layers => => writing image     sha256:91790c87bcb096a83c2bd4eb512bc8b134c757cda0bdee4038187f98148e2eda => => naming to docker.io/library/getting-started`
    
    First off, you should notice that the build was much faster. And, you'll see that several steps are using previously cached layers. Pushing and pulling this image and updates to it will be much faster as well.
    

## [Multi-stage builds](https://docs.docker.com/get-started/workshop/09_image_best/#multi-stage-builds)

Multi-stage builds are an incredibly powerful tool to help use multiple stages to create an image. There are several advantages for them:

- Separate build-time dependencies from runtime dependencies
- Reduce overall image size by shipping only what your app needs to run

### [Maven/Tomcat example](https://docs.docker.com/get-started/workshop/09_image_best/#maventomcat-example)

When building Java-based applications, you need a JDK to compile the source code to Java bytecode. However, that JDK isn't needed in production. Also, you might be using tools like Maven or Gradle to help build the app. Those also aren't needed in your final image. Multi-stage builds help.

Explain

`# syntax=docker/dockerfile:1 [FROM](https://docs.docker.com/reference/dockerfile/#from "Learn more about the FROM instruction") maven AS build [WORKDIR](https://docs.docker.com/reference/dockerfile/#workdir "Learn more about the WORKDIR instruction") /app [COPY](https://docs.docker.com/reference/dockerfile/#copy "Learn more about the COPY instruction") . . [RUN](https://docs.docker.com/reference/dockerfile/#run "Learn more about the RUN instruction") mvn package [FROM](https://docs.docker.com/reference/dockerfile/#from "Learn more about the FROM instruction") tomcat [COPY](https://docs.docker.com/reference/dockerfile/#copy "Learn more about the COPY instruction") --from=build /app/target/file.war /usr/local/tomcat/webapps` 

In this example, you use one stage (called `build`) to perform the actual Java build using Maven. In the second stage (starting at `FROM tomcat`), you copy in files from the `build` stage. The final image is only the last stage being created, which can be overridden using the `--target` flag.

### [React example](https://docs.docker.com/get-started/workshop/09_image_best/#react-example)

When building React applications, you need a Node environment to compile the JS code (typically JSX), SASS stylesheets, and more into static HTML, JS, and CSS. If you aren't doing server-side rendering, you don't even need a Node environment for your production build. You can ship the static resources in a static nginx container.

Explain

`# syntax=docker/dockerfile:1 [FROM](https://docs.docker.com/reference/dockerfile/#from "Learn more about the FROM instruction") node:18 AS build [WORKDIR](https://docs.docker.com/reference/dockerfile/#workdir "Learn more about the WORKDIR instruction") /app [COPY](https://docs.docker.com/reference/dockerfile/#copy "Learn more about the COPY instruction") package* yarn.lock ./ [RUN](https://docs.docker.com/reference/dockerfile/#run "Learn more about the RUN instruction") yarn install [COPY](https://docs.docker.com/reference/dockerfile/#copy "Learn more about the COPY instruction") public ./public [COPY](https://docs.docker.com/reference/dockerfile/#copy "Learn more about the COPY instruction") src ./src [RUN](https://docs.docker.com/reference/dockerfile/#run "Learn more about the RUN instruction") yarn run build [FROM](https://docs.docker.com/reference/dockerfile/#from "Learn more about the FROM instruction") nginx:alpine [COPY](https://docs.docker.com/reference/dockerfile/#copy "Learn more about the COPY instruction") --from=build /app/build /usr/share/nginx/html`

In the previous Dockerfile example, it uses the `node:18` image to perform the build (maximizing layer caching) and then copies the output into an nginx container.

## [Summary](https://docs.docker.com/get-started/workshop/09_image_best/#summary)

In this section, you learned a few image building best practices, including layer caching and multi-stage builds.

Related information:

- [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
- [Dockerfile best practices](https://docs.docker.com/build/building/best-practices/)

## [Next steps](https://docs.docker.com/get-started/workshop/09_image_best/#next-steps)

In the next section, you'll learn about additional resources you can use to continue learning about containers.

[What next](https://docs.docker.com/get-started/workshop/10_what_next/)

# What next after the Docker workshop

Although you're done with the workshop, there's still a lot more to learn about containers.

Here are a few other areas to look at next.

## [Container orchestration](https://docs.docker.com/get-started/workshop/10_what_next/#container-orchestration)

Running containers in production is tough. You don't want to log into a machine and simply run a `docker run` or `docker compose up`. Why not? Well, what happens if the containers die? How do you scale across several machines? Container orchestration solves this problem. Tools like Kubernetes, Swarm, Nomad, and ECS all help solve this problem, all in slightly different ways.

The general idea is that you have managers who receive the expected state. This state might be "I want to run two instances of my web app and expose port 80." The managers then look at all of the machines in the cluster and delegate work to worker nodes. The managers watch for changes (such as a container quitting) and then work to make the actual state reflect the expected state.

## [Cloud Native Computing Foundation projects](https://docs.docker.com/get-started/workshop/10_what_next/#cloud-native-computing-foundation-projects)

The CNCF is a vendor-neutral home for various open-source projects, including Kubernetes, Prometheus, Envoy, Linkerd, NATS, and more. You can view the [graduated and incubated projects here](https://www.cncf.io/projects/) and the entire [CNCF Landscape here](https://landscape.cncf.io/). There are a lot of projects to help solve problems around monitoring, logging, security, image registries, messaging, and more.

## [Getting started video workshop](https://docs.docker.com/get-started/workshop/10_what_next/#getting-started-video-workshop)

Docker recommends watching the video workshop from DockerCon 2022. Watch the entire video or use the following links to open the video at a particular section.

- [Docker overview and installation](https://youtu.be/gAGEar5HQoU)
- [Pull, run, and explore containers](https://youtu.be/gAGEar5HQoU?t=1400)
- [Build a container image](https://youtu.be/gAGEar5HQoU?t=3185)
- [Containerize an app](https://youtu.be/gAGEar5HQoU?t=4683)
- [Connect a DB and set up a bind mount](https://youtu.be/gAGEar5HQoU?t=6305)
- [Deploy a container to the cloud](https://youtu.be/gAGEar5HQoU?t=8280)

## [Creating a container from scratch](https://docs.docker.com/get-started/workshop/10_what_next/#creating-a-container-from-scratch)

If you'd like to see how containers are built from scratch, Liz Rice from Aqua Security has a fantastic talk in which she creates a container from scratch in Go. While the talk does not go into networking, using images for the filesystem, and other advanced topics, it gives a deep dive into how things are working.

## [Language-specific guides](https://docs.docker.com/get-started/workshop/10_what_next/#language-specific-guides)

If you are looking for information on how to containerize an application using your favorite language, see the [Language-specific guides](https://docs.docker.com/guides/language/).