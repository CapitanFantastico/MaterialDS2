.
- Ver también [[Interfaces]] 

El principio de diseño de software Polymorphism de GRASP se refiere a la capacidad de los objetos de diferentes clases de responder a un mismo mensaje de manera específica a su tipo. Esto se logra mediante el uso de la [[herencia]] y la implementación de métodos polimórficos que pueden comportarse de manera distinta según el tipo de objeto al que se apliquen.

Aquí tienes un ejemplo sencillo en Python que ilustra el principio de diseño de software Polymorphism de GRASP:

```python
class Animal:
    def hablar(self):
        pass

class Perro(Animal):
    def hablar(self):
        return "¡Guau!"

class Gato(Animal):
    def hablar(self):
        return "¡Miau!"

class Vaca(Animal):
    def hablar(self):
        return "¡Muu!"

# Crear instancias de diferentes animales
perro = Perro()
gato = Gato()
vaca = Vaca()

# Llamar al método hablar de cada animal
print(perro.hablar())  # Output: ¡Guau!
print(gato.hablar())   # Output: ¡Miau!
print(vaca.hablar())   # Output: ¡Muu!
```

En este ejemplo, la clase `Animal` es una [[clase]] base que define un [[método]] `hablar` que será implementado de manera específica por las subclases. Las clases `Perro`, `Gato` y `Vaca` heredan de la clase `Animal` y cada una implementa su propio comportamiento para el método `hablar`.

El principio de diseño Polymorphism de GRASP se aplica en la forma en que el método `hablar` se comporta de manera polimórfica, es decir, cada subclase de `Animal` responde al mismo mensaje (`hablar`) de manera específica a su tipo. Al llamar al método `hablar` en cada instancia de animal, obtenemos un comportamiento distinto dependiendo del tipo de animal, lo que demuestra el polimorfismo en acción.

Al seguir el principio de diseño de software Polymorphism de GRASP, se promueve la reutilización de código y la flexibilidad en el diseño del sistema, ya que las diferentes subclases pueden comportarse de manera distinta pero aún así responder al mismo mensaje de manera coherente. Esto facilita la extensibilidad y mantenimiento del sistema.

- Ver también [[Interfaces]] 
