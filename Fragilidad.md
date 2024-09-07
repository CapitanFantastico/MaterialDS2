.
**Definición:** La fragilidad se refiere a la tendencia del software a romperse o generar errores en áreas no relacionadas cuando se realiza un cambio en el código.

**Ejemplo:**
Supongamos que en un sistema de gestión de inventarios, decides modificar la lógica de cálculo del inventario disponible:

```python
class Inventario:
    def calcular_disponible(self, producto):
        disponible = producto.stock_inicial - producto.ventas
        if producto.tiene_descuento:
            disponible -= producto.unidades_descontadas
        return disponible
```

Si cambias la forma en que se calculan las unidades descontadas o decides agregar un nuevo tipo de descuento, podrías romper accidentalmente otras partes del sistema que dependen de la forma en que se calcula `calcular_disponible`.

**Consecuencia:** Este diseño es frágil porque un cambio en una parte del código puede tener efectos negativos en otras áreas, incluso en aquellas que no parecían estar relacionadas.