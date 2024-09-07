.
El concepto de "Diseño por contrato" fue introducido por [[Bertrand Meyer]], no por [[Barbara Liskov]], aunque se relaciona con principios similares como el Principio de Sustitución de Liskov (LSP) que sí fue formulado por ella. El Diseño por contrato es un enfoque en la programación orientada a objetos que trata las especificaciones de una interfaz, como un contrato legal entre un proveedor (por ejemplo, una clase o un método) y un consumidor (el código que utiliza esa clase o método). Aquí están los elementos clave:

1. **Precondiciones:** Son las condiciones que deben ser verdaderas antes de que se ejecute un método. Estas definen lo que el método espera del código que llama al método.
   
2. **Postcondiciones:** Son las condiciones que deben ser verdaderas después de que se ha ejecutado el método. Estas definen lo que el método promete realizar antes de finalizar.

3. **Invariantes de clase:** Son condiciones que deben ser siempre verdaderas para todas las instancias de una clase. Estas condiciones deben mantenerse verdaderas antes y después de cualquier operación en la clase, manteniendo la consistencia del estado de la instancia a lo largo de su vida útil.

### Ejemplo Sencillo

Supongamos que tenemos una clase de cuenta bancaria donde puedes retirar dinero:

```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance
        assert self.balance >= 0, "El balance inicial debe ser no negativo."

    def withdraw(self, amount):
        assert amount > 0, "El monto a retirar debe ser positivo."
        assert self.balance >= amount, "Fondos insuficientes para el retiro."

        self.balance -= amount
        
        assert self.balance >= 0, "El balance no debe ser negativo después del retiro."
        return self.balance
```

En este ejemplo:
- **Invariantes de clase:** El balance nunca debe ser negativo.
- **Precondiciones en `withdraw`:** El monto a retirar debe ser positivo y suficiente saldo en la cuenta.
- **Postcondiciones en `withdraw`:** El balance actualizado no debe ser negativo.

Este método asegura que el estado del objeto `BankAccount` es siempre válido según las reglas definidas, y tanto el llamador como el método se adhieren a sus respectivas responsabilidades, como si fuera un contrato.