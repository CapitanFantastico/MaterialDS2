.
La programación orientada a objetos (OOP) en Python permite usar tanto herencia como composición para organizar y estructurar el código. A continuación, te muestro cómo puedes convertir un ejemplo que utiliza herencia en uno que utiliza composición, para mostrar cómo se pueden utilizar estos conceptos para alcanzar resultados similares en Python.

### Ejemplo con Herencia

Supongamos que tienes una clase `Motor` y una clase `Carro`, donde `Carro` hereda de `Motor`.

```python
class Motor:
    def __init__(self, cilindros):
        self.cilindros = cilindros
        self.estado = "apagado"

    def encender(self):
        self.estado = "encendido"
        print("Motor encendido.")

    def apagar(self):
        self.estado = "apagado"
        print("Motor apagado.")

class Carro(Motor):
    def __init__(self, cilindros, marca):
        super().__init__(cilindros)
        self.marca = marca

    def conducir(self):
        if self.estado == "encendido":
            print(f"Conduciendo mi {self.marca}.")
        else:
            print("El motor está apagado.")
```

En este ejemplo, `Carro` hereda de `Motor`, lo que significa que cada objeto `Carro` tiene todas las propiedades y métodos de `Motor`.

### Conversión a Composición

En la composición, en lugar de que `Carro` herede de `Motor`, `Carro` tendría un `Motor` como atributo.

```python
class Motor:
    def __init__(self, cilindros):
        self.cilindros = cilindros
        self.estado = "apagado"

    def encender(self):
        self.estado = "encendido"
        print("Motor encendido.")

    def apagar(self):
        self.estado = "apagado"
        print("Motor apagado.")

class Carro:
    def __init__(self, cilindros, marca):
        self.motor = Motor(cilindros)  # Composición aquí
        self.marca = marca

    def encender_motor(self):
        self.motor.encender()

    def apagar_motor(self):
        self.motor.apagar()

    def conducir(self):
        if self.motor.estado == "encendido":
            print(f"Conduciendo mi {self.marca}.")
        else:
            print("El motor está apagado.")
```

### Ventajas de la Composición sobre la Herencia

- **Flexibilidad**: La composición permite cambiar las capacidades del objeto en tiempo de ejecución al asignar diferentes objetos a las propiedades del compuesto.
- **Menor Acoplamiento**: Reduce la dependencia entre clases. En el ejemplo de composición, la clase `Carro` no depende directamente de los métodos internos de `Motor`, sólo utiliza su interfaz pública.
- **Fácil Mantenimiento**: Los cambios en la clase `Motor` afectan menos a la clase `Carro`, porque `Carro` solo interactúa con `Motor` a través de su interfaz pública.

Este simple cambio muestra cómo la composición puede ser una alternativa poderosa a la herencia, proporcionando mayor flexibilidad y facilitando la gestión y el mantenimiento del código.

---
Plantea un ejemplo en Python, sin el uso de frameworks, que muestre la aplicación del principio de desarrollo de software: Composition over inheritance. Además, muestra el diagrama de clases correspondiente.

El principio de "Composición sobre herencia" sugiere que se debe preferir la composición de objetos sobre la herencia de clases para reutilizar el código y construir relaciones entre clases. A continuación, te mostraré un ejemplo en Python que sigue este principio.

```python
class Engine:
    def start(self):
        print("Engine started")

    def stop(self):
        print("Engine stopped")

class Car:
    def __init__(self):
        self.engine = Engine()

    def start(self):
        self.engine.start()

    def stop(self):
        self.engine.stop()

class ElectricEngine:
    def start(self):
        print("Electric engine started")

    def stop(self):
        print("Electric engine stopped")

class ElectricCar:
    def __init__(self):
        self.engine = ElectricEngine()

    def start(self):
        self.engine.start()

    def stop(self):
        self.engine.stop()

# Crear instancias de Car y ElectricCar
car = Car()
electric_car = ElectricCar()

# Iniciar y detener el coche y el coche eléctrico
car.start()
car.stop()

electric_car.start()
electric_car.stop()
```

En este ejemplo, tenemos las clases `Engine` y `Car`, que representan un motor genérico y un coche con un motor genérico respectivamente. También tenemos las clases `ElectricEngine` y `ElectricCar`, que representan un motor eléctrico y un coche con un motor eléctrico respectivamente.

La clase `Car` tiene un atributo `engine` que es una instancia de la clase `Engine`, y la clase `ElectricCar` tiene un atributo `engine` que es una instancia de la clase `ElectricEngine`. Ambas clases `Car` y `ElectricCar` tienen métodos `start` y `stop` que delegan la llamada al método correspondiente del objeto `engine`.

Al seguir el principio de "Composición sobre herencia", hemos utilizado la composición para construir la relación entre el coche y el motor, en lugar de heredar directamente de una clase de motor. Esto nos permite reutilizar la lógica del motor en múltiples tipos de coches sin depender de la jerarquía de herencia.

A continuación, se presenta el diagrama de clases para este ejemplo:

```
+-------------------------------------+
|              Engine                 |
+-------------------------------------+
| + start(): void                    |
| + stop(): void                     |
+-------------------------------------+

+-------------------------------------+
|                Car                  |
+-------------------------------------+
| - engine: Engine                   |
+-------------------------------------+
| + start(): void                    |
| + stop(): void                     |
+-------------------------------------+

+-------------------------------------+
|          ElectricEngine             |
+-------------------------------------+
| + start(): void                    |
| + stop(): void                     |
+-------------------------------------+

+-------------------------------------+
|            ElectricCar              |
+-------------------------------------+
| - engine: ElectricEngine           |
+-------------------------------------+
| + start(): void                    |
| + stop(): void                     |
+-------------------------------------+
```

En este diagrama de clases, se muestran las clases `Engine`, `Car`, `ElectricEngine` y `ElectricCar`, junto con sus atributos y métodos. La clase `Car` y `ElectricCar` utilizan la composición para construir la relación con la clase `Engine` y `ElectricEngine` respectivamente, en lugar de heredar directamente de ellas. Esto sigue el principio de "Composición sobre herencia" y proporciona una mayor flexibilidad y reutilización de código.

---

Plantea un ejemplo en Python, sin el uso de frameworks, que muestre un sistema de creación de sillas de distinto tipo, por ejemplo, silla de oficina y silla gamer, usando herencia.
Luego modifica el código para que además permita crear esos mismos tipos de sillas, ahora con la posibilidad de que vengan de dos colores distintos, ejemplo. rojo y azul.
Luego modifica el código para que además permita crear esas mismas sillas, ahora en tamaño grande o pequeño.


Aquí tienes un ejemplo en Python que muestra un sistema de creación de sillas de distintos tipos (silla de oficina y silla gamer) usando herencia:

```python
class Chair:
    def __init__(self, chair_type):
        self.chair_type = chair_type

    def sit(self):
        print(f"Sitting on a {self.chair_type} chair")

class OfficeChair(Chair):
    def __init__(self):
        super().__init__("office")

class GamerChair(Chair):
    def __init__(self):
        super().__init__("gamer")

# Crear instancias de sillas
office_chair = OfficeChair()
gamer_chair = GamerChair()

office_chair.sit()
gamer_chair.sit()
```

En este código, tenemos la clase base `Chair` que tiene un método `sit` para simular sentarse en una silla. Luego, creamos las subclases `OfficeChair` y `GamerChair` que heredan de la clase base `Chair` y definen el tipo de silla correspondiente.

Para permitir la creación de sillas en diferentes colores, podemos modificar el código de la siguiente manera:

```python
class Chair:
    def __init__(self, chair_type, color):
        self.chair_type = chair_type
        self.color = color

    def sit(self):
        print(f"Sitting on a {self.color} {self.chair_type} chair")

class OfficeChair(Chair):
    def __init__(self, color):
        super().__init__("office", color)

class GamerChair(Chair):
    def __init__(self, color):
        super().__init__("gamer", color)

# Crear instancias de sillas en diferentes colores
red_office_chair = OfficeChair("red")
blue_gamer_chair = GamerChair("blue")

red_office_chair.sit()
blue_gamer_chair.sit()
```

Ahora, cada silla tiene un atributo adicional `color`. Al crear instancias de `OfficeChair` y `GamerChair`, especificamos el color de la silla.

Finalmente, para permitir la creación de sillas en diferentes tamaños, podemos modificar el código de la siguiente manera:

```python
class Chair:
    def __init__(self, chair_type, color, size):
        self.chair_type = chair_type
        self.color = color
        self.size = size

    def sit(self):
        print(f"Sitting on a {self.size} {self.color} {self.chair_type} chair")

class OfficeChair(Chair):
    def __init__(self, color, size):
        super().__init__("office", color, size)

class GamerChair(Chair):
    def __init__(self, color, size):
        super().__init__("gamer", color, size)

# Crear instancias de sillas en diferentes tamaños
large_red_office_chair = OfficeChair("red", "large")
small_blue_gamer_chair = GamerChair("blue", "small")

large_red_office_chair.sit()
small_blue_gamer_chair.sit()
```

Ahora, cada silla tiene un atributo adicional `size`. Al crear instancias de `OfficeChair` y `GamerChair`, especificamos el tamaño de la silla. Esto nos permite crear sillas de oficina y gamer en diferentes colores y tamaños.



la aplicación del principio de desarrollo de software: Composition over inheritance. Además, muestra el diagrama de clases correspondiente.


Si aplicamos composición en lugar de herencia en el ejemplo de las sillas, tendríamos una estructura donde las sillas contienen un objeto de tipo `ChairType` que define el tipo, color y tamaño de la silla. Aquí tienes un ejemplo de cómo sería en Python:

```python
class ChairType:
    def __init__(self, chair_type, color, size):
        self.chair_type = chair_type
        self.color = color
        self.size = size

class Chair:
    def __init__(self, chair_type):
        self.chair_type = chair_type

    def sit(self):
        print(f"Sitting on a {self.chair_type.color} {self.chair_type.size} {self.chair_type.chair_type} chair")

# Crear instancias de ChairType para definir los atributos de las sillas
red_large_office_type = ChairType("office", "red", "large")
blue_small_gamer_type = ChairType("gamer", "blue", "small")

# Crear instancias de sillas que contienen un objeto de tipo ChairType
red_large_office_chair = Chair(red_large_office_type)
blue_small_gamer_chair = Chair(blue_small_gamer_type)

red_large_office_chair.sit()
blue_small_gamer_chair.sit()
```

En este código, creamos la clase `ChairType` que define el tipo, color y tamaño de la silla. Luego, la clase `Chair` contiene un objeto de tipo `ChairType` que define las características específicas de la silla. Al crear instancias de `Chair`, pasamos un objeto `ChairType` que define las propiedades de la silla.

Este enfoque de composición permite una mayor flexibilidad al definir las características de las sillas, ya que podemos cambiarlas dinámicamente en tiempo de ejecución al modificar el objeto `ChairType` asociado a cada silla.


---

Composicion Sobre Herencia en POO explicacion
Eduardo Zepeda
Eduardo Zepeda
11 de octubre de 2023
Traducciones:
- en: Composition over inheritance in OOP simple explanation
⏲ Tiempo de lectura 2 minutos
Arquitectura de software
Composition over inheritance, o composición sobre herencia es un tema recurrente en la programación orientada a objectos. Generalmente, se explica de una manera muy compleja, pero hoy voy a tratar de simplificarlo al punto en que los puristas me detesten.

Empezamos, imagina que tienes una gigantesca caja de ladrillos LEGO, sí, esos pequeños bloques de plástico que causan un dolor inimaginable cuando los pisas. Pero, en este caso, no los usaremos para causar dolor sino para construir diferentes tipos de automóviles.

Herencia o composición
Para construir nuestros diminutos automóviles, existen dos maneras:

Herencia: Puedes empezar con un diseño de automóvil básico, y luego hacerle cambios para crear diferentes tipos de automóviles. Pero, a veces, esto puede ser un completo desastre, puesto que puedes terminar con algunos automóviles extraños que no funcionarán correctamente.

Composición: En lugar de empezar con un automóvil básico y cambiarlo, puedes utilizar piezas LEGO más pequeñas para construir las diferentes partes de un automóvil, como ruedas, puertas y ventanas. Luego, junta esas piezas para crear distintos tipos de automóviles. De esta forma, tienes más control y flexibilidad para crear exactamente el tipo de coche que quieres sin hacer un desastre.

Por lo tanto, la composición sobre la herencia significa que a menudo es mejor construir cosas poniendo partes más pequeñas juntas en lugar de cambiar una cosa grande para hacer algo nuevo.

Composición sobre herencia, ejemplo
Y puesto en un ejemplo usando código en Python obtendriamos algo como:


# Inheritance o herencia

```python

class Car:
    def start_engine(self):
        print("Starting engine")

class SportsCar(Car):
    def start_engine(self):
        print("Rrrrrrrr! Starting engine")

```
# Composition o composición

```python
class Engine:
    def start(self):
        print("Starting engine")

class Car:
    def __init__(self):
        self.engine = Engine()

    def start_engine(self):
        self.engine.start()

class SportsCar:
    def __init__(self):
        self.engine = Engine()

    def start_engine(self):
        print("Vroooooom! Starting engine")

# Using Composition
regular_car = Car()
regular_car.start_engine()

fast_car = SportsCar()
fast_car.start_engine()

```

En el ejemplo de herencia, empezamos con un “Automóvil” básico y lo modificamos para hacer un “SportsCar”. En el ejemplo de composición, construimos un “Automóvil” y un “SportsCar” combinando piezas más pequeñas, como el motor. Es como utilizar piezas de LEGO para construir coches, y nos da más control y flexibilidad a la hora de escribir nuestros programas.