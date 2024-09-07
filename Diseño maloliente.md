.
**"Design smells"** (olores de diseño) se refiere a indicios o señales en el diseño de software que sugieren la presencia de problemas en la arquitectura o en la estructura general del sistema. A diferencia de los **[[Codigo maloliente]]**, que se enfocan en problemas a nivel de código, los **design smells** se centran en problemas que afectan el diseño global del sistema, como su modularidad, flexibilidad, y mantenibilidad.

Los design smells suelen indicar que el sistema podría volverse difícil de escalar, modificar, o comprender a medida que crece. Abordarlos es crucial para mantener la calidad a largo plazo del software.

### Ejemplos comunes de design smells:

1. **[[Rigidez]]**:
   - **Descripción**: El sistema es difícil de cambiar porque cada modificación provoca una cascada de cambios en otras partes del sistema.
   - **Consecuencia**: Falta de flexibilidad y alta resistencia al cambio.
   - **Solución**: Utilizar principios de diseño como la **[[inversión de dependencias]]** o aplicar [[Patrones de diseño]] que promuevan la flexibilidad.
2. **[[Fragilidad]]**:
   - **Descripción**: El sistema tiende a romperse en lugares inesperados cuando se hacen cambios.
   - **Consecuencia**: Las modificaciones en una parte del sistema causan fallos en otras partes aparentemente no relacionadas.
   - **Solución**: Aplicar la [[refactorización]] para mejorar la cohesión y reducir las dependencias innecesarias.
3. **[[Inmovilidad]]**:
   - **Descripción**: Es difícil reutilizar partes del sistema en otro contexto porque están demasiado entrelazadas con el resto del sistema.
   - **Consecuencia**: Dificultad para la reutilización de código y alto acoplamiento. 
   - **Solución**: Aislar y modularizar componentes, de manera que sean más independientes y reutilizables.
4. **[[Viscosidad]]**:
   - **Descripción**: Hacer cambios de diseño que sigan las buenas prácticas es difícil, mientras que los cambios rápidos y sucios son más fáciles de implementar.
   - **Consecuencia**: Los desarrolladores se inclinan por soluciones subóptimas que deterioran la calidad del diseño.
   - **Solución**: Facilitar que las buenas prácticas sean las soluciones más simples de implementar.
   - Nota: [[Síntoma de los cristales rotos]] 
5. **[[Abstracciones inapropiadas]]**:
   - **Descripción**: Abstracciones mal diseñadas que no se alinean con el dominio del problema, o que son demasiado generales o específicas.
   - **Consecuencia**: La abstracción incorrecta puede complicar el uso y mantenimiento del sistema.
   - **Solución**: Refactorizar para crear abstracciones más precisas y alineadas con las necesidades del sistema.
6. **[[Sobreingeniería]]**:
   - **Descripción**: El diseño es excesivamente complejo, considerando escenarios o características que no son necesarios.
   - **Consecuencia**: Aumento innecesario de la complejidad, lo que puede ralentizar el desarrollo y dificultar la comprensión.
   - **Solución**: Simplificar el diseño enfocándose en los requisitos actuales y evitar anticiparse innecesariamente a futuros cambios.

### Importancia de abordar los design smells:
Los design smells son críticos porque afectan la calidad global del software. Si no se abordan, pueden llevar a un software difícil de mantener, frágil ante los cambios y costoso de escalar. La solución generalmente involucra la **refactorización del diseño**, que incluye reestructurar la arquitectura y mejorar las abstracciones, la cohesión y el acoplamiento.

### Relación con los code smells:
Mientras que los code smells afectan el nivel del código, los design smells afectan el nivel de arquitectura y diseño. Ambos son importantes de identificar y resolver para asegurar un desarrollo sostenible y un software de alta calidad.

