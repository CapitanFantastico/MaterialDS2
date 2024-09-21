.
Bourne Shell (`sh`) parece soportar el uso de `alias` en algunos entornos, por varios factores relacionados con cómo se implementan y configuran los shells en sistemas modernos. En particular, esto se debe a la evolución de los shells y cómo se mantienen las compatibilidades hacia atrás en diferentes sistemas operativos.

### **Razones por las que `alias` funciona en `sh` en ciertos entornos**

1. **Compatibilidad con otros Shells (Dash, Bash como `sh`)**:
   - En muchos sistemas operativos modernos, lo que se ejecuta al llamar `sh` no es el antiguo Bourne Shell original. En su lugar, se ejecuta un shell más moderno, como `Dash` o incluso una versión reducida de `Bash`, que se comporta de manera similar al Bourne Shell, pero con extensiones adicionales.
   - `Dash` (Debian Almquist Shell) es un shell que se utiliza a menudo como `/bin/sh` en muchas distribuciones de Linux por su rapidez y eficiencia en comparación con Bash. Aunque mantiene la sintaxis básica de Bourne Shell, incluye algunas características adicionales como el soporte para `alias`.

2. **`Bash` en Modo `sh`**:
   - En algunas configuraciones, cuando ejecutas `sh`, en realidad se invoca una versión de `Bash` que corre en modo de compatibilidad con `sh`. Esto significa que `Bash` se comporta como `sh`, pero conserva muchas de sus funcionalidades adicionales, incluyendo `alias`. Este comportamiento es posible porque `Bash`, al ser un shell compatible con Bourne, puede cambiar su comportamiento dependiendo de cómo es invocado (si es ejecutado como `bash` o como `sh`).

3. **Implementaciones de `sh` en Sistemas Modernos**:
   - Las implementaciones modernas del shell pueden incluir características adicionales por conveniencia o para mejorar la compatibilidad con scripts existentes. Aunque no es parte del estándar POSIX de `sh`, el soporte para `alias` se ha incluido en algunas implementaciones porque es una característica ligera y ampliamente utilizada.

4. **Configuración Específica del Ambiente (`overthewire.org`)**:
   - En la plataforma `overthewire.org`, el shell que se está ejecutando como `sh` podría estar configurado para incluir funcionalidades de `alias` debido a que está utilizando una implementación compatible con `alias`, como `Dash` o `Bash`. El entorno está configurado para proporcionar una experiencia práctica y segura para aprender, por lo que es posible que ciertas extensiones se habiliten intencionalmente para mantener un entorno más familiar y funcional.

### **Verificando el Shell Real que se Está Ejecuntado**
Para confirmar cuál shell se está ejecutando realmente cuando usas `sh`, puedes utilizar los siguientes comandos desde el prompt del shell:

```bash
ps -p $$ -o comm=
```

Este comando mostrará el nombre real del proceso del shell que está corriendo. En muchos casos, podrías ver `dash`, `bash`, o incluso `sh` dependiendo de cómo el sistema esté configurado.
