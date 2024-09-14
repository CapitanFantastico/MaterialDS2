.
Un **spy** es una técnica utilizada en las pruebas de software que permite monitorear o espiar el comportamiento de un objeto real, proporcionando la capacidad de verificar interacciones con ese objeto y, en algunos casos, modificar el comportamiento de los métodos que se están espiando. Los spies son una herramienta útil en el ámbito de las pruebas unitarias, especialmente cuando se usa en combinación con técnicas de mocking y stubbing.

### Características del Spy:

1. **Monitoreo de Interacciones**: Los spies permiten registrar y verificar cómo se interactúa con un objeto, incluyendo qué métodos se llaman, con qué argumentos y cuántas veces. Esto es útil para asegurarse de que el código bajo prueba interactúa correctamente con sus dependencias.

2. **Comportamiento Real**: A diferencia de un mock, que simula el comportamiento de un objeto, un spy utiliza el objeto real y puede invocar sus métodos originales. Esto significa que puedes obtener el comportamiento real del objeto mientras aún puedes realizar verificaciones sobre él.

3. **Modificación de Comportamiento**: En algunos frameworks, es posible modificar el comportamiento del método mientras se espiaba. Por ejemplo, puedes decidir que un método devuelva un valor diferente de lo que normalmente haría.

4. **Uso Típico**: Utilizas spies cuando deseas realizar pruebas en la interacción con un objeto real (en lugar de un objeto simulado) pero aún necesitas una cierta capacidad para interceptar y controlar cómo se comporta durante la prueba.

### Ejemplo de Uso:

Imagina que tienes una clase `Calculadora` con un método que utiliza un servicio externo para obtener tasas de cambio:

```java
public class Calculadora {
    private CurrencyService currencyService;

    public Calculadora(CurrencyService currencyService) {
        this.currencyService = currencyService;
    }

    public double convertir(double cantidad, String moneda) {
        double tasa = currencyService.obtenerTasa(moneda);
        return cantidad * tasa;
    }
}
```

Si quieres probar la clase `Calculadora`, puedes espiar el objeto `CurrencyService` para verificar que el método `obtenerTasa` se llamó con el argumento correcto y al mismo tiempo permitir que se ejecute su lógica real.

```java
import static org.mockito.Mockito.*;

CurrencyService currencyServiceSpy = spy(new CurrencyService());
Calculadora calculadora = new Calculadora(currencyServiceSpy);

// Ejecutar el método a probar
calculadora.convertir(100, "USD");

// Verificar interacciones
verify(currencyServiceSpy).obtenerTasa("USD");
```

### Ventajas de Usar Spies:

- **Flexibilidad**: Permiten monitorear y verificar el comportamiento de objetos reales sin tener que crear mocks completamente.
- **Pruebas Más Realistas**: Al usar objetos reales, se pueden lograr pruebas que reflejan más de cerca cómo se comporta el sistema en producción.
- **Verificaciones Precisas**: Permiten verificar que se llamen métodos específicos y en qué contexto, lo cual puede ser crítico para las pruebas unitarias.

### Conclusión

Los spies son una herramienta eficaz en el arsenal de los desarrolladores de pruebas, combinando las ventajas de trabajar con objetos reales (para rendimiento y complejidad) con la capacidad de interceptar y verificar interacciones. Usar spies adecuadamente puede ayudar a garantizar que el código funcione como se espera en situaciones del mundo real, al mismo tiempo que proporciona una forma de comprobar las interacciones en las pruebas.
