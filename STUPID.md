.
- https://codideep.com/blogpost/stupid-vs-solid

La primera vez que escuche de este acrónimo me pareció muy gracioso, cuando fui revisando cada palabra que lo componen, me di cuenta que en muchas ocasiones escribí código STUPID.

A continuación, veamos con más detalle las malas prácticas de STUPID.

### 1. Singleton

En ingeniería de software, el patrón singleton es un patrón de diseño de software que restringe la instanciación de una clase a una instancia "única". Esto es útil cuando se necesita exactamente un objeto para coordinar acciones en todo el sistema.

Realmente Singleton no es el problema, el problema es cuando aplicamos mal este patrón y lo usamos en todas partes.

Por ejemplo:

public class DataBaseHelper {
    
    public static int executeQuery(String query) {
        ...
    }
}

Tendríamos la clase DataBaseHelper, con su método estático executeQuery, dando vuelta por todo nuestro programa, sin necesidad de inyectar ninguna dependencia, porque ya tenemos el objeto singleton. Los principales problemas de esto son:

- Nuestras clases mantendrán un estado global, dificultando realizar test.
- Nuestras clases, que dependen del objeto singleton, ocultan sus dependencias.
- Nuestro software se vuelve estrictamente acoplado a la implementación de los singletons.

Personalmente creo que deberíamos evitar el patrón singleton, porque en la mayoría de casos podemos remplazarlo por algo mejor, pero puede que en ciertos casos utilizar este patrón este bien. Por ello creo que debemos considerar cada patrón como un 'súper poder', y cada poder conlleva una gran responsabilidad.

### 2. Tight Coupling

El acoplamiento apretado; La implementación de nuestro código es fuertemente acoplado y no es tolerante a cambios.

Este problema es una consecuencia de utilizar singleton, imaginemos que en nuestra anterior clase DataBaseHelper, el método executeQuery, por algún motivo necesitamos agregar un argumento o cambiar el tipo de retorno, esto afectaría a todos los módulos donde utilicemos esta función, ahí podemos notar que nuestros módulos estarían acoplados a la implementación de la clase DataBaseHelper .

### 3. Untestability

Código que no es 'testeable', código que está acoplado.

La importancia de los test, en muchos casos, es minimizada atribuyendo que este aumenta el tiempo de desarrollo, si bien es cierto, los test nos proporcionan muchos beneficios, de los cuales podríamos destacar:

- Nos proporcionan retroalimentación de que cada componente sigue funcionando.
- Nos fuerza a tener un software mejor diseñado, menos acoplado, y más fácil de mantener.
- Los desarrolladores sienten mayor libertad de refactorizar el código, con la confianza de que todo sigue funcionando.

Es importante escribir código que sea fácilmente 'testeable', imaginen que el código que escriben hoy, será refactorizado por un asesino mañana.

### 4. Premature Optimization

Una prematura optimización, puede ocasionar muchos problemas y costos innecesarios, podemos terminar escribiendo código ilegible o montando un cluster para una web que tiene 10 visitas diarias. Tenemos que tener mucho cuidado cuando queremos anticiparnos a los requisitos.

### 5. Indescriptive Naming

Nombramiento indescriptible, tenemos que tener en cuenta que escribimos código para personas, por eso es importante nombrar de forma correcta nuestras clases, métodos, atributos y variables, y no utilizar abreviaciones.

### 6. Duplication

Código duplicado, tener el mismo código en distintos lugares es un problema, si hay alguna modificación, tendremos que hacerlo n veces, la cantidad que este duplicado.

### S O L I D

_SOLID son una colección de principios de diseño de software, introducidos por Robert Martin, estos principios nos ayudan a conseguir un código limpio, mantenible, escalable y tolerante a cambios._

### 1. Single Responsability Principle (SRP)

Una clase solo debe tener una razón para cambiar.

Principio de responsabilidad única, este principio nos dice que cada clase o método debe tener una responsabilidad única, nunca debería haber más de una razón para que nuestra clase cambie.

La definición de este principio parece simple, sin embargo, alcanzar esta simplicidad puede resultar complicado, un truco que se usa para respetar este principio es tener clases pequeñas con objetivos acotados, pero te preguntarás qué ganamos respetando este principio, podemos destacar:

- Una alta cohesión y robustez en nuestro código
- Permitir composición de clases (inyectar colaboradores)
- Evitamos la duplicidad de código

Veamos un ejemplo de una clase que rompe este principio:

final class User {
    private String firstName;
    private String lastName;
    private String birthDate;

    public User(String firstName, String lastName, String birthDate) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.birthDate = birthDate;
    }

     public boolean isYourBirthDate() {
         //Is your birthday today?
     }

     public void save() {
         // save user in CSV
     }
}

Tenemos una clase User con dos métodos isYourBirthDate (comprueba si hoy es su cumpleaños) y save (guarda al usuario en un archivo CSV), y podríamos tener el siguiente código siendo usado por un cliente:

User userRegistered = new User("Robert", "Huamán Cáceres", "03/07");

if(userRegistered.isYourBirthDate()) {
    System.out.println("Happy Birthday!!!");
}

userRegistered.save();

La clase User rompe el principio SRP, porque tiene más de una razón para cambiar, sabe como modelar los datos y como guardar esos datos en un archivo CSV.

Si necesitáramos cambiar algo en el modelo de datos o cambiar la forma de guardar el usuario, a una base de datos MySql por ejemplo, vemos que tenemos 2 razones que nos podrían hacer modificar esta clase.

Veamos como podríamos refactorizar esta clase, para poder cumplir el principio SRP:

final class User {
    private String firstName;
    private String lastName;
    private String birthDate;

    public User(String firstName, String lastName, String birthDate) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.birthDate = birthDate;
    }

     public boolean isYourBirthDate() {
         //Is your birthday today?
     }
}

interface Repository {
    void save(User user);
}

final class CSVRepository implements Repository {

    @Override
    public void save(User user) {
        // save user in CSV
    }
}

Si tendríamos que cambiar a una base de datos MySql, lo haríamos sin tener que modificar la clase User

final class MySqlRepository implements Repository {

    @Override
    public void save(User user) {
        // save user in mysql
    }
}

En el cliente:

User userRegistered = new User("Robert", "Huamán Cáceres", "03/07");

// save the user in a CSV file
CSVRepository csvStorage = new CSVRepository();
csvStorage.save(userRegistered);

// save the user in MySQL database
MySqlRepository mysqlStorage = new MySqlRepository();
mysqlStorage.save(userRegistered);

Ahora tenemos un código más cohesionado, robusto y compuesto de colaboradores.

### 2. Open/Close Principle (OCP)

_Las clases, módulos, funciones, etc. deberían estar abiertas a extensión y cerradas a modificación._

El principio de abierto/cerrado, nos dice que debemos diseñar nuestros módulos, clases y funciones de tal manera que si se requiere agregar alguna funcionalidad, no debamos modificar nuestro código existente, sino, escribir el código nuevo. La forma de conseguir esto es evitando depender de implementaciones específicas, y hacer uso de clases abstractas o interfaces, con la finalidad de poder agregar nuevas funcionalidades sin tener que modificar implementaciones anteriores.

Podemos ver que el principio SRP y OCP son complementarios, recordando la clase User que tiene un método save para poder almacenarse en un archivo CSV, al agregar una nueva característica para que el usuario pueda guardarse en una base de datos MySql, vemos que esta nueva característica se convierte en una razón secundaria para cambiar la clase User, y de esta manera rompemos el principio SRP y OCP.

Veamos un ejemplo, tenemos la clase PayrollEmployee, que tiene una propiedad hourlyWage que es el monto que gana por hora, y la propiedad extraHours donde establecemos las horas extras de un empleado en planilla o nómina.

final class PayrollEmploye {
    private String socialSecurityNumber;
    private String firstName;
    private double hourlyWage;
    private int extraHours;

    public PayrollEmploye(String firstName, double hourlyWage, String socialSecurityNumber) {
        this.firstName = firstName;
        this.hourlyWage = hourlyWage;
        this.socialSecurityNumber = socialSecurityNumber;
    }

    public void setExtraHours(int extraHours) {
        this.extraHours = extraHours;
    }

    public int getExtraHours() {
        return this.extraHours;
    }

    public double getHourlyWage() {
        return this.hourlyWage;
    }
}

Y tenemos una clase OvertimeSalaryCalculator con el método getExtraSalary que nos calcula el monto por las horas extras trabajadas.

final class OvertimeSalaryCalculator {
    public double getExtraSalary(PayrollEmploye employee) {
        return employee.getHourlyWage() * employee.getExtraHours();
    }
}

En el cliente:

PayrollEmploye decoratedEmployee = new PayrollEmploye("Robert", 30, "SSN-0001");
decoratedEmployee.setExtraHours(4);

OvertimeSalaryCalculator salaryCalculator = new OvertimeSalaryCalculator();

double extraSalary = salaryCalculator.getExtraSalary(decoratedEmployee);

Podemos ver que estamos respetando el principio SRP, pero qué pasaría si nace un nuevo requerimiento de agregar una nueva clase para empleados externos ExternalEmployee, y queremos reutilizar la clase OvertimeSalaryCalculator para calcular el salario por las horas extras, veremos que tendremos que modificar nuestro código ya existente, estamos incumpliendo el principio OCP.

Hay dos formas de refactorizar este código, respetando el principio OCP:

**1. Interfaces**

La interfaz Employee:

interface Employee {
    int getExtraHours();
    double getHourlyWage();
}

Las clases PayrollEmploye y ExternalEmployee implementan Employee

final class PayrollEmploye implements Employee {
    private String firstName;
    private int extraHours;
    private double hourlyWage;
    private String socialSecurityNumber;

    public PayrollEmploye(String firstName, double hourlyWage, String socialSecurityNumber) {
        this.firstName = firstName;
        this.hourlyWage = hourlyWage;
        this.socialSecurityNumber = socialSecurityNumber;
    }

    public void setExtraHours(int extraHours) {
        this.extraHours = extraHours;
    }

    @Override
    public int getExtraHours() {
        return this.extraHours;
    }

    @Override
    public double getHourlyWage() {
        return this.hourlyWage;
    }
}

final class ExternalEmployee implements Employee {
    private String firstName;
    private int extraHours;
    private double hourlyWage;

    public ExternalEmployee(String firstName, double hourlyWage) {
        this.firstName = firstName;
        this.hourlyWage = hourlyWage;
    }

    public void setExtraHours(int extraHours) {
        this.extraHours = extraHours;
    }

    @Override
    public int getExtraHours() {
        return this.extraHours;
    }

    @Override
    public double getHourlyWage() {
        return this.hourlyWage;
    }
}

La clase OvertimeSalaryCalculator:

final class OvertimeSalaryCalculator {
    public double getExtraSalary(Employee employee) {
        return employee.getHourlyWage() * employee.getExtraHours();
    }
}

Vemos que nuestra clase OvertimeSalaryCalculator realiza el cálculo en base a un objeto que implemente Employee, por lo que sólo estamos acoplados a la interfaz.

**2. Clases Abstractas**

La clase abstracta Employee

abstract class Employee {
    abstract int getExtraHours();
    abstract double getHourlyWage();

    public double getExtraSalary() {
        return this.getHourlyWage() * this.getExtraHours();
    }
}

Las clases PayrollEmploye y ExternalEmployee heredan de Employee

final class PayrollEmploye extends Employee {
    private String firstName;
    private int extraHours;
    private double hourlyWage;
    private String socialSecurityNumber;

    public PayrollEmploye(String firstName, double hourlyWage, String socialSecurityNumber) {
        this.firstName = firstName;
        this.hourlyWage = hourlyWage;
        this.socialSecurityNumber = socialSecurityNumber;
    }

    public void setExtraHours(int extraHours) {
        this.extraHours = extraHours;
    }

    @Override
    public int getExtraHours() {
        return this.extraHours;
    }

    @Override
    public double getHourlyWage() {
        return this.hourlyWage;
    }
}

final class ExternalEmployee extends Employee {
    private String firstName;
    private int extraHours;
    private double hourlyWage;

    public ExternalEmployee(String firstName, double hourlyWage) {
        this.firstName = firstName;
        this.hourlyWage = hourlyWage;
    }

    public void setExtraHours(int extraHours) {
        this.extraHours = extraHours;
    }

    @Override
    public int getExtraHours() {
        return this.extraHours;
    }

    @Override
    public double getHourlyWage() {
        return this.hourlyWage;
    }
}

La clase OvertimeSalaryCalculator:

final class OvertimeSalaryCalculator {
    public double getExtraSalary(Employee employee) {
        return employee.getExtraSalary();
    }
}

Ahora al heredar de la clase abstracta Employee, nuestras clases cuentan con el método getExtraSalary ya implementado, llevando la lógica a nuestro modelo.

El Cliente

PayrollEmploye decoratedEmployee = new PayrollEmploye("Robert", 30, "SSN-0001");
decoratedEmployee.setExtraHours(4);

ExternalEmployee externalEmployee = new ExternalEmployee("Junior", 20);
decoratedEmployee.setExtraHours(1);

OvertimeSalaryCalculator salaryCalculator = new OvertimeSalaryCalculator();

double payrollExtraSalary = salaryCalculator.getExtraSalary(decoratedEmployee);
double externalExtraSalary = salaryCalculator.getExtraSalary(externalEmployee);

Ahora si estamos respetando el principio OCP, algo que es importante mencionar, es que debemos usar las interfaces cuando vayamos a desacoplar entre capas, y utilizar clases abstractas para modelos de dominio.

### 3. Liskov Sustitution Principle (LSP)

_Si S es un subtipo de T, instancias de T deberían poderse sustituir por instancias de S sin alterar las propiedades del programa._

El principio de sustitución de liskov, nos dice que teniendo una jerarquía donde establecemos un contrato en la clase padre, se debe garantizar que se cumple dicho contrato en la clase hijo, permitiéndonos sustituir al padre por el hijo.

Veamos un ejemplo, tenemos la interface SavingAccount:

interface SavingAccount {
    boolean withdrawal(double amount);
}

Y las clases RegularSavingAccount y FixDepositeSavingAccount que implementan a SavingAccount

final class RegularSavingAccount implements SavingAccount {

    @Override
    public boolean withdrawal(double amount) {
        // implement withdrawal
    }
}

final class FixDepositeSavingAccount implements SavingAccount {
    @Override
    public boolean withdrawal(double amount) {
        throw new Exception("not available in this type of account");
    }
}

Podríamos tener una función que realice el retiro de cualquier cuenta:

public boolean withdrawFromAccount(SavingAccount account) {
			...
      account.withdrawal(requiredAmount);
			...
}

En el cliente:

//Ok
withdrawFromAccount(new RegularSavingAccount());
// Throws a runtime exception
withdrawFromAccount(new FixDepositeSavingAccount());

Si pasamos una instancia de FixDepositeSavingAccount a la función withdrawFromAccount obtendríamos una excepción en tiempo de ejecución, y estaríamos rompiendo el principio de sustitución de lisktov, puesto que la clase hija FixDepositeSavingAccount, no respeta el contrato de su clase padre, porqué este tipo de cuenta no permite los retiros de dinero.

Los principales problemas con esto son:

- El código arroja un error en tiempo de ejecución, dando cabida a comportamientos no controlados del sistema, o resultados incorrectos.
- Forzamos a FixDepositeSavingAccount implementar un método que no es utilizado por esta clase.

La solución la veremos en el siguiente punto ya que los principios LSP y ISP son complementarias.

### 4. Interface Segregation Principle (ISP)

El principio de segregación de interfaces, nos dice que ninguna clase debe ser forzada a depender de métodos que no utiliza.

Como vimos en el ejemplo anterior, nuestra clase FixDepositeSavingAccount, esta obligada a implementar el método de retiro de dinero, pero este tipo de cuenta no soporta o permite los retiros, nos damos cuenta que estamos violando los principios LSP e ISP.

¿Cómo solucionamos este problema respetando ambos principios?

Definiendo contratos de interface basándonos en los clientes que lo usan, y no en las implementaciones que pudieran tener. (Las interfaces pertenecen a los clientes).

Creamos dos nuevas interfaces SavingAccountWithWithdrawal y SavingAccountWithoutWithdrawal que heredan de SavingAccount

interface SavingAccount {
    ...
}

interface SavingAccountWithWithdrawal extends SavingAccount {
    boolean withdrawal(double amount);
}

interface SavingAccountWithoutWithdrawal extends SavingAccount {
    ...
}

Y las clases de tipo de cuenta:

final class RegularSavingAccount implements SavingAccountWithWithdrawal {

    @Override
    public boolean withdrawal(double amount) {
        // implement withdrawal
    }
}

final class FixDepositeSavingAccount implements SavingAccountWithoutWithdrawal {
    ...
}

De esta manera, si intentamos retirar dinero de una cuenta de tipo FixDepositeSavingAccount, tendremos un error en compilación.

//Ok
withdrawFromAccount(new RegularSavingAccount());
// Compile time error!
withdrawFromAccount(new FixDepositeSavingAccount());

Respetando estos principios, conseguimos que nuestro código tenga una alta cohesión y bajo acoplamiento estructural.

### 5. Dependency Inversion Principle (DIP)

_Los módulos de alto nivel no deberían depender de los módulos de bajo nivel. Ambos deberían depender de abstracciones._

El principio de inversión de dependencias tiene 2 puntos importantes:

- Las abstracciones no deberían depender de los detalles.
- Los detalles deben depender de las abstracciones.

Algo que tenemos que tener en cuenta es que el principio DIP no es lo mismo que la inyección de dependencias. La inyección de dependencias trata de cómo un objeto adquiere una dependencia. Por otro lado DIP trata sobre el nivel de abstracción, quiere decir que dependeremos de las interfaces (contratos) de estas dependencias y no de implementaciones concretas. Este principio tiene como finalidad facilitar la modificación y sustitución de implementaciones.

Veamos un ejemplo:

**1. Acoplados a las dependencias.** 

La clase InMemoryUsersRepository

final class InMemoryUsersRepository {
    private final Map users = Collections.unmodifiableMap(new HashMap() {
        {
            put(1, new User("2b79d12d-30d9-4e08-8181-22f61cb3a34f", "Robert", "HC"));
            put(2, new User("b20f29bb-c5ef-43a4-8a10-87e5f633503a", "Bryanne", "Huamán Cáceres"));
        }
    });

    public Optional search(Integer id) {
        return Optional.ofNullable(users.get(id));
    }
}

La clase UserSearcher

final class UserSearcher {
    private final InMemoryUsersRepository usersRepository = new InMemoryUsersRepository();

    public Optional search(Integer id) {
        return usersRepository.search(id);
    }
}

En este ejemplo, vemos que estamos instanciando a InMemoryUsersRepository dentro de la clase UserSearcher, esto quiere decir cuando utilicemos el método search, estaremos fuertemente acoplados a la implementación del repositorio InMemoryUsersRepository.

**2. Inyección de dependencias.** 

La clase UserSearcher

final class UserSearcher {
    private final InMemoryUsersRepository usersRepository;
    
    public UserSearcher(InMemoryUsersRepository usersRepository) {
        this.usersRepository = usersRepository;
    }

    public Optional search(Integer id) {
        return usersRepository.search(id);
    }
}

Vemos que reducimos el acoplamiento de nuestra clase UserSearcher, inyectando la dependencia que tiene respecto a InMemoryUsersRepository, en el propio constructor. De esta manera la clase UserSearcher es abierta a informar las dependencias que tiene, y la clase que la instancie será la encargada de resolver dichas dependencias.

Aunque aún nuestro código sigue acoplado a la implementación de InMemoryUsersRepository, conseguimos exponer este acoplamiento.

**3. Inversión de dependencias.**

La interface UsersRepository

interface UsersRepository {
    Optional search(Integer id);
}

La clase InMemoryUsersRepository

final class InMemoryUsersRepository implements UsersRepository {
		...
}

La clase UserSearcher

final class UserSearcher {
    private UsersRepository usersRepository;

    public UserSearcher(UsersRepository usersRepository) {
        this.usersRepository = usersRepository;
    }

    public Optional search(Integer id) {
        return usersRepository.search(id);
    }
}

Vemos que la clase UserSearcher recibe por el constructor una implementación que cumpla con el contrato de la interfaz UsersRepository.

De esta manera, el acoplamiento de UserSearcher es con la interface UsersRepository, y las diferentes implementaciones estarán acopladas a cumplir el contrato de la interface, de modo que si quisiéramos cambiar la implementación de una búsqueda en memoria InMemoryUsersRepository a una búsqueda en base de datos, bastaría con implementar una clase MySqlUsersRepository que cumpla con el contrato de la interfaz UsersRepository.

> CONCLUSIÓN
> 
> El objetivo de los principios SOLID, es evitar el fuerte acoplamiento haciendo nuestro código más fácil de manejar y comprender; implementar estos principios implica un cambio en nuestra forma de pensar y diseñar software. Escribamos menos código STUPID y comencemos a escribir un mejor código, haciendo que nuestra vida como programadores sea mucho más fácil.
> 
> Para concluir, quiero recalcar que estos son principios y no leyes, mantengamos la mente abierta siempre a mejorar.