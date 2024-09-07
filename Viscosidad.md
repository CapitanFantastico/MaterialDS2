.
**Definición:** La viscosidad se refiere a la dificultad de realizar cambios correctos en el código debido a que la solución más fácil y rápida suele ser incorrecta o sucia, en lugar de la solución adecuada.

**Ejemplo:**
Supongamos que en un sistema de reservas, la forma correcta de agregar una nueva funcionalidad es seguir una estructura bien definida de capas y patrones de diseño. Sin embargo, debido a la complejidad del sistema o la falta de documentación, los desarrolladores a menudo optan por soluciones rápidas y desordenadas:

```python
class Reserva:
    def crear_reserva(self, cliente, fecha):
        # Código para crear una reserva
        # La forma correcta sería usar una capa de servicios, pero...
        # Se agregan funcionalidades aquí directamente por simplicidad
        if cliente.es_vip:
            self.dar_descuento(cliente)
        self.reservas.append({'cliente': cliente, 'fecha': fecha})
```

En este caso, la "viscosidad del diseño" impulsa a los desarrolladores a modificar el código de manera rápida, insertando lógica directamente en lugares inapropiados, en lugar de seguir la arquitectura establecida.

**Consecuencia:** Este diseño es viscoso porque dificulta la realización de cambios limpios y adecuados, fomentando soluciones rápidas pero incorrectas.

