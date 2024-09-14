.
Las **pruebas automáticas de software** (o **pruebas automatizadas**) son un proceso en el cual scripts o herramientas de software se utilizan para ejecutar pruebas sobre una aplicación sin la intervención manual de un ser humano. El objetivo es validar que una funcionalidad específica del software funcione correctamente. En lugar de que los testers realicen las pruebas manualmente, las pruebas automáticas permiten ejecutar una serie de pruebas de manera repetitiva, rápida y precisa.

### **Características de las pruebas automáticas**:

1. **Ejecución programada**: Las pruebas automáticas se configuran para ejecutarse de forma regular, por ejemplo, después de cada actualización o cambio de código (en el caso de [[Integración continua]]/[[Entrega y despliegue Continuo]] **Continuous Integration/Continuous Delivery - CI/CD**).
2. **Uso de scripts o herramientas**: Los testers o desarrolladores crean scripts que simulan la interacción del usuario o verifican el comportamiento del sistema.
3. **Repetibilidad**: Se pueden ejecutar tantas veces como sea necesario, asegurando consistencia en los resultados sin el riesgo de errores humanos.
4. **Velocidad y eficiencia**: Las pruebas automatizadas suelen ser mucho más rápidas que las pruebas manuales, permitiendo cubrir más casos de prueba en menos tiempo.
5. **Cobertura más amplia**: Permite probar grandes conjuntos de datos, diferentes combinaciones de entradas y salidas, o ejecutar pruebas de regresión sin intervención manual.

### **Beneficios de las pruebas automáticas**:

- **Ahorro de tiempo**: Los equipos pueden ejecutar pruebas con mayor frecuencia y cubrir más áreas de la aplicación en menos tiempo.
- **Mayor precisión**: Reducen los errores humanos que pueden ocurrir durante las pruebas manuales.
- **Eficiencia**: Facilitan la identificación de errores en una etapa temprana del desarrollo, reduciendo los costos de corrección de defectos.
- **Escalabilidad**: Son útiles cuando hay grandes volúmenes de pruebas repetitivas, como pruebas de regresión que necesitan ejecutarse cada vez que el código se actualiza.
- **Soporte para CI/CD**: Son esenciales para los flujos de trabajo modernos de desarrollo continuo, donde se espera que el software sea probado y entregado rápidamente.

### **Tipos de pruebas que pueden automatizarse**:

1. **[[Pruebas unitarias]]**:
   - Verifican el comportamiento de componentes individuales del software, como funciones o métodos, en aislamiento.
   - Son fundamentales para validar que cada unidad de código funcione correctamente.

2. **[[Pruebas de integración]]**:
   - Aseguran que diferentes módulos o componentes del sistema funcionen bien juntos.
   - Verifican que la interacción entre ellos no genere errores.

3. **[[Pruebas de regresión]]**:
   - Se ejecutan para asegurarse de que los nuevos cambios en el código no afecten las funcionalidades existentes.

4. **[[Pruebas funcionales]]**:
   - Evalúan si el sistema funciona según las especificaciones y si las funcionalidades entregan los resultados esperados.

5. **[[Pruebas de desempeño o de rendimiento]]**:
   - Automatizan la medición de la velocidad, estabilidad y capacidad de respuesta de una aplicación bajo ciertas condiciones.

6. **[[Pruebas de carga y estrés]]**:
   - Evalúan cómo el sistema maneja grandes volúmenes de usuarios o datos, o condiciones extremas, para verificar su estabilidad y rendimiento.

### **Herramientas comunes para pruebas automáticas**:

- **[[Selenium]]**: Se utiliza para la automatización de pruebas de aplicaciones web.
- **[[JUnit]], [[NUnit]], [[PyTest]]**: Herramientas para realizar pruebas unitarias en Java, .NET y Python, respectivamente.
- **[[Cypress]]**: Framework para pruebas de frontend web.
- **[[Appium]]**: Herramienta para pruebas automatizadas de aplicaciones móviles.
- **[[Jenkins]]**: Herramienta de CI/CD que puede integrar pruebas automáticas en los procesos de desarrollo.

### **Proceso de implementación de pruebas automáticas**:

1. **Identificar [[Casos de prueba]]**: Determina qué partes del software son las mejores candidatas para ser automatizadas (pruebas repetitivas, críticas, o de alto riesgo).
2. **Escribir los scripts de prueba**: Usa el lenguaje de [[Scripting]] de la herramienta seleccionada para codificar las pruebas.
3. **Ejecutar las pruebas**: Configura las pruebas para que se ejecuten automáticamente en los momentos clave (por ejemplo, tras cada confirmación de código).
4. **Revisar resultados**: Analiza los reportes generados por las pruebas para identificar errores o fallos.
5. **Mantener los scripts**: A medida que el software evoluciona, los scripts de prueba deben ser actualizados para reflejar los cambios en la funcionalidad.

### **Cuándo no usar pruebas automáticas**:

- **[[Pruebas de usabilidad]]**: Requieren la interacción y juicio humano, por lo que no se pueden automatizar.
- **[[Pruebas exploratorias]]**: Este tipo de pruebas se basa en la creatividad y el descubrimiento de errores inesperados, lo cual es difícil de automatizar.