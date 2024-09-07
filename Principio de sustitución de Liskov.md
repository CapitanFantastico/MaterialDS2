.
- Ver [[Diseño por contrato]] 

El Principio de Sustitución de Liskov (LSP) es otro de los principios SOLID y es esencial en la programación orientada a objetos. Según este principio, los objetos de una clase derivada deben ser capaces de reemplazar a los objetos de la clase base sin afectar la integridad del programa. 

Esencialmente, significa que las subclases deben ser sustituibles por sus clases base.

### Ejemplo Sencillo en Python

Supongamos que estamos trabajando en un sistema de gestión para un parque zoológico, y queremos modelar diferentes tipos de aves.

```python
class Bird:
    def fly(self):
        return "This bird can fly."

class Duck(Bird):
    def fly(self):
        return "Duck flies."

class Penguin(Bird):
    def fly(self):
        return "Penguin can't fly!"
```

Si bien el ejemplo anterior sigue una herencia técnica, no cumple con LSP porque la clase `Penguin` cambia el comportamiento esperado de la clase base `Bird`. Según LSP, todas las subclases de `Bird` deberían poder volar si el método `fly()` se está invocando.

Para adherir al LSP, debemos estructurar nuestra jerarquía de clases para que no alteremos el comportamiento esperado:

```python
class FlyingBird:
    def fly(self):
        return "This bird can fly."

class NonFlyingBird:
    def walk(self):
        return "This bird can walk."

class Duck(FlyingBird):
    pass  # Duck inherits flying behavior

class Penguin(NonFlyingBird):
    pass  # Penguin inherits walking behavior
```

### Uso de las Clases

Aquí, `Duck` y `Penguin` están clasificados más adecuadamente según sus habilidades, respetando LSP. Ambas clases pueden ser usadas en contextos que esperan sus respectivos comportamientos sin sorpresas:

```python
def bird_activity(bird):
    if isinstance(bird, FlyingBird):
        print(bird.fly())
    elif isinstance(bird, NonFlyingBird):
        print(bird.walk())

duck = Duck()
penguin = Penguin()

bird_activity(duck)    # Expected behavior: can fly
bird_activity(penguin) # Expected behavior: can walk
```

### Salida
```
This bird can fly.
This bird can walk.
```

Este diseño asegura que cada subclase de `FlyingBird` y `NonFlyingBird` puede ser utilizada sin violar las expectativas del comportamiento heredado de su clase base, cumpliendo así con el Principio de Sustitución de Liskov.