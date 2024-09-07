.
Este principio establece que una clase no debe ser forzada a implementar interfaces que no utiliza. En lugar de tener interfaces monolíticas, es preferible tener interfaces específicas para cada cliente.

En este ejemplo, crearemos una interfaz `Trabajador` que inicialmente tiene métodos relacionados con el trabajo de un empleado. Luego, aplicaremos el principio de Segregación de Interfaces dividiendo esta interfaz en interfaces más específicas para cumplir con el principio.

```python
# Interfaz original
class Trabajador:
    def trabajar(self):
        pass

    def tomar_descanso(self):
        pass

# Aplicando el principio de Segregación de Interfaces
class Trabajador:
    def trabajar(self):
        pass

class Descansador:
    def tomar_descanso(self):
        pass

# Clase que implementa las interfaces segregadas
class Empleado(Trabajador, Descansador):
    def trabajar(self):
        print("Trabajando...")

    def tomar_descanso(self):
        print("Tomando un descanso...")

# Uso de la clase Empleado
empleado1 = Empleado()
empleado1.trabajar()
empleado1.tomar_descanso()
```

En este ejemplo, inicialmente teníamos una interfaz `Trabajador` que contenía métodos relacionados con el trabajo y el descanso de un empleado. Sin embargo, al aplicar el principio de Segregación de Interfaces, dividimos esta interfaz en dos interfaces más específicas: `Trabajador` que contiene el método `trabajar` y `Descansador` que contiene el método `tomar_descanso`.

Luego creamos la clase `Empleado` que implementa las interfaces segregadas `Trabajador` y `Descansador`. De esta manera, la clase `Empleado` solo implementa los métodos que necesita y no se ve obligada a implementar métodos que no utiliza, cumpliendo así con el principio de Segregación de Interfaces de SOLID.

---

```python
# Interfaz original
class Trabajador:
    def administra(self):
        pass

    def compra(self):
        pass

    def empaca(self):
        pass

    def vende(self):
        pass

    def contrataTrabajadores(self):
        pass

# Aplicando el principio de Segregación de Interfaces
class Trabajador:
    def esContratado(self):
        pass

    def esLiquidado(self):
        pass

    def saleAVacaciones(self):
        pass

    def entraDeVacaciones(self):
        pass

	def iniciaLabores(self):
        pass

	def terminaLabores(self):
        pass
        
class Administrador(Trabajador):
    def administra(self):
        pass

class Vendedor(Trabajador):
    def vende(self):
        pass

class Comprador(Trabajador):
    def compra(self):
        pass

class Empacador(Trabajador):
    def empaca(self):
        pass

class Contratador(Trabajador):
    def contrata(self):
        pass

# Clase que implementa las interfaces segregadas
class EmpleadoAdministrador(Administrador):
    def trabajar(self):
        print("Trabajando...")

    def tomar_descanso(self):
        print("Tomando un descanso...")

# Uso de la clase Empleado
empleado1 = Empacador()
empleado2 = Administrador()
empleado1.empaca()
empleado2.administra()
```
