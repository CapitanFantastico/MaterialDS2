.
El principio de diseño de software Expert de GRASP se refiere a asignar la responsabilidad de una tarea a la clase que posee la información necesaria para realizarla de manera experta. Esto ayuda a promover un diseño cohesivo y a evitar la dispersión de la lógica de negocio en diferentes partes del sistema.

Aquí tienes un ejemplo sencillo en Python que ilustra el principio de diseño de software Expert de GRASP:

```python
class Producto:
    def __init__(self, nombre, precio):
        self.nombre = nombre
        self.precio = precio

class CarritoDeCompras:
    def __init__(self):
        self.productos = []

    def agregar_producto(self, producto):
        self.productos.append(producto)

    def calcular_total(self):
        total = 0
        for producto in self.productos:
            total += producto.precio
        return total

# Crear instancias de productos
producto1 = Producto("Camiseta", 20)
producto2 = Producto("Pantalón", 30)

# Crear una instancia de CarritoDeCompras
carrito = CarritoDeCompras()

# Agregar productos al carrito
carrito.agregar_producto(producto1)
carrito.agregar_producto(producto2)

# Calcular el total de la compra
total_compra = carrito.calcular_total()
print("Total de la compra:", total_compra)
```

En este ejemplo, tenemos dos clases: `Producto` y `CarritoDeCompras`. La clase `Producto` representa un producto con un nombre y un precio. La clase `CarritoDeCompras` se encarga de gestionar los productos en un carrito y calcular el total de la compra.

El principio de diseño Expert de GRASP se aplica al método `calcular_total()` de la clase `CarritoDeCompras`. Esta clase es la experta en tener la información necesaria para calcular el total de la compra, ya que tiene acceso a la lista de productos y sus precios. De esta manera, se asigna la responsabilidad de cálculo del total al objeto que tiene la información relevante para realizar esta tarea de manera experta.

Al seguir el principio de diseño de software Expert de GRASP, se promueve un diseño cohesivo y fácil de mantener, ya que la lógica relacionada con el cálculo del total de la compra se encuentra en un solo lugar, en la clase `CarritoDeCompras`. Esto facilita la [[extensibilidad]] del sistema y evita la dispersión de la lógica de negocio en diferentes partes del código.
