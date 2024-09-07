.
- https://qastack.mx/programming/3085285/difference-between-cohesion-and-coupling

---

Un programa con alto acoplamiento y baja cohesión es aquel en el cual los módulos están fuertemente interconectados y cada módulo realiza una variedad de tareas no necesariamente relacionadas entre sí. Este tipo de diseño es generalmente desaconsejado porque dificulta la comprensión, mantenimiento y escalabilidad del código.

![[Pasted image 20240902144930.png]]

![[Pasted image 20240902145214.png]]

![[Pasted image 20240902145225.png]]

![[Pasted image 20240902145330.png]]

![[Pasted image 20240902145444.png]]

Ejemplo en Python de un programa que exhibe alto acoplamiento y baja cohesión. Este programa intenta manejar información de empleados y realizar operaciones de cálculo, pero todo está mezclado en una sola clase, lo que hace que sea difícil de mantener y modificar.

Un ejemplo de la implementación de este principio es el
- [[Patrón de diseño Observer]] 

### Ejemplo de Alto Acoplamiento y Baja Cohesión en Python

```python
class EmployeeManager:
    def __init__(self):
        self.employees = []  # Lista de empleados
        self.total_sales = 0

    def add_employee(self, name, department, sales):
        self.employees.append((name, department, sales))
        self.total_sales += sales

    def calculate_bonus(self, sales):
        # Cálculo de bonificación basado en ventas
        if sales > 10000:
            return sales * 0.1
        else:
            return sales * 0.05

    def print_employee_details(self):
        for emp in self.employees:
            print(f"Name: {emp[0]}, Department: {emp[1]}, Sales: {emp[2]}")

    def total_bonus(self):
        total = 0
        for emp in self.employees:
            total += self.calculate_bonus(emp[2])
        return total

# Uso de la clase
manager = EmployeeManager()
manager.add_employee("Alice", "Sales", 12000)
manager.add_employee("Bob", "IT", 9000)
manager.print_employee_details()
print("Total Bonus: ", manager.total_bonus())
```

### Problemas con este Diseño

1. **Alto Acoplamiento**: 
   - La clase `EmployeeManager` maneja detalles de empleados, realiza cálculos de ventas y bonificaciones. Estas funciones están altamente acopladas, lo que significa que un cambio en la forma de manejar los detalles de los empleados podría afectar las funciones de cálculo de bonificaciones y viceversa.

2. **Baja Cohesión**:
   - La clase realiza demasiadas tareas que no están estrechamente relacionadas entre sí. La gestión de empleados y los cálculos de bonificaciones podrían ser responsabilidades separadas en módulos o clases distintas.




# Alta cohesión, bajo acoplamiento

Para mejorar el código proporcionado hacia un diseño de alta cohesión y bajo acoplamiento, podemos seguir algunos principios de diseño orientado a objetos. La idea es dividir el programa en partes más pequeñas, cada una con una responsabilidad claramente definida. A continuación, describo cómo podemos reestructurar el código para alcanzar estos objetivos.

### Solución con Alta Cohesión y Bajo Acoplamiento

**1. Definir una clase `Employee` para encapsular los detalles de los empleados:**

Esta clase se encargará únicamente de los atributos relacionados con los empleados, como nombre, departamento y ventas.

```python
class Employee:
    def __init__(self, name, department, sales):
        self.name = name
        self.department = department
        self.sales = sales
```

**2. Crear una clase `SalesManager` para manejar operaciones relacionadas con las ventas:**

Esta clase se enfocará en las operaciones que involucran las ventas y cálculos de bonificaciones, trabajando con objetos `Employee`.

```python
class SalesManager:
    def __init__(self):
        self.employees = []

    def add_employee(self, employee):
        self.employees.append(employee)

    def calculate_bonus(self, employee):
        if employee.sales > 10000:
            return employee.sales * 0.1
        return employee.sales * 0.05

    def print_employee_details(self):
        for emp in self.employees:
            print(f"Name: {emp.name}, Department: {emp.department}, Sales: {emp.sales}")

    def total_bonus(self):
        return sum(self.calculate_bonus(emp) for emp in self.employees)
```

**Uso de las clases:**

La siguiente sección del código muestra cómo se pueden utilizar las clases `Employee` y `SalesManager` para gestionar empleados y calcular bonificaciones, respectivamente.

```python
# Creación de instancias de empleados
alice = Employee("Alice", "Sales", 12000)
bob = Employee("Bob", "IT", 9000)

# Creación y uso de SalesManager
manager = SalesManager()
manager.add_employee(alice)
manager.add_employee(bob)
manager.print_employee_details()
print("Total Bonus: ", manager.total_bonus())
```

### Beneficios de este diseño:

- **Alta Cohesión:** Cada clase tiene una responsabilidad clara y bien definida. `Employee` solo gestiona datos de empleados y `SalesManager` se encarga de las operaciones relacionadas con las ventas y bonificaciones.
  
- **Bajo Acoplamiento:** Las clases `Employee` y `SalesManager` interactúan entre sí pero son independientes en términos de funcionalidad. Cambios en una clase no requieren cambios en la otra, siempre y cuando se mantenga la interfaz entre ellas.

Este enfoque facilita el mantenimiento y la escalabilidad del código, al mismo tiempo que mejora la legibilidad y la gestión de cambios futuros.
