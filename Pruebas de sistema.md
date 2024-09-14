.
Las pruebas de sistema son un nivel de prueba de software que evalúa el comportamiento y rendimiento del sistema completo e integrado. Estas pruebas se realizan después de las pruebas de integración y antes de las pruebas de aceptación. El objetivo principal es verificar que el sistema cumple con los requisitos especificados y funciona correctamente como un todo.

Características clave de las pruebas de sistema:

1. Alcance: Abarcan todo el sistema, incluyendo hardware, software, interfaces y dependencias externas.

2. Entorno: Se realizan en un entorno lo más cercano posible al de producción.

3. Perspectiva: Se enfocan en la perspectiva del usuario final y los requisitos del negocio.

4. Tipos de pruebas incluidas:
   - [[Pruebas funcionales]]
   - [[Pruebas de desempeño o de rendimiento]] 
   - [[Pruebas de seguridad]]
   - [[Pruebas de usabilidad]]
   - [[Pruebas de recuperación]]
   - [[Pruebas de compatibilidad]]

5. Objetivos específicos:
   - Verificar la integración correcta de todos los componentes
   - Validar el flujo de datos entre los diferentes módulos
   - Comprobar el comportamiento del sistema bajo diferentes condiciones
   - Identificar defectos que solo se manifiestan a nivel de sistema completo

6. Técnicas utilizadas:
   - [[Pruebas de caja negra]]
   - [[Pruebas basadas en escenarios]] 
   - [[Pruebas de casos de uso]] 

7. Duración: Generalmente son más extensas que otros niveles de prueba debido a su alcance.

8. Automatización: Pueden incluir una combinación de pruebas manuales y automatizadas.

9. Documentación: Requieren una planificación detallada y documentación exhaustiva de los casos de prueba.

Las pruebas de sistema son cruciales para asegurar que el software cumple con los requisitos funcionales y no funcionales antes de pasar a las pruebas de aceptación o su implementación en producción.



---
Las pruebas funcionales y de sistema son fundamentales para verificar que el software completo funcione según lo esperado desde la perspectiva del usuario final.

### **Pruebas Funcionales**:
Las pruebas funcionales se enfocan en asegurar que cada función del software cumple con los requerimientos especificados. No se preocupan tanto por cómo funciona internamente, sino por el **resultado** de las acciones desde un punto de vista del usuario.

### **Pruebas de Sistema**:
Las pruebas de sistema verifican que el software funcione de manera correcta en su **totalidad** y no solo como módulos individuales. A menudo abarcan todo el sistema y pueden incluir pruebas de integración, funcionales, y de rendimiento, verificando que todo interactúa correctamente en un entorno real.

#### Planteamiento del Caso:
Continuaremos con el ejemplo de **gestión de tareas (To-Do List)**, pero esta vez vamos a simular una interacción más amplia, como si se tratara de un sistema completo. Supondremos que las tareas se gestionan mediante una interfaz de consola y queremos verificar que el flujo de las funcionalidades más importantes esté funcionando adecuadamente.

### 1. **Estructura del Proyecto**
La estructura del proyecto será la misma, pero vamos a agregar un archivo que actúa como una interfaz de consola y un archivo de pruebas de sistema.

```
/proyecto_tareas/
│
├── app.py               # Código principal de la aplicación
├── external_storage.py   # Simulación del almacenamiento externo
├── main.py              # Interfaz de consola para el sistema de gestión de tareas
├── test_functional.py   # Pruebas funcionales
└── test_system.py       # Pruebas de sistema
```

### 2. **Paso 1: Interfaz de consola (main.py)**

Este archivo simula la interfaz de un usuario que gestiona las tareas a través de una consola, ofreciendo opciones para añadir, listar y eliminar tareas.

```python
# main.py

from app import ToDoList
from external_storage import ExternalStorage

def show_menu():
    print("\n1. Añadir Tarea")
    print("2. Ver Tareas")
    print("3. Eliminar Tarea")
    print("4. Salir")

def main():
    storage = ExternalStorage()
    todo_list = ToDoList(storage)

    while True:
        show_menu()
        option = input("\nSelecciona una opción: ")

        if option == '1':
            task_description = input("Escribe la descripción de la tarea: ")
            try:
                todo_list.add_task(task_description)
                print(f"Tarea '{task_description}' añadida.")
            except ValueError as e:
                print(f"Error: {e}")

        elif option == '2':
            tasks = todo_list.get_all_tasks()
            if not tasks:
                print("No hay tareas.")
            else:
                for task in tasks:
                    print(f"{task['id']}: {task['description']}")

        elif option == '3':
            task_id = int(input("Escribe el ID de la tarea a eliminar: "))
            try:
                todo_list.delete_task(task_id)
                print(f"Tarea con ID {task_id} eliminada.")
            except ValueError as e:
                print(f"Error: {e}")

        elif option == '4':
            print("Saliendo...")
            break

        else:
            print("Opción no válida, intenta de nuevo.")

if __name__ == "__main__":
    main()
```

### 3. **Paso 2: Pruebas Funcionales (test_functional.py)**

En este archivo probaremos que las funcionalidades individuales, cuando son utilizadas juntas, cumplen con las expectativas del usuario.

```python
# test_functional.py

import unittest
from app import ToDoList
from external_storage import ExternalStorage

class TestFunctionalToDoList(unittest.TestCase):

    def setUp(self):
        self.storage = ExternalStorage()
        self.todo_list = ToDoList(self.storage)

    def test_add_and_list_tasks(self):
        # Prueba añadir dos tareas y listarlas
        self.todo_list.add_task("Tarea A")
        self.todo_list.add_task("Tarea B")
        tasks = self.todo_list.get_all_tasks()
        self.assertEqual(len(tasks), 2)
        self.assertEqual(tasks[0]['description'], "Tarea A")
        self.assertEqual(tasks[1]['description'], "Tarea B")

    def test_delete_task_functional(self):
        # Prueba añadir tareas y eliminar una de ellas
        self.todo_list.add_task("Tarea A")
        self.todo_list.add_task("Tarea B")
        self.todo_list.delete_task(1)
        tasks = self.todo_list.get_all_tasks()
        self.assertEqual(len(tasks), 1)
        self.assertEqual(tasks[0]['description'], "Tarea B")

    def test_invalid_delete(self):
        # Prueba eliminar una tarea que no existe
        self.todo_list.add_task("Tarea A")
        with self.assertRaises(ValueError):
            self.todo_list.delete_task(99)

if __name__ == '__main__':
    unittest.main()
```

### 4. **Paso 3: Pruebas de Sistema (test_system.py)**

Estas pruebas verificarán el sistema en su totalidad, simulando el comportamiento de un usuario que interactúa con la interfaz de consola. Usaremos un enfoque para simular la entrada y salida estándar de la consola.

```python
# test_system.py

import unittest
from io import StringIO
from unittest.mock import patch
from main import main

class TestSystem(unittest.TestCase):

    @patch('builtins.input', side_effect=['1', 'Tarea A', '1', 'Tarea B', '2', '4'])
    @patch('sys.stdout', new_callable=StringIO)
    def test_add_tasks_system(self, mock_stdout, mock_input):
        # Simula la interacción del usuario añadiendo dos tareas y listándolas
        main()
        output = mock_stdout.getvalue()
        self.assertIn("Tarea 'Tarea A' añadida.", output)
        self.assertIn("Tarea 'Tarea B' añadida.", output)
        self.assertIn("1: Tarea A", output)
        self.assertIn("2: Tarea B", output)

    @patch('builtins.input', side_effect=['1', 'Tarea A', '1', 'Tarea B', '3', '1', '2', '4'])
    @patch('sys.stdout', new_callable=StringIO)
    def test_delete_task_system(self, mock_stdout, mock_input):
        # Simula la interacción del usuario añadiendo y eliminando tareas
        main()
        output = mock_stdout.getvalue()
        self.assertIn("Tarea 'Tarea A' añadida.", output)
        self.assertIn("Tarea 'Tarea B' añadida.", output)
        self.assertIn("Tarea con ID 1 eliminada.", output)
        self.assertNotIn("1: Tarea A", output)
        self.assertIn("2: Tarea B", output)

if __name__ == '__main__':
    unittest.main()
```

### 5. **Ejecución de las Pruebas**

Para ejecutar las pruebas de sistema y funcionales, utiliza el siguiente comando para cada archivo de prueba en la terminal de **VSCode**:

```bash
python -m unittest test_functional.py
```

```bash
python -m unittest test_system.py
```
---
El módulo `test_system.py` es un conjunto de pruebas unitarias que utiliza el framework `unittest` para probar la funcionalidad del sistema desde un nivel más elevado, simulando la interacción del usuario con la función `main()` del módulo `main.py`. A continuación, te explico qué hace este código y cómo funcionan las pruebas:

### Descripción general:

Este módulo de pruebas utiliza `unittest`, el módulo de pruebas incorporado en Python, junto con el uso de mocks proporcionados por `unittest.mock`. Simula entradas de usuario con `@patch('builtins.input')` y captura la salida estándar con `@patch('sys.stdout')`. Las pruebas verifican si las tareas se agregan correctamente y si las eliminaciones funcionan según lo esperado.

### Estructura de las pruebas:

1. **Clase `TestSystem`**: Esta clase hereda de `unittest.TestCase`, lo que permite ejecutar pruebas de manera automática. Tiene dos métodos de prueba que prueban diferentes funcionalidades del sistema:
    
    - `test_add_tasks_system`
    - `test_delete_task_system`
2. **Uso de `patch()`**:
    
    - Se utiliza `@patch('builtins.input')` para simular las entradas del usuario. En lugar de depender de la interacción real con un usuario, se pasa una lista de entradas simuladas mediante el parámetro `side_effect`.
    - Se usa `@patch('sys.stdout')` para redirigir la salida estándar (lo que normalmente se imprime en la consola) a un objeto `StringIO`, de modo que se pueda capturar y analizar lo que el programa imprimiría en la consola.

### Pruebas:

#### 1. **Método `test_add_tasks_system`**:

Este método prueba la funcionalidad de agregar tareas y listarlas. Simula una interacción de usuario con las siguientes entradas:

- `'1'`: Indica que se selecciona la opción de agregar una tarea.
- `'Tarea A'`: Nombre de la primera tarea.
- `'1'`: Se selecciona nuevamente la opción de agregar una tarea.
- `'Tarea B'`: Nombre de la segunda tarea.
- `'2'`: Se selecciona la opción de listar las tareas.
- `'4'`: Simula la opción para salir del sistema.

Tras ejecutar estas entradas, se captura la salida y se verifica que:

- Se impriman mensajes indicando que ambas tareas ("Tarea A" y "Tarea B") fueron añadidas.
- Ambas tareas aparezcan listadas con sus respectivos IDs (`1` y `2`).

#### 2. **Método `test_delete_task_system`**:

Este método prueba la funcionalidad de agregar, eliminar tareas y listar el resultado. Simula la siguiente interacción:

- `'1'`: Se selecciona la opción de agregar una tarea.
- `'Tarea A'`: Nombre de la primera tarea.
- `'1'`: Se selecciona la opción de agregar otra tarea.
- `'Tarea B'`: Nombre de la segunda tarea.
- `'3'`: Se selecciona la opción de eliminar una tarea.
- `'1'`: Indica que se eliminará la tarea con ID 1 (Tarea A).
- `'2'`: Se selecciona la opción para listar las tareas restantes.
- `'4'`: Simula la opción para salir del sistema.

Después de ejecutar la prueba, se verifica que:

- La tarea "Tarea A" se añada correctamente.
- La tarea "Tarea B" también se añada correctamente.
- Se imprima un mensaje indicando que la tarea con ID 1 ("Tarea A") fue eliminada.
- La tarea "Tarea B" aún aparezca listada y la tarea "Tarea A" ya no esté en la lista.

### Resumen:

Este módulo simula una serie de interacciones de usuario, agregando, eliminando y listando tareas en un sistema, y verifica que el comportamiento del sistema sea el esperado. Utiliza `patch()` para inyectar entradas simuladas y capturar las salidas sin requerir una interacción real del usuario.

---

### **Explicación de las Pruebas:**

- **Pruebas Funcionales**: Verifican que el sistema permite realizar operaciones como añadir, listar y eliminar tareas correctamente. Se centran en la ejecución de funciones clave y su correcto funcionamiento.
- **Pruebas de Sistema**: Simulan la interacción del usuario con el sistema desde la perspectiva de la interfaz de consola, validando el comportamiento completo del programa, tal como lo percibiría un usuario real.

---

### **Conceptos Clave:**
- **Pruebas Funcionales**: Aseguran que las funciones del sistema cumplen con los requisitos establecidos desde una perspectiva externa.
- **Pruebas de Sistema**: Verifican la integración de todos los componentes en un entorno simulado que replica el uso real del sistema.
- **Simulación de Entrada/Salida**: Se usan técnicas como `patch` y `StringIO` para simular la interacción con la consola y automatizar las pruebas.

Este enfoque abarca la cobertura total de las pruebas de software, asegurando tanto el comportamiento individual de los módulos como su integración completa en el sistema. 