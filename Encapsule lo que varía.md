.
Este principio se apoya en:
- [[Principio de única responsabilidad]] 
- [[Principio abierto cerrado]] 

El principio "Encapsulate What Varies" se refiere a encapsular las partes del código que son propensas a cambios en clases separadas o módulos, de modo que los cambios en esas partes no afecten al resto del sistema. Aquí te dejo un ejemplo en Python que ilustra este principio utilizando un sistema de envío de paquetes con diferentes tipos de envío (por tierra, por aire) y diferentes empresas de envío:

```python
class Shipping:
    def __init__(self, package, company):
        self.package = package
        self.company = company

    def calculate_cost(self):
        # Lógica para calcular el costo de envío
        pass

class Package:
    def __init__(self, weight, destination):
        self.weight = weight
        self.destination = destination

class GroundShippingCompany:
    def __init__(self):
        self.rate_per_kg = 1.5

class AirShippingCompany:
    def __init__(self):
        self.rate_per_kg = 3.0

# Crear un paquete y seleccionar una empresa de envío
xpackage = Package(5, "New York")
ground_shipping = GroundShippingCompany()
air_shipping = AirShippingCompany()

# Calcular el costo de envío por tierra
ground_shipping_package = Shipping(xpackage, ground_shipping)
ground_shipping_cost = ground_shipping_package.calculate_cost()

# Calcular el costo de envío por aire
air_shipping_package = Shipping(xpackage, air_shipping)
air_shipping_cost = air_shipping_package.calculate_cost()
```

En este ejemplo, encapsulamos las partes que varían en clases separadas: `Package` representa un paquete con su peso y destino, `GroundShippingCompany` y `AirShippingCompany` representan empresas de envío con tarifas diferentes por kilogramo. La clase `Shipping` se encarga de calcular el costo de envío para un paquete dado y una empresa de envío específica.

Al encapsular lo que varía en clases separadas, podemos cambiar fácilmente el tipo de envío (por tierra, por aire) o la empresa de envío sin afectar al resto del sistema. Esto hace que el código sea más flexible y fácil de mantener en caso de futuros cambios en los requisitos del sistema.
