.
Las **pruebas de usabilidad** son un tipo de evaluación que se realiza en software o productos digitales (como aplicaciones web o móviles) para verificar qué tan fácil y eficiente es para los usuarios interactuar con ellos. El objetivo principal de las pruebas de usabilidad es identificar problemas en la interfaz de usuario ([[UI]]) o en la experiencia de usuario ([[UX]]), mejorar la accesibilidad y optimizar el diseño para que sea más intuitivo y fácil de usar.

==Las pruebas de usabilidad no son automatizadas== (por ahora)
### **Objetivos de las pruebas de usabilidad**:
1. **Identificar problemas**: Determinar qué aspectos de la interfaz o funcionalidad confunden a los usuarios o no funcionan como se espera.
2. **Mejorar la satisfacción del usuario**: Garantizar que los usuarios tengan una experiencia fluida, eficiente y agradable.
3. **Optimizar la eficiencia**: Asegurarse de que los usuarios puedan completar sus tareas de manera rápida y sin errores.
4. **Validar el diseño**: Comprobar si el diseño cumple con las expectativas y necesidades de los usuarios finales.

### **Aspectos clave evaluados en las pruebas de usabilidad**:
1. **Facilidad de uso**: Qué tan fácil es para los usuarios realizar tareas específicas.
2. **Aprendizaje**: Cuánto tiempo les toma a los nuevos usuarios aprender a usar el sistema.
3. **Eficiencia**: Qué tan rápido los usuarios pueden completar las tareas una vez que aprenden a usar el sistema.
4. **Satisfacción**: Cómo se sienten los usuarios después de interactuar con el sistema, si lo consideran agradable o frustrante.
5. **Memorabilidad**: Qué tan bien pueden los usuarios recordar cómo usar el sistema después de un período de no utilizarlo.

### **Cómo se realizan las pruebas de usabilidad**:

1. **Selección de usuarios**: Se reclutan personas que representen al público objetivo del software. Es crucial probar con usuarios reales para obtener resultados relevantes.
  
2. **Definición de tareas**: Se diseñan tareas específicas que los usuarios deben completar, como "registrarse en la plataforma" o "comprar un producto". Estas tareas reflejan escenarios comunes que los usuarios reales enfrentarán.

3. **Observación**: Durante la prueba, los usuarios interactúan con el software mientras los evaluadores observan cómo lo usan. En algunos casos, las pruebas pueden ser grabadas en video para analizar después.
   - Los evaluadores pueden registrar cuánto tiempo toma completar cada tarea, cuántos errores cometen los usuarios y cualquier punto en el que se confunden o se frustran.

4. **Retroalimentación**: Después de que los usuarios han completado las tareas, se les puede pedir que ofrezcan retroalimentación sobre su experiencia, proporcionando insights sobre las áreas donde el software es difícil de usar o confuso.

5. **Informe y recomendaciones**: Los evaluadores analizan los resultados, identifican patrones comunes de problemas, y proporcionan recomendaciones para mejorar la usabilidad.

### **Tipos de pruebas de usabilidad**:

1. **Pruebas moderadas**: Un evaluador guía a los participantes a través de las tareas, haciendo preguntas o proporcionando aclaraciones según sea necesario.
   
2. **Pruebas no moderadas**: Los usuarios completan las tareas sin intervención del evaluador, generalmente en línea, y las interacciones se registran automáticamente.

3. **Pruebas de laboratorio**: Se realizan en un entorno controlado, con observadores que monitorizan en tiempo real el comportamiento de los usuarios.

4. **Pruebas de campo**: Los usuarios prueban el software en su propio entorno, proporcionando una visión más realista de cómo usarían la herramienta en su vida diaria.

5. **Test A/B**: Se ofrecen dos versiones diferentes del software o del diseño a distintos usuarios, y se compara cuál versión ofrece una mejor usabilidad.

### **Beneficios de las pruebas de usabilidad**:

1. **Mejoran la experiencia de usuario**: Detectan los problemas en la interfaz y UX que impiden que los usuarios interactúen de manera efectiva con el software.
   
2. **Reducen errores y frustración**: Al identificar los puntos donde los usuarios cometen errores o se frustran, los desarrolladores pueden ajustar el diseño para reducir esos problemas.

3. **Aumentan la eficiencia y productividad**: Un software con buena usabilidad permite a los usuarios completar tareas rápidamente, lo que mejora la productividad y reduce el tiempo dedicado a resolver problemas o aprender a usar el sistema.

4. **Incrementan la satisfacción del cliente**: Los usuarios que tienen una experiencia positiva son más propensos a usar el software de manera continua y a recomendarlo a otros.

### **Ejemplo de una prueba de usabilidad**:

Supongamos que una empresa está desarrollando una nueva aplicación móvil de banca en línea. El equipo de diseño desea probar qué tan intuitiva es la interfaz de usuario para que los clientes realicen transferencias de dinero.

- Se seleccionan usuarios que utilizan la banca en línea regularmente.
- Se les asigna la tarea de "transferir $100 a un amigo".
- Durante la prueba, los evaluadores observan cómo los usuarios navegan por la aplicación, si encuentran el botón para iniciar una transferencia, si entienden el proceso, y cuánto tiempo les toma completar la tarea.
- Después de la prueba, se les pregunta a los usuarios si se sintieron cómodos usando la aplicación o si encontraron algún aspecto confuso.

Con esta información, el equipo de desarrollo puede hacer ajustes, como rediseñar ciertos botones o simplificar el flujo de trabajo, para mejorar la usabilidad.


---
Estas pruebas se enfocan en evaluar la experiencia de usuario. Aunque se suelen hacer manualmente, en algunos casos se pueden simular aspectos específicos a través de pruebas automatizadas. Para la aplicación **To-Do List**, podríamos hacer pruebas para verificar la claridad de los mensajes de error o el flujo de navegación.

#### Ejemplo:
Simulamos un caso donde el usuario intenta realizar una acción incorrecta y verificamos si los mensajes de error son claros.

```python
# test_usability.py

import unittest
from io import StringIO
from unittest.mock import patch
from main import main

class TestUsabilityToDoList(unittest.TestCase):

    @patch('builtins.input', side_effect=['3', '99', '4'])
    @patch('sys.stdout', new_callable=StringIO)
    def test_error_message_clarity(self, mock_stdout, mock_input):
        # Verificamos que los mensajes de error son claros y entendibles para el usuario
        main()
        output = mock_stdout.getvalue()
        self.assertIn("Error: El ID de la tarea debe ser mayor que 0", output)
        self.assertNotIn("Error técnico no manejado", output)

if __name__ == '__main__':
    unittest.main()
```


