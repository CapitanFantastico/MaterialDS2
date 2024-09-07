.
**Definición:** La inmovilidad se refiere a la dificultad para reutilizar partes del código en otro sistema o contexto debido a dependencias innecesarias o a una integración excesiva.

**Ejemplo:**
Imagina que tienes un módulo de autenticación que está fuertemente acoplado al sistema de gestión de usuarios de una aplicación específica:

```python
class Autenticacion:
    def __init__(self, sistema_usuarios):
        self.sistema_usuarios = sistema_usuarios

    def autenticar(self, nombre_usuario, contrasena):
        usuario = self.sistema_usuarios.buscar_usuario(nombre_usuario)
        if usuario and usuario.contrasena == contrasena:
            return True
        return False
```

Este módulo de autenticación no puede ser fácilmente reutilizado en otra aplicación porque depende de un sistema de gestión de usuarios específico (`sistema_usuarios`). Para reutilizarlo, tendrías que refactorizar el código para desacoplarlo.

**Consecuencia:** Este diseño es inmóvil porque el código no puede ser extraído y reutilizado en otros contextos sin modificaciones significativas.

