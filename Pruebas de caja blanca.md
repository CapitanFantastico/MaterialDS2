.
Las **pruebas de caja blanca** (también conocidas como **pruebas estructurales** o **pruebas de cristal**) son un enfoque de pruebas de software en el que el tester tiene acceso completo al **código fuente** del sistema y lo utiliza para diseñar casos de prueba. Este tipo de pruebas se enfoca en verificar la lógica interna, las estructuras de control y los flujos de datos del software, asegurando que el código funcione correctamente y esté libre de errores.

### **Características clave de las pruebas de caja blanca**:

1. **Conocimiento del código**:
   - El tester necesita tener acceso al código fuente y debe comprender su lógica, estructura y algoritmos para diseñar casos de prueba efectivos.
   
2. **Validación de la lógica interna**:
   - Se revisan las estructuras de control (bucles, condiciones, bifurcaciones) y el flujo de datos dentro del sistema para detectar posibles errores o comportamientos incorrectos.

3. **[[Cobertura de código]]** **:
   - Se busca asegurar que todas las rutas y combinaciones posibles en el código hayan sido ejecutadas y probadas. Las métricas de cobertura son clave (cobertura de líneas, cobertura de decisiones, cobertura de ramas, etc.).

4. **Pruebas de "caja transparente"**:
   - A diferencia de las pruebas de caja negra, las pruebas de caja blanca permiten al tester "ver" dentro del sistema y analizar el código directamente para encontrar errores.

### **Objetivo de las pruebas de caja blanca**:
El principal objetivo es garantizar que todas las rutas y bloques del código funcionen según lo esperado. También se busca optimizar el rendimiento y la eficiencia del software, detectando posibles problemas de lógica, seguridad o rendimiento.

### **Aspectos que cubren las pruebas de caja blanca**:

1. **[[Cobertura de código]]**: 
   - Se evalúa qué porcentaje del código ha sido probado mediante casos de prueba. Existen varios tipos de cobertura:
     - **Cobertura de sentencias**: Verifica que todas las líneas de código se ejecuten al menos una vez.
     - **Cobertura de ramas o decisiones**: Asegura que cada bifurcación en el código (condiciones if/else) sea ejecutada y probada en todos sus caminos posibles.
     - **Cobertura de condiciones**: Garantiza que todas las condiciones individuales en decisiones complejas se prueben por separado.

2. **Verificación de flujos de datos**:
   - Se revisa cómo las variables y los datos fluyen a través del código, asegurando que se inicialicen correctamente, se utilicen de manera adecuada y no se presenten fugas de memoria.

3. **Análisis de ciclos y bucles**:
   - Se prueban todas las estructuras de bucles y ciclos para asegurarse de que funcionen correctamente y no se produzcan bucles infinitos o cuellos de botella.

4. **Detección de vulnerabilidades de seguridad**:
   - Se puede usar para identificar problemas de seguridad en el código, como validaciones insuficientes, posibles ataques de inyección SQL, o acceso inseguro a datos.

### **Técnicas para las pruebas de caja blanca**:

1. **Pruebas de caminos básicos**:
   - Consiste en identificar todos los caminos posibles que el flujo de control del programa puede tomar y diseñar casos de prueba para cubrir cada uno de ellos.

2. **Pruebas de flujo de datos**:
   - Se analiza cómo las variables se inicializan, utilizan y destruyen durante la ejecución del programa. Se buscan errores como variables no inicializadas, uso de variables innecesarias, o fugas de memoria.

3. **Pruebas de condiciones y bucles**:
   - Aseguran que las estructuras de control condicionales y los bucles en el código se comporten correctamente en todas las situaciones posibles, probando casos límite, iteraciones mínimas, máximas y medias.

4. **Análisis estático**:
   - Se examina el código sin ejecutarlo, en busca de defectos sintácticos, vulnerabilidades de seguridad, o estructuras ineficientes.

5. **Cobertura de mutantes**:
   - Se realizan pequeñas modificaciones intencionales en el código (mutaciones) para verificar si los casos de prueba pueden detectar estos cambios. Si los casos de prueba no fallan con estas modificaciones, puede ser una señal de que no son lo suficientemente exhaustivos.


### **Ventajas de las pruebas de caja blanca**:

- **Cobertura exhaustiva del código**: Se asegura que se prueben todas las rutas posibles del software, lo que ayuda a detectar errores difíciles de encontrar mediante pruebas de caja negra.
- **Detección temprana de errores**: Al analizar el código desde el inicio, se pueden detectar errores antes de que lleguen al usuario final, lo que reduce el costo de correcciones.
- **Optimización del rendimiento**: Permiten identificar cuellos de botella y oportunidades para mejorar la eficiencia del software, dado que se analiza el flujo interno del sistema.

### **Desventajas de las pruebas de caja blanca**:

- **Requieren conocimiento del código**: Es necesario que el tester tenga habilidades técnicas avanzadas y entienda la estructura y lógica del código, lo que puede hacer que las pruebas sean más complejas.
- **Tiempo y costo**: Debido a la exhaustividad de las pruebas y el análisis del código, pueden requerir más tiempo y recursos que otros enfoques.
- **No detecta errores funcionales**: Al enfocarse en la estructura interna del software, puede no detectar si el sistema cumple correctamente con las expectativas del usuario final o los requisitos funcionales.

### **Ejemplo de pruebas de caja blanca**:

Supongamos que se quiere probar una función que determina si un número es par o impar:

```python
def es_par(numero):
    if numero % 2 == 0:
        return True
    else:
        return False
```

Un test de caja blanca analizaría todas las rutas posibles en esta función, creando casos de prueba para cubrir cada una:

1. **Caso de prueba 1**: Se pasa un número par (por ejemplo, 4).
   - Camino: La condición `numero % 2 == 0` es verdadera, por lo que se debe retornar `True`.

2. **Caso de prueba 2**: Se pasa un número impar (por ejemplo, 3).
   - Camino: La condición `numero % 2 == 0` es falsa, por lo que se debe retornar `False`.

Además de validar el comportamiento correcto para entradas válidas, también podría analizarse cómo la función maneja entradas inusuales, como números negativos, cero o incluso no enteros.

### **Conclusión:**
Las pruebas de caja blanca son una herramienta poderosa para verificar la calidad interna del código, ayudando a asegurar que todos los caminos posibles dentro del sistema se comporten como se espera. Son cruciales para detectar problemas relacionados con la lógica y el rendimiento del código, y son complementarias a las pruebas de caja negra, que se centran más en las funcionalidades visibles para el usuario final.