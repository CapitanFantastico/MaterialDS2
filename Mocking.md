.
Cuando escriba pruebas es sólo cuestión de tiempo antes de que necesite crear una versión "falsa" de un servicio interno — o externo. Esto se conoce comúnmente como simulación.

- Ver https://webdriver.io/es/docs/component-testing/mocking/

Técnica utilizada en el ámbito de las pruebas de software, especialmente en pruebas unitarias, para simular el comportamiento de objetos y controlar sus interacciones con el código que se está probando.

**Definición**: El mocking es una técnica que crea objetos simulados (mocks) que no solo imitan el comportamiento de un objeto real, sino que también permiten verificar las interacciones con ese objeto.

**Características**:

- **Verificación de Interacción**: Los mocks permiten comprobar si un método fue llamado, cuántas veces se llamó y con qué argumentos, lo que es útil para validar que el código interactúa correctamente con sus dependencias.
- **Configuración Avanzada**: Los mocks pueden configurarse para que respondan de manera diferente según las circunstancias, lo que permite simular diferentes escenarios de prueba.
- **Precisión en el Comportamiento**: Los mocks pueden ser más detallados en el seguimiento del comportamiento de los métodos, lo que facilita pruebas más exhaustivas sobre cómo se producen las interacciones.

**Ejemplo**: Supongamos que tienes un servicio que envía correos electrónicos. Puedes crear un mock del objeto que gestiona el envío de correos y verificar que se invoque el método de envío cuando se realiza una acción específica en tu lógica de negocio.
