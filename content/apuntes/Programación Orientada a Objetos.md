---
Title: Programación Orientada a Objetos
Fecha: 2025-06-02
Hora: 1092
tags: ['programacion', 'enciclopedia', 'post']
---

---

## I. Introducción a la Programación Orientada a Objetos (POO)

La programación orientada a objetos es un paradigma que organiza el código en objetos, cada uno con sus propios datos (*atributos*) y comportamientos (*métodos*), evitando que otros objetos tengan acceso a estos elementos de manera no controlada.

Los beneficios y objetivos de POO son:

- **Natural**: Permite construir un sistema que modele elementos del mundo real.
- **Confiable**: Un programa bien diseñado y codificado va a funcionar como es esperado sin importar el tamaño, y el testing se vuelve más sencillo.
- **Reusable**: Una vez un problema es resuelto se puede volver a usar la solución.
- **Fácil de mantener**: Se estima que del 60%-80% del trabajo en un programa es el mantenimiento, el 20% es el desarrollo. Un bug se puede resolver corrigiendo una sola parte.
- **Extendible**: Un software creado en POO puede crecer y cambiar sin muchas dificultades.
- **Oportuno**: Varias partes del programa se pueden desarrollar en paralelo. Es esencial realizar correctamente el análisis y diseño.

### 1.1 Diferencias entre POO y la programación estructurada

A diferencia de la programación estructurada, donde el código se escribe en *funciones* que resuelven un problema lógico y este se ejecuta en orden de arriba hacia abajo, la POO organiza el código en un sistema conectado basado en *objetos*, y el orden en que se escriben las partes de una clase no afecta su funcionamiento.

Algunos lenguajes como Python o JavaScript no usan archivos de clase como Java o C#, pero siguen permitiendo la programación orientada a objetos. En su lugar, organizan el código en módulos, lo que ayuda a manejar proyectos grandes de manera más ordenada.

### 1.2 Los 4 pilares de POO

- **Encapsulación**: Es la combinación de atributos y métodos en una sola entidad (objeto), el cual solo debe permitir el acceso a sus datos y comportamiento a otros objetos con los que va a interactuar.
- **Abstracción**: Permite mostrar solo los elementos esenciales de un objeto al usuario final, ocultando los detalles internos de su implementación.
- **Herencia**: Permite que una clase aproveche los atributos y métodos de una ya existente sin tener que repetir el código, sino únicamente adicionando lo que le falte.
- **Polimorfismo**: Es la capacidad que tiene un método para comportarse de distintas maneras según el objeto que lo esté usando.
- **(+) Composición**: Aunque no es un principio oficial de POO la composición es un concepto importante que asimila que un objeto está formado por otros objetos, estableciendo una relación de dependencia entre ellos.

## II. Conceptos básicos de POO

### 2.1 Objetos

Son elementos que componen un sistema. Este contiene datos y comportamientos.

**Ejemplo**

En un automóvil las distintas partes que lo conforman son *objetos*, los cuales se pueden comunicar entre sí para funcionar.

#### Características de los objetos

##### Atributos

Los atributos representan las propiedades de un objeto y almacenan su información en un momento dado. Estos definen el *estado* del objeto y pueden cambiar durante la ejecución del programa.

**Elementos de un atributo**

- **Un nombre**, que lo identifica dentro de la clase.
- **Un tipo de dato**, que determina qué valores puede almacenar.
- **Un nivel de acceso**, que controla cómo se puede modificar o leer.

**Ejemplo en C#**

```csharp
class Persona
{
    // Atributos de la clase Persona (nivel de acceso, tipo de dato y nombre)
    private string nombre;
    private int edad;
}
```

##### Métodos

Representan lo que el objeto puede hacer.

La diferencia entre un método y una función es que los *métodos* son parte de los objetos y pueden acceder a sus datos, mientras que las *funciones* solo trabajan con los valores que se les pasan como parámetros.

**Elementos de un método**

- **Nombre**: Identifica al método dentro de la clase.
- **Parámetros**: Valores de entrada que el método puede recibir para procesar (puede no tener parámetros).
- **Tipo de retorno**: El tipo de dato que el método devuelve al terminar su ejecución. Puede ser un tipo de dato (`int`, `string`, `bool`, etc.) o `void` si no devuelve nada.
- **Cuerpo**: Conjunto de instrucciones o código que define qué hace el método.
- **Modificadores de acceso**: Palabras clave que controlan el acceso (public, private) o comportamiento especial (static, virtual, etc.) del método.

**Los métodos se pueden activar/invocar al**:

- **Recibir un mensaje**: Se invocó el método desde otro objeto
- **Con un cambio de estado**: Un atributo cambió en el objeto.

**Para que el método sea invocado, se requiere conocer**:

- **Nombre** del método.
- **Parámetros** a pasar al método (Si es que el método los acepta).
- **Tipo de dato** que va a retornar el método.

**Ejemplo en C#**

La clase `Persona` se define con dos atributos (`nombre` y `edad`) y un método `MostrarInfo()` que imprime esos datos. En `Main`, se crea una instancia basada en `Persona`, se le asignan valores y se llama al método para mostrar la información.

```csharp
class Persona
{
	// Declaración de variables
    public string nombre;
    public int edad;

    // Método para mostrar información de la persona
    public void MostrarInfo()
    {
        Console.WriteLine($"Nombre: {nombre}, Edad: {edad}");
    }
}

class Program
{
    static void Main()
    {
        // Creación de un objeto Persona y asignación de valores
        Persona persona1 = new Persona();
        persona1.nombre = "Juan";
        persona1.edad = 25;

        // Llamada al método MostrarInfo()
        persona1.MostrarInfo(); // Salida: Nombre: Juan, Edad: 25
    }
}
```
### 2.2 Clases

Una clase es el plano a partir del cual se determinan los atributos y métodos que contendrá un objeto. Esto permite reutilizar código para crear múltiples instancias del mismo objeto.

**Ejemplo**

Una empresa que tiene varios empleados. Cada empleado es un *objeto*, pero todos se crean a partir de una misma *clase* llamada `Empleado`.

#### Elementos en una clase

En una clase, el orden de los elementos presentes debe ser:

1. **Nombre de la clase**
2. **Atributos**
3. **Constructores**
4. **Funciones de interfaz (Getters y Setters)**
5. **Demás métodos**

#### Relaciones entre clases

En sistemas POO las clases no suelen trabajar de forma aislada, sino que estas se relacionan entre sí de diversas maneras para representar interacciones, dependencias y jerarquías. Estas relaciones ayudan a estructurar el código de forma más clara, reutilizable y mantenible.

Se entiende que una clase puede ser "propietaria" de otra cuando es responsable de su creación, gestión y eliminación. Además, algunas relaciones se consideran más "fuertes", ya que implican una mayor relación, mientras que otras son más "débiles", porque solo llevan a cabo una interacción temporal.

##### Dependencia - "usa"

Una clase depende de otra cuando utiliza temporalmente sus datos o comportamiento para cumplir una operación. La clase dependiente no necesita almacenar una referencia al objeto, solo usarlo mientras dura el método.

Se usa cuando una clase necesita ayuda de otra para ejecutar una acción puntual.

**Ejemplo en C#:**

Una `Impresora` *usa* un `Documento` para imprimir su contenido.

```csharp
class Documento
{
    public string Contenido { get; set; }
}

// Clase dependiente
class Impresora
{
    public void Imprimir(Documento doc)
    {
        Console.WriteLine("Imprimiendo: " + doc.Contenido);
    }
}
```

##### Asociación - "conoce a" o "trabaja con"

Una clase puede estar relacionada a otra mediante la referencia de uno de sus atributos. Sin embargo, esto no implica que una controle a la otra. Esta relación puede ser unidireccional o bidireccional.

Suele usarse cuando dos clases colaboran entre sí pero sin depender mutuamente una de la otra.

**Ejemplo en C#**

El `Profesor` *conoce a* un `Estudiante`, es decir, solo lo tiene de referencia.

```csharp
class Estudiante
{
    public string Nombre { get; set; }
}

class Profesor
{
    public Estudiante Alumno { get; set; }  // Asociación: conoce a Estudiante
}
```

##### Agregación - "tiene un" (Existe por separado)

Una clase puede contener objetos de otra clase, pero esos objetos pueden vivir por sí mismos fuera del contenedor.

Se puede usar para representar componentes que son parte de otros, pero que a su vez pueden existir de manera independiente.

**Ejemplo en C#**

Una `Universidad` *tiene* `Carrera`(s) pero podrían existir fuera de ella también, como en otra universidad diferente.

```csharp
class Carrera
{
    public string Nombre { get; set; }
}

class Universidad
{
    public List<Carrera> Carreras { get; set; } = new List<Carrera>();
}
```

##### Composición - "tiene un" (No existe por separado)

Una clase puede poseer objetos de otras clases, pero a diferencia de la agregación, estos no pueden existir independientemente, ya que si la clase contenedora desaparece, los objetos controlados también desaparecen.

Se suele usar cuando un objeto forma parte inseparable de otro y no tiene sentido que exista por si solo.

**Ejemplo en C#**

Una `Casa` *tiene* `Habitacion`(es), y estas solo pueden ser creadas y gestionadas por la misma `Casa`, por lo que no podrían estar fuera de ella.

```csharp
class Habitacion
{
    public int Numero { get; set; }
}

class Casa
{
    private List<Habitacion> habitaciones = new List<Habitacion>();

    public Casa()
    {
        habitaciones.Add(new Habitacion { Numero = 1 });
        habitaciones.Add(new Habitacion { Numero = 2 });
    }
}
```

##### Herencia - "es un"

Las clases pueden tener una relación jerárquica, donde una clase hereda los atributos y comportamientos de otra (Clase base y clase hija) con el fin de crear una clase más especializada.

Se usa la herencia cuando una clase comparte funcionalidad con otra pero también necesita comportamientos propios.

**Ejemplo en C#**

`Perro` *es un* `Animal` ya que hereda esa descripción y comportamientos, pero también añade los comportamientos propios de esa especie, como ladrar.

```csharp
class Animal
{
    public void Comer()
    {
        Console.WriteLine("El animal está comiendo.");
    }
}

class Perro : Animal
{
    public void Ladrar()
    {
        Console.WriteLine("Guau!");
    }
}
```

#### Tipos de clases

Así como existen diferentes formas en las que se relacionan las clases, también existen distintos tipos de clases según su propósito, restricciones y forma de implementación. Estos tipos permiten organizar el código de forma más clara, flexible y segura.

##### Clase concreta

Es la clase tradicional que se puede instanciar directamente. Contiene la implementación completa de todos sus métodos y puede heredar o ser heredada.

Se usa para crear objetos funcionales que representen entidades del sistema.

**Ejemplo en C#**

`Persona` es una clase funcional que se puede usar normalmente.

```csharp
class Persona
{
    public string Nombre { get; set; }

    public void Saludar()
    {
        Console.WriteLine($"Hola, soy {Nombre}");
    }
}
```

##### Clase abstracta

Una clase abstracta no puede ser instanciada directamente. Sirve como clase base para otras clases. Puede contener métodos abstractos (sin implementación) que deben ser definidos por las clases hijas, así como métodos normales.

Se usa para definir una estructura base común que otras clases deben completar y especializar.

**Ejemplo en C#**

`Animal` define lo general, `Perro` completa lo específico.

```csharp
abstract class Animal
{
    public abstract void HacerSonido();  // Método obligatorio sin implementar
    
    public void Dormir() => Console.WriteLine("Zzz...");
}

class Perro : Animal
{
    public override void HacerSonido()
    {
        Console.WriteLine("Guau!");
    }
}
```

##### Clase estática

Una clase estática no puede ser instanciada ni heredada. Todos sus miembros también deben ser `static`. Es decir, no trabaja con datos de objetos, sino que ofrece funciones o utilidades que se pueden usar directamente desde la clase.

Se utiliza para agrupar métodos que no necesitan mantener estado, como funciones matemáticas, validaciones, conversiones, u otras herramientas.

**Ejemplo en C#**

La clase `Calculadora` contiene métodos que se pueden usar sin necesidad de crear una instancia.

```csharp
static class Calculadora
{
    public static int Sumar(int a, int b) => a + b;
}

// Posible implementación en otra parte del programa
int resultado = Calculadora.Sumar(2, 3); // Salida: 8

// Implementación incorrecta
Calculadora calc = new Calculadora();
int resultado = calc.Sumar(3, 4);
```

##### Clase sellada

Una clase sellada no puede ser heredada. Esto impide que otras clases modifiquen o extiendan su comportamiento. También puede mejorar el rendimiento del sistema en tiempo de ejecución.

Se usa cuando se quiere proteger una clase para que nadie más la extienda o modifique, especialmente en bibliotecas, servicios, o clases críticas.

**Ejemplo en C#**

`Logger` registra los eventos en una aplicación. No queremos que alguien herede de ella y cambie la forma en que se registran los mensajes, como su formato, por lo que se crea como clase sellada.

```csharp
sealed class Logger
{
    public void LogInfo(string mensaje)
    {
        Console.WriteLine($"[INFO] {mensaje}");
    }

    public void LogError(string mensaje)
    {
        Console.WriteLine($"[ERROR] {mensaje}");
    }
}
```

##### Interfaz

Una interfaz garantiza que cualquier clase que la implemente tendrá cierto comportamiento, sin importar cómo lo haga, lo cual se define mediante un conjunto de métodos y propiedades sin implementación. Las clases que implementan la interfaz están obligadas a proporcionar su propia versión de esos miembros.

Se usa para definir contratos que distintas clases pueden implementar de manera diferente.

**Ejemplo en C#**

`Auto : IVehiculo` se compromete a implementar el comportamiento definido por la interfaz `IVehiculo`.

```csharp
interface IVehiculo
{
    void Encender();
}

class Auto : IVehiculo
{
    public void Encender()
    {
        Console.WriteLine("Auto encendido.");
    }
}
```

##### Clase parcial

Una clase parcial se puede dividir en varios archivos del mismo proyecto. Todos los fragmentos se unen en tiempo de compilación como si fuera una sola clase.

Se utiliza para organizar mejor el código, especialmente en proyectos grandes o con código generado automáticamente (como en Windows Forms), y el programador añade lógica personalizada en otro archivo.

**Ejemplo C#**

El compilador trata como una sola clase a los siguientes archivos:

Archivo `Persona.cs`

```csharp
public partial class Persona
{
    public string Nombre { get; set; }
}
```

Archivo `Persona.Saludo.cs`

```csharp
public partial class Persona
{
    public void Saludar() => Console.WriteLine($"Hola, soy {Nombre}");
}
```

##### Clase genérica

Una clase **genérica** permite trabajar con distintos tipos de datos sin duplicar código. Se define con un parámetro de tipo `<T>`, el cual se especifica al momento de crear una instancia.

Se suele utilizar para colecciones, contenedores, utilidades y estructuras reutilizables.

**Ejemplo en C#**

Se puede usar una instancia de `Caja` con cualquier tipo de dato.

```csharp
class Caja<T>
{
    public T Contenido { get; set; }
}

// Posibles implementaciones en el programa
Caja caja1 = new Caja<int> { Contenido = 100 }; 
Caja caja2 = new Caja<string> { Contenido = "Hola" };
```

#### Cardinalidad

Expresa las relaciones entre clases, mediante el número de entidades a las que otra entidad puede estar relacionada. Cada caso se puede dar según los requerimientos del sistema.

- **1 a 1**: Cada instancia de una clase se relaciona con **una sola** instancia de la otra clase. **Ejemplo**: Un `Docente` imparte **exactamente un** `Curso`, y ese `Curso` es impartido por **exactamente un** `Docente`.
- **1 a muchos**: Una instancia de una clase se relaciona con **múltiples** instancias de otra clase, pero no al revés. **Ejemplo:** Un `Docente` puede impartir **muchos** `Cursos`, pero cada `Curso` es impartido por **solo un** `Docente`.
- **Muchos a muchos**: Varias instancias de una clase se pueden relacionar con **varias** instancias de otra clase, y viceversa. **Ejemplo:** Un `Docente` puede impartir varios `Cursos`, y un mismo `Curso` puede ser impartido por varios `Docentes` (por ejemplo, en equipo).

### 2.3 Tipos de datos no primitivos

Los tipos de datos no primitivos son estructuras más complejas que los datos simples y se crean a partir de estos. Algunos de los tipos más comunes son:

- **Objetos**: Instancias de clases que combinan datos (atributos) y funcionalidades (métodos).
- **Arreglos (Arrays)**: Conjuntos de elementos del mismo tipo organizados de manera que cada valor se almacena en una posición específica identificada por un índice.
- **Matrices**: Son arreglos de dos o más dimensiones que organizan los datos en filas y columnas, permitiendo representar estructuras como tablas o gráficos.
- **Listas**: Son colecciones dinámicas de elementos, similares a los arreglos, pero con la diferencia de que pueden cambiar de tamaño y permiten agregar o eliminar datos con facilidad.

### 2.4 Documentación y buenas prácticas

#### Recomendaciones

- **Manejo de accesos**: Por defecto, se recomienda colocar cualquier dato como *privado*. En el caso de los constructores, se recomienda que siempre sean públicos salvo en casos especiales.
- **Creación de constructores**: Incluir un constructor si la clase tiene atributos.
- **Reducir el Scope o ámbito**: Los datos deben tener el ámbito lo más pequeño posible para facilitar la solución de errores.
- **Reducir la interdependencia**: Las clases deben ser concisas. Cambiar el código en una clase no debe afectar a otra clase. Los cambios en las interfases deben evitarse.
- **Abstraer código no portable**: Si tenemos código que no se puede llevar a otra plataforma, lo mejor es abstraerlo dentro de su propia clase.
- **Pensar en la persistencia**: Es importante pensar en la manera en la que se guardarán lo datos, ya sea en forma de un archivo en disco, en una base de datos relacional o en una base de datos orientada a objetos.
- **Código limpio y mantenible**: El código debe usar cada elemento de la forma adecuada. Se deben tener convenios (patrones) para nombrar cada elemento del código.

**Ejemplo código "sucio"**

```csharp
int a1, a2, a3;

while(true)
{
  a1++;
  a2 =  a1*3;
  a3 = a1+a2;
  if(a3>5)
     break;
}
```

Problemas:
- Varias variables declaradas en una misma línea y con nombres ambiguos.
- No se han inicializado las variables.
- Uso de un ciclo infinito con salida forzada, en lugar de usar la condición que provee.

#### Documentación del código

Se documenta el inicio de la clase, los atributos y los métodos.

**Ejemplos**

Para el inicio de las **clases** se puede usar este formato:

```csharp
/// Descripción breve.
/// Autor: AUTOR
/// Fecha: DD-MM-YY
/// Versión: 1.0.0
/// Modificación: DD-MM-YY
```

Para el inicio de los **métodos**:

```csharp
/// Descripción breve.
/// Autor: AUTOR
/// Fecha: DD-MM-YY
/// Versión: 1.0.0
/// Modificación: DD-MM-YY
/// <param name=""> </param>
/// <param name=""> </param>
/// <returns> </returns>
```

Para los **atributos**:

```csharp
private double resultado; // Descripción muy breve.
```

En el caso de elementos que estén dentro de los métodos, solo se documenta lo relevante, más no cada línea.

#### Diagrama de clases

Se usa para modelar la estructura de clases en la programación orientada a objetos. Muestra las clases, sus atributos, métodos y relaciones (herencia, asociación, composición, etc.).

![Plataformas Abiertas 1_05-06-2025-7.png](/imagenes/Plataformas%20Abiertas%201_05-06-2025-7.png)

Las relaciones entre clases se representan de diferente manera:

| **Relación**    | **Significado**                     | **Representación**                        |
| --------------- | ----------------------------------- | ----------------------------------------- |
| **Dependencia** | "Usa"                               | Línea punteada con flecha abierta `---->` |
| **Asociación**  | "Conoce a" / "Trabaja con"          | Línea continua con flechas abiertas `──>` |
| **Agregación**  | "Tiene un" (existe por separado)    | Línea con rombo blanco `----◊`            |
| **Composición** | "Tiene un" (no existe por separado) | Línea con rombo negro `----◆`             |
| **Herencia**    | "Es un"                             | Línea con flecha triangular vacía `──▷`   |

![Programación Orientada a Objetos_21-07-2025.png](/imagenes/Programaci%C3%B3n%20Orientada%20a%20Objetos_21-07-2025.png)

## III. Ciclo de vida de un objeto

### 3.1 Creación del objeto

#### Constructores

Los constructores son métodos especiales que se ejecutan automáticamente cuando se crea una instancia de una clase (objeto). Su función principal es inicializar el objeto, asignando valores iniciales a sus atributos si es necesario.

Algunas características clave son:

- Tienen el mismo nombre que la clase en la que está definido.
- No tienen un tipo de retorno (ni siquiera `void`).
- Suelen ser públicos para permitir la creación de instancias.
- Si no se programa un constructor explícitamente, algunos lenguajes como C# generan un constructor vacío por defecto (`default`) que invoca al constructor de la clase base y permite crear instancias sin inicializar valores específicos.
- Si nuestra clase tiene atributos es buena práctica incluir un constructor.

**Ejemplo en C#**

```csharp
class Persona
{
    // Atributos de la clase
    public string Nombre;
    public int Edad;

    // Constructor de la clase
    public Persona(string pNombre, int pEdad)
    {
        Nombre = pNombre;
        Edad = pEdad;
    }

    // Método para mostrar información
    public void MostrarInfo()
    {
        Console.WriteLine($"Nombre: {Nombre}, Edad: {Edad}");
    }
}
```

#### Instanciación

Un constructor es invocado cuando se utiliza el operador de instanciación `new`.

```csharp
class Program
{
    static void Main()
    {
        // Creación de un objeto Persona utilizando el constructor
        Persona persona1 = new Persona("Juan", 25);
        
		// Invocación del método MostrarInfo() con los parámetros del objeto persona1
        persona1.MostrarInfo(); // Salida: Nombre: Juan, Edad: 25
    }
}
```

##### Operadores de instanciación

Los operadores de instanciación se usan para crear nuevos objetos en memoria. Su propósito es asignar espacio y ejecutar el constructor de una clase o estructura para inicializarla. Gracias a estos operadores, podemos trabajar con objetos de manera flexible y reutilizar código fácilmente.

- **`new`**: Crea una nueva instancia de una clase, estructura, arreglo o delegado. Llama automáticamente al constructor de la clase o estructura.
  
  **Ejemplo en C#**

```csharp
Persona juan = new Persona();
int[] numeros = new int[5];
```

- **`typeof`**: Devuelve un objeto `Type` que representa un tipo en tiempo de ejecución. No crea una instancia, pero es útil para obtener información sobre un tipo.
  
  **Ejemplo en C#**

```csharp
Type tipoPersona = typeof(Persona);
```

- **`Activator.CreateInstance<T>()`**: Crea dinámicamente una instancia de una clase sin usar `new`. Útil cuando el tipo se desconoce en tiempo de compilación.
  
  **Ejemplo en C#**

```csharp
Persona juan = Activator.CreateInstance<Persona>();
```

- **`default`**: Asigna el valor predeterminado a un tipo. Para tipos de referencia, devuelve `null`. Para tipos de valor, devuelve `0`, `false` o equivalente.
  
  **Ejemplo en C#**

```csharp
Persona personaPorDefecto = default(Persona);  // null
int numero = default(int);  // 0
```

### 3.3 Uso del objeto

#### Acceso a atributos y métodos

Una vez que un objeto ha sido creado (instanciado), podemos acceder a sus atributos y métodos para realizar operaciones y manipular sus datos.

Se accede a los miembros de un objeto usando el operador punto (`.`).
Por ejemplo, si `persona1` es un objeto, `persona1.Nombre` accede al atributo `Nombre` y `persona1.MostrarInfo()` llama al método.

### 3.4 Alcance y duración del objeto

#### Variables de instancia y variables locales

- **Variables de instancia**: Existen mientras el objeto esté en memoria y pertenecen a cada instancia.
- **Variables locales**: Solo existen dentro del método donde se declaran y desaparecen al terminar la ejecución de ese método.

```csharp
class Animal
{
    string nombre; // Variable de instancia

    public void AsignarNombre()
    {
        string mensaje = "Nombre asignado"; // Variable local
        nombre = "Perro";
        Console.WriteLine(mensaje);
    }
}
```

### 3.5 Destrucción y gestión de memoria

En C#, la gestión de memoria es automática gracias al recolector de basura (GC), que elimina objetos cuando ya no se usan. No es necesario liberar memoria manualmente en la mayoría de los casos.

Para liberar recursos externos como archivos, conexiones o streams, se usa el patrón `Dispose()` junto con la palabra clave `using`. Esto garantiza que el recurso se cierre correctamente al terminar su uso.

**Ejemplo en C#**

```csharp
using (StreamReader lector = new StreamReader("archivo.txt"))
{
    string linea = lector.ReadLine();
    Console.WriteLine(linea);
} // Aquí se llama automáticamente a Dispose()
```

#### Destructores

Los destructores sirven para limpiar memoria, cerrar archivos, o finalizar cualquier cosa que lo requiera, y se invocan automáticamente cuando el objeto deja de existir. No todos los lenguajes lo implementan. Lleva el mismo nombre de la clase pero lleva `~` al inicio.

## IV. Mecanismos de POO

### 4.1 Encapsulación y acceso

La encapsulación es un principio fundamental de la POO que protege los datos dentro de un objeto y regula su acceso. Para lograrlo, se emplean los *controles de acceso*, los cuales determinan:

- **Visibilidad**: Define qué partes del código pueden acceder a los atributos y métodos.
- **Manipulación**: Controla cómo y cuándo los atributos de un objeto pueden modificarse.

El uso adecuado de estos controles permite garantizar que solo las partes autorizadas del código puedan interactuar con su contenido. Para ello, se deben comprender los *modificadores de acceso* y los métodos específicos que permiten acceder o modificar los datos de manera segura (*accessors* y *mutators*). 

#### Modificadores de acceso

Utilizando estos modificadores podemos indicar el tipo de acceso a los datos del programa. Estos se colocan antes de la declaración de la clase, atributo o método, y se pueden combinar según sea requerido.

- **Público (public)**: El exterior tiene acceso.
- **Privado (private)**: Solo el mismo objeto puede acceder.
- **Protegido (protected)**: Únicamente tienen acceso los objetos dentro de la cadena de herencia.
- **Estático (static)**: Indica que un atributo o método pertenece a una clase y puede ser utilizado por todas sus instancias.
- **Final (final)**: Vuelve inmutable a un elemento:
	- **En atributos**, evita que el valor cambie después de su inicialización.
	- **En métodos**, evita que sea sobrescrito por una clase heredada.
	- **En clases**, evita que la clase sea heredada.

#### Accessors

Por defecto, todos los atributos deben ser privados, por lo que para poder acceder a ellos se utilizan los accessors, los cuales permiten el acceso a los datos internos de un objeto por medio de reglas controladas. Pueden implementarse mediante métodos (*getters* y *setters* tradicionales) o *propiedades*:

##### Funciones de interfaz

- **Getters**: Métodos que devuelven el valor de un atributo.

**Ejemplo en C#**

Método que permite obtener el valor del atributo `edad`.

```csharp
public int getEdad() {
    return edad;
}
```

- **Setters**: Métodos que permiten asignar un nuevo valor a un atributo.

**Ejemplo en C#**

Método que permite asignar un nuevo valor al atributo `edad`, asegurando que solo se permita si `nuevaEdad` es mayor a `0`.

```csharp
public void setEdad(int nuevaEdad) {
    if (nuevaEdad > 0) {
        this.edad = nuevaEdad;
    }
}
```

##### Propiedades

Se suelen utilizar propiedades Getter y Setter en lugar de los métodos.

**Ejemplo en C#**

Método donde `get` permite obtener el valor de `edad`, mientras que el `set` permite modificar `edad` solo si `value` es mayor a `0`. `value` es una palabra asignada en C# que representa el valor que se intenta asignar.

```csharp
// Se declara la variable como private
private int edad;

// Se declara la propiedad como public para que pueda ser accesada. Se cambia a PascalCase.
public int Edad {
    get { return edad; }
    set { if (value > 0) edad = value; }
}
```

#### Mutators

Son aquellos métodos que permiten modificar progresivamente el estado interno del objeto. Aunque los setters también son mutators, no todos los mutators son setters.

**Ejemplo en C#**

Método que incrementa el valor de `saldo` sumando a este el valor de `cantidad`.

```csharp
public void depositar(double cantidad) {
	if (cantidad > 0)
	{
		saldo += cantidad;
	}
}
```

#### Ámbito o scope

El ámbito (scope) en POO define la zona del código donde una variable, atributo o método es accesible. Este concepto es esencial para controlar la visibilidad y el uso de los datos dentro de una clase o función.

En C#, el ámbito de una variable o método se define según dónde y cómo se declara:

- **Ámbito de variables locales**: Una variable declarada dentro de un método solo existe dentro de ese método y no puede ser accedida fuera de él.
- **Ámbito de atributos de clase**: Un atributo declarado dentro de una clase pero fuera de cualquier método puede ser accedido por los métodos de la misma clase y, dependiendo de su modificador de acceso, por otras clases.
- **Ámbito de parámetros**: Los parámetros de un método solo existen dentro del método donde fueron declarados y no pueden ser accedidos fuera de él.

**Ejemplo en C#**

Tenemos una clase `Coche` que almacena la marca de un automóvil. Usamos diferentes tipos de variables para demostrar cómo el ámbito (scope) afecta su uso. Esto ayuda a entender qué variables pueden usarse en distintos lugares del código y cuáles solo existen por un momento.

```csharp
class Coche
{
    // Variable de instancia (ámbito de clase)
    private string marca;

    // Método para asignar una marca al coche
    public void AsignarMarca(string nuevaMarca)
    {
        // Variable local (solo existe dentro de este método)
        string mensaje = "Marca asignada correctamente.";

        // Asignamos el valor del parámetro a la variable de instancia
        marca = nuevaMarca;

        // Mostramos el mensaje
        Console.WriteLine(mensaje);
    }

    // Método para obtener la marca del coche
    public string ObtenerMarca()
    {
        return marca;
    }
}

class Program
{
    static void Main()
    {
        Coche miCoche = new Coche();

        // Llamamos al método y pasamos un parámetro
        miCoche.AsignarMarca("Toyota");

        // Mostramos la marca asignada
        Console.WriteLine("La marca del coche es: " + miCoche.ObtenerMarca());
    }
}
```

##### This

Cuando una variable local o un parámetro de método tiene el mismo nombre que un atributo de clase, se puede usar la palabra clave `this` para diferenciar entre ambos.

**Ejemplo en C#**

```csharp
class Coche
{
    private string marca;

    public void AsignarMarca(string marca)
    {
        // Sin this: se refiere al parámetro
        // Con this: se refiere al atributo de la instancia
        this.marca = marca;
    }
}
```

##### Static

La palabra clave `static` se utiliza para declarar atributos o métodos que pertenecen a la clase y a todas sus instancias y se puede acceder a él sin crear un objeto de la clase.


```csharp
class Contador
{
    // Atributo estático compartido por todos los objetos
    public static int totalObjetos = 0;

    public Contador()
    {
        // Al crear una nueva instancia, incrementamos el contador compartido
        totalObjetos++;
    }

    public static void MostrarTotal()
    {
        Console.WriteLine("Total de objetos creados: " + totalObjetos);
    }
}
```

```csharp
class Program
{
    static void Main()
    {
        Contador c1 = new Contador();
        Contador c2 = new Contador();

        // Llamamos a un método estático sin crear una instancia
        Contador.MostrarTotal(); // Output: Total de objetos creados: 2
    }
}

```

### 4.2 Abstracción e interfaces propias

La abstracción es un principio que permite mostrar solo los elementos esenciales de un objeto al usuario final, ocultando los detalles internos de su implementación. En otras palabras, se enfoca en "qué hace" un objeto en lugar de "cómo lo hace", facilitando su uso para el usuario final sin necesidad de que conozca su funcionamiento interno. Un mecanismo clave para lograr la abstracción son las *interfaces*.

#### Interfaz propia

La interfaz es la forma fundamental de comunicación entre objetos, la cual es compuesta por aquellos atributos y métodos que necesitamos mostrar al exterior, y es aquella que define cómo los usuarios finales de esa clase/objeto interactúan con ella. Algunas características importantes son:

- Podemos empezar una clase sin interfaz y sólo crearla si es necesario. La interfaz debe ser mínima.
- Hay que tomar en cuenta quién es el usuario y sus necesidades.
- La interfaz incluye la sintaxis para invocar al método y saber lo que regresa.
- Requiere de una *implementación* para ser efectiva.

**Ejemplo en C#**

La interfaz declara el método `HacerSonido()`, pero no dice cómo debe hacerlo.

```csharp

public interface IAnimal
{
    void HacerSonido(); // Solo se declara, sin implementación
}

```

##### Implementación

Para que una clase esté bien construida se requiere la interfaz y la implementación. Mientras que la interfaz define un método pero no el cómo, la implementación define cómo funcionan esos métodos.

**Ejemplo en C#**

Aquí la clase `Perro` implementa la interfaz `IAnimal` y le da su propio comportamiento.

```csharp

public class Perro : IAnimal //Implementa la interfaz
{
	// Se define el comportamiento
    public void HacerSonido() {
        Console.WriteLine("¡Guau!");
    }
}

```

Aquí la clase `Gato` implementa la interfaz `IAnimal` y le da su propio comportamiento.

```csharp

public class Gato : IAnimal //Implementa la interfaz
{
	// Se define el comportamiento
    public void HacerSonido() {
        Console.WriteLine("¡Miau!");
    }
}

```

Ahora creamos un objeto `Perro` y llamamos su método `HacerSonido()`. Hacemos lo mismo con un objeto `Gato` Esto es la aplicación de la interfaz y la implementación.

```csharp

class Program
{
    static void Main()
    {
		// Se crea un objeto de la clase Perro dentro de una variable de tipo IAnimal llamada Tomasina.
        IAnimal Tomasina = new Perro();
	    // Se aplica la interfaz e implementación. Salida: ¡Guau!
        Tomasina.HacerSonido();

		// Se crea un objeto de la clase Gato dentro de una variable de tipo IAnimal llamada Selina.
        IAnimal Selina = new Gato();
	    // Se aplica la interfaz e implementación. Salida: ¡Miau!
        Selina.HacerSonido();
    }
}

```

### 4.3 Herencia y especialización

La herencia es una característica esencial en la reutilización de código, ya que permite que una clase herede el contenido de otra, es decir, permite que una clase aproveche los atributos y métodos de una ya existente sin tener que repetir el código, sino únicamente adicionando lo que le falte.

Al aplicar la herencia, se define primero la *clase principal*, que será la más abstracta, es decir, la que establece la estructura general sin implementar todos los detalles. Por su parte, las *clases heredadas*, más concretas, se encargan de implementar los detalles específicos del objeto.

Algunos lenguajes permiten la *herencia múltiple*, donde una clase hereda de más de una clase principal. Sin embargo, puede generar conflictos y aumentar la complejidad, por lo que lenguajes como C# y Java no la admiten y usan *interfaces* en su lugar.

#### Jerarquía de clases

- **Superclase (Clase padre)**: Contiene todos los atributos y métodos que son comunes a las clases que descienden de ella. *Ej.* Persona.
- **Subclase (Clase hija)**: Es una extensión de la superclase, donde toma toda su información de esta y adiciona lo propio. *Ej.* Persona --> Empleado.

La relación "es-un" describe cómo se establece la herencia entre clases, ya que una clase hija hereda características y comportamientos de una clase padre.

### 4.4 Polimorfismo dinámico y estático

El polimorfismo es la capacidad que tiene un método para comportarse de distintas maneras según el objeto que lo esté usando.

Existen dos tipos:

- **Polimorfismo dinámico**: El método se decide cuando el programa se está ejecutando, es decir, el programa elige qué método ejecutar mientras está corriendo.
- **Polimorfismo estático**: El método se elige antes de que el programa se ejecute, al compilar, es decir, el compilador elige cuál versión del método usar al momento de traducir el código.

#### Sobreescritura (Overriding)

Es la técnica por la cual una subclase reemplaza la implementación de un método heredado de su clase padre, sin cambiar la estructura original.

Esto es útil porque las subclases pueden mantener la misma interfaz, pero con un comportamiento propio según sus necesidades.

La sobreescritura requiere de la herencia y se considera *dinámica* porque ocurre en el tiempo de ejecución.

**Ejemplo**

Se tiene una superclase llamada `Animal` con un método `HacerSonido()`. Cada subclase (como `Perro` o `Gato`) hereda este método, pero lo implementa de manera distinta:

- `Perro.HacerSonido()` → 🐶 "¡Guau!"
- `Gato.HacerSonido()` → 🐱 "¡Miau!"

#### Sobrecarga (Overloading)

Ocurre cuando hay varios métodos con el mismo nombre, pero con diferentes parámetros. El compilador decide cuál método usar dependiendo de los argumentos.

La sobrecarga no requiere de la herencia y se considera *estática* porque ocurre en el tiempo de compilación.

##### Sobrecarga de métodos

La sobrecarga de métodos permite definir varios métodos con el mismo nombre, pero con diferentes parámetros. Esto permite flexibilidad, ya que se pueden usar diferentes versiones del método según la necesidad.

**Reglas de sobrecarga**:

1. Deben tener el mismo nombre.
2. Deben diferenciarse por el número o tipo de parámetros.
3. No pueden diferenciarse solo por el tipo de retorno.

**Ejemplo en C#**

```csharp
class Calculadora
{
    // Método para sumar dos números enteros
    public int Sumar(int a, int b)
    {
        return a + b;
    }

    // Sobrecarga del método para sumar tres números
    public int Sumar(int a, int b, int c)
    {
        return a + b + c;
    }
}

class Program
{
    static void Main()
    {
        Calculadora calc = new Calculadora();

        // Uso del método con dos parámetros
        Console.WriteLine(calc.Sumar(3, 5)); // Salida: 8

        // Uso del método sobrecargado con tres parámetros
        Console.WriteLine(calc.Sumar(3, 5, 2)); // Salida: 10
    }
}
```

##### Sobrecarga de constructores

La sobrecarga implica tener más de una versión del constructor, diferenciándolos por la cantidad y tipo de parámetros que reciben. Esto nos da flexibilidad al instanciar objetos, ya que se pueden crear con diferentes niveles de información según las necesidades del programa.

**Ejemplo en C#**

```csharp
class Persona
{
    private string nombre;
    private int edad;

    // Constructor con dos parámetros
    public Persona(string nombre, int edad)
    {
        this.nombre = nombre;
        this.edad = edad;
    }

    // Constructor con solo el nombre (edad por defecto)
    public Persona(string nombre)
    {
        this.nombre = nombre;
        this.edad = 0; // Valor por defecto
    }

    public void MostrarInfo()
    {
        Console.WriteLine($"Nombre: {nombre}, Edad: {edad}");
    }
}

class Program
{
    static void Main()
    {
        // Usando el constructor con nombre y edad
        Persona persona1 = new Persona("Juan", 25);
        persona1.MostrarInfo(); // Salida: Nombre: Juan, Edad: 25

        // Usando el constructor con solo el nombre
        Persona persona2 = new Persona("Ana");
        persona2.MostrarInfo(); // Salida: Nombre: Ana, Edad: 0
    }
}
```

##### Sobrecarga de operadores

La sobrecarga de operadores es una técnica que permite redefinir el comportamiento de operadores ( \+,  \-,  \*,  \==, etc.) cuando se usan con objetos de una clase personalizada, más no reemplaza su función original en el programa. Es decir, en lugar de recurrir a métodos tradicionales para realizar ciertas operaciones, la sobrecarga permite que los objetos interactúen de forma más intuitiva, como si estos fueran tipos de datos sencillos.

La sobrecarga de operadores se usa cuando queremos que las operaciones con objetos sean más naturales en lugar de depender de métodos específicos. Sin embargo, no todos los operadores son sobrecargables, y su abuso puede hacer que el código sea menos claro si no se usan adecuadamente.

Sus características principales son:

- El significado de un operador puede cambiar según los tipos de datos que opera.
- Se puede definir el comportamiento de los operadores para que actúen sobre nuestros propios tipos.
- No todos los lenguajes de programación permiten la sobrecarga de operadores.
- La sobrecarga debe ser implementada de manera que mantenga la lógica esperada del operador y no genere confusión.

**Ejemplo en C#**

Vamos a sobrecargar el operador `+` para que pueda sumar dos objetos `Punto`, combinando sus coordenadas `x` e `y`. Sin esta sobrecarga, `PuntoA + PuntoB` daría error, pero al definir su comportamiento, podemos hacer que devuelva un nuevo punto con la suma de las coordenadas.

```csharp
class Punto
{
    // Propiedades para almacenar las coordenadas X e Y
    public int X { get; set; }
    public int Y { get; set; }

    // Constructor que inicializa un punto con valores X e Y
    public Punto(int x, int y)
    {
        X = x;
        Y = y;
    }

    // Sobrecarga del operador + para sumar dos objetos Punto
    public static Punto operator +(Punto a, Punto b)
    {
        // Devuelve un nuevo Punto con la suma de las coordenadas
        return new Punto(a.X + b.X, a.Y + b.Y);
    }

    // Método para mostrar el punto en consola
    public void Mostrar()
    {
        Console.WriteLine($"Punto ({X}, {Y})");
    }
}

class Program
{
    static void Main()
    {
        // Creación de dos objetos Punto
        Punto p1 = new Punto(2, 3);
        Punto p2 = new Punto(4, 5);
        
        // Uso de la sobrecarga del operador + para sumar los puntos
        Punto resultado = p1 + p2; // Equivalente a resultado = new Punto(6, 8);

        // Muestra el resultado en consola
        resultado.Mostrar(); // Salida: Punto (6, 8)
    }
}
```

###### Sobrecarga de operadores aritméticos

- **`+` (suma)** → Puede sumar dos objetos, como combinar coordenadas de dos puntos o concatenar información personalizada.
  **Ejemplo**: `VectorA + VectorB` suma sus componentes y devuelve un nuevo vector.
- **`-` (resta)** → Puede definir una diferencia entre objetos, como restar valores de dos cuentas bancarias.
  **Ejemplo**: `CuentaA - CuentaB` podría calcular la diferencia de saldo.
- **`*` (multiplicación)** → Puede escalar objetos, como multiplicar un vector por un número.
  **Ejemplo**: `Vector * 2` duplica sus valores.
- **`/` (división)** → Puede definir una relación entre objetos, como dividir un objeto en partes.
  Ejemplo: `Pizza / 4` podría representar repartir la pizza en 4 porciones.

###### Sobrecarga de operadores de comparación

- **\== (igualdad)** → Compara si dos objetos son equivalentes según sus atributos.
  **Ejemplo**: `PersonaA` \== `PersonaB` podría verificar si tienen el mismo nombre y edad.
- **\!= (desigualdad)** → Verifica si dos objetos son distintos.
  **Ejemplo**: `AutoA` \!= `AutoB` podría comparar si tienen diferentes placas.
- ** \< y  \> (menor o mayor que)** → Permiten comparar objetos según un criterio específico.
  **Ejemplo**: `EmpleadoA > EmpleadoB` podría significar que gana más salario.

###### Sobrecarga de operadores de incremento/decremento

- **`++` (incremento)** → Puede aumentar el valor de un objeto.
  **Ejemplo**: `Nivel++` podría aumentar el nivel de un personaje en un juego.
- **`--` (decremento)** → Puede reducir el valor de un objeto.
  **Ejemplo**: `Cupo--` podría disminuir la cantidad de espacios disponibles en un evento.

###### Sobrecarga de operadores de conversión

- **`explicit` / `implicit`** → Permiten convertir un objeto en otro tipo.
  **Ejemplo**: `Producto` podría convertirse en `string` para mostrar su nombre en una factura.

### 4.5 Composición

La composición es un principio en el que un objeto está formado por otros objetos, estableciendo una relación de dependencia entre ellos. En programación, este enfoque nos ayuda a la reutilización de código y la modularidad, permitiéndonos construir clases complejas combinando múltiples clases más pequeñas y especializadas.

La relación "tiene-un" describe cómo se establece la composición entre clases, ya que un objeto posee o contiene otros objetos en su interior.

#### Decoración

Es un patrón de diseño que permite envolver un objeto en tiempo de ejecución con otro objeto para extender o modificar su comportamiento sin tener que crear otras sub clases.

También se definen dos tipos de decoradores:

- **Decorador base**: Clase que implementa la misma interfaz que el componente original y contiene una referencia al objeto que se desea decorar.
- **Decorador concreto**: Clase que extiende al decorador base y agrega funcionalidades específicas.

- Interfaz
	- Clase Base
		- Decorador base
			- Decorador conceto

## V. Estructuras de datos abstractos

En POO, son modelos que permiten organizar y gestionar datos de manera eficiente. Estas estructuras permiten almacenar objetos y manipularlos según ciertas reglas de acceso y recorrido.

### 5.1 Estructuras de datos lineales

Son aquellas estructuras donde los elementos están organizados de forma secuencial, uno después del otro.

#### Arreglo (Array)

Un arreglo es una colección de tamaño fijo que almacena elementos del mismo tipo en posiciones contiguas de memoria. A diferencia de estructuras como las listas, los arreglos no pueden crecer o reducirse después de su creación. Además, el índice con el que inicia es 0.

Se usa cuando se conoce el número exacto de elementos y no se necesita cambiar su tamaño, como al tener registros fijos.

**Ejemplo en C#**

Se crea un arreglo con tres enteros. Si quieres acceder al segundo elemento: `numeros[1]` devuelve `20`.

```csharp
int[] numeros = new int[3] { 10, 20, 30 };
```

##### Referenciar objetos

Un arreglo también puede contener objetos. Al acceder a un elemento se obtiene una referencia, no una copia.

```csharp
CAuto miAuto = miTienda[1];
// miAuto apunta al mismo objeto que está en el índice 1 del arreglo
```

Esto significa que si se modifica `miAuto`, también se está modificando `miTienda[1]`, porque ambos apuntan al mismo espacio en memoria.

##### Indexer

Es una especie de propiedad para arreglos, que permite acceder a una colección. En C#, solo se puede tener uno por clase. Colocar un indexer nos permite poner el arreglo en privado.

**Ejemplo en C#**

Implementación del indexer.

```csharp
class TiendaAutos
{
    private CAuto[] autos = new CAuto[10];

    public CAuto this[int i]
    {
        get => autos[i];
        set => autos[i] = value;
    }
}

// Esto permite ocultar directamente el arreglo autos y accederlo desde fuera con:
CAuto miAuto = tienda[2];
```

#### Lista Ligada (Linked List)

Una lista ligada es una colección donde cada elemento (nodo) apunta al siguiente. No hay acceso directo por índice, sino que se recorre desde el inicio.

Se usa cuando necesitas insertar o eliminar elementos frecuentemente en cualquier parte de la lista.

**Ejemplo en C#**

Se crea una lista ligada de nombres. En este caso el recorrido se hace con un ciclo.

```csharp
LinkedList<string> nombres = new LinkedList<string>();
nombres.AddLast("Ana");
nombres.AddFirst("Luis");

foreach (var nombre in nombres)
{
    Console.WriteLine(nombre);
}
// Salida: Luis, Ana
```

#### Pila (Stack)

Una pila es una estructura donde el último elemento en entrar es el primero en salir (Last In, First Out).

Se usa para manejar flujos reversibles, como en el caso de un historial de navegación.

**Ejemplo en C#**

Se agregan dos elementos a la pila por medio de `Push()`, mientras que `Pop()` elimina de la pila al último que entró y la guarda en la variable `actual`.

```csharp
Stack<string> historial = new Stack<string>();
historial.Push("Página1");
historial.Push("Página2");

string actual = historial.Pop(); // Página2
Console.WriteLine(actual);
```

#### Cola (Queue)

Una cola es una estructura donde el primer elemento en entrar es el primero en salir (First In, First Out).

Se usa cuando se necesitan procesar elementos en el orden en que llegaron, como en colas de impresión, tickets de atención a clientes, etc.

**Ejemplo en C#**

Se agregan dos tareas a la cola. Al hacer `Dequeue()`, se extrae la primera tarea ingresada ("Tarea1"), eliminándola de la cola, respetando el orden en el que llegaron.

```csharp
Queue<string> tareas = new Queue<string>();
tareas.Enqueue("Tarea1");
tareas.Enqueue("Tarea2");

string siguiente = tareas.Dequeue(); // Tarea1
Console.WriteLine(siguiente);
```

#### Hash tables (Diccionarios, Maps)

Una tabla hash almacena datos en pares clave-valor. Internamente, usa una función hash que permite localizar rápidamente un valor a partir de su clave.

Se usa para buscar datos rápidamente mediante una clave única, como directorios, catálogos, etc.

**Ejemplo en C#**

Se crea un diccionario donde las claves son nombres y los valores son edades. Al pedir `edades["Ana"]`, se accede directamente al valor 30 sin necesidad de recorrer toda la colección.

```csharp
Dictionary<string, int> edades = new Dictionary<string, int>();
edades["Juan"] = 25;
edades["Ana"] = 30;

Console.WriteLine(edades["Ana"]); // 30
```

### 5.2 Estructura de datos no lineales

Estas estructuras no siguen un orden secuencial, y permiten representar relaciones más complejas entre elementos.

#### Árbol (Tree)

Un árbol es una estructura jerárquica donde cada nodo puede tener múltiples hijos, pero solo un padre. Existen varios tipos.

Se usa en sistemas jerárquicos como menús, organización de archivos, árboles de decisiones, etc.

**Ejemplo en C#**

Se crea un árbol binario manualmente, con un nodo raíz que tiene dos hijos: uno a la izquierda con valor 5 y otro a la derecha con valor 15. Cada nodo puede expandirse.

```csharp
class Nodo
{
    public int Valor;
    public Nodo Izquierda;
    public Nodo Derecha;
}

Nodo raiz = new Nodo { Valor = 10 };
raiz.Izquierda = new Nodo { Valor = 5 };
raiz.Derecha = new Nodo { Valor = 15 };

```

#### Grafo

Un grafo es una estructura formada por nodos (vértices) y conexiones (aristas). Representa relaciones complejas entre elementos.

Se usa para representar mapas, relaciones entre entidades, etc.

**Ejemplo en C#**

Se construye un grafo no dirigido: el nodo "A" está conectado a "B" y "C", y "B" también conecta con "A" y "D". Se usa un diccionario donde cada nodo tiene una lista de vecinos.

```csharp
Dictionary<string, List<string>> grafo = new Dictionary<string, List<string>>();
grafo["A"] = new List<string> { "B", "C" };
grafo["B"] = new List<string> { "A", "D" };
```

## VI. Manejo de datos en POO

Es común que los objetos contengan información importante que debe conservarse incluso después de que el programa finaliza. Para lograr esto se aplican técnicas como la serialización, que permiten guardar y recuperar el estado de los objetos desde archivos. Esto hace posible mantener configuraciones o datos entre ejecuciones, así como permitir que la información se comparta fácilmente entre distintos sistemas o plataformas.

### Persistencia

En POO, la persistencia se refiere a guardar el estado de un objeto para luego reconstruirlo cuando se necesite. Es decir, permite que los datos de un programa no se pierdan cuando el programa finaliza.

### Serialización Binaria (POO)

La serialización binaria convierte un objeto en una secuencia de bytes, que puede almacenarse en un archivo o enviarse a través de la red. Posteriormente, puede recuperarse mediante deserialización, restaurando el estado exacto del objeto.

Solo puede ser interpretado por sistemas que conozcan su estructura interna, ya que no está en un formato legible.
### Serialización con XML (Programación estructurada)

La serialización XML convierte un objeto en texto legible, utilizando etiquetas `<xml>`. Es una forma estructurada y estandarizada, útil para la portabilidad con otros sistemas o lenguajes.

La desventaja es que cualquiera puede abrir el archivo y modificarlo, por lo que tiene menor seguridad por default.

#### Serialización normal con XML

Este tipo de serialización toma un objeto único y lo transforma en un archivo XML plano. Solo se guarda el estado de una instancia y no incluye relaciones con otros objetos.
#### Serialización por composición con XML

Este enfoque permite serializar un objeto compuesto por otros objetos, reflejando sus relaciones en POO.

### Deserialización

La deserialización es el proceso inverso: convertir los datos almacenados (binarios o XML) de nuevo en objetos en memoria. Esto permite recuperar el estado original del objeto y seguir trabajando con él en el programa.

## VII. Patrones de diseño en POO

Un patrón de diseño es una solución reutilizable, comprobada y estructurada a un problema común que aparece constantemente al diseñar sistemas orientados a objetos.

Básicamente, son guías o plantillas que ayudan a resolver un problema específico de diseño.

**Sus elementos son**

- **Nombre**: Forma de referirse al patrón de diseño.
- **Problema**: Explica cuándo debe usarse el patrón.
- **La solución**: Describe la estructura general, las clases involucradas, las relaciones entre ellas y cómo colaboran para resolver el problema.
- **Las consecuencias**: Analiza el impacto del patrón, tomando en cuenta el costo/beneficio, espacio/tiempo, lenguaje, impacto en flexibilidad, extensión y portabilidad.

Los patrones de diseño se agrupan en tres categorías, según el tipo de problema que ayudan a resolver.
### 7.1 Patrones de creación

Se enfocan en cómo se crean los objetos. Permiten crear instancias de forma flexible.

- **Fábrica abstracta**: Permite crear objetos relacionados sin especificar sus clases concretas.
- **Método fábrica**: Delega la creación de objetos a una subclase.
- **Prototipo**: Clona objetos a partir de una instancia de prototipo existente.
- **Singleton**: Asegura que solo exista una instancia de una clase y provee un punto de acceso global.

### 7.2 Patrones de estructura

Ayudan a organizar las clases u objetos en estructuras más grandes sin perder flexibilidad. Mejoran la reutilización de componentes.

- **Adaptador**: Convierte la interfaz de una clase en otra esperada por el cliente.
- **Puente**: Separa una abstracción de su implementación para que ambas puedan variar.
- **Decorador**: Añade funcionalidades a un objeto de forma dinámica sin modificar su clase.
- **Fachada**: Proporciona una interfaz simplificada a un conjunto complejo de clases.
- **Proxy**: Controla el acceso a un objeto, actuando como intermediario.

### 7.3 Patrones de comportamiento

Ayudan a definir la comunicación entre objetos en el sistema y cómo es controlado el flujo.

- **Comando**: Encapsula una solicitud como un objeto, permitiendo parametrizar y deshacer operaciones.
- **Interprete**: Define una gramática y un intérprete para entender y procesar expresiones.
- **Iterador**: Permite recorrer una colección sin exponer su implementación interna.
- **Observador**: Notifica automáticamente a múltiples objetos cuando el estado de otro cambia.
- **Estrategia**: Permite definir una familia de algoritmos y seleccionarlos dinámicamente.

### 7.4 Anti-patrones

Los anti-patrones representan malas soluciones que se aplican comúnmente a problemas de diseño, pero que resultan en malos resultados.

- Muestran prácticas que parecen buenas al inicio, pero fallan a largo plazo.
- También incluyen recomendaciones sobre cómo salir de una mala implementación hacia una solución más adecuada.

## VIII. POO y la programación orientada a eventos

La Programación Orientada a Eventos (POE) es un paradigma que se basa en la interacción con eventos, es decir, acciones que ocurren en el sistema, como hacer clic en un botón, mover el mouse, o recibir una notificación externa.

Cuando se combina con la Programación Orientada a Objetos (POO), permite crear aplicaciones interactivas donde los objetos pueden reaccionar a eventos. Este enfoque es común en interfaces gráficas de usuario y en sistemas donde las acciones del usuario determinan el flujo del programa como videojuegos.

### 8.1 Interfaces gráficas y eventos

En las interfaces gráficas, los eventos son disparados por acciones del usuario (clicks, teclas, movimientos), y se puede programar la reacción del sistema usando manejadores de eventos.

#### Eventos

Un evento es un mecanismo que permite que un objeto notifique a otros objetos cuando algo relevante ocurre.

En C#, los eventos se basan en delegados. Un evento necesita:

- **Un delegado** que define la firma del método que responderá al evento.
- **Un evento** declarado con la palabra clave event.
- **Uno o varios manejadores (handlers)** que se suscriben al evento.

#### Delegados

Un delegado es una especie de puntero a función, que define qué tipo de métodos se pueden invocar a través del evento.

#### Handlers

Un handler es un método que responde a un evento. Se suscribe a un evento y se ejecuta automáticamente cuando ese evento ocurre.

#### Sinks

Un sink es un término técnico usado para referirse al objeto que recibe el evento. Es decir, es el receptor del evento. También se puede considerar sink a la clase que contiene los handlers suscritos al evento.

### 8.2 Excepciones y manejo de errores

Las excepciones son eventos inesperados que ocurren durante la ejecución de un programa y pueden interrumpir su funcionamiento normal. Para evitar que el programa falle, se utiliza un mecanismo de *manejo de excepciones*.

El manejo de excepciones se realiza con los bloques `try...catch`, que permiten identificar y manejar errores de manera controlada, y se utilizan  cuando no se puede evitar el error con una validación como es el caso al leer un archivo, tener falta de memoria, acceder a una base de datos o convertir datos de entrada del usuario, etc.

Es recomendable colocar una excepción en secciones del código que identifiquemos como riesgosas como en zonas de apertura de archivos o comunicación red.

**Ejemplo en C#**

Se maneja una división por cero para evitar que el programa se detenga.

```csharp
class Program
{
    static void Main()
    {
	    // Código que podría generar una excepción
        try
		{
		    int numero = int.Parse(Console.ReadLine()); // Puede fallar si el usuario ingresa texto
		    Console.WriteLine("Número ingresado: " + numero);
		}
		
		// Código para manejar la excepción
		catch (FormatException)
		{
		    Console.WriteLine("Error: Entrada no válida.");
		}
    }
}
```

---

## / Más Información

**Anterior**: `[[Conceptos Generales de Programación]]`

### Lenguajes de programación

- `[[C Sharp]]`
- `[[Java]]`
- `[[JavaScript]]`
- `[[Python]]`

---