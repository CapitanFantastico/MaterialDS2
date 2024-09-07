.
El principio **DRY** (Don't Repeat Yourself), traducido como "No te repitas", es un concepto fundamental en el desarrollo de software que tiene como objetivo reducir la duplicación de código y de conocimiento en un sistema. Fue introducido en el libro *The Pragmatic Programmer* de Andrew Hunt y David Thomas.

### ¿En qué consiste el principio DRY?

El principio DRY establece que **cualquier pieza de conocimiento o lógica en un sistema de software debe tener una única representación no redundante**. Esto significa que, en lugar de duplicar código o información en múltiples lugares, se debe consolidar en un único lugar. Si surge la necesidad de realizar cambios, solo se necesita modificar un único lugar, lo que minimiza errores y facilita el mantenimiento.

### Beneficios del principio DRY:

1. **Mantenibilidad**:
   - Reducir la duplicación de código hace que el sistema sea más fácil de mantener. Un cambio en la lógica central se refleja en todos los lugares que utilizan esa lógica, evitando inconsistencias.

2. **Legibilidad**:
   - Un código que sigue el principio DRY es más fácil de leer y entender, ya que no está cargado de repeticiones innecesarias.

3. **Reutilización**:
   - Al consolidar la funcionalidad común en un solo lugar, es más fácil reutilizar el código en diferentes partes del sistema.

4. **Reducción de errores**:
   - Cuando el código se repite, es fácil introducir errores si un cambio se realiza en un lugar pero se olvida en otro. DRY minimiza este riesgo.

### Ejemplos de DRY en la práctica:

1. **Funciones o métodos**:
   - En lugar de repetir el mismo fragmento de código en varios lugares, se puede encapsular en una función o método que se invoca desde diferentes partes del programa.

   ```python
   # Violando DRY
   total_price = item_price * quantity
   discounted_price = item_price * quantity * discount

   # Aplicando DRY
   def calculate_total(price, quantity):
       return price * quantity

   total_price = calculate_total(item_price, quantity)
   discounted_price = calculate_total(item_price, quantity) * discount
   ```

2. **Herencia y composición**:
   - En la programación orientada a objetos, las clases base o las composiciones pueden ser utilizadas para evitar duplicación de código en las subclases o clases relacionadas.

   ```java
   class Employee {
       String name;
       double salary;

       public void work() {
           // logic for work
       }
   }

   class Manager extends Employee {
       // Manager specific logic
   }

   class Developer extends Employee {
       // Developer specific logic
   }
   ```

3. **Configuraciones centralizadas**:
   - Configuraciones como rutas, URLs, o parámetros de conexión a bases de datos no deberían estar duplicadas en varias partes del código. En su lugar, deben almacenarse en un archivo de configuración centralizado.

   ```yaml
   # config.yml
   database:
     host: localhost
     port: 5432
   ```

### Excepciones al principio DRY:

Si bien el principio DRY es ampliamente beneficioso, hay momentos en que se puede justificar alguna duplicación:
- **Claridad y simplicidad**: En casos donde la abstracción del código puede hacer que sea menos claro o más difícil de entender, se podría considerar aceptar cierta repetición para mantener la claridad.
- **Optimización temprana**: A veces es mejor evitar la optimización prematura. Consolidar el código demasiado temprano podría llevar a abstracciones incorrectas o complicaciones innecesarias.

En resumen, el principio DRY fomenta la eficiencia y la coherencia en el desarrollo de software al evitar la repetición de código y de conocimiento, lo que facilita la mantenibilidad, la legibilidad y la reutilización del software. Sin embargo, como todos los principios, debe aplicarse con criterio, considerando siempre el contexto y las necesidades específicas del proyecto.