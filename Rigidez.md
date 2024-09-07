.
**Definición:** La rigidez se refiere a la dificultad de hacer cambios en el código debido a que una modificación en un lugar del sistema afecta muchas otras partes del mismo.

**Ejemplo:**
Imagina que tienes un sistema de gestión de pedidos en el que cada tipo de pedido (por ejemplo, `PedidoNacional`, `PedidoInternacional`) tiene una clase específica, y estas clases tienen una implementación similar, pero con ligeras diferencias.

```python
class PedidoNacional:
    def calcular_precio_total(self, precio_base):
        # Código que calcula el precio total para pedidos nacionales
        return precio_base + self.calcular_impuestos(precio_base)

    def calcular_impuestos(self, precio_base):
        return precio_base * 0.15

class PedidoInternacional:
    def calcular_precio_total(self, precio_base):
        # Código que calcula el precio total para pedidos internacionales
        return precio_base + self.calcular_impuestos(precio_base)

    def calcular_impuestos(self, precio_base):
        return precio_base * 0.25
```

En este sistema, si necesitas cambiar la forma en que se calculan los impuestos, tendrás que modificar múltiples clases. Si hay muchos tipos de pedidos, este cambio se vuelve costoso y propenso a errores.

**Consecuencia:** Este diseño es rígido porque una pequeña modificación afecta muchas partes del sistema, haciendo que el código sea difícil de cambiar y mantener.
