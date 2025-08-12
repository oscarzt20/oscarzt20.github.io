---
Title: Programación IV - Conceptos Básicos de POO
Fecha: 2025-08-08
Hora: 01:54
tags: ['enciclopedia', 'post']
---

---

## I. Conceptos básicos de POO

### 1.1 Objetos

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

#### Ciclo de vida de un objeto

##### Creación del objeto

###### Constructores

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

###### Instanciación

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

###### Operadores de instanciación

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

##### Uso del objeto

###### Acceso a atributos y métodos

Una vez que un objeto ha sido creado (instanciado), podemos acceder a sus atributos y métodos para realizar operaciones y manipular sus datos.

Se accede a los miembros de un objeto usando el operador punto (`.`).
Por ejemplo, si `persona1` es un objeto, `persona1.Nombre` accede al atributo `Nombre` y `persona1.MostrarInfo()` llama al método.

##### Alcance y duración del objeto

###### Variables de instancia y variables locales

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

##### Destrucción y gestión de memoria

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

###### Destructores

Los destructores sirven para limpiar memoria, cerrar archivos, o finalizar cualquier cosa que lo requiera, y se invocan automáticamente cuando el objeto deja de existir. No todos los lenguajes lo implementan. Lleva el mismo nombre de la clase pero lleva `~` al inicio.

### 1.2 Clases

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

### 1.3 Tipos de datos no primitivos

Los tipos de datos no primitivos son estructuras más complejas que los datos simples y se crean a partir de estos. Algunos de los tipos más comunes son:

- **Objetos**: Instancias de clases que combinan datos (atributos) y funcionalidades (métodos).
- **Arreglos (Arrays)**: Conjuntos de elementos del mismo tipo organizados de manera que cada valor se almacena en una posición específica identificada por un índice.
- **Matrices**: Son arreglos de dos o más dimensiones que organizan los datos en filas y columnas, permitiendo representar estructuras como tablas o gráficos.
- **Listas**: Son colecciones dinámicas de elementos, similares a los arreglos, pero con la diferencia de que pueden cambiar de tamaño y permiten agregar o eliminar datos con facilidad.

---

## / Más Información

- [Programación I - Algoritmos](/apuntes/programación-i---algoritmos/)
- [Programación II - Conceptos Básicos](/apuntes/programación-ii---conceptos-básicos/)
- [Programación III - Introducción a la Programación Orientada a Objetos](/apuntes/programación-iii---introducción-a-la-programación-orientada-a-objetos/)
- [Programación IV - Conceptos Básicos de POO](/apuntes/programación-iv---conceptos-básicos-de-poo/)
- [Programación V - Mecanismos de POO](/apuntes/programación-v---mecanismos-de-poo/)
- [Programación VI - Estructuras de Datos Abstractos](/apuntes/programación-vi---estructuras-de-datos-abstractos/)
- [Programación VII - Manejo de Datos](/apuntes/programación-vii---manejo-de-datos/)
- [Programación VIII - POO y la Programación Orientada a Eventos](/apuntes/programación-viii---poo-y-la-programación-orientada-a-eventos/)
- [Programación IX - Patrones de Diseño](/apuntes/programación-ix---patrones-de-diseño/)
- [Programación - Guías Documentación y Buenas Prácticas](/apuntes/programación---guías-documentación-y-buenas-prácticas/)

---