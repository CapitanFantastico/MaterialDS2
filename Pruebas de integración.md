.
Las pruebas de integración son un tipo de prueba de software que se enfoca en verificar la interacción y la comunicación entre diferentes componentes, módulos o sistemas independientes una vez que han sido integrados. El objetivo principal de estas pruebas es asegurar que, al combinar las unidades individuales que han pasado las pruebas unitarias, funcionen correctamente en un entorno integrado.

Algunas características importantes de las pruebas de integración son:

1. **Interacción entre Componentes**: Se centran en cómo interactúan las distintas partes del sistema. Pueden incluir la comunicación entre módulos, la interfaz entre la base de datos y la aplicación, o la integración de servicios externos.

2. **Detección de Problemas de Interfaz**: Ayudan a identificar errores que podrían no haber sido descubiertos durante las pruebas unitarias, tales como fallas en la forma en que los componentes envían o reciben datos.

3. **Tipos de Pruebas de Integración**:
   - **[[Pruebas de Integración de Big Bang]]**: Se integran todos los componentes al mismo tiempo y se realizan pruebas en conjunto.
   - **[[Pruebas de Integración Incremental]]**: Se integran y prueban los componentes de manera gradual, lo que puede ser hacia arriba (desde piezas individuales hacia el todo), o hacia abajo (desde el todo hacia las piezas).
   - **[[Pruebas de Integración por Paquete]]**: Se integran grupos de componentes relacionadas y se prueban en conjunto.

4. **Automatización**: Al igual que las pruebas unitarias, las pruebas de integración se pueden automatizar utilizando herramientas específicas, lo que facilita su ejecución repetida a lo largo del proceso de desarrollo.

5. **Refuerzo de las Pruebas Unitarias**: Aunque las pruebas unitarias verifican el funcionamiento de componentes individuales, las pruebas de integración aseguran que estas unidades funcionen correctamente juntas, abordando problemas que surgen debido a la interacción entre ellas.

6. **Entornos de Prueba**: Las pruebas de integración se llevan a cabo típicamente en un entorno que simula el sistema de producción para evaluar cómo los componentes interactúan en condiciones más realistas.

Las pruebas de integración son fundamentales para garantizar la calidad y la robustez de sistemas complejos, ayudando a minimizar problemas en las fases posteriores del desarrollo y en la producción.

---

Las **pruebas de integración** se enfocan en verificar la correcta interacción entre diferentes módulos o componentes de una aplicación, asegurando que se comporten correctamente cuando trabajan juntos. A continuación, plantearemos un ejemplo de pruebas de integración utilizando el mismo sistema de gestión de tareas (**To-Do List**), pero esta vez simulando que interactuamos con un servicio externo o un componente adicional.

### 1. **Planteamiento del Caso: Gestión de Tareas con Almacenamiento Externo**

En este ejemplo, extenderemos el caso anterior para integrar un componente adicional: una **simulación de un almacenamiento externo**, donde se guardan las tareas en un servicio (en lugar de una lista en memoria). Así, las pruebas de integración verificarán cómo interactúan los componentes entre sí: la clase `ToDoList` con la clase `ExternalStorage`.

### 2. **Estructura del proyecto**
La estructura del proyecto será similar a la anterior, pero con la inclusión de una clase para simular el almacenamiento externo.

```
/proyecto_tareas/
│
├── app.py             # Código principal de la aplicación
├── external_storage.py # Simulación del almacenamiento externo
└── test_integration.py # Archivo con las pruebas de integración
```

### 3. **Paso 1: Código principal (app.py)**

El archivo `app.py` sigue siendo el mismo, pero ahora pasaremos el componente de almacenamiento externo como dependencia de `ToDoList`.

```python
# app.py

class ToDoList:
    def __init__(self, storage):
        self.storage = storage

    def add_task(self, task):
        if not task:
            raise ValueError("La tarea no puede estar vacía")
        self.storage.save_task({'description': task})

    def get_all_tasks(self):
        return self.storage.load_tasks()

    def delete_task(self, task_id):
        if task_id <= 0:
            raise ValueError("El ID de la tarea debe ser mayor que 0")
        self.storage.delete_task(task_id)
```

### 4. **Paso 2: Simulación del almacenamiento externo (external_storage.py)**

En lugar de usar una lista local como antes, simularemos que las tareas se guardan en un servicio externo. Este módulo proporcionará una interfaz para "guardar", "cargar" y "eliminar" tareas.

```python
# external_storage.py

class ExternalStorage:
    def __init__(self):
        # Simulamos un almacenamiento externo como una lista de tareas
        self.tasks = []
        self.next_id = 1

    def save_task(self, task):
        task['id'] = self.next_id
        self.tasks.append(task)
        self.next_id += 1

    def load_tasks(self):
        return self.tasks

    def delete_task(self, task_id):
        self.tasks = [task for task in self.tasks if task['id'] != task_id]
```

### 5. **Paso 3: Pruebas de Integración (test_integration.py)**

Las **pruebas de integración** ahora validarán si la interacción entre `ToDoList` y `ExternalStorage` funciona como se espera.

```python
# test_integration.py

import unittest
from app import ToDoList
from external_storage import ExternalStorage

class TestToDoListIntegration(unittest.TestCase):

    def setUp(self):
        # Usamos el almacenamiento externo como dependencia
        self.storage = ExternalStorage()
        self.todo_list = ToDoList(self.storage)

    def test_add_and_get_task(self):
        # Añadir una tarea y verificar que se guarda en el almacenamiento externo
        self.todo_list.add_task("Tarea 1")
        tasks = self.todo_list.get_all_tasks()
        self.assertEqual(len(tasks), 1)
        self.assertEqual(tasks[0]['description'], "Tarea 1")

    def test_delete_task(self):
        # Añadir dos tareas, eliminar una y verificar que se eliminó correctamente
        self.todo_list.add_task("Tarea 1")
        self.todo_list.add_task("Tarea 2")
        self.todo_list.delete_task(1)
        tasks = self.todo_list.get_all_tasks()
        self.assertEqual(len(tasks), 1)
        self.assertEqual(tasks[0]['description'], "Tarea 2")

    def test_delete_invalid_task(self):
        # Intentar eliminar una tarea con un ID no válido
        self.todo_list.add_task("Tarea 1")
        with self.assertRaises(ValueError):
            self.todo_list.delete_task(-1)

if __name__ == '__main__':
    unittest.main()
```

### 6. **Ejecución de las pruebas**

Para ejecutar las pruebas de integración en **VSCode**, simplemente sigue los mismos pasos que en el caso de las pruebas unitarias:

1. Abre el proyecto en **VSCode**.
2. En la terminal de **VSCode**, ejecuta el siguiente comando:
   ```bash
   python -m unittest test_integration.py
   ```

---

### **Explicación de las pruebas:**
- **Prueba de añadir y obtener tareas (`test_add_and_get_task`)**: Verifica que la tarea añadida a través de `ToDoList` se guarde correctamente en el almacenamiento externo y se pueda recuperar.
- **Prueba de eliminar tarea (`test_delete_task`)**: Verifica que al eliminar una tarea en `ToDoList`, esta también desaparece del almacenamiento externo.
- **Prueba de eliminar tarea inválida (`test_delete_invalid_task`)**: Verifica que se lance una excepción si intentamos eliminar una tarea con un ID inválido.

---

### **Conceptos Clave para la Clase Práctica:**
- **Pruebas de integración**: Se verifican las interacciones entre diferentes componentes, en este caso, la clase `ToDoList` y `ExternalStorage`.
- **Simulación de almacenamiento externo**: No interactuamos con una base de datos real ni con un servicio externo, pero simulamos su comportamiento con el fin de validar la integración.
- **Verificación del flujo completo**: Las pruebas de integración aseguran que el flujo entre la lógica de negocio y el almacenamiento funcione correctamente, desde añadir hasta eliminar tareas.

Este caso te proporciona un ejemplo sencillo pero completo de cómo realizar pruebas de integración en un entorno sin frameworks de desarrollo.





## Ver también 
- https://www.youtube.com/watch?v=pxOwxsBFYYo - 