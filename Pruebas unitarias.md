.
Las pruebas unitarias son un tipo de prueba de software que se centra en verificar el correcto funcionamiento de componentes individuales del código, conocidos como "unidades". Una unidad puede ser una función, un método o una clase, y las pruebas unitarias se utilizan para asegurar que estas pequeñas partes del software operen como se espera. 

Algunas características clave de las pruebas unitarias son:

1. **Enfoque en la Unidad**: Las pruebas se llevan a cabo en componentes individuales del sistema, lo que permite a los desarrolladores identificar rápidamente problemas específicos.

2. **Automatización**: Generalmente, las pruebas unitarias se implementan con el uso de frameworks de pruebas como JUnit (para Java), NUnit (para .NET), o pytest (para Python), lo que facilita la ejecución automática de pruebas.

3. **Desarrollo Ágil**: Son una práctica común en el desarrollo ágil y se implementan a menudo como parte del enfoque de "desarrollo guiado por pruebas" (TDD, por sus siglas en inglés), donde las pruebas se escriben antes del código de la unidad a probar.

4. **Rápidas y Aisladas**: Las pruebas unitarias son rápidas de ejecutar y se ejecutan de forma aislada, lo que significa que no dependen del estado o contexto de otras unidades del software.

5. **Facilitan el Mantenimiento**: Al probar unidades de manera aislada, ayudan a detectar errores en etapas tempranas, lo que reduce el costo y esfuerzo requerido para corregir defectos más adelante en el ciclo de desarrollo.

6. **Documentación del Código**: Sirven como una forma de documentación, ya que el conjunto de pruebas unitarias puede ayudar a otros desarrolladores a entender cómo debería comportarse cada unidad.

Las pruebas unitarias son fundamentales para garantizar la calidad del software y son una práctica recomendada en el desarrollo moderno.

### **Herramientas**: 

- [[JUnit]] 
- [[JMockit]] 



---

Pruebas unitarias de un sistema de gestión de tareas (To-Do List). El objetivo será realizar pruebas sobre las funcionalidades principales de la aplicación sin depender de ningún tipo de almacenamiento persistente.

### 1. **Estructura del proyecto**
La estructura del proyecto será la siguiente:

```
/proyecto_tareas/
│
├── app.py            # Código principal de la aplicación
└── test_app.py       # Archivo con las pruebas unitarias
```

### 2. **Paso 1: Código principal (app.py)**

```python
# app.py

class ToDoList:
    def __init__(self):
        self.tasks = []
        self.next_id = 1

    def add_task(self, task):
        if not task:
            raise ValueError("La tarea no puede estar vacía")
        self.tasks.append({'id': self.next_id, 'description': task})
        self.next_id += 1

    def get_all_tasks(self):
        return self.tasks

    def delete_task(self, task_id):
        if task_id <= 0:
            raise ValueError("El ID de la tarea debe ser mayor que 0")
        self.tasks = [task for task in self.tasks if task['id'] != task_id]
```

Este código implementa las siguientes funcionalidades:
- **add_task**: Añade una tarea a la lista, asignando un identificador único.
- **get_all_tasks**: Devuelve todas las tareas actuales.
- **delete_task**: Elimina una tarea dado su identificador.

### 3. **Paso 2: Pruebas Unitarias (test_app.py)**

Ahora vamos a implementar las pruebas unitarias para las funciones anteriores. Usaremos el módulo `unittest` de Python.

```python
# test_app.py

import unittest
from app import ToDoList

class TestToDoList(unittest.TestCase):

    def setUp(self):
        self.todo_list = ToDoList()

    def test_add_task(self):
        # Añadir una tarea y verificar que se ha añadido correctamente
        self.todo_list.add_task("Tarea 1")
        self.assertEqual(len(self.todo_list.get_all_tasks()), 1)
        self.assertEqual(self.todo_list.get_all_tasks()[0]['description'], "Tarea 1")

    def test_add_empty_task(self):
        # Intentar añadir una tarea vacía debe lanzar una excepción
        with self.assertRaises(ValueError):
            self.todo_list.add_task("")

    def test_get_all_tasks(self):
        # Añadir múltiples tareas y verificar que se recuperan correctamente
        self.todo_list.add_task("Tarea 1")
        self.todo_list.add_task("Tarea 2")
        tasks = self.todo_list.get_all_tasks()
        self.assertEqual(len(tasks), 2)

    def test_delete_task(self):
        # Eliminar una tarea y verificar que se ha eliminado correctamente
        self.todo_list.add_task("Tarea 1")
        self.todo_list.add_task("Tarea 2")
        self.todo_list.delete_task(1)
        self.assertEqual(len(self.todo_list.get_all_tasks()), 1)
        self.assertEqual(self.todo_list.get_all_tasks()[0]['description'], "Tarea 2")

    def test_delete_invalid_task(self):
        # Intentar eliminar una tarea con un ID no válido debe lanzar una excepción
        with self.assertRaises(ValueError):
            self.todo_list.delete_task(-1)

if __name__ == '__main__':
    unittest.main()
```

### 4. **Ejecución de las pruebas**

Para ejecutar las pruebas unitarias, sigue los siguientes pasos en **VSCode**:

1. Abre el proyecto en **VSCode**.
2. En la terminal de **VSCode**, ejecuta el siguiente comando:
   ```bash
   python -m unittest test_app.py
   ```
3. Deberías ver un resultado que indica cuántas pruebas se han ejecutado y si todas han pasado correctamente.

---

### **Explicación de las pruebas:**
- **Prueba de añadir tarea (`test_add_task`)**: Verifica que al añadir una tarea, ésta se guarde correctamente y se asigne una descripción.
- **Prueba de añadir tarea vacía (`test_add_empty_task`)**: Verifica que al intentar añadir una tarea vacía, se lance una excepción (`ValueError`).
- **Prueba de obtener todas las tareas (`test_get_all_tasks`)**: Verifica que las tareas añadidas se puedan recuperar correctamente.
- **Prueba de eliminar tarea (`test_delete_task`)**: Verifica que se pueda eliminar una tarea existente, y que las tareas restantes permanezcan intactas.
- **Prueba de eliminar tarea inválida (`test_delete_invalid_task`)**: Verifica que al intentar eliminar una tarea con un ID no válido, se lance una excepción.

---

### **Conceptos Clave:**
- **Pruebas unitarias**: Se verifica cada funcionalidad de la clase `ToDoList` de manera aislada.
- **Excepciones**: Se manejan casos de errores comunes, como añadir una tarea vacía o eliminar una tarea con un ID no válido.
- **[[unittest]]**: Se utiliza el módulo estándar de Python para pruebas, mostrando cómo se ejecutan y verifican diferentes casos.

Este ejemplo sencillo de gestión de tareas es ideal para mostrar los conceptos fundamentales de las pruebas unitarias. ¿Te gustaría profundizar en algún aspecto más o agregar más funcionalidad para las próximas etapas?

---
- Ver [[Pruebas unitarias 2]] 