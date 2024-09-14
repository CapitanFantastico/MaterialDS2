.
Un **caso de prueba** es un conjunto de condiciones o variables bajo las cuales un tester determina si un sistema de software o una de sus funcionalidades está funcionando como se espera. Es una herramienta esencial en el proceso de pruebas de software para validar que el software cumple con los requisitos especificados y para detectar posibles fallos o errores en el sistema.

### **Componentes clave de un caso de prueba**:

1. **Identificador (ID del caso de prueba)**:
   - Un código único que ayuda a identificar el caso de prueba. Esto facilita su referencia en documentos y herramientas de pruebas.

2. **Descripción del caso de prueba**:
   - Una breve descripción que explica lo que el caso de prueba está diseñado para verificar. Por ejemplo, "Verificar que el usuario puede iniciar sesión con credenciales válidas".

3. **Precondiciones**:
   - Condiciones que deben cumplirse antes de ejecutar el caso de prueba. Esto puede incluir datos que deben estar presentes en la base de datos o configuraciones específicas del sistema.

4. **Pasos para ejecutar**:
   - Un conjunto de instrucciones detalladas que el tester debe seguir para realizar el caso de prueba. Estos pasos son muy importantes para garantizar que el caso de prueba sea repetible.

5. **Datos de prueba**:
   - Información específica que se debe usar durante la ejecución del caso de prueba, como entradas, archivos o configuraciones. Por ejemplo, credenciales de usuario o datos de formulario.

6. **Resultados esperados**:
   - El comportamiento esperado del sistema después de ejecutar los pasos del caso de prueba. Esto es clave para determinar si el sistema funciona correctamente o no.

7. **Resultado real**:
   - El comportamiento observado del sistema durante la ejecución del caso de prueba. Se compara con el resultado esperado para determinar si el caso de prueba es "pasado" o "fallado".

8. **Resultado**:
   - El resultado del caso de prueba puede ser "pass" (si el sistema cumple con los resultados esperados) o "fail" (si no lo hace).

9. **Postcondiciones**:
   - Cualquier estado que deba alcanzarse o verificarse después de ejecutar el caso de prueba.

10. **Notas adicionales o comentarios**:
    - Información adicional o contexto relevante que puede ser útil para el tester o el equipo.

### **Ejemplo de caso de prueba**:

| **ID**                 | TC001                                                                                                                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Descripción**        | Verificar que el sistema permite al usuario iniciar sesión con credenciales válidas                                                                                      |
| **Precondiciones**     | El usuario debe tener una cuenta creada                                                                                                                                  |
| **Pasos**              | 1. Navegar a la página de inicio de sesión<br>2. Ingresar un nombre de usuario válido<br>3. Ingresar una contraseña válida<br>4. Hacer clic en el botón "Iniciar sesión" |
| **Datos de prueba**    | Nombre de usuario: `usuario1`, Contraseña: `Password123`                                                                                                                 |
| **Resultado esperado** | El sistema redirige al usuario a la página de inicio                                                                                                                     |
| **Resultado real**     | El sistema redirige correctamente a la página de inicio                                                                                                                  |
| **Resultado**          | Pass                                                                                                                                                                     |
| **Postcondiciones**    | El usuario está conectado al sistema                                                                                                                                     |

### **Tipos de casos de prueba**:

1. **Casos de prueba funcionales**:
   - Verifican si una funcionalidad específica del software cumple con los requisitos. Por ejemplo, "Verificar que el botón de búsqueda devuelve los resultados correctos".

2. **Casos de prueba no funcionales**:
   - Verifican aspectos no relacionados directamente con las funcionalidades, como el rendimiento, la seguridad o la usabilidad. Por ejemplo, "Verificar que la página se carga en menos de 2 segundos".

3. **Casos de prueba negativos**:
   - Están diseñados para probar el comportamiento del sistema frente a entradas inválidas o escenarios inesperados. Por ejemplo, "Verificar que el sistema muestra un mensaje de error al ingresar una contraseña incorrecta".

4. **Casos de prueba de regresión**:
   - Se usan para verificar que los cambios recientes en el código (como corrección de errores o nuevas funcionalidades) no hayan afectado negativamente otras partes del sistema.

5. **Casos de prueba de borde**:
   - Verifican el comportamiento del sistema en los límites de los valores aceptables, como el valor máximo o mínimo permitido para una entrada.

6. **Casos de prueba basados en datos**:
   - Se ejecutan varias veces con diferentes datos de entrada para verificar cómo el sistema maneja una variedad de entradas.

### **Importancia de los casos de prueba**:

- **Claridad**: Los casos de prueba proporcionan una manera clara y estructurada de verificar la funcionalidad de un sistema.
- **Trazabilidad**: Permiten que los equipos de desarrollo y pruebas rastreen qué requisitos del sistema han sido probados y cuáles no.
- **Eficiencia**: Permiten identificar errores de manera sistemática y organizada.
- **Repetibilidad**: Los casos de prueba pueden ser reutilizados en diferentes ciclos de pruebas, lo que aumenta la eficiencia del proceso de pruebas.
