.
El concepto de Clean Architecture, propuesto por [[Robert C. Martin]] (también conocido como Uncle Bob), es un enfoque para diseñar sistemas de software que busca crear aplicaciones mantenibles, escalables y testables. A continuación, se describen los principios y componentes clave de Clean Architecture:

1. **Separación de preocupaciones**: Clean Architecture promueve la separación de diferentes preocupaciones en el software, lo que significa que cada parte del sistema debe tener una responsabilidad clara y definida.

2. **Capas de Arquitectura**: La arquitectura se organiza en capas concéntricas, donde cada capa tiene un propósito específico. Las capas típicas son:
   - **Capa de Entidades**: Contiene las reglas de negocio y las entidades del dominio.
   - **Capa de Casos de Uso**: Define las operaciones que el sistema puede realizar, orquestando la lógica de negocio.
   - **Capa de Interfaces**: Maneja la interacción con el mundo exterior, como interfaces de usuario o APIs.
   - **Capa de Infraestructura**: Se encarga de la implementación de detalles técnicos, como bases de datos, servicios externos, etc.

![[Pasted image 20240903210308.png]]

3. **Dependencias Invertidas**: Las dependencias deben fluir hacia adentro, es decir, las capas externas pueden depender de las capas internas, pero no al revés. Esto permite que las reglas de negocio no se vean afectadas por cambios en la infraestructura.

4. **Testabilidad**: Al tener una clara separación de responsabilidades y dependencias, es más fácil realizar pruebas unitarias y de integración, lo que mejora la calidad del software.

5. **Independencia de Frameworks**: ==Clean Architecture no está ligada a ningún framework específico==, lo que permite que el sistema sea más flexible y adaptable a cambios futuros.

6. **Independencia de la UI**: La lógica de negocio y los casos de uso no deben depender de la interfaz de usuario, lo que permite cambiar la UI sin afectar la lógica del negocio.

En resumen, Clean Architecture busca crear sistemas que sean fáciles de entender, mantener y escalar, al mismo tiempo que se asegura que la lógica de negocio esté aislada de detalles técnicos y de implementación.
