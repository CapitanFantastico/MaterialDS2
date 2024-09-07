.
DISEÑAR = PARTIR, DESCOMPONER

El principio de descomposición es un enfoque fundamental en el diseño y desarrollo de software que implica dividir un ***sistema complejo*** en ***partes más pequeñas*** y manejables. Este principio se basa en la idea de que es más fácil entender, desarrollar y mantener componentes individuales que un sistema completo. A continuación, se describen sus características y beneficios:

1. **Modularidad**: La descomposición promueve la creación de módulos o componentes independientes que encapsulan una funcionalidad específica. Esto permite que cada módulo se desarrolle, pruebe y mantenga de manera aislada.

2. **Facilidad de Entendimiento**: Al dividir un sistema en partes más pequeñas, los desarrolladores pueden comprender mejor cada componente y su función dentro del sistema, lo que facilita el aprendizaje y la colaboración.

3. **Reutilización de Código**: Los componentes descompuestos pueden ser reutilizados en diferentes partes del sistema o en otros proyectos, lo que reduce la duplicación de código y mejora la eficiencia del desarrollo.

4. **Mantenimiento Simplificado**: Los cambios en un componente específico son menos propensos a afectar a otros componentes, lo que facilita el mantenimiento y la evolución del sistema a lo largo del tiempo.

5. **Escalabilidad**: La descomposición permite que los equipos trabajen en diferentes componentes simultáneamente, lo que facilita la escalabilidad del desarrollo y la implementación de nuevas funcionalidades.

6. **Pruebas Más Efectivas**: Los componentes más pequeños son más fáciles de probar de manera aislada, lo que mejora la calidad del software y facilita la identificación de errores.

7. **Facilitación de la Colaboración**: La descomposición permite que diferentes equipos o desarrolladores trabajen en diferentes partes del sistema al mismo tiempo, lo que mejora la colaboración y la eficiencia del trabajo en equipo.


---

A continuación, se presenta un ejemplo en Python que ilustra el principio de descomposición. En este caso, se desarrollará un programa simple que gestiona una lista de tareas. ==El programa se descompone en varias funciones, cada una encargada de una tarea específica==.

```python
# Función para mostrar el menú de opciones
def mostrar_menu():
    print("1. Agregar tarea")
    print("2. Ver tareas")
    print("3. Eliminar tarea")
    print("4. Salir")

# Función para agregar una tarea a la lista
def agregar_tarea(tareas):
    tarea = input("Ingrese la tarea: ")
    tareas.append(tarea)
    print(f"Tarea '{tarea}' agregada.")

# Función para ver todas las tareas
def ver_tareas(tareas):
    if not tareas:
        print("No hay tareas en la lista.")
    else:
        print("Lista de tareas:")
        for i, tarea in enumerate(tareas, start=1):
            print(f"{i}. {tarea}")

# Función para eliminar una tarea de la lista
def eliminar_tarea(tareas):
    ver_tareas(tareas)
    if tareas:
        indice = int(input("Ingrese el número de la tarea a eliminar: ")) - 1
        if 0 <= indice < len(tareas):
            tarea_eliminada = tareas.pop(indice)
            print(f"Tarea '{tarea_eliminada}' eliminada.")
        else:
            print("Índice inválido.")

# Función principal que ejecuta el programa
def main():
    tareas = []
    while True:
        mostrar_menu()
        opcion = input("Seleccione una opción: ")
        if opcion == '1':
            agregar_tarea(tareas)
        elif opcion == '2':
            ver_tareas(tareas)
        elif opcion == '3':
            eliminar_tarea(tareas)
        elif opcion == '4':
            print("Saliendo del programa.")
            break
        else:
            print("Opción no válida. Intente de nuevo.")

# Ejecutar el programa
if __name__ == "__main__":
    main()
```

### Descomposición en el Ejemplo:

1. **Funciones Específicas**: Cada función (`mostrar_menu`, `agregar_tarea`, `ver_tareas`, `eliminar_tarea`) tiene una ==responsabilidad clara y específica==, lo que facilita su comprensión y mantenimiento.

2. **Función Principal**: La función `main` orquesta el flujo del programa, llamando a las funciones según la opción seleccionada por el usuario.

3. **Modularidad**: Cada función puede ser ==probada y modificada de manera independiente==, lo que mejora la mantenibilidad del código.

Este enfoque permite que el programa sea más fácil de entender y modificar en el futuro, cumpliendo con el principio de descomposición.


---


Aquí tienes otro ejemplo sencillo del principio de descomposición en Python, donde descomponemos un programa en funciones más pequeñas y especializadas:

```python
def obtener_datos_usuario():
    nombre = input("Ingrese su nombre: ")
    edad = int(input("Ingrese su edad: "))
    return nombre, edad

def validar_edad(edad):
    if edad >= 18:
        print("Eres mayor de edad.")
    else:
        print("Eres menor de edad.")

def saludar_usuario(nombre):
    print(f"Hola, {nombre}! Bienvenido.")

# Programa principal
nombre, edad = obtener_datos_usuario()
saludar_usuario(nombre)
validar_edad(edad)
```

En este ejemplo, hemos descompuesto el programa en tres funciones más pequeñas y especializadas:

1. La función `obtener_datos_usuario()` se encarga de solicitar al usuario su nombre y edad, y luego devuelve estos datos.

2. La función `validar_edad(edad)` verifica si la edad ingresada es mayor o igual a 18 años e imprime un mensaje correspondiente.

3. La función `saludar_usuario(nombre)` recibe el nombre del usuario y le da la bienvenida con un mensaje.

Al aplicar el principio de descomposición, hemos dividido el programa en partes más pequeñas y cada función se encarga de una tarea específica. Esto hace que el código sea más fácil de entender, mantener y modificar, ya que cada función tiene una responsabilidad clara y bien definida.
