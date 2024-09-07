.
- [[Bajo acoplamiento, alta cohesión]] 

El principio de diseño de software Low Coupling de GRASP se refiere a la idea de reducir la dependencia entre las clases y componentes de un sistema, de manera que los cambios en una clase no afecten directamente a otras clases. Esto se logra mediante la separación de responsabilidades y la minimización de las interacciones directas entre componentes.

Aquí tienes un ejemplo sencillo en Python que ilustra el principio de diseño de software Low Coupling de GRASP:

```python
class Calculadora:
    def sumar(self, a, b):
        return a + b

class Impresora:
    def imprimir_resultado(self, resultado):
        print("El resultado es:", resultado)

# Crear una instancia de la Calculadora y la Impresora
calculadora = Calculadora()
impresora = Impresora()

# Realizar una operación de suma y imprimir el resultado
resultado = calculadora.sumar(5, 3)
impresora.imprimir_resultado(resultado)
```

En este ejemplo, tenemos dos clases, `Calculadora` e `Impresora`, que tienen responsabilidades separadas: la `Calculadora` se encarga de realizar operaciones matemáticas, en este caso una suma, y la `Impresora` se encarga de imprimir resultados en la consola.

Las clases están diseñadas de manera que no tienen una dependencia directa entre sí. La `Calculadora` no sabe cómo se va a imprimir el resultado y la `Impresora` no sabe cómo se realizan las operaciones matemáticas. Esto reduce el acoplamiento entre las clases y facilita la modificación de una clase sin afectar a la otra.

Al seguir el principio de diseño de software Low Coupling de GRASP, se favorece la modularidad y la flexibilidad del sistema, ya que las clases están desacopladas y pueden evolucionar de forma independiente. Además, se facilita la reutilización de código y la mantenibilidad del sistema, ya que los cambios en una clase tienen un impacto limitado en otras clases.
 
- [[Bajo acoplamiento, alta cohesión]] 