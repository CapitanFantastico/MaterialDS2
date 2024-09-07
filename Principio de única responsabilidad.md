.
Ejemplo en Python que ilustra el principio de Única Responsabilidad (Single Responsibility Principle, SRP) de los principios SOLID. 

Este principio establece que una clase debe tener una sola razón para cambiar, es decir, cada clase debe tener una única responsabilidad o tarea.

En este ejemplo, crearemos una clase llamada `Empleado` que inicialmente tiene la responsabilidad de almacenar la información de un empleado y calcular su salario. Sin embargo, luego aplicaremos el principio de Única Responsabilidad dividiendo esta clase en dos clases separadas para cumplir con el principio.

```python
class Empleado:
    def __init__(self, nombre, salario_base, horas_trabajadas):
        self.nombre = nombre
        self.salario_base = salario_base
        self.horas_trabajadas = horas_trabajadas

    def calcular_salario(self):
        return self.salario_base + (self.horas_trabajadas * 10)  # Suponiendo un salario por hora de 10

# Aplicando el principio de Única Responsabilidad
class Empleado:
    def __init__(self, nombre):
        self.nombre = nombre

class CalculadoraSalario:
    def __init__(self, empleado, salario_base, horas_trabajadas):
        self.empleado = empleado
        self.salario_base = salario_base
        self.horas_trabajadas = horas_trabajadas

    def calcular_salario(self):
        return self.salario_base + (self.horas_trabajadas * 10)  # Suponiendo un salario por hora de 10

# Uso de las clases
empleado1 = Empleado("Juan")
calculadora = CalculadoraSalario(empleado1, 1000, 40)
salario = calculadora.calcular_salario()
print(f"El salario de {empleado1.nombre} es: {salario}")
```

En este ejemplo, inicialmente teníamos una clase `Empleado` que almacenaba la información del empleado y calculaba su salario. Sin embargo, al aplicar el principio de Única Responsabilidad, dividimos esta funcionalidad en dos clases separadas: `Empleado` que se encarga únicamente de almacenar la información del empleado, y `CalculadoraSalario` que se encarga de calcular el salario del empleado.

Al dividir las responsabilidades de esta manera, cada clase tiene una única responsabilidad y es más fácil de mantener, extender y probar. Esto cumple con el principio de Única Responsabilidad de SOLID.
