.
Las UAT (User Acceptance Testing, o Pruebas de Aceptación del Usuario) son un tipo específico de pruebas de aceptación realizadas por los usuarios finales o clientes para validar que un sistema o software cumple con sus requisitos y expectativas antes de su implementación definitiva. Este es un paso crucial en el ciclo de vida del desarrollo de software, ya que asegura que el producto final es adecuado para su uso previsto.

### Características clave de las UAT:

1. **Perspectiva del Usuario**: Las UAT se centran en el punto de vista y las necesidades del usuario final. El objetivo es verificar que el software funcione correctamente en situaciones reales de uso para los usuarios que lo manejarán.

2. **Verificación de Requisitos Funcionales**: Estas pruebas aseguran que el software cumpla con los requisitos funcionales y no funcionales previamente establecidos y documentados.

3. **Entorno Realista**: Idealmente, las pruebas de aceptación del usuario se llevan a cabo en un entorno que simula la producción, de modo que los usuarios puedan experimentar el sistema en condiciones que se asemejan a su uso diario.

4. **Evaluación de Usabilidad**: Además de verificar que todas las funciones operen adecuadamente, las UAT también pueden evaluar la facilidad de uso y la experiencia del usuario con el sistema.

5. **Criterios de Aceptación**: Se definen criterios específicos que deben cumplirse para que el software sea aceptado. Si el software no cumple con estos criterios, puede requerir ajustes antes de la entrega final.

6. **Participación del Cliente**: Las UAT son generalmente organizadas y llevadas a cabo por los propios usuarios finales o por representantes del cliente, lo que facilita la recepción de retroalimentación directa y permite realizar ajustes necesarios.

7. **Fase Final Pruebas**: Las UAT se realizan al final del desarrollo y antes de la implementación en producción. Esto es esencial para la validación definitiva del producto.

### Importancia de las UAT:

- **Satisfacción del Cliente**: Aseguran que el software se alinea con las expectativas y necesidades de los usuarios finales, lo que es fundamental para la satisfacción del cliente.
- **Detección de Problemas**: Ayudan a identificar problemas que pueden no haber sido detectados durante las pruebas anteriores.
- **Minimizan Riesgos**: Validan el software antes de su lanzamiento, lo que reduce el riesgo de fallos o insatisfacción del usuario después de la implementación.

En resumen, las UAT son una parte crítica del proceso de desarrollo de software que asegura que el producto final sea aceptable y satisfactorio para el cliente y los usuarios finales.


---

Las **pruebas de aceptación** verifican si un sistema cumple con los requisitos y expectativas del cliente o usuario final. Su objetivo es garantizar que el software haga lo que se espera de él en escenarios reales de uso. En el caso de nuestra aplicación **To-Do List**, las pruebas de aceptación se centrarán en la experiencia completa de un usuario interactuando con la aplicación y la satisfacción de los requisitos definidos.

### **Escenarios de Pruebas de Aceptación**:
Para estructurar las pruebas de aceptación, vamos a imaginar algunos requisitos funcionales del cliente:
1. **Añadir una tarea**: El usuario debe poder añadir una tarea y verla en la lista.
2. **Listar tareas**: El usuario debe poder ver todas las tareas que ha añadido.
3. **Eliminar una tarea**: El usuario debe poder eliminar una tarea seleccionándola por su ID.
4. **Manejo de errores**: Si el usuario intenta eliminar una tarea inexistente o introducir una tarea vacía, el sistema debe dar un mensaje de error claro.

### **1. Estructura del Proyecto**:
La estructura del proyecto será la misma, pero añadiremos un archivo para las pruebas de aceptación.

```
/proyecto_tareas/
│
├── app.py               # Código principal de la aplicación
├── external_storage.py   # Simulación del almacenamiento externo
├── main.py              # Interfaz de consola para el sistema de gestión de tareas
├── test_functional.py   # Pruebas funcionales
├── test_system.py       # Pruebas de sistema
└── test_acceptance.py   # Pruebas de aceptación
```

### **2. Definición de Escenarios de Aceptación (test_acceptance.py)**

Vamos a implementar las pruebas de aceptación usando un enfoque similar a las pruebas de sistema, pero simulando escenarios completos basados en los requisitos de los usuarios.

```python
# test_acceptance.py

import unittest
from io import StringIO
from unittest.mock import patch
from main import main

class TestAcceptanceToDoList(unittest.TestCase):

    @patch('builtins.input', side_effect=['1', 'Comprar leche', '2', '4'])
    @patch('sys.stdout', new_callable=StringIO)
    def test_add_and_list_task_acceptance(self, mock_stdout, mock_input):
        # Escenario: Añadir una tarea y listar las tareas
        main()
        output = mock_stdout.getvalue()
        # Verificamos que la tarea fue añadida correctamente y que aparece en la lista
        self.assertIn("Tarea 'Comprar leche' añadida.", output)
        self.assertIn("1: Comprar leche", output)

    @patch('builtins.input', side_effect=['1', 'Ir al gimnasio', '1', 'Hacer la cena', '2', '3', '1', '2', '4'])
    @patch('sys.stdout', new_callable=StringIO)
    def test_add_delete_task_acceptance(self, mock_stdout, mock_input):
        # Escenario: Añadir dos tareas, eliminar una y listar las tareas
        main()
        output = mock_stdout.getvalue()
        # Verificamos que las tareas se añaden, eliminan y muestran correctamente
        self.assertIn("Tarea 'Ir al gimnasio' añadida.", output)
        self.assertIn("Tarea 'Hacer la cena' añadida.", output)
        self.assertIn("Tarea con ID 1 eliminada.", output)
        self.assertNotIn("1: Ir al gimnasio", output)
        self.assertIn("2: Hacer la cena", output)

    @patch('builtins.input', side_effect=['1', '', '4'])
    @patch('sys.stdout', new_callable=StringIO)
    def test_invalid_task_acceptance(self, mock_stdout, mock_input):
        # Escenario: Intentar añadir una tarea vacía y verificar el manejo del error
        main()
        output = mock_stdout.getvalue()
        self.assertIn("Error: La tarea no puede estar vacía", output)

    @patch('builtins.input', side_effect=['3', '99', '4'])
    @patch('sys.stdout', new_callable=StringIO)
    def test_invalid_delete_task_acceptance(self, mock_stdout, mock_input):
        # Escenario: Intentar eliminar una tarea con un ID inexistente
        main()
        output = mock_stdout.getvalue()
        self.assertIn("Error: El ID de la tarea debe ser mayor que 0", output)

if __name__ == '__main__':
    unittest.main()
```

### **3. Escenarios de Aceptación:**

#### **Escenario 1: Añadir y listar tareas**
- **Acción**: El usuario añade la tarea "Comprar leche" y la lista.
- **Resultado esperado**: La tarea aparece en la lista con el ID 1.
- **Verificación**: La salida de la consola muestra el mensaje de éxito al añadir la tarea y luego la lista muestra la tarea correctamente.

#### **Escenario 2: Añadir, eliminar y listar tareas**
- **Acción**: El usuario añade dos tareas ("Ir al gimnasio" y "Hacer la cena"), elimina la primera tarea, y luego lista las tareas restantes.
- **Resultado esperado**: La primera tarea es eliminada correctamente y la segunda tarea sigue en la lista.
- **Verificación**: La salida de la consola refleja la eliminación exitosa y muestra las tareas correctas al listar.

#### **Escenario 3: Intentar añadir una tarea vacía**
- **Acción**: El usuario intenta añadir una tarea vacía.
- **Resultado esperado**: Se muestra un mensaje de error indicando que no se pueden añadir tareas vacías.
- **Verificación**: La salida de la consola muestra el mensaje de error correcto.

#### **Escenario 4: Intentar eliminar una tarea inexistente**
- **Acción**: El usuario intenta eliminar una tarea con un ID que no existe (ID 99).
- **Resultado esperado**: Se muestra un mensaje de error indicando que el ID de la tarea no es válido.
- **Verificación**: La salida de la consola muestra el mensaje de error adecuado.

### **4. Ejecución de las Pruebas de Aceptación**

Para ejecutar las pruebas de aceptación en **VSCode**, utiliza el siguiente comando en la terminal:

```bash
python -m unittest test_acceptance.py
```

### **Explicación de las Pruebas de Aceptación**:

- **Pruebas basadas en casos de uso reales**: Las pruebas de aceptación reflejan cómo un usuario interactuaría con el sistema desde el inicio hasta el final, verificando que las funciones principales satisfacen los requisitos.
- **Simulación de la interacción del usuario**: Usamos `patch` para simular la entrada del usuario y `StringIO` para capturar la salida de la consola y verificar que el sistema responde correctamente en cada escenario.
- **Enfoque en la experiencia del usuario**: Estas pruebas verifican si la aplicación hace lo que se espera en escenarios reales, en lugar de enfocarse en detalles técnicos.

### **5. Conceptos Clave para la Clase Práctica:**

- **Pruebas de aceptación**: Son el último nivel de pruebas antes de la entrega del sistema, y están centradas en verificar que el sistema cumple con los requisitos y expectativas del usuario final.
- **Simulación de entradas y salidas**: Se simulan interacciones reales del usuario con el sistema y se verifica la salida para asegurarse de que cumple con las expectativas.
- **Pruebas basadas en escenarios**: Cada prueba de aceptación se construye en torno a un escenario realista, verificando que el software funcione según lo previsto en el mundo real.

---

Con este ejemplo, has cubierto las pruebas de aceptación para la aplicación **To-Do List**, enfocándote en el usuario final y asegurando que la experiencia general sea la esperada. 