.
Técnica utilizada en el ámbito de las pruebas de software, especialmente en pruebas unitarias, para simular el comportamiento de objetos y controlar sus interacciones con el código que se está probando.

**Definición**: El stubbing es el proceso de reemplazar métodos en un objeto con implementaciones alternativas (stub) que devuelven valores predefinidos o controlados, sin ejecutar la lógica real del método.

**Características**:

- **Control de Respuestas**: Los stubs permiten dar respuestas específicas a llamadas de métodos, lo que facilita el manejo de situaciones en las que el componente externo (como bases de datos, servicios web, etc.) no está disponible o no es relevante para la prueba.
- **Simplificación de Escenarios**: Ayudan a simplificar las pruebas al eliminar la necesidad de configurar toda la lógica de ejecución del método real, permitiendo enfocarse en el comportamiento del código en prueba.
- **No Verificación de Interacciones**: Los stubs no verifican si un método ha sido llamado o cuántas veces; su finalidad es simplemente proporcionar una respuesta.

**Ejemplo**: Si tienes un método que obtiene datos de una base de datos, puedes crear un stub para ese método que devuelve un conjunto de datos predefinido, evitando la necesidad de realizar una consulta real mientras pruebas la lógica que usa esos datos.