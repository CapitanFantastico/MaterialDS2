.
					 ![[Fig.Triángulo de hierro de los proyectos.png]] 


- Las pruebas ayudan a validar que el alcance del software se ajusta a los **requerimientos** establecidos

- Las pruebas ayudan a NO salirnos de los **costos y tiempo** proyectados en el plan inicial

- Siendo así, las pruebas nos ayudan a conseguir una buena **calidad del software**

- Escribir un software sin defectos es **imposible**

- Especificar los requisitos claros y completos es muy **difícil**

- NO se puede demostrar que un software está libre de errores

- Las pruebas garantizan una **disminución** significativa de los **fallos** de software

- Las pruebas garantizan la **retroalimentación** del software lo antes posible

- NO se deberían probar trivialidades

- Las pruebas NO son depuración, la depuración no es efectiva

- Informar de forma temprana los riesgos: bajo rendimiento, módulos con alto índice de fallos, para tomar acciones

- Fases mentales ante las pruebas

	- Fase 0 (Muy mal): 
		- Pensar que no hay diferencia entre pruebas y depuración, y que a parte del soporte a la depuración, las pruebas no tienen ningún propósito

	- Fase 1 (Mal):
		- Pensar que el objetivo de las pruebas es demostrar que el software funciona
	
	- Fase 2 (Regular): 
		- Pensar que el objetivo de las pruebas es demostrar que el sofware NO funciona
	
	- Fase 3 (Bien):
		- Pensar que el propósito de la prueba NO es demostrar nada, sino **reducir el riesgo percibido cuando el software no trabaja en valores aceptables**
	
	- Fase 4 (Muy bien):
		- Pensar que las pruebas no son un acto sino **una disciplina que arroja software de bajo riesgo sin mucho esfuerzo en pruebas**

- [[Correspondencia entre valores y pruebas del software]] 

---

- https://marceloandrader.github.io/blog/2021/03/23/parte-1-introducci%C3%B3n-a-pruebas-de-software/
# Parte 1: Introducción a las pruebas de software

Cuando iniciamos en el mundo del desarrollo de software, generalmente estamos muy enfocados en hacer que una característica funcione, o arreglar un bug y dedicamos tiempo en un ciclo de: pruebo manualmente lo que los usuarios me piden, funciona? no, verifico que cambios necesito, hago los cambios en el código y vuelvo a probar que el requerimiento funciona, funciona? si, lo pongo en producción.

Este ciclo de desarrollo está bien para proyectos pequeños que se van a quedar pequeños, y no críticos. El problema está en que no somos adivinos y no podemos saber a futuro que lo que estamos desarrollando va a quedarse pequeño y no crítico para el negocio.

Generalmente no pasa eso, los desarrollos se realizan por algo y mientras más se usa más crítico se vuelve. Por esta razón es importante desde los inicios de un nuevo proyecto tener una ==infraestructura adecuada para tener pruebas automatizadas== que las puedan ejecutar los desarrolladores localmente, y también se puedan ejecutar en los sistemas de [[Integración continua]] . Adicional a [[Pruebas automáticas]] es muy importante mantener [[Pruebas manuales]] ya que las pruebas automáticas generalmente sólo verifican lo que el desarrollador piensa que se debe probar.


# ¿Qué son pruebas de software?

Las Pruebas de software, son ==procesos cíclicos== que permiten a los desarrolladores verificar si un requerimiento o cambio en el sistema es correcto o no. Adicionalmente permite verificar que una versión específica del software tenga todos los requerimientos solicitados. También pueden ayudar a verificar que el software puede funcionar correctamente en diferentes medios o con diferentes integraciones, como por ejemplo en diferentes sistemas operativos, o en diferentes versiones de software base.

# ¿Por qué son importantes las pruebas de software?

Sin pruebas me parece que es imposible conocer si estamos haciendo algo correcto, no creo que nadie pueda simplemente cambiar código y ponerlo en producción sin siquiera verificar en su ambiente que el cambio hace lo que debe hacer.

Aún en ambientes donde no se tienen pruebas automatizadas, las pruebas manuales son la única forma de verificación de que el software funcione luego de realizar un cambio, y son válidas pero estas ==no escalan== con el software y su complejidad.

# ¿Cómo funcionan las pruebas de software?

Hay muchas formas de probar software, tenemos [[Pruebas manuales]], [[Pruebas automáticas]], [[pruebas unitarias]], [[pruebas de integración]], [[Pruebas de aceptación de usuario]], etc.

==Generalmente los desarrolladores primero deciden qué comportamiento o característica requiere una validación, planifican cómo se puede verificar que el software funciona como se detalla, crea un script de prueba para verificar y ejecuta este script cada vez que hace cambios en el código hasta confirmar que funciona.==

La parte de “crear un script de prueba”, es así tanto para pruebas manuales o automáticas, la diferencia radica en que para las manuales lo crea en su mente y en las automáticas lo crea en un archivo de código. ==Como se puede ver, las pruebas manuales cumplen el mismo papel que las automáticas pero de la forma en la que se crean no se pueden compartir con el equipo de trabajo y son muy lentas en ejecutar.==

# Beneficios de pruebas en el software

**Asegura funcionalidad completa** Asegura que todos los requerimientos desarrollados estén presentes en el producto final.

**Alerta temprana** Permite saber muy temprano en el desarrollo de software acerca de defectos que pueden afectar negativamente al usuario.

**Reconstrucción de código** Si tenemos un conjunto de pruebas muy amplio, es mucho más fácil hacer reconstrucciones internas del código para ==mejorar arquitectura== [[Refactorización]] sin afectar al usuario final.

Estos son algunos de los beneficios, debe haber muchos más. Pero lo más importante que me gustaría compartir es que las pruebas son muy críticas en el desarrollo, y que está bien si lo hace manualmente por ahora, pero que deben comenzar a planificar un cambio en sus mentes y en sus procesos para incorporar pruebas automáticas, al principio es muy duro, van a pensar que escribir los tests los hace más lentos, que no son importantes, que hacen más complejo el desarrollo, pero una vez interiorizado el desarrollo con pruebas automáticas van a ver atrás y preguntarse ¿cómo realizaron tantos sistemas sin pruebas automáticas? Les va a parecer una locura. Sí tienen que cruzar ese valle oscuro, pero al otro lado hay cosas muy buenas, como tranquilidad de que no vas a dañar nada en producción, aumentar la calidad de tus productos para que el cliente ya no sea el departamento de QA.

---
- https://marceloandrader.github.io/blog/2021/04/01/parte-2-tipos-de-pruebas-de-software/

# Parte 2: Tipos De Pruebas de Software

# [[Pruebas de caja negra]]

Toda la arquitectura interna del sistema es oculta a quien lo prueba. Es decir el usuario de prueba solo conoce **lo que el producto se supone que tiene que hacer** pero no **cómo lo hace**. Los usuarios de prueba solo observa los resultados o el comportamiento del producto y no necesitan ser programadores. Generalmente estas pruebas las realizan los usuarios finales o personas que no son parte del proceso de desarrollo.

# [[Pruebas de caja blanca]]

Es lo opuesto a las anteriores, es decir que quien prueba conce la estructura interna del software. Estos usuarios de prueba evaluan la lógica de los programas a través de casos de prueba específicos. Al auditar el flujo de las entradas de prueba, el usuario puede verificar que todos los casos han sido manejados correctamente.

Otra clasificación general para los métodos de pruebas es pruebas manuales versus pruebas automatizadas. Muchas tipos de pruebas se pueden hacer tanto manualmente como de forma automatizada. Esta distinción indica como la prueba es completada.

# [[Pruebas manuales]]

Una persona como probador toma el rol de un usuario final del software y chequea casos de prueba uno por uno. Es una forma tradicional de verificar el software y en algunos casos es necesario porque puede detectar cosas que no pueden las pruebas automatizadas como ==apariencia visual de un sitio==. Pero esta forma de ejecutar pruebas no escala, cuando el software es muy grande y complejo no se puede volver a probar todo el sistema.

# [[Pruebas automaticas]] 

Es el proceso de usar software denominado un framework de pruebas para crear casos de pruebas que se ejecutan y comparan el resultado del programa con el resultado esperado. Algunos ejemplos de este tipo de frameworks son [[Selenium]], [[Codeception]], [[Cucumber]].

Ahora revisaremos las metodologías de pruebas clasificadas entre funcionales y no funcionales, la diferencia está en si la prueba se enfoca en el comportamiento del software o su operación interna.

# [[Pruebas funcionales]]

Son un tipo de [[Pruebas de caja negra]] que generan los casos de prueba usando los [[Requerimientos y especificaciones del software]].

Algunas de estas metodologías incluyen:

- [[Pruebas unitarias]] (Unit testing)
- [[Pruebas de integración]] (Integration testing)
- [[Pruebas de sistema]] (System testing)
- [[Pruebas de aceptación de usuario]] de usuario (Acceptance testing)
- [[Pruebas de regresión]] (Regression testing)
- [[Pruebas de humo]] (Smoke testing)

# [[Pruebas no funcionales]]

Son un tipo de pruebas que verifican cómo un programa opera en lugar de si un comportamiento es correcto. Por ejemplo un test no funcional prueba que tan bien un programa se ejecuta con ==una carga alta de transacciones, o mientras funciona por un largo tiempo.==

Las pruebas no funcionales más usadas son:

- [[Pruebas de desempeño o de rendimiento]] (Performance testing)
- [[Pruebas de seguridad]] (Security testing)
- [[Pruebas de usabilidad]] (Usability testing)
- [[Pruebas de compatibilidad]] (Compatibility testing)
- [[Pruebas de estrés]] (Stress or load testing)


---

## Organización jerárquicamente de las pruebas de software

![[Fig.Organización Jerárquica de las Pruebas.png]]


### **1. [[Pruebas Unitarias]]** 
**Nivel más bajo y básico de la jerarquía.**
- **Enfoque**: Verificar el correcto funcionamiento de las unidades individuales de código (funciones, métodos, clases).
- **Propósito**: Asegurar que cada componente, de manera aislada, produzca los resultados esperados.
- **Responsabilidad**: Desarrolladores.
  
---

### **2. [[Pruebas de Integración]]** [[QA]] [[TAE]] 
**Segundo nivel, se centra en la integración de los módulos.**
- **Enfoque**: Probar la interacción entre varios módulos o componentes para asegurarse de que funcionen bien juntos.
- **Propósito**: Identificar problemas en las interfaces o interacciones entre componentes.
- **Responsabilidad**: Desarrolladores y equipos de [[QA]] (calidad).

---

### **3. [[Pruebas de Sistema]]** [[QA]] [[TAE]] 
**Tercer nivel, abarca todo el sistema.**
- **Enfoque**: Validar el comportamiento del sistema completo, verificando que todas las funcionalidades trabajen juntas como se espera.
- **Propósito**: Asegurar que el sistema, en su totalidad, cumpla con los requisitos funcionales y no funcionales.
- **Responsabilidad**: Equipos de [[QA]] o testers dedicados.
  
---

### **4. [[Pruebas de aceptación de usuario]]** [[UAT]] [[QA]] 
**Cuarto nivel, se centra en la validación del sistema frente a los requisitos del cliente.**
- **Enfoque**: Validar que el sistema satisface los criterios de aceptación definidos por el cliente o el negocio.
- **Propósito**: Garantizar que el producto final sea adecuado para el uso real por parte del cliente o usuario final.
- **Responsabilidad**: Clientes, usuarios finales o equipos de QA.

---

### **Otras pruebas complementarias**:

- **[[Pruebas de Regresión]]**: Son parte de la jerarquía pero no tienen un nivel específico; se ejecutan tras realizar cambios en el código para asegurar que no haya introducido nuevos errores.

- **[[Pruebas de Desempeño o de Rendimiento]]**: Pueden realizarse después de las pruebas de integración o de sistema para garantizar que la aplicación maneje la carga esperada.
  
- **[[Pruebas de Usabilidad]]**: Se llevan a cabo para evaluar la facilidad de uso de la aplicación, y se ejecutan típicamente después de las pruebas de sistema.

- **[[Pruebas de Seguridad]]**: Generalmente realizadas en la fase de pruebas de sistema o de aceptación para identificar vulnerabilidades.

- **[[Pruebas de Compatibilidad]]**: Verifican si la aplicación funciona correctamente en diferentes entornos, sistemas operativos, o versiones del lenguaje.

- **[[Pruebas Exploratorias]]**: Aunque no tienen un lugar fijo en la jerarquía, pueden realizarse en cualquier nivel, dependiendo de la necesidad de descubrir comportamientos inesperados.

---
- https://marceloandrader.github.io/blog/2021/04/09/parte-3-proceso-de-creaci%C3%B3n-de-pruebas-y-mejores-pr%C3%A1cticas/

# Parte 3: Proceso de creación de pruebas y mejores prácticas

En esta parte vamos a revisar el proceso para la creación de pruebas y algunas mejores prácticas.


# [[Ciclo de vida de las pruebas]]

Cualquiera sea la metodología para las diferentes partes del sistema, se espera poder seguir un proceso que permita mantenernos enfocados en los requerimientos del producto y en desarrollar características una a la vez. 

Este proceso tiene 6 pasos:

1. **[[Análisis de requerimientos]]**:  El equipo de desarrollo se reune con los usuarios para revisar que requerimientos y características va a tener el producto. Por cada característica el grupo analiza una especificación que pueda ser probada y que permita indicar que se ha hecho correctamente.
    
2. **[[Plan de pruebas]]**: Aquí el equipo de desarrollo analiza la forma específica cómo se desarrollaran las pruebas. Puntos comunes son: qué recursos se necesitan? qué métricas cuantitativas podemos usar para probar el requerimiento? y cuáles factores de riesgo iniciales pueden afectar el resultado? Lo más importante es tener las métricas y los casos específicos muy enlazados a la especificación del producto.
    
3. **[[Desarrollo de los casos de prueba]]**: En este paso ya se desarrolla los casos de prueba o el conjunto de pruebas que verifica que el requerimiento se ha completado. Aquí usamos los procesos de pruebas funcionales para pruebas generales, o procesos de pruebas no funcionales para requerimientos específicos como pruebas de usabilidad.
    
4. **[[Configuración de ambiente de pruebas]]**: Se creará un ambiente de pruebas. Si el producto se va a instalar en varias plataformas, se requiere al menos un ambiente de pruebas por cada plataforma. Esto se logra generalmente con frameworks de pruebas y algunas máquinas virtuales. O a través de un sistema de integración continua como [[GitHub actions]] 
    
5. **[[Ejecución de las pruebas]]**: En este paso se ejecuta las pruebas y se guardan todas las métricas decididas.
    
6. **[[Análisis de resultados de pruebas]]**: En este punto se verifica cómo estuvo la ejecución de las pruebas. Es posible que para los próximos tests se requieran diferentes métricas, un ambiente de pruebas más refinado (diferentes dependencias) y regresar al desarrollo de la solución para mejorar las métricas alcanzadas.
    

Todo este proceso es **iterativo** y generalmente no se lo ve como pasos, si te dan un requerimiento generalmente en tu cabeza analizas que tipos de pruebas puedes ejecutar para revisar la funcionalidad, qué voy a medir como parte del desarrollo del producto, se genera el caso de prueba usando [[Red-Green development]] que es escribo el test, lo ejecuto, da error **RED**, implemento el código mínimo para pasar la prueba y hacerlo **GREEN** y sigo implementado el programa al mismo tiempo que el test.

# Mejores prácticas de pruebas de software

- **No usar solamente pruebas automatizadas** Las pruebas automatizadas solo verifican defectos que el programador sabe y busca. Al menos se debe tener un paso de pruebas manuales para verificar defectos inesperados.
    
- **Escribir [[Casos de prueba]] en lenguaje simple o pseudocódigo** Esto permite compartir la verificación de las pruebas con los miembros no técnicos del equipo.
    
- **Usar solo ambientes de pruebas controlados y aislados para evitar interferencia externa** Es preferible trabajar en un ambiente repetible como un contenedor [[Docker]] , ya que se sabe específicamente qué está instalado en ese contenedor, no ejecutarlos en la máquina local ya que puede haber dependencias no controladas.
    
- **Escojer Métricas específicas y cuantificables** De esta forma se puede llevar un registro para agregar a los reportes.
    
- **Probar antes del paso de [[QA]]** Esto permite probar siempre durante el desarrollo y no solo al final, ayuda a ahorrar mucho tiempo al probar los componentes centrales bien desde el principio.
    
- **Crear pruebas incrementales** Hay que ir agregando condiciones dentro de la prueba para verificar dónde el programa falla.
    
- **Maximizar [[Cobertura de pruebas de software]]** Lo ideal es llegar a un 100% de cobertura, que quiere decir que las pruebas ejecutan todo el código fuente. De tal forma que todos los posibles caminos dentro del programa son ejecutados por las pruebas.
    
- **Hacer que otro desarrollador cree las pruebas de integración o aceptación** Esto permite evitar un sesgo de confirmación, ya que los casos de pruebas son escritos por alguien más.
    
- **Usar nombres útiles** Los casos se deben nombrar de acuerdo a la condición y requerimiento de la prueba. Evitar nombres como test1 o performanceTest, usar algo más específico por ejemplo calculoDeHorasParaEmpleadosConTurnosDeCambioDeDia
    
- **Usar herramientas de pruebas de software** En el mercado hay un sin número de herramientas que permiten realizar las pruebas analiza la que mejor se adapte a tu equipo.
    
---

- https://marceloandrader.github.io/blog/2021/04/13/parte-4-ejemplo-pr%C3%A1ctico-de-pruebas-de-software/

# Parte 4: Ejemplo práctico de Pruebas De Software

En esta artículo vamos a aplicar los conceptos anteriors al crear una aplicación pequeña en laravel.

# Requerimiento funcional de la aplicación

La aplicación va a servir a una escuela, y se requiere registrar a los estudiantes los datos a registrar son nombres completos, ciudad y fecha de nacimiento. Se debe validar que los estudiantes sean menores de 18 años. Y que tenga todos los datos completos.

# Crear la aplicación

Este no es un tutorial para aprender laravel, pero voy a poner los comandos que use para generar una [aplicación inicial](https://github.com/marceloandrader/laravel-example-software-testing).

```bash
$ composer create-project laravel/laravel laravel-example-software-testing
$ cd laravel-example-software-testing
$ php artisan serve
```

Editar el archivo .env para usar sqlite `DB_CONNECTION=sqlite` y `DB_DATABASE=/full-path-a-la-base/software-testing-dev.sqlite` y crear la base de datos usando `sqlite3 /full-path-a-la-base/software-testing-dev.sqlite`.

[Github commit con cambio de configuración de la base](https://github.com/marceloandrader/laravel-example-software-testing/commit/42b506bcec7141c978d88ae387f7fe25c82ae90f)

Por defecto al crear una nueva aplicación, también se crean 2 tests de ejemplo  
una prueba unitaria y otra funcional:

![[Pasted image 20240909153434.png]]

También voy a crear un modelo denominado Estudiante con los campos solicitados, para poder almacenar en una base de datos.

```bash
$ php artisan make:model -m Estudiante
$ php artisan migrate
```

[Github commit con modelo y migración](https://github.com/marceloandrader/laravel-example-software-testing/commit/ee937a15951e2e050eef9e55ef557d6c364c9fd3)

# Casos de prueba

## [[Prueba unitaria]]

Para poder crear un estudiante debemos primero validar si su edad es menor a 18 años. Como habíamos visto en la parte 2 generalmente las pruebas funcionales se comienzan desde lo más pequeño hasta lo más grande. Vamos a iniciar con una prueba unitaria para calcular la edad del estudiante. Para esto voy a generar un test unitario con: `php artisan make:test --unit CalcularEdadTest` dentro de este test voy a comenzar creando un objeto de tipo Estudiante seteando una fecha de nacimiento y llamando a la funcion `getEdad()` por supuesto este test va a fallar al llamar a `php artisan test tests/Unit/CalcularEdadTest.php` al realizar esto también voy formando mi API pública ya que la forma de llamar ciertas funciones desde el test es cómo se llamaran las funciones desde la aplicación.

Regreso a mi modelo y creo la función `getEdad` que reste la fecha actual con la fecha de nacimiento y obtengo la edad del estudiante.

[Github commit con prueba unitaria e implementación](https://github.com/marceloandrader/laravel-example-software-testing/commit/cf80fc35fd8d26141453734e401c338463219985)

Como pueden observar en el test, se trata de verificar la mayor cantidad de posibilidades en nuestro caso probe con 2 fechas y sin fecha para verificar que la prueba pase en los 3 casos.

![[Pasted image 20240909153510.png]]
## Prueba de Integración

Un ejemplo de prueba de integración es usar más de 1 componente, en este caso podemos probar el uso de la clase Estudiante ya en el contexto de creación desde un controlador. Para lo cual crearemos uno usando `php artisan make:controller --model=Estudiante EstudianteController` y comenzaré a probar la función create. Pero antes de comenzar en el controlador crearé una prueba de integración con `php artisan make:test CrearEstudianteTest`. Al realizar un post con datos a /estudiantes que es donde montamos el recurso en app/routes/web.php el error fallará con error status code 200 es diferente a 201 esperado.

Implemento la función `store` en el controlador tomando los datos del request y creando un estudiante.

[Github commit con prueba de integración e implementación](https://github.com/marceloandrader/laravel-example-software-testing/commit/88850fd140f1cfd6f9f631868642c76c9f22c3ea)

Pero aun nos falta realizar la prueba con un estudiante que quiera registrarse que no sea menor de edad. Actualizamos el test para enviar una persona adulta y al ejecutar va a funcionar sin problema, debemos cambiar el test para esperar un resultado [422](https://httpstatuses.com/422) entidad no procesable.

[Github commit con validación de edad en controlador](https://github.com/marceloandrader/laravel-example-software-testing/commit/791606c9bb2fd9536087c1bbffbca379b03052bf)

![[Pasted image 20240908203842.png]]
## Pruebas de Sistema

Para realizar una prueba de sistema se debe realizar la prueba como si fuera un usuario real manejando un browser, para esto existen varias herramientas, en nuestro caso no he creado pantallas de usuario para poder interactuar con la aplicación por lo que no puedo todavía crear este tipo de pruebas. Pero una vez hecho ese paso en laravel se puede instalar [dusk](https://laravel.com/docs/8.x/dusk) para realizar las pruebas usando chromedriver.

El API de dusk es muy fluida, puedes crear sesiones de usuario llenar formularios etc.

## Pruebas de Aceptación

Estas las debe realizar alguien adicional al desarrollador, en nuestro caso que es un ejemplo pequeño y se requiere conocimientos técnicos, la prueba la puede realizar otro desarrollador usando alguna herramienta como [curl](https://marceloandrader.github.io/blog/2021/02/03/curl-la-navaja-suiza-de-los-protocolos-de-internet/) o [imsomnia](https://insomnia.rest/) para realizar la llamada a crear un estudiante.

# Pruebas no funcionales

Se puede realizar varias pruebas no funcionales a nuestra aplicación de ejemplo.

Para el caso de pruebas de desempeño se puede probar el servicio de creación de estudiantes usando [[wrk]] (https://github.com/wg/wrk) para verificar la cantidad de peticiones que puede recibir.

No podemos realizar pruebas de seguridad ya que este servicio no está protegido todavía, pero una vez que se agregue un token JWT o algún otro, se puede usar una herramienta de pentesting para verificar. Adicional como parte de medida de seguridad del código se puede usar `composer outdated` para escanear dependencias desactualizadas que generalmente son la causa de problemas de seguridad.

Por motivos de tiempo hay otros tipos de pruebas que no estamos tomando en cuenta, pero si comienzan con las pruebas anteriormente mencionadas ya están bastante bien, y su código puede seguir creciendo en complejidad y pueden estar tranquilos al realizar cambios ya que tienen una buena batería de tests que puede identificar errores fácil y rápidamente.

---

## Glosario
[[ISTQB]] 
[[TAE]] 

