.
![[Pasted image 20240910091800.png]]

El **ciclo de vida de las pruebas de software** (Software Testing Life Cycle o [[STLC]]) es un proceso estructurado que define las etapas involucradas en la planificación, ejecución y evaluación de las pruebas en el desarrollo de software. Cada fase del ciclo de vida tiene objetivos específicos y entregables, y está orientada a garantizar que el software cumple con los requisitos funcionales y no funcionales antes de ser lanzado.

### Fases del ciclo de vida de las pruebas de software (STLC):

1. **Análisis de requerimientos**:
   - En esta fase, el equipo de pruebas colabora con analistas, desarrolladores y otras partes interesadas para entender y revisar los **requisitos funcionales y no funcionales** del software.
   - Se identifican los aspectos que deben ser probados y se aclaran los detalles con el equipo de desarrollo.
   - **Entregable**: [[Documento de requisitos de prueba]], que contiene los requerimientos y casos de prueba identificados.

2. **Planificación de las pruebas**:
   - Se elabora un plan de pruebas basado en el análisis de los requisitos. Este plan detalla el enfoque que se seguirá para las pruebas, los tipos de pruebas a realizar, los recursos necesarios, el cronograma y el entorno de pruebas.
   - Se definen los criterios de entrada y salida para las pruebas, y se identifican los riesgos.
   - **Entregable**: **[[Plan de pruebas de software]]** que cubre la estrategia, el alcance, los riesgos y la asignación de responsabilidades.

3. **Diseño de casos de prueba**:
   - En esta fase, se crean **[[Casos de prueba]] detallados** para validar los diferentes aspectos del software. Cada caso de prueba describe las entradas, condiciones de ejecución y resultados esperados.
   - Se preparan también los **datos de prueba** que serán utilizados en las pruebas, asegurando que cubran tanto escenarios positivos como negativos.
   - **Entregable**: Conjunto de **casos de prueba** y datos de prueba documentados.

4. **Configuración del entorno de pruebas**:
   - En esta fase, se prepara el entorno en el que se ejecutarán las pruebas. Esto incluye la configuración del hardware, software, red y otras dependencias necesarias para que las pruebas se realicen de manera efectiva.
   - Puede ser necesario preparar entornos específicos para pruebas funcionales, de rendimiento o de compatibilidad.
   - **Entregable**: **Entorno de pruebas configurado y listo** para la ejecución.

5. **Ejecución de pruebas**:
   - Se ejecutan los casos de prueba creados en la fase anterior. Los resultados de cada ejecución se comparan con los resultados esperados.
   - Si se encuentran fallos o errores, se documentan en un informe y se notifican al equipo de desarrollo para su corrección.
   - **Entregable**: **Registro de resultados de pruebas** y reportes de defectos.

6. **Cierre de pruebas**:
   - En esta fase, se evalúa si todas las pruebas planificadas han sido ejecutadas y si los criterios de salida se han cumplido (por ejemplo, el número aceptable de fallos o defectos).
   - Se genera un **informe de cierre de pruebas**, que incluye un resumen de los casos de prueba ejecutados, los defectos encontrados y su estado, así como una evaluación general de la calidad del software.
   - **Entregable**: **Informe de cierre de pruebas** y métricas del proceso de prueba.

7. **Post-evaluación y mantenimiento**:
   - Después de la entrega del software, se sigue monitoreando su desempeño en entornos reales.
   - En caso de que se identifiquen nuevos defectos o problemas en producción, se realizan pruebas de mantenimiento para corregirlos y asegurar que los cambios no introduzcan nuevos errores.
   - **Entregable**: Actualizaciones de los casos de prueba y mantenimiento de la calidad del software.

### **Resumen de las fases del STLC**:
| Fase                          | Actividades principales                                                   | Entregables                           |
| ------------------------------ | ------------------------------------------------------------------------- | ------------------------------------- |
| **Análisis de requerimientos**  | Revisión de requisitos y definición de pruebas                            | Documento de requisitos de prueba     |
| **Planificación de pruebas**    | Estrategia de pruebas, cronograma, asignación de recursos                 | Plan de pruebas                       |
| **Diseño de casos de prueba**   | Creación de casos de prueba y preparación de datos                        | Casos de prueba, datos de prueba      |
| **Configuración del entorno**   | Preparación del entorno necesario para ejecutar las pruebas               | Entorno de pruebas                    |
| **Ejecución de pruebas**        | Ejecución de los casos de prueba, identificación y reporte de defectos    | Resultados de pruebas, reportes de defectos |
| **Cierre de pruebas**           | Evaluación de pruebas completadas y generación de informes                | Informe de cierre de pruebas          |
| **Mantenimiento**               | Pruebas posteriores a la entrega (en caso de correcciones o actualizaciones) | Actualizaciones de pruebas            |

### **Importancia del STLC**:

- **Calidad del software**: Siguiendo un proceso estructurado de pruebas, se asegura que el software sea probado exhaustivamente y se detecten la mayoría de los defectos antes de la entrega.
- **Eficiencia en las pruebas**: Cada fase está planificada y documentada, lo que permite realizar las pruebas de manera más eficiente y organizada.
- **Comunicación clara**: Al tener un ciclo de vida bien definido, todas las partes involucradas (desarrolladores, testers, gerentes de proyecto) tienen una idea clara de los objetivos, tareas y plazos.

El ciclo de vida de las pruebas es fundamental para asegurar que el producto final entregue una alta calidad y satisfaga las necesidades de los usuarios.