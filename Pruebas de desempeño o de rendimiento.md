.
Las pruebas de desempeño son un tipo de prueba de software que se realizan para evaluar la capacidad de un sistema o aplicación bajo condiciones específicas. Estas pruebas se centran en ==medir el rendimiento del software en términos de respuesta, velocidad, estabilidad, y uso de recursos==, con el fin de garantizar que el sistema pueda soportar la carga de usuarios y datos que se espera en un entorno de producción.

### Características Clave de las Pruebas de Desempeño:

1. **Medición de Rendimiento**: Se centran en medir varios aspectos del rendimiento del sistema, como el tiempo de respuesta, la capacidad de procesamiento, la carga máxima que el sistema puede manejar, y el uso de recursos como CPU, memoria y ancho de banda.

2. **Tipos de Pruebas de Desempeño**:
   - **[[Pruebas de carga]]**: Evaluar cómo el sistema maneja un número específico de usuarios o transacciones durante un período determinado.
   - **[[Pruebas de estrés]]**: Determinar los límites del sistema al someterlo a cargas extremas para identificar en qué punto empieza a fallar.
   - **[[Pruebas de escalabilidad]]**: Evaluar cómo el sistema responde a un aumento en la carga o dimensiones (número de usuarios, volúmenes de datos) y si puede escalar adecuadamente.
   - **[[Pruebas de estabilidad]]**: Medir el comportamiento del sistema durante un tiempo prolongado bajo condiciones de carga estándar para asegurar que no haya degradación en el rendimiento.
   - [[Comparación entre pruebas de rendimiento]] 

3. **Simulación de Cargas del Mundo Real**: Estas pruebas suelen incluir la simulación de la actividad de múltiples usuarios simultáneamente para reflejar condiciones de uso real en el entorno de producción.

4. **Uso de Herramientas Especializadas**: Existen herramientas y software específicos para ejecutar pruebas de desempeño, como [[LoadRunner]], [[JMeter]], y [[Gatling]], que ayudan a automatizar el proceso y recopilar datos de rendimiento de forma efectiva.

5. **Detección de Cuellos de Botella**: Ayudan a identificar áreas del sistema que están limitando la capacidad de rendimiento, permitiendo a los equipos de desarrollo y operación optimizar el sistema antes del lanzamiento.

### Importancia de las Pruebas de Desempeño:

1. **Satisfacción del Usuario**: Garantizar que las aplicaciones respondan rápidamente y funcionen sin problemas bajo carga es vital para la experiencia del usuario. Un mal rendimiento puede llevar a la frustración del usuario y potencialmente a la pérdida de negocio.

2. **Preparación para el Lanzamiento**: Estas pruebas son esenciales antes de poner en producción un sistema, asegurando que puede manejar la carga de usuarios que se anticipa sin fallos.

3. **Optimización de Recursos**: Ayudan a identificar el uso ineficiente de recursos, lo que puede llevar a ajustes en la arquitectura del software y en la infraestructura de hardware.

4. **Aumento de la Confianza**: Realizar pruebas de desempeño efectivas proporciona una mayor confianza a los desarrolladores y a los interesados sobre la capacidad del sistema para manejar las demandas del negocio.

En resumen, las pruebas de desempeño son un componente crítico del aseguramiento de la calidad en el desarrollo de software, jugando un papel fundamental en la validación de que una aplicación será capaz de manejar adecuadamente la carga y ofrecer un rendimiento fiable a los usuarios finales.

---
### **Performance Testing**
Evalúan la velocidad, capacidad de respuesta, y estabilidad del sistema bajo una carga específica. En nuestro caso, podríamos probar el tiempo que toma para listar un gran número de tareas.

#### Ejemplo:
Medimos el tiempo de respuesta al listar un gran número de tareas.

```python
# test_performance.py

import unittest
import time
from main import add_task, list_tasks

class TestPerformanceToDoList(unittest.TestCase):

    def test_list_task_performance(self):
        # Simulamos la adición de 10,000 tareas
        for i in range(10000):
            add_task(f"Tarea {i+1}")
        
        # Medimos el tiempo que toma listar las tareas
        start_time = time.time()
        tasks = list_tasks()
        end_time = time.time()
        
        # Verificamos que el tiempo no excede un límite razonable (ej. 1 segundo)
        self.assertLess(end_time - start_time, 1.0)

if __name__ == '__main__':
    unittest.main()
```

También llamadas [[Pruebas de carga]],  estas pruebas verifican cómo el sistema se comporta bajo una carga pesada de usuarios o datos. En el caso de la **To-Do List**, podríamos simular la adición de miles de tareas para ver si el sistema sigue funcionando correctamente o se degrada en rendimiento.

#### Ejemplo:
Este ejemplo simula la adición de un gran número de tareas.



```python
# test_load.py

import unittest
from main import add_task, list_tasks

class TestLoadToDoList(unittest.TestCase):

    def test_add_large_number_of_tasks(self):
        # Simulamos la adición de 10,000 tareas
        for i in range(10000):
            add_task(f"Tarea {i+1}")
        
        # Verificamos que se han añadido todas las tareas
        tasks = list_tasks()
        self.assertEqual(len(tasks), 10000)

if __name__ == '__main__':
    unittest.main()
```

