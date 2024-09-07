.
- Ver también [[Interfaces]] 

El **encapsulamiento y ocultamiento de la información** y la **abstracción** son conceptos relacionados en la programación orientada a objetos, pero no son lo mismo. Ambos juegan un papel importante en la creación de software modular, mantenible y fácil de entender, pero abordan diferentes aspectos del diseño de sistemas.

### Encapsulamiento y Ocultamiento de la Información

**Encapsulamiento** es el principio de agrupar datos (atributos) y comportamientos (métodos) relacionados dentro de una misma unidad, generalmente una clase u objeto.  **Ocultamiento de la información** es un aspecto del encapsulamiento que se refiere a restringir el acceso directo a ciertos detalles internos de esa unidad, exponiendo solo lo necesario a través de una interfaz pública.

- **Encapsulamiento**:
  - Permite agrupar datos y métodos relacionados en una sola entidad.
  - Facilita la gestión y el mantenimiento del código al mantener los datos y las operaciones que los manipulan juntos.

- **Ocultamiento de la Información**:
  - Protege los detalles internos de la implementación de un objeto, evitando que el código externo dependa de ellos.
  - Se logra a través de modificadores de acceso, como `private`, `protected`, y `public` en muchos lenguajes de programación.
  - Mejora la seguridad y robustez del sistema, ya que los cambios internos no afectan el código que usa la interfaz pública.

**Ejemplo**:
En una clase `Coche`, los detalles sobre cómo se enciende el motor (por ejemplo, cómo se manipula la corriente eléctrica) pueden estar ocultos. El usuario del objeto solo necesita invocar el método `encender()` y no preocuparse por los detalles internos.

```java
class Coche {
    private Motor motor;

    public void encender() {
        motor.activar(); // Detalles internos ocultos
    }
}
```

### Abstracción

**Abstracción** es el principio de representar las características esenciales y omitir los detalles irrelevantes para simplificar el diseño y la interacción con un sistema. La abstracción permite trabajar con conceptos de alto nivel, sin necesidad de preocuparse por las complejidades subyacentes.

- **Abstracción**:
  - Se centra en lo que hace un objeto o sistema, no en cómo lo hace.
  - Se utiliza para definir interfaces o clases abstractas que establecen un contrato para el comportamiento esperado sin proporcionar la implementación detallada.
  - Ayuda a reducir la complejidad al permitir a los desarrolladores pensar en términos de funciones y responsabilidades, en lugar de detalles de implementación.

**Ejemplo**:
Podemos tener una clase abstracta `FiguraGeometrica` que define un método `calcularArea()`. Las clases concretas como `Circulo` o `Rectangulo` implementan este método de acuerdo con sus propios detalles.

```java
abstract class FiguraGeometrica {
    abstract double calcularArea();
}

class Circulo extends FiguraGeometrica {
    private double radio;
    
    @Override
    double calcularArea() {
        return Math.PI * radio * radio;
    }
}

class Rectangulo extends FiguraGeometrica {
    private double largo;
    private double ancho;
    
    @Override
    double calcularArea() {
        return largo * ancho;
    }
}
```

### Diferencias Clave:

1. **Foco**:
   - **Encapsulamiento/Ocultamiento de la Información**: Se enfoca en cómo agrupar y proteger los datos y métodos dentro de un objeto.
   - **Abstracción**: Se enfoca en simplificar y generalizar el comportamiento y las interacciones con los objetos.

2. **Objetivo**:
   - **Encapsulamiento/Ocultamiento de la Información**: Mantener los detalles internos privados y controlar cómo se accede y modifica el estado de un objeto.
   - **Abstracción**: Definir interfaces claras y simplificadas que representen la esencia de un concepto, omitiendo detalles específicos.

3. **Aplicación**:
   - **Encapsulamiento/Ocultamiento de la Información**: Se aplica al nivel de la clase o del objeto para proteger los datos y comportamientos.
   - **Abstracción**: Se aplica al nivel del diseño para crear modelos simplificados y generalizados de sistemas complejos.

### Relación entre ambos:

- **Encapsulamiento** ayuda a implementar **abstracción** al permitir que un objeto o módulo exponga solo lo necesario a través de una interfaz pública, ocultando los detalles de implementación.
- **Abstracción** depende del encapsulamiento para garantizar que solo se exponga la información relevante y esencial, lo que permite a los desarrolladores trabajar con conceptos más simples y manejables.

En resumen, aunque relacionados, el encapsulamiento y ocultamiento de la información se centran en la protección y organización de datos dentro de un objeto, mientras que la abstracción se centra en simplificar y generalizar la interfaz y el comportamiento del sistema.

---

En Python, un ejemplo sencillo de abstracción podría ser la implementación de una clase `Vehiculo` que tiene atributos y métodos para representar un vehículo genérico. A través de la abstracción, podemos definir una clase base con ciertos atributos y métodos comunes a todos los vehículos, sin especificar la implementación detallada de cada tipo de vehículo.

Aquí tienes un ejemplo sencillo de abstracción en Python:

```python
from abc import ABC, abstractmethod

# Clase base abstracta Vehiculo
class Vehiculo(ABC):
    def __init__(self, marca, modelo):
        self.marca = marca
        self.modelo = modelo

    @abstractmethod
    def acelerar(self):
        pass

    @abstractmethod
    def frenar(self):
        pass

# Clase concreta que hereda de Vehiculo
class Coche(Vehiculo):
    def acelerar(self):
        print(f"{self.marca} {self.modelo} acelerando")

    def frenar(self):
        print(f"{self.marca} {self.modelo} frenando")

# Clase concreta que hereda de Vehiculo
class Moto(Vehiculo):
    def acelerar(self):
        print(f"{self.marca} {self.modelo} acelerando")

    def frenar(self):
        print(f"{self.marca} {self.modelo} frenando")

# Uso de las clases
coche = Coche("Ford", "Focus")
moto = Moto("Honda", "CBR")

coche.acelerar()
coche.frenar()

moto.acelerar()
moto.frenar()
```

En este ejemplo, la clase abstracta `Vehiculo` define dos métodos abstractos `acelerar` y `frenar`, que deben ser implementados por las clases concretas que heredan de ella. Las clases `Coche` y `Moto` son ejemplos de clases concretas que heredan de `Vehiculo` y proporcionan una implementación específica para los métodos `acelerar` y `frenar`.

La abstracción nos permite definir una clase base común para todos los vehículos, sin entrar en detalles específicos de cada tipo de vehículo. Esto facilita la creación de nuevos tipos de vehículos en el futuro y promueve la reutilización de código.


[[Interfaces]] 