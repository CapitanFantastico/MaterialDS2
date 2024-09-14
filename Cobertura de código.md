.
- Ver https://www.atlassian.com/es/continuous-delivery/software-testing/code-coverage

En el contexto de pruebas de software, el término **cobertura** se refiere al grado en que el código fuente de una aplicación ha sido ejecutado durante el proceso de pruebas. Es una métrica utilizada para evaluar qué parte del código ha sido probada, identificando secciones no cubiertas por las pruebas. Cuanto mayor sea la cobertura, mayor es la confianza de que las pruebas han validado adecuadamente el comportamiento del sistema.

### Tipos comunes de cobertura en pruebas:

1. **Cobertura de declaraciones (Statement Coverage)**:
   - Verifica cuántas líneas o declaraciones del código se han ejecutado durante las pruebas.
   - Objetivo: Asegurarse de que todas las instrucciones individuales han sido probadas al menos una vez.

2. **Cobertura de ramas (Branch Coverage)**:
   - Verifica cuántas de las posibles ramas de decisión (como las condicionales `if-else`) han sido ejecutadas.
   - Objetivo: Probar todas las posibles rutas de decisión en el código.

3. **Cobertura de condiciones (Condition Coverage)**:
   - Verifica si todas las condiciones individuales en una expresión lógica (por ejemplo, las subcondiciones de un `if`) han sido probadas en todas sus combinaciones posibles (verdadero o falso).
   - Objetivo: Asegurar que cada parte de una expresión condicional haya sido evaluada con todos los resultados posibles.

4. **Cobertura de bucles (Loop Coverage)**:
   - Verifica si todos los bucles (`for`, `while`) han sido ejecutados y probados en todas las condiciones posibles (por ejemplo, si el bucle se ejecuta ninguna, una, o varias veces).
   
5. **Cobertura de caminos (Path Coverage)**:
   - Verifica si todas las combinaciones posibles de caminos de ejecución han sido probadas. Es una métrica más exhaustiva, ya que examina todas las rutas posibles que el flujo del programa puede seguir.
   
### Beneficios de la cobertura en pruebas:

- **Identificación de áreas no probadas**: Ayuda a identificar partes del código que no han sido probadas, lo que podría significar posibles errores o comportamientos no validados.
- **Mejora la calidad del software**: Una mayor cobertura reduce la posibilidad de que errores ocultos lleguen a producción.
- **Confianza en la estabilidad del código**: Una alta cobertura ofrece mayor confianza de que el código ha sido examinado adecuadamente bajo diferentes escenarios.

### Limitaciones:

- **Cobertura no garantiza la ausencia de errores**: Incluso si se logra una cobertura del 100%, eso no garantiza que el software esté libre de errores, ya que no mide la efectividad de las pruebas.
- **Foco en la cantidad y no en la calidad**: Es posible tener una cobertura alta sin necesariamente probar todos los escenarios relevantes o los casos extremos.

### Herramientas para medir cobertura:
Existen diversas herramientas que permiten medir la cobertura en pruebas para diferentes lenguajes de programación, como:
- **Python**: `coverage.py`
- **Java**: `JaCoCo`
- **JavaScript**: `Istanbul`
- **C#**: `dotCover`

En resumen, **la cobertura en pruebas** es una métrica que evalúa el porcentaje del código ejecutado durante las pruebas, permitiendo a los equipos de calidad identificar áreas del software que podrían no haber sido probadas adecuadamente.