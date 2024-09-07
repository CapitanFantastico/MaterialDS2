.
**Clean Code** es un concepto en el desarrollo de software que se refiere a escribir código que sea **legible, mantenible y eficiente**. El término se popularizó gracias al libro *"Clean Code: A Handbook of Agile Software Craftsmanship"* escrito por [[Robert C. Martin]] (conocido como "Uncle Bob"). Este libro y sus principios han tenido una gran influencia en la forma en que los desarrolladores abordan la escritura de código.

### ¿En qué consiste Clean Code?

El concepto de Clean Code se basa en la idea de que el código debería ser fácil de entender para otros desarrolladores (o para ti mismo en el futuro), fácil de modificar y extender, y eficiente en su propósito. Esto implica seguir una serie de principios y buenas prácticas que guían a los desarrolladores a escribir código de alta calidad.

### Principios y características de Clean Code:

1. **Legibilidad**:
   - El código debe ser claro y fácil de leer. Esto implica usar nombres de variables, funciones y clases que sean descriptivos y reflejen su propósito.
   - Comentarios innecesarios deben evitarse si el código se explica por sí mismo. Si un comentario es necesario, debe ser claro y preciso.

   ```java
   // Ejemplo de código legible
   double calculateAnnualSalary(Employee employee) {
       return employee.getMonthlySalary() * 12;
   }
   ```

2. **Simplicidad**:
   - El código debe ser tan simple como sea posible, sin dejar de cumplir con los requisitos. La simplicidad evita errores y facilita el mantenimiento.

   ```java
   // Ejemplo de código simple
   boolean isAdult(int age) {
       return age >= 18;
   }
   ```

3. **Funciones pequeñas y enfocadas**:
   - Las funciones deben ser pequeñas y realizar solo una tarea. Esto mejora la legibilidad y la reutilización del código.

   ```java
   // Ejemplo de función enfocada
   void saveUser(User user) {
       validateUser(user);
       database.save(user);
   }
   ```

4. **Nombres significativos**:
   - Los nombres de las variables, funciones, y clases deben ser expresivos y reflejar claramente su propósito o contenido. Evita abreviaturas innecesarias y nombres genéricos.

   ```java
   // Ejemplo de nombres significativos
   String userFirstName;
   String userLastName;
   ```
	Nota: **FLDSMDFR** "Flint Loco Diatónica Super Mutante Duplicadora de Comida".


5. **Evitar duplicación**:
   - El código duplicado es un enemigo de Clean Code. Si un fragmento de código aparece en más de un lugar, debería abstraerse en una función o clase para evitar duplicación y facilitar el mantenimiento.

   ```java
   // Ejemplo de evitar duplicación
   double calculateDiscount(double price, double discountRate) {
       return price * discountRate;
   }
   ```

6. **Responsabilidad única**:
   - Cada clase y función debe tener una única responsabilidad o propósito, conocido como [[Principio de única responsabilidad]] (Single Responsibility Principle, SRP). Esto facilita la comprensión y la modificación del código.

   ```java
   // Ejemplo de responsabilidad única
   class InvoicePrinter {
       void printInvoice(Invoice invoice) {
           // logic to print invoice
       }
   }

   class InvoiceCalculator {
       double calculateTotal(Invoice invoice) {
           // logic to calculate total
       }
   }
   ```

7. **Pruebas exhaustivas**:
   - Clean Code también incluye la creación de pruebas unitarias y de integración para garantizar que el código funciona como se espera y para facilitar futuras modificaciones.

8. **Manejo adecuado de errores**:
   - Los errores y excepciones deben manejarse de manera que el flujo de la aplicación sea claro y controlado, sin causar confusión o resultados inesperados.

   ```java
   // Ejemplo de manejo adecuado de errores
   try {
       user.save();
   } catch (DatabaseException e) {
       // Handle exception gracefully
       logError(e);
   }
   ```

9. **Documentación cuando es necesaria**:
   - Aunque el código limpio debe ser en su mayoría autodescriptivo, la documentación es útil para explicar decisiones complejas de diseño o para dar una visión general del sistema.

### Beneficios de escribir Clean Code:

- **Mantenibilidad**: El código limpio es más fácil de entender y modificar, lo que facilita su mantenimiento a lo largo del tiempo.
- **Colaboración**: En un equipo, el código limpio permite a otros desarrolladores comprender rápidamente la lógica del programa y contribuir sin confusiones.
- **Menos errores**: Un código claro y bien estructurado reduce la probabilidad de errores y facilita la identificación y corrección de problemas.
- **Eficiencia**: Facilita la reutilización del código y evita el tiempo perdido en tratar de entender código complicado o mal escrito.

### Ejemplo de código antes y después de aplicar Clean Code:

**Antes**:
```java
void calc(Employee e) {
    double m = e.getM() * 12;
    double b = m * 0.8;
    // other logic
}
```

**Después** (aplicando Clean Code):
```java
void calculateBonus(Employee employee) {
    double annualSalary = employee.getMonthlySalary() * 12;
    double bonus = annualSalary * 0.8;
    // other logic
}
```

Ver también
- https://www.ionos.com/es-us/digitalguide/paginas-web/desarrollo-web/clean-code-que-es-el-codigo-limpio/