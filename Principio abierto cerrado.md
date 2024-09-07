.
El Principio Open/Closed es uno de los principios SOLID de programación orientada a objetos. Este principio establece que las entidades de software (clases, módulos, funciones, etc.) deben estar abiertas para la extensión, pero cerradas para la modificación. Esto significa que deberías poder cambiar el comportamiento de una entidad extendiéndola, sin modificar el código fuente original.

Aquí te presento un ejemplo sencillo en Python que ilustra este principio:

### Escenario
Imagina que estás desarrollando un sistema de facturación y necesitas implementar diferentes tipos de facturas. La estructura básica de una factura es la misma, pero el cálculo del total puede variar dependiendo de si la factura incluye impuestos, descuentos, u otros factores.

### Implementación Básica
Primero, creamos una clase base llamada `Invoice` que otras clases pueden extender para adaptarse a diferentes tipos de facturación.

```python
class Invoice:
    def __init__(self, subtotal):
        self.subtotal = subtotal

    def total(self):
        return self.subtotal  # Default behavior

# Extending the base class to handle different scenarios
class TaxInvoice(Invoice):
    def __init__(self, subtotal, tax_rate):
        super().__init__(subtotal)
        self.tax_rate = tax_rate

    def total(self):
        tax_amount = self.subtotal * self.tax_rate
        return self.subtotal + tax_amount

class DiscountInvoice(Invoice):
    def __init__(self, subtotal, discount):
        super().__init__(subtotal)
        self.discount = discount

    def total(self):
        return self.subtotal - self.discount
```

### Uso de las Clases
Podemos crear diferentes tipos de facturas sin modificar la clase `Invoice` original. La clase `Invoice` está "cerrada" para modificación (no necesitas cambiarla cuando se introducen nuevos tipos de facturas), pero "abierta" para extensión (puedes crear nuevos tipos de facturas heredando de ella).

```python
# Creando diferentes tipos de facturas
normal_invoice = Invoice(100)
tax_invoice = TaxInvoice(100, 0.15)  # 15% de impuesto
discount_invoice = DiscountInvoice(100, 10)  # $10 de descuento

# Imprimiendo los totales calculados
print(f"Normal Invoice Total: ${normal_invoice.total()}")
print(f"Tax Invoice Total: ${tax_invoice.total()}")
print(f"Discount Invoice Total: ${discount_invoice.total()}")
```

### Salida
```
Normal Invoice Total: $100
Tax Invoice Total: $115.0
Discount Invoice Total: $90
```

Este enfoque permite a los desarrolladores añadir nuevas funcionalidades y manejar nuevos casos sin alterar el código existente que ya ha sido probado y validado, siguiendo el principio de Open/Closed.