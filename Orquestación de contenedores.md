- https://learn.microsoft.com/es-es/azure/architecture/microservices/design/orchestration
- https://www.ibm.com/mx-es/topics/container-orchestration

Hoy en día, [Kubernetes](https://www.ibm.com/mx-es/topics/kubernetes) es la plataforma de orquestación de contenedores más popular y la mayoría de los proveedores de nube pública, incluidos Amazon Web Services (AWS), Google Cloud Platform, IBM® Cloud, y Microsoft Azure, ofrecen servicios administrados de Kubernetes. Otras herramientas de orquestación de contenedores incluyen Docker Swarm y Apache Mesos.

Más sobre los contenedores y por qué necesitan orquestación

Los[contenedores](https://www.ibm.com/mx-es/topics/containers) son componentes de aplicación livianos y ejecutables que combinan el código fuente de la aplicación con todas las bibliotecas y dependencias del sistema operativo (SO) necesarias para ejecutar el código en cualquier entorno. 

La capacidad de crear contenedores existe desde hace décadas, pero estuvo ampliamente disponible en 2008, cuando Linux incluyó la funcionalidad de contenedores en su kernel. Y luego se utilizó ampliamente con la llegada de la plataforma de contenerización de código abierto [Docker](https://www.ibm.com/mx-es/topics/docker) en 2013. (Docker es tan popular que "contenedores Docker" y "contenedores" a menudo se usan indistintamente). 

Debido a que son más pequeñas, más eficientes en recursos y portátiles que las [máquinas virtuales (VM)](https://www.ibm.com/mx-es/topics/virtual-machines), los contenedores (más específicamente, los [microservicios](https://www.ibm.com/mx-es/topics/microservices) en contenedores o las funcionalidades [sin servidor](https://www.ibm.com/mx-es/topics/serverless)) se han convertido en las _unidades informáticas_ de [aplicaciones nativas de la nube](https://www.ibm.com/mx-es/topics/cloud-native) modernas. (Para obtener más información sobre los beneficios de los contenedores, consulte la visualización interactiva de datos a continuación)

En pequeñas cantidades, los contenedores son bastante fáciles de implementar y administrar manualmente. Pero en la mayoría de las organizaciones, el número de aplicaciones en contenedores está creciendo rápidamente y gestionándolas a escala. Especialmente, como parte de una [canalización de integración continua](https://www.ibm.com/mx-es/topics/continuous-integration)/[entrega continua](https://www.ibm.com/mx-es/topics/continuous-delivery) (CI/CD) o [DevOps](https://www.ibm.com/mx-es/topics/devops), es imposible sin automatización.

Introduzca la orquestación de contenedores, que automatiza las tareas de operaciones relacionadas con la implementación y ejecución de aplicaciones y servicios en contenedores. Según [una investigación reciente de](https://www.ibm.com/downloads/cas/VG8KRPRM) IBM, el 70 % de los desarrolladores que utilizan contenedores informan que utilizan una solución de orquestación de contenedores, y el 70 % de ellos informan que utilizan un servicio de orquestación de contenedores completamente administrado (gestionado en la nube) en su organización.

[Descargar el informe completo: Contenedores en la empresa - This link downloads a pdf](https://www.ibm.com/downloads/cas/VG8KRPRM)

Cómo funciona la orquestación de contenedores

Aunque existen diferencias en las metodologías y capacidades de las herramientas, la orquestación de contenedores es esencialmente un proceso de tres pasos (o ciclo, cuando forma parte de un proceso ágil o DevOps iterativo).

La mayoría de las herramientas de orquestación de contenedores admiten un modelo de configuración declarativa: un desarrollador escribe un archivo de configuración (en YAML o JSON, según la herramienta) que define un estado de configuración deseado. La herramienta de orquestación que ejecuta el archivo utiliza su propia inteligencia para lograr ese estado. El archivo de configuración normalmente

- Define qué imágenes de contenedor componen la aplicación y dónde se encuentran (en qué)  
      
    
- Aprovisiona los contenedores con almacenamiento y otros recursos  
      
    
- Define y protege las conexiones de red  
      
    
- Especifica el control de versiones (para implementaciones por fases o canary).

La herramienta de orquestación programa la implementación de los contenedores (y las réplicas de los contenedores, para mayor resiliencia) en un host. Elige el mejor host en función de la capacidad de CPU disponible, la memoria u otros requisitos o restricciones especificados en el archivo de configuración. 

Una vez que se implementan los contenedores, la herramienta de orquestación administra el ciclo de vida de la aplicación en contenedores en función del archivo de definición de contenedor (a menudo un Dockerfile). Esto incluye 

- Gestionar la escalabilidad (arriba y abajo), el equilibrio de carga y la asignación de recursos entre los contenedores  
      
    
- Garantizar la disponibilidad y el rendimiento mediante la reubicación de los contenedores a otro host en caso de que se produzca una interrupción o escasez de recursos del sistema  
      
    
- Recopilación y almacenamiento de datos de registro y otra telemetría utilizada para monitorear el estado y el rendimiento de la aplicación.

### Beneficios de la orquestación de contenedores

  
Probablemente esté claro que el principal beneficio de la orquestación de contenedores es la _automatización ,_y no solo porque reduce en gran medida el esfuerzo y la complejidad de administrar un gran estado de aplicaciones contenerizadas. Al automatizar las operaciones, la orquestación respalda un enfoque ágil o DevOps que permite a los equipos desarrollar e implementar en ciclos rápidos e iterativos y lanzar nuevas características y capacidades más rápidamente.

Además, la inteligencia de una herramienta de orquestación puede mejorar o ampliar muchos de los beneficios inherentes de la contenerización. Por ejemplo, la selección automatizada de host y la asignación de recursos, basada en la configuración declarativa, maximiza el uso eficiente de los recursos informáticos; la supervisión automatizada de la salud y la reubicación de contenedores maximizan la disponibilidad.

Kubernetes

Como se indicó anteriormente, Kubernetes es la plataforma de orquestación de contenedores más popular. Junto con otras herramientas en el ecosistema de contenedores, Kubernetes permite a una empresa ofrecer una [plataforma como servicio (PaaS)](https://www.ibm.com/mx-es/topics/paas) altamente productiva. Abordar muchas de las tareas y problemas relacionados con la infraestructura y las operaciones en torno al desarrollo de aplicaciones nativas de la nube para que los equipos de desarrollo puedan centrarse exclusivamente en la programación y la innovación.

Las ventajas de Kubernetes sobre otras soluciones de orquestación son en gran medida el resultado de su funcionalidad más completa y sofisticada en varias áreas, que incluyen:

- **Implementación de contenedores.** Kubernetes implementa un número específico de contenedores en un host especificado y los mantiene en ejecución en el estado deseado  
      
    
- **Implementaciones.** Una implementación es un cambio en una implementación. Kubernetes le permite iniciar, pausar, reanudar o revertir implementaciones.  
      
    
- **Descubrimiento de servicios.** Kubernetes puede exponer automáticamente un contenedor a Internet o a otros contenedores utilizando un nombre [DNS o una dirección IP.](https://www.ibm.com/mx-es/topics/dns)   
      
    
- **Aprovisionamiento de almacenamiento.** Los desarrolladores pueden configurar Kubernetes para montar almacenamiento local o en la nube persistente para sus contenedores según sea necesario.  
      
    
- **Equilibrio de carga y escalabilidad** Cuando aumenta el tráfico a un contenedor, Kubernetes puede emplear [equilibrio](https://www.ibm.com/mx-es/topics/load-balancing) de carga y escalado para distribuirlo en toda la red para garantizar la estabilidad y el rendimiento. (También ahorra a los desarrolladores el trabajo de configurar un balanceador de carga).  
      
    
- **Autoreparación para alta disponibilidad.** Cuando un contenedor falla, Kubernetes puede reiniciarlo o reemplazarlo automáticamente. También puede retirar contenedores que no cumplan con los requisitos de control sanitario.  
      
     
- **Soporte y portabilidad en múltiples proveedores de nube** Como se indicó anteriormente, Kubernetes disfruta de un amplio soporte en todos los principales proveedores de nube. Esto es especialmente importante para las organizaciones que implementan aplicaciones en un entorno [de](https://www.ibm.com/mx-es/topics/hybrid-cloud) [nube híbrida](https://www.ibm.com/mx-es/topics/multicloud) o multinube .  
      
    
- **Ecosistema creciente de herramientas de código abierto.** Kubernetes también tiene un establo en constante expansión de usabilidad y herramientas de redes para mejorar sus capacidades a través de la API de Kubernetes. Estos incluyen [KNative](https://www.ibm.com/mx-es/topics/knative), que permite que los contenedores se ejecuten como cargas de trabajo sin servidor; e [Istio](https://www.ibm.com/mx-es/topics/istio), una malla de servicio de código abierto.
---

### Orquestación de contenedores con Kubernetes

Operar cientos de miles de contenedores en un sistema puede volverse inmanejable y requiere una solución de administración de orquestación.   

Ahí es donde entra en juego la [orquestación de contenedores](https://www.ibm.com/es-es/topics/container-orchestration), lo que permite a las empresas gestionar grandes volúmenes a lo largo de su estilo de vida, proporcionando: 

- Suministro
- Redundancia
- Monitorización de comprobación de estado
- asignación de recursos
- Escalado y [equilibrio de carga](https://www.ibm.com/es-es/topics/load-balancing)
- Movimiento entre hosts físicos

Aunque existen otras plataformas de orquestación de contenedores (por ejemplo, Apache Mesos, Nomad, [Docker Swarm](https://www.ibm.com/blog/docker-swarm-vs-kubernetes-a-comparison/)), [Kubernetes](https://www.ibm.com/es-es/topics/kubernetes) se ha convertido en el estándar de la industria.

La arquitectura de Kubernetes consiste en clústeres en ejecución que permiten que los contenedores se ejecuten en varias máquinas y entornos. Cada clúster suele estar formado por _nodos de trabajo_, que ejecutan las aplicaciones en contenedores, y _nodos del plan de control_, que controlan el clúster. El plano de control actúa como orquestador del clúster de Kubernetes. Incluye varios componentes: el servidor [de API](https://www.ibm.com/es-es/topics/api) (gestiona todas las interacciones con Kubernetes), el gestor de control (gestiona todos los procesos de control), el gestor de controladores de nube (la interfaz con la API del proveedor de nube), etc. Los nodos de trabajo ejecutan contenedores mediante entornos de ejecución de contenedores como Docker. Los pods, las unidades desplegables más pequeñas de un clúster, contienen uno o más contenedores de aplicaciones y comparten recursos, como almacenamiento e información de red.

Kubernetes permite a los desarrolladores y operadores declarar el estado deseado de su entorno de contenedor general a través de archivos YAML. Después, Kubernetes realiza todo el trabajo de procesamiento para establecer y mantener ese estado, con actividades que incluyen la implementación de un número específico de instancias de una aplicación o carga de trabajo determinada, el reinicio de esa aplicación si falla, el equilibrio de carga, el escalado automático, las implementaciones sin tiempo de inactividad y más. La orquestación de contenedores con Kubernetes también es crucial para la [integración y la entrega continuas (CI/CD)](https://www.ibm.com/es-es/think/topics/ci-cd-pipeline) o la canalización de [DevOps](https://www.ibm.com/es-es/topics/devops), lo que sería imposible sin automatización.

En 2015, Google donó Kubernetes a la Cloud Native Computing Foundation (CNCF)8, el centro de computación nativa en la nube de código abierto y neutral para proveedores operado bajo los auspicios de la Linux Foundation. Desde entonces, Kubernetes se ha convertido en la herramienta de orquestación de contenedores más utilizada para ejecutar cargas de trabajo basadas en contenedores en todo el mundo. En un informe del CNCF9, Kubernetes es el segundo proyecto [de código abierto](https://www.ibm.com/es-es/topics/open-source) más grande del mundo (después de Linux) y la principal herramienta de orquestación de contenedores para el 71 % de las empresas Fortune 100. 

### ¿Qué son los contenedores como servicio ([[CaaS]])?

[Los contenedores como servicio (CaaS)](https://www.ibm.com/es-es/topics/containers-as-a-service) [son un servicio de cloud computing](https://www.ibm.com/es-es/topics/cloud-computing) que permite a los desarrolladores gestionar e implementar aplicaciones en contenedores, dando a las empresas de todos los tamaños acceso a soluciones en nube portátiles y fácilmente escalables.

[[CaaS]] proporciona una plataforma basada en la nube en la que los usuarios pueden agilizar la virtualización basada en contenedores y los procesos de gestión de contenedores. Los proveedores de CaaS ofrecen una gran variedad de funciones, que incluyen (pero no se limitan a) tiempos de ejecución de contenedores, capas de orquestación y administración de almacenamiento persistente.

Al igual que la [infraestructura como servicio (IaaS)](https://www.ibm.com/es-es/topics/iaas), la plataforma como servicio ([[PaaS]]) y el [software como servicio (SaaS)](https://www.ibm.com/es-es/topics/saas), [[CaaS]] está disponible de proveedores de servicios en la nube (por ejemplo, [[AWS]], [[Google Cloud Services]], [[IBM Cloud]], [[Microsoft Azure]]) a través de un modelo de pago como precio, que solo permite utilizar los usuarios. 

Casos de uso para contenedores

Las organizaciones usan contenedores para admitir lo siguiente:

#### microservicios

Los contenedores son pequeños y ligeros, lo que los convierte en un buen complemento para las arquitecturas de microservicios, en las que las aplicaciones se construyen a partir de muchos servicios poco acoplados e implementables de forma independiente.

#### DevOps

La combinación de microservicios como arquitectura y contenedores como plataforma es una base común para muchos equipos de desarrollo y operaciones que adoptan metodologías DevOps. Por ejemplo, los contenedores admiten canalizaciones de DevOps, incluida la implementación de [integración](https://www.ibm.com/es-es/topics/continuous-integration) e [implementación continuas](https://www.ibm.com/es-es/topics/continuous-deployment) (CI/CD).

#### Híbrido y multinube

Dado que los contenedores pueden ejecutarse de forma consistente en cualquier lugar, en ordenadores portátiles, en las instalaciones y en entornos de nube, son una arquitectura subyacente ideal para escenarios de [nube híbrida](https://www.ibm.com/es-es/topics/hybrid-cloud) y [multinube](https://www.ibm.com/es-es/topics/multicloud) en los que las organizaciones operan a través de una mezcla de múltiples nubes públicas en combinación con su propio centro de datos.

#### Modernización y migración de aplicaciones

Uno de los enfoques más comunes para la [modernización de aplicaciones](https://www.ibm.com/es-es/topics/application-modernization) es la creación de aplicaciones en contenedores para preparar la [migración a la nube](https://www.ibm.com/es-es/topics/cloud-migration).  

#### Cargas de trabajo de IA y ML

La contenerización (es decir, las imágenes Docker organizadas con Kubernetes) permite rápidamente a los canales de DevOps implementar aplicaciones de [inteligencia artificial (IA)](https://www.ibm.com/es-es/topics/artificial-intelligence) y [machine learning (ML)](https://www.ibm.com/es-es/topics/machine-learning) en entornos de cloud computing.

#### Generative AI

Los contenedores también ofrecen una forma eficiente de implementar y administrar los [modelos de lenguaje de gran tamaño (LLM)](https://www.ibm.com/es-es/topics/large-language-models) asociados con la [IA generativa](https://www.ibm.com/es-es/topics/generative-ai), lo que proporciona portabilidad y escalabilidad cuando se usa con herramientas de orquestación. Además, los cambios realizados en el LLM se pueden empaquetar rápidamente en una nueva imagen de contenedor, lo que agiliza el desarrollo y las pruebas.

[Más información sobre casos de uso, aplicaciones y ejemplos de contenedores](https://www.ibm.com/blog/containers-use-cases/)

El ecosistema de contenedores más amplio: Istio y Knative

Más allá de Kubernetes, dos de los proyectos más populares en el ecosistema de los contenedores son ISTIO y KNative.

### Malla de servicio Istio

A medida que los desarrolladores utilizan contenedores para construir y ejecutar arquitecturas de microservicios, las inquietudes en torno a su gestión van más allá de las consideraciones sobre el ciclo de vida de los contenedores individuales. La forma en que grandes cantidades de pequeños servicios, a menudo denominados "malla de servicios", se conectan y relacionan entre sí, ha pasado a ser un asunto importante. [Istio](https://www.ibm.com/es-es/topics/istio) facilita a los desarrolladores la gestión entre otras cosas entre de los retos asociados a la detección, el tráfico, la monitorización y la seguridad. 

### [[Knative]] y sin servidor

[Knative](https://www.ibm.com/es-es/topics/knative) (pronunciada "kay-native") es una plataforma de código abierto que proporciona una fácil incorporación a [la informática sin servidor](https://www.ibm.com/es-es/topics/serverless), el modelo de desarrollo y ejecución de aplicaciones en la nube que permite a los desarrolladores crear y ejecutar código de aplicaciones sin aprovisionamiento ni gestión de servidores o infraestructura de backend.

 En lugar de implementar una instancia continua de código que permanece inactiva a la espera de solicitudes, el código sin servidor se implementa cuando es necesario, ampliándolo o reduciéndolo según fluctúe la demanda, y luego se retira cuando no se utiliza. La tecnología sin servidor evita el desperdicio de capacidad informática y energía, y reduce los costes, ya que solo paga por ejecutar el código cuando se está ejecutando.

Seguridad y gobierno de contenedores

Dado que los contenedores desempeñan un papel importante en el desarrollo y la implementación de software en entornos de nube híbrida, las organizaciones deben asegurarse de que sus cargas de trabajo en contenedores permanezcan a salvo de amenazas de seguridad externas e internas.

Los contenedores se pueden implementar en cualquier lugar, lo que crea nuevas superficies de ataque que rodean el entorno basado en contenedores. Las áreas de seguridad vulnerables incluyen imágenes de contenedores, registros de imágenes, tiempos de ejecución de contenedores, plataformas de orquestación de contenedores y sistemas operativos host.

Para empezar, las empresas deben integrar la seguridad de los contenedores en sus políticas de seguridad y en su estrategia general. Dichas estrategias deben incluir las mejores prácticas de seguridad junto con herramientas de software de seguridad basadas en la nube. Este enfoque holístico debe diseñarse para proteger las aplicaciones en contenedores y su infraestructura subyacente a lo largo de todo el ciclo de vida del contenedor.

Las mejores prácticas de seguridad incluyen una estrategia [zero trust](https://www.ibm.com/es-es/topics/zero-trust) que asume que la seguridad de una red compleja siempre está en riesgo de amenazas externas e internas. Además, los contenedores requieren un enfoque [DevSecOps.](https://www.ibm.com/es-es/topics/devsecops) DevSecOps es una práctica de desarrollo de aplicaciones que automatiza la integración de las prácticas de seguridad en cada fase del ciclo de vida de desarrollo del software, desde el diseño inicial hasta la integración, las pruebas, la entrega y la implementación.

Las organizaciones también deben aprovechar las herramientas de seguridad de contenedores adecuadas para mitigar los riesgos. Las soluciones de seguridad automatizadas incluyen la gestión de la configuración, el control de acceso, el análisis en busca de [malware](https://www.ibm.com/es-es/topics/malware) o [ciberataques](https://www.ibm.com/es-es/topics/cyber-attack), la segmentación de la red, la monitorización y mucho más. 

Además, hay herramientas de software disponibles para garantizar que las cargas de trabajo en contenedores se adhieran a los estándares regulatorios y de cumplimiento como RGPD, HIPAA, etcétera.