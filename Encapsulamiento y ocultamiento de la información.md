.
El término **"encapsulamiento"** y el principio de **"encapsulamiento y ocultamiento de la información"** están estrechamente relacionados, pero no son exactamente lo mismo. Vamos a diferenciarlos:

### Encapsulación:
- **Definición**: En programación orientada a objetos, **encapsulación** se refiere al proceso de agrupar datos (atributos) y el código que opera sobre esos datos (métodos) dentro de una única unidad, llamada **clase**. Este concepto también incluye la idea de que los detalles internos de cómo funcionan esos métodos y atributos están ocultos al resto del programa.

- **Objetivo**: La encapsulación tiene como objetivo proteger los datos internos de un objeto y asegurar que solo puedan ser manipulados de maneras controladas, típicamente a través de métodos públicos que la clase proporciona.

- **Ejemplo**: En una clase `CuentaBancaria`, los atributos como `saldo` podrían ser privados, mientras que los métodos como `depositar` y `retirar` serían públicos. Esto asegura que el `saldo` solo pueda ser modificado a través de estos métodos, evitando modificaciones arbitrarias y no controladas.

### Ocultamiento de la información:
- **Definición**: El **ocultamiento de la información** es un principio más amplio que se refiere a la práctica de restringir el acceso a ciertos detalles internos de un módulo o clase para que otras partes del sistema no puedan depender de ellos. Esto significa que solo se expone lo necesario para interactuar con el módulo, mientras que los detalles de implementación se mantienen ocultos.

- **Objetivo**: El objetivo del ocultamiento de la información es minimizar la interdependencia entre diferentes partes de un sistema (bajo acoplamiento), facilitando cambios y mejoras en el código sin afectar otras partes del sistema. También contribuye a mejorar la seguridad y la mantenibilidad del software.

- **Ejemplo**: Siguiendo el ejemplo anterior, el `saldo` de la `CuentaBancaria` está oculto y no puede ser accedido directamente desde fuera de la clase. Otros objetos solo pueden interactuar con él a través de los métodos `depositar` y `retirar`. Esto asegura que el código que usa `CuentaBancaria` no dependa de cómo se almacena o calcula el saldo internamente.

### Relación entre ambos:
- **Encapsulación** es una técnica que se utiliza para lograr el **ocultamiento de la información**. Es decir, encapsular datos y métodos dentro de una clase es una forma de implementar el principio de ocultamiento de la información, ya que permite proteger los detalles internos de una clase y controlar cómo otras partes del programa pueden interactuar con ella.

- Mientras que **encapsulación** se refiere más a la mecánica específica de agrupar y proteger datos dentro de una clase, el **ocultamiento de la información** se refiere a la idea más general de esconder detalles innecesarios para reducir la complejidad y mejorar la independencia de los diferentes componentes del sistema.

En resumen, la **encapsulación** es una herramienta que ayuda a implementar el **ocultamiento de la información** dentro de la programación orientada a objetos. Ambos conceptos trabajan juntos para mejorar la modularidad, seguridad, y mantenibilidad del software.

---

El principio de Encapsulamiento y ocultamiento de la información se refiere a la idea de que los detalles internos de un objeto deben estar ocultos y solo accesibles a través de métodos públicos. Esto ayuda a garantizar la integridad y consistencia de los datos, así como a proteger la información sensible de ser modificada de manera incorrecta.

Aquí tienes un ejemplo sencillo en Python que ilustra el principio de Encapsulamiento y ocultamiento de la información:

```python
class Persona:
    def __init__(self, nombre, edad):
        self.__nombre = nombre  # Atributo privado
        self.__edad = edad  # Atributo privado

    def obtener_nombre(self):
        return self.__nombre

    def obtener_edad(self):
        return self.__edad

    def actualizar_edad(self, nueva_edad):
        if nueva_edad > 0:
            self.__edad = nueva_edad
        else:
            print("La edad debe ser un número positivo.")

# Programa principal
persona = Persona("Juan", 30)

print("Nombre:", persona.obtener_nombre())
print("Edad:", persona.obtener_edad())

persona.actualizar_edad(-5)  # Intentamos actualizar la edad con un valor negativo

print("Nueva Edad:", persona.obtener_edad())  # La edad no se actualiza si es un valor negativo
```

En este ejemplo, la clase `Persona` tiene dos atributos privados `__nombre` y `__edad`, que están ocultos del exterior de la clase. Para acceder a estos atributos, se han definido métodos públicos `obtener_nombre()` y `obtener_edad()`, que devuelven los valores de los atributos correspondientes.

Además, se ha definido el método público `actualizar_edad()` que permite actualizar la edad de la persona, pero solo si el nuevo valor es positivo. Esto garantiza que la edad se actualice de manera segura y se mantiene la coherencia de los datos.

Al utilizar el principio de Encapsulamiento y ocultamiento de la información, se protege la integridad de los datos al restringir el acceso directo a los atributos de la clase y al proporcionar métodos específicos para interactuar con ellos. Esto ayuda a prevenir errores y a mantener la consistencia de los datos en el programa.
