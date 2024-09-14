.
Las pruebas de regresión son un tipo de prueba de software que se realiza para verificar que las modificaciones realizadas en el código (como correcciones de errores, mejoras o nuevas funcionalidades) no hayan introducido nuevos errores ni afectado negativamente al funcionamiento existente del software. El objetivo principal es asegurar que el software siga funcionando de acuerdo con los requisitos especificados después de estos cambios.

### Características Clave de las Pruebas de Regresión:

1. **Verificación de Funcionalidades Existentes**: Se prueba que las funcionalidades que previamente estaban funcionando correctamente continúen haciéndolo después de cambios en el código.

2. **Automatización**: Las pruebas de regresión suelen ser automatizadas para facilitar su ejecución frecuente y eficiente. Esto es especialmente útil en ciclos de desarrollo ágil donde se realizan cambios frecuentes en el software.

3. **Cobertura de Casos de Prueba**: Pueden incluir un conjunto de casos de prueba existentes (de pruebas unitarias, pruebas de integración, entre otros) que se ejecutan para validar que nada se ha roto debido a los nuevos cambios.

4. **Foco en Cambios Recientes**: Aunque se pueden ejecutar pruebas más amplias, es común que las pruebas de regresión se centren en los componentes que han sido modificados recientemente y en aquellos que están relacionados o dependen de esos cambios.

5. **Frecuencia de Ejecución**: Se realizan de manera regular, especialmente en entornos de [[Integración continua]] y [[Entrega y despliegue Continuo]] (CI/CD), donde es fundamental garantizar la estabilidad del sistema tras cada nueva integración de código.

### Importancia de las Pruebas de Regresión:

1. **Mantener la Calidad del Software**: Aseguran que las nuevas actualizaciones no introduzcan errores en las funcionalidades existentes, lo que es esencial para mantener la calidad del software.

2. **Reducción de Riesgos**: Detectar problemas temprano ayuda a reducir el riesgo de que las nuevas versiones del software presenten fallos cuando son lanzadas.

3. **Facilitar el Mantenimiento**: Permiten realizar cambios en el software de manera más segura, ya que el equipo de desarrollo puede tener confianza en que no afectarán negativamente a las partes del sistema que ya están funcionando bien.

4. **Aumento de la Eficiencia**: La automatización de pruebas de regresión ayuda a realizar pruebas de manera más rápida y eficiente, liberando tiempo para concentrarse en probar nuevas funcionalidades y mejorar el software.

En resumen, las pruebas de regresión son una práctica fundamental en el desarrollo de software que ayuda a garantizar que las modificaciones en el código no comprometan la integridad y funcionalidad del sistema, manteniendo así la confianza en el producto a lo largo de su ciclo de vida.

---
### 1. **Pruebas de Regresión**
Estas pruebas aseguran que los cambios recientes en el código no han introducido nuevos errores en funcionalidades que previamente funcionaban correctamente.

#### Ejemplo:
Supongamos que añadimos una nueva funcionalidad que permite **editar una tarea**. Queremos asegurarnos de que esta nueva función no afecta negativamente a las funciones ya existentes, como agregar, listar o eliminar tareas.

```python
# test_regression.py

import unittest
from io import StringIO
from unittest.mock import patch
from main import main

class TestRegressionToDoList(unittest.TestCase):

    @patch('builtins.input', side_effect=['1', 'Estudiar', '2', '4'])
    @patch('sys.stdout', new_callable=StringIO)
    def test_add_and_list_task_still_works_after_edit_feature(self, mock_stdout, mock_input):
        # Verificamos que después de añadir la funcionalidad de editar, añadir y listar tareas sigue funcionando
        main()
        output = mock_stdout.getvalue()
        self.assertIn("Tarea 'Estudiar' añadida.", output)
        self.assertIn("1: Estudiar", output)

if __name__ == '__main__':
    unittest.main()
```

