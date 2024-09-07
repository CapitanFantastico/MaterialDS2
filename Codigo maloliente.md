.
El término **"code smell"** (a veces traducido como "código maloliente") se refiere a indicios o señales en el código que sugieren la presencia de problemas potenciales o mala calidad en su diseño o estructura. Aunque un code smell no necesariamente implica que el código está incorrecto o que hay errores funcionales, sí indica que el código podría ser difícil de mantener, extender, o entender, lo cual podría llevar a problemas más graves en el futuro.

### Ejemplos comunes de code smells:

- **Funciones largas**: Métodos o funciones que son excesivamente largos y hacen demasiado trabajo. Esto puede dificultar la comprensión y el mantenimiento.

- **Nombres confusos**: Variables, funciones o clases que tienen nombres poco descriptivos o engañosos, lo que complica la lectura y entendimiento del código.

- **Duplicación de código**: Bloques de código idénticos o muy similares que aparecen en múltiples lugares del proyecto, lo cual puede hacer que la actualización o corrección del código sea tediosa y propensa a errores.

- **Clases gigantes**: Clases que tienen demasiadas responsabilidades o contienen demasiado código. Esto puede hacer que sean difíciles de gestionar y probar.

- **Código muerto**: Fragmentos de código que nunca se ejecutan o que ya no son necesarios. Este tipo de código crea desorden y confusión.

- **Comentar en exceso**: Comentarios que intentan explicar código complejo en lugar de refactorizarlo para hacerlo más claro. El código bien escrito debe ser autoexplicativo.

- **Dependencias excesivas**: Código que depende en gran medida de muchas otras clases o módulos, lo que puede dificultar el mantenimiento y prueba del mismo.

### Cómo abordar los code smells:
Los code smells no deben ser ignorados, ya que suelen ser un síntoma de problemas más profundos en el diseño o la arquitectura del software. La solución para los code smells típicamente involucra **refactorización** del código, es decir, reestructurarlo sin cambiar su comportamiento externo para mejorar su calidad.

### Ejemplo práctico:
Si una función tiene demasiadas responsabilidades, un buen enfoque es dividirla en varias funciones más pequeñas y enfocadas, cada una con una responsabilidad clara. Esto no solo mejora la legibilidad, sino que también facilita el testing y reduce la posibilidad de errores.

El término "code smell" fue popularizado por [[Martin Fowler]] en su libro *Refactorización: Improving the Design of Existing Code*, donde describe varias técnicas para identificar y eliminar estos olores de código a través de la refactorización.

Ver también
- https://www.ionos.com/es-us/digitalguide/paginas-web/desarrollo-web/code-smell/?srsltid=AfmBOoq1mik3G6laQOjtrlhGote5-T7HhlGnMmWmDetDdc9m2wtuWfDD
- https://www.ionos.com/es-us/digitalguide/paginas-web/desarrollo-web/clean-code-que-es-el-codigo-limpio/
- [[Codigo limpio]] 

