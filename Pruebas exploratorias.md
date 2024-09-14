.
Las **pruebas exploratorias** son un tipo de prueba de software que se basa en la experiencia y el conocimiento del tester para explorar activamente una aplicación ==SIN== un conjunto de [[Casos de prueba]] previamente definidos. A diferencia de las pruebas tradicionales, en las que los pasos y resultados esperados están predefinidos, en las pruebas exploratorias el tester interactúa con el software de manera más libre y flexible, buscando activamente defectos o comportamientos inesperados.

### **Características clave de las pruebas exploratorias:**

1. **Sin guion predefinido**: A diferencia de las pruebas basadas en un plan de pruebas detallado, el tester no sigue un conjunto fijo de casos de prueba. En cambio, va explorando el sistema a medida que lo va conociendo.
   
2. **Aprendizaje en el proceso**: El tester va aprendiendo sobre la aplicación a medida que la prueba, lo que le permite ajustar su enfoque en tiempo real. Si encuentra un área problemática, puede dedicar más tiempo a explorarla.

3. **Creatividad e intuición**: Se apoya en la capacidad del tester para ser creativo, pensar en diferentes escenarios de uso y anticipar cómo el sistema podría fallar o comportarse de manera incorrecta.

4. **Rápido feedback**: Permite obtener un feedback rápido sobre la estabilidad y el comportamiento del sistema, lo que es útil en entornos ágiles o cuando se necesita verificar cambios de manera rápida.

5. **Enfocada en áreas críticas**: El tester puede enfocarse en partes del software que cree que son más propensas a tener errores, como nuevas características, partes modificadas del código o áreas críticas del negocio.

6. **Documentación mínima**: En lugar de una extensa documentación de casos de prueba, el tester puede registrar notas o sesiones de prueba breves, describiendo los problemas que encuentra y los pasos que siguió para reproducirlos.

### **Ventajas de las pruebas exploratorias:**

- **Flexibilidad**: No está limitada por un conjunto rígido de casos de prueba, lo que permite descubrir problemas que pueden no haber sido anticipados.
- **Adaptación rápida**: Se puede adaptar a cambios en la aplicación o a requisitos que no estaban completamente especificados.
- **Cobertura más amplia**: Los testers pueden descubrir errores en áreas no previstas inicialmente, ya que prueban el software desde diferentes perspectivas.
- **Detección de errores inesperados**: Puede encontrar errores en áreas inesperadas que las pruebas automatizadas o planificadas podrían no detectar.

### **Desventajas de las pruebas exploratorias:**

- **Difícil de reproducir**: Como no siguen un conjunto de pasos estrictos, puede ser difícil documentar exactamente cómo se encontró un error o cómo reproducirlo.
- **Cobertura no garantizada**: Al no tener casos de prueba predefinidos, es posible que algunas áreas del software no se prueben adecuadamente.
- **Requiere testers experimentados**: Los mejores resultados provienen de testers con experiencia y buen conocimiento del sistema, ya que dependen de la intuición y el conocimiento del tester.

### **Ejemplo de uso:**

Imagina que estás probando una aplicación **To-Do List** en la que el usuario puede añadir, eliminar y listar tareas. En una prueba exploratoria, un tester podría:
1. Añadir varias tareas de diferentes tipos (largas, cortas, con caracteres especiales).
2. Probar qué sucede si intenta añadir una tarea vacía o con demasiados caracteres.
3. Eliminar tareas en diferentes órdenes o eliminar una tarea que ya ha sido eliminada.
4. Intentar ejecutar acciones rápidas, como añadir y eliminar tareas consecutivamente para ver cómo responde el sistema.
5. Interactuar con la interfaz en modos inesperados, como cerrar la aplicación en medio de una operación, para ver cómo maneja los errores.

### **Cuándo usar pruebas exploratorias:**

- **Al inicio de un proyecto**: Cuando el sistema está en una etapa temprana de desarrollo y los requisitos pueden no estar completamente definidos.
- **En proyectos ágiles**: Cuando los ciclos de desarrollo son rápidos y no hay tiempo para escribir casos de prueba detallados para cada nueva funcionalidad.
- **Para pruebas de regresión rápidas**: Cuando se necesita verificar rápidamente si nuevas funcionalidades o cambios recientes han causado errores en otras partes del sistema.
- **Para complementar pruebas automatizadas**: Las pruebas exploratorias pueden encontrar errores que las pruebas automatizadas o planificadas no detectan.

### **Técnica para realizar pruebas exploratorias:**
Una técnica común en pruebas exploratorias es la **"charla de pruebas"** (test session). Consiste en establecer un objetivo general para la sesión de prueba, como "verificar la funcionalidad de eliminación de tareas" y luego dedicar un tiempo fijo, por ejemplo, 30 minutos, a explorar diferentes escenarios relacionados con esa funcionalidad.

### **Herramientas complementarias:**
Aunque las pruebas exploratorias suelen ser manuales, algunas herramientas ayudan a capturar lo que ocurre durante una sesión de prueba. Por ejemplo, herramientas como **Session-Based Test Management** ([[SBTM]]) permiten documentar sesiones exploratorias, y herramientas de captura de pantallas o logs pueden ayudar a registrar los pasos seguidos durante la prueba.
