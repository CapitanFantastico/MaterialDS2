.
En **DevOps** y **pruebas de software**, el término **scripting** se refiere al proceso de escribir <u>pequeños programas</u>, generalmente llamados **scripts**, para automatizar tareas repetitivas o complejas que de otro modo tendrían que realizarse manualmente. Estos scripts son especialmente útiles para la <u>automatización de pruebas, implementación continua, y otras tareas de desarrollo y operaciones.</u>

Los lenguajes más usados para escribir scripts incluyen [[Python]], [[Bash]], [[Perl]], [[Ruby]], y [[PowerShell]].
Estos lenguajes son generalmente más fáciles de escribir y ejecutar que los lenguajes compilados.

### **Usos**:

1. **Automatización de pruebas**:
   - Los scripts se utilizan para automatizar casos de prueba, como pruebas unitarias, pruebas de integración, pruebas funcionales y no funcionales.
   - Esto permite que las pruebas se ejecuten automáticamente, lo que aumenta la eficiencia y reduce el error humano.
  
2. **Implementación en [[Pipelines]] [[CI]]/[[CD]]**: [[CI-CD]]
   - En el contexto de [[DevOps]], los scripts son fundamentales para los [[Pipeline]]s de **[[Integración Continua]] ([[CI]])** y **Entrega Continua ([[CD]])**.
   - Por ejemplo, un script puede automatizar el proceso de ejecutar pruebas cada vez que se hace una nueva integración de código en el repositorio.

4. **Automatización de tareas repetitivas**:
   - En pruebas de software, un script puede automatizar tareas como la configuración del entorno de pruebas, la preparación de datos de prueba, la limpieza del sistema después de las pruebas, o la generación de informes de resultados.

### **Ejemplos de scripting:

1. **Ejecución de pruebas automáticas**:
   - Un script puede automatizar la ejecución de una suite de pruebas de software. Cada vez que se realiza un cambio en el código, el script se ejecuta para probar el sistema de manera automática.
   - Ejemplo en Python:
     ```python
     import unittest
     def test_sum():
         assert sum([1, 2, 3]) == 6, "Error: Expected sum to be 6"
     
     if __name__ == '__main__':
         unittest.main()
     ```

2. **Scripting para configuraciones automáticas**:
   - Por ejemplo, scripts Bash se pueden usar para configurar automáticamente servidores, ejecutar aplicaciones o preparar el entorno de pruebas antes de comenzar la ejecución.
     ```bash
     #! /bin/bash
     # Script to set up a test environment
     echo "Starting test environment setup..."
     docker-compose up -d
     echo "Environment ready"
     ```

3. **Ejecución de pruebas con [[Jenkins]]**:
   - En una herramienta como Jenkins, un script puede iniciar automáticamente el proceso de compilación, pruebas, y despliegue de software tras cada commit.
     ```groovy
     pipeline {
         agent any
         stages {
             stage('Build') {
                 steps {
                     sh 'make build'
                 }
             }
             stage('Test') {
                 steps {
                     sh 'make test'
                 }
             }
             stage('Deploy') {
                 steps {
                     sh 'make deploy'
                 }
             }
         }
     }
     ```

### **Desafíos del scripting:

1. **Mantenimiento de scripts**:
   - A medida que los sistemas cambian y evolucionan, los scripts de prueba también deben actualizarse para reflejar los nuevos comportamientos del software.
   
2. **Costo inicial**:
   - Crear y configurar scripts automatizados puede requerir tiempo y recursos al principio, aunque luego generen ahorros en tiempo y esfuerzo.

---

Ver
- [[Bash scripting]] <
- [[Python scripting]] 
- [[Ejemplo bash scripting vs python scripting]] <
- [[PowerShell scripting]] 
- [[Perl scipting]]
- [[Ruby scripting]]

