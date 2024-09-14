.
Ejemplo sencillo de un sistema de gestión de tareas (To-Do List) que se conecta a una base de datos PostgreSQL. Vamos a crear un código básico en Python y luego veremos cómo realizar pruebas unitarias. Aquí no usaremos frameworks de desarrollo, y el entorno será manejado con **VSCode**.

### 1. **Estructura del proyecto**
El proyecto tendrá la siguiente estructura:
```
/proyecto_tareas/
│
├── app.py            # Código principal de la aplicación
├── database.py       # Código de conexión a PostgreSQL
├── test_app.py       # Archivo con las pruebas unitarias
└── requirements.txt  # Dependencias del proyecto (psycopg2) 
```

### 2. **Paso 1: Código principal (app.py)**

```python
# app.py

from database import Database

class ToDoList:
    def __init__(self, db):
        self.db = db

    def add_task(self, task):
        if not task:
            raise ValueError("La tarea no puede estar vacía")
        self.db.insert_task(task)

    def get_all_tasks(self):
        return self.db.get_tasks()

    def delete_task(self, task_id):
        if task_id <= 0:
            raise ValueError("El ID de la tarea debe ser mayor que 0")
        self.db.delete_task(task_id)
```

### 3. **Paso 2: Conexión a PostgreSQL (database.py)**

```python
# database.py

import psycopg2

class Database:
    def __init__(self, dbname, user, password, host):
        self.conn = psycopg2.connect(dbname=dbname, user=user, password=password, host=host)
        self.cursor = self.conn.cursor()

    def insert_task(self, task):
        query = "INSERT INTO tasks (description) VALUES (%s)"
        self.cursor.execute(query, (task,))
        self.conn.commit()

    def get_tasks(self):
        self.cursor.execute("SELECT * FROM tasks")
        return self.cursor.fetchall()

    def delete_task(self, task_id):
        query = "DELETE FROM tasks WHERE id = %s"
        self.cursor.execute(query, (task_id,))
        self.conn.commit()

    def close(self):
        self.cursor.close()
        self.conn.close()
```

Este código permite la inserción, recuperación y eliminación de tareas en la base de datos PostgreSQL. Asegúrate de tener una tabla creada en PostgreSQL llamada `tasks` con al menos un campo `description` y un `id`.

### 4. **Paso 3: Pruebas Unitarias (test_app.py)**

Las pruebas unitarias se centrarán en probar la clase `ToDoList` de manera aislada, simulando la interacción con la base de datos usando **[[Mocking]]** (aunque sin frameworks de testing avanzados).

```python
# test_app.py

import unittest
from app import ToDoList

class MockDatabase:
    def __init__(self):
        self.tasks = []
    
    def insert_task(self, task):
        self.tasks.append({'id': len(self.tasks) + 1, 'description': task})
    
    def get_tasks(self):
        return self.tasks
    
    def delete_task(self, task_id):
        self.tasks = [task for task in self.tasks if task['id'] != task_id]

class TestToDoList(unittest.TestCase):
    def setUp(self):
        self.mock_db = MockDatabase()
        self.todo_list = ToDoList(self.mock_db)
    
    def test_add_task(self):
        self.todo_list.add_task("Tarea 1")
        self.assertEqual(len(self.mock_db.get_tasks()), 1)
        self.assertEqual(self.mock_db.get_tasks()[0]['description'], "Tarea 1")

    def test_add_empty_task(self):
        with self.assertRaises(ValueError):
            self.todo_list.add_task("")
    
    def test_get_all_tasks(self):
        self.todo_list.add_task("Tarea 1")
        self.todo_list.add_task("Tarea 2")
        tasks = self.todo_list.get_all_tasks()
        self.assertEqual(len(tasks), 2)
    
    def test_delete_task(self):
        self.todo_list.add_task("Tarea 1")
        self.todo_list.add_task("Tarea 2")
        self.todo_list.delete_task(1)
        self.assertEqual(len(self.mock_db.get_tasks()), 1)

    def test_delete_invalid_task(self):
        with self.assertRaises(ValueError):
            self.todo_list.delete_task(-1)

if __name__ == '__main__':
    unittest.main()
```

### 5. **Paso 4: Instalación de dependencias**

En el archivo `requirements.txt`, añade la siguiente línea para instalar `psycopg2`, el conector de Python para PostgreSQL.

```text
psycopg2==2.9.1
```

### 6. **Paso 5: Ejecutar las pruebas en VSCode**

1. Abre VSCode y asegúrate de tener Python y PostgreSQL instalados.
2. En la terminal de VSCode, instala las dependencias con:
   ```bash
   pip install -r requirements.txt
   ```
3. Luego, ejecuta las pruebas con el siguiente comando:
   ```bash
   python -m unittest test_app.py
   ```

---

### **Conceptos Clave:**
- **Pruebas unitarias**: Se validan individualmente las funciones y métodos.
- **Mocking**: Simulamos el comportamiento de la base de datos para no depender de la interacción real con PostgreSQL en las pruebas unitarias.
- **Excepciones**: Se muestran cómo manejar errores (e.g., tareas vacías, ID de tarea inválido).

Este es solo el primer paso centrado en las pruebas unitarias. Puedes expandirlo más adelante para agregar otros tipos de pruebas como pruebas de integración y sistema.


---

## Glosario

[[psycopg]]  