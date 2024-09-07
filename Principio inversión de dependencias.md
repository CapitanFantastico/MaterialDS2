.
- Ver también [[Interfaces]] 

El principio de Dependency Inversion es un principio de diseño de software que establece que los módulos de alto nivel no deben depender directamente de los módulos de bajo nivel. En su lugar, ambos deben depender de abstracciones. Además, las abstracciones no deben depender de los detalles, sino que los detalles deben depender de las abstracciones.

Este principio promueve la separación de preocupaciones y la flexibilidad en el diseño de software al invertir la dirección de las dependencias. En lugar de que los módulos de alto nivel dependan directamente de los módulos de bajo nivel, ambos deben depender de abstracciones que definan interfaces comunes.

Aquí tienes un ejemplo en Python sin el uso de frameworks que ilustra el principio de Dependency Inversion:

```python
# Abstracción
class Database:
    def read(self):
        pass

# Implementación concreta de bajo nivel
class MySQLDatabase(Database):
    def read(self):
        return "Leyendo datos de MySQL"

# Implementación concreta de bajo nivel
class PostgresDatabase(Database):
    def read(self):
        return "Leyendo datos de Postgres"

# Clase de alto nivel que depende de la abstracción
class DataReader:
    def __init__(self, database):
        self.database = database

    def read_data(self):
        return self.database.read()

# Uso
mysql_db = MySQLDatabase()
data_reader = DataReader(mysql_db)
print(data_reader.read_data())

postgres_db = PostgresDatabase()
data_reader = DataReader(postgres_db)
print(data_reader.read_data())
```

En este ejemplo, la clase `Database` actúa como una abstracción que define el método `read`. Las clases `MySQLDatabase` y `PostgresDatabase` son implementaciones concretas de bajo nivel que implementan el método `read`. La clase `DataReader` es un módulo de alto nivel que depende de la abstracción `Database` en lugar de depender directamente de las implementaciones concretas.

A continuación, se muestra un diagrama de clases simplificado:

```
+----------------+
|    Database    |
+----------------+
|    read()      |
+----------------+
        ^
        |
        |
+----------------+       +-------------------+
| MySQLDatabase  |       | PostgresDatabase  |
+----------------+       +-------------------+
|    read()      |       |     read()        |
+----------------+       +-------------------+
        ^                        ^
        |                        |
        |                        |
+----------------+       +-------------------+
|   DataReader   |
+----------------+
|    read_data() |
+----------------+
```

En este diagrama, `Database` es la abstracción, `MySQLDatabase` y `PostgresDatabase` son las implementaciones concretas de bajo nivel, y `DataReader` es el módulo de alto nivel que depende de la abstracción `Database`.

- Ver también [[Interfaces]] 
