---
Date: 2025-08-08
Time: 01:54
tags:
- enciclopedia
- aprenderProgramacion
slug: programacion-iv-elementos-de-poo
title: Programación IV - Elementos de POO
---

---

La POO nos ofrece una manera de pensar que se asemeja más al mundo real. En este enfoque, las *clases* describen cómo es algo y qué puede hacer, mientras que los *objetos* son las cosas que creamos a partir de esa descripción.

Comprender cómo funcionan y se relacionan los objetos y las clases es esencial, porque gracias a ellos podemos construir programas organizados en partes que cooperan entre sí.

Por ejemplo: Una *clase* `Libro` define que todo libro tiene un `Título` y un `Autor`, y que puede `Abrir()` o `Cerrar()`. Cada libro que creemos a partir de esa clase será un *objeto* con su propio título y autor, pero que tiene las mismas funciones que cualquier otro libro.

## I. Clases

Una clase es el plano que describe un tipo de objeto. Dentro de ella, se determinan los atributos y métodos que contendrá.

Cuando usamos ese plano para crear algo concreto, tenemos un objeto.

Gracias a este mecanismo podemos crear múltiples representaciones (instancias) de la misma clase, reutilizando código y manteniendo consistencia.

### 1.1 Elementos en una clase

En una clase, el orden de los elementos presentes debe ser:

1. **Nombre de la clase**: Cómo se llamará el molde.
2. **Atributos**: Datos que describen al objeto.
3. **Constructores**: Formas de crear el objeto e inicializarlo.
4. **Funciones de interfaz (Getters y Setters)**: Métodos para acceder o modificar atributos de manera controlada.
5. **Demás métodos**: Acciones que el objeto puede realizar.

**Ejemplo en C#**:

En una empresa existen varios empleados. Todos los empleados son distintos, pero todos provienen de una misma clase llamada `Empleado`, que define qué datos y acciones tiene cualquier empleado.

```csharp
class Empleado
{
    // Atributos que describen al empleado
    public string Nombre { get; set; }
    public int Edad { get; set; }

    // Método que el empleado puede hacer
    public void Trabajar()
    {
        Console.WriteLine($"{Nombre} está trabajando.");
    }
}
```

Luego, para crear objetos (empleados específicos), usamos la clase como molde:

```csharp
Empleado e1 = new Empleado(); // Creación del objeto

e1.Nombre = "Laura";
e1.Edad = 30;

e1.Trabajar(); // Muestra: Laura está trabajando.
```

## II. Objetos

Los objetos con una representación de cosas que existen del mundo real (una persona, un auto o un producto) o de un sistema (una conexión a una base de datos o un formulario).

El objeto se traduce a código mediante *atributos* (sus características) y *métodos* (sus acciones o comportamientos).

**Ejemplo**:

En un automóvil las distintas partes que lo conforman son *objetos*, los cuales se pueden comunicar entre sí para funcionar.

### 2.1 Atributos

Los atributos representan las *propiedades* de un objeto y almacenan su información en un momento dado, es decir su *estado*. Estos pueden cambiar durante la ejecución del programa.

- **Propiedad** = Dato específico.
- **Estado** = Conjunto de propiedades de un objeto en un momento dado.

**Elementos de un atributo**:

- **Nombre**: cómo se llama la propiedad.
- **Tipo de dato**: qué clase de información guarda (texto, número, etc.).
- **Nivel de acceso**: quién puede ver o modificar ese dato.

**Ejemplo en C#**:

Definimos un objeto `Persona` que tiene dos atributos con nivel de acceso `private` : `nombre` y `edad`.

```csharp
class Persona
{
    // Atributos de la clase Persona
    // nivel de acceso, tipo de dato y nombre
    private string nombre;
    private int edad;
}
```

### 2.2 Métodos

Los métodos son las *acciones* que un objeto puede realizar.

A diferencia de una función, los métodos son parte de los objetos y pueden acceder a sus datos, mientras que las funciones trabajan de manera independiente.

**Elementos de un método**:

- **Nombre**: Identifica el método dentro de la clase.
- **Parámetros**: Valores de entrada para procesar (puede no tener).
- **Tipo de retorno**: El tipo de dato que el método devuelve al terminar su ejecución (`int`, `string`, `bool`, etc.) o `void` si no devuelve nada.
- **Cuerpo**: Instrucciones que ejecuta.
- **Modificadores de acceso**: Palabras clave que controlan el acceso (public, private) o comportamiento especial (static, virtual, etc.).

**Los métodos se pueden activar/invocar al**:

- **Recibir un mensaje**: Se invocó el método desde otro objeto
- **Con un cambio de estado**: Un atributo cambió en el objeto.

**Para que el método sea invocado, se requiere conocer**:

- **Nombre** del método.
- **Parámetros** a pasar al método (si es que el método los acepta).
- **Tipo de dato** que va a retornar el método (si es que regresa algo).

**Ejemplo en C#**:

La clase `Persona` se define con dos atributos (`nombre` y `edad`) y un método `MostrarInfo()` que imprime esos datos. En `Main`, se crea una instancia basada en `Persona`, se le asignan valores y se llama al método para mostrar la información.

```csharp
class Persona
{
	// Atributos
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
        persona1.MostrarInfo(); // Nombre: Juan, Edad: 25
    }
}
```

## III. Ciclo de vida de un objeto

Cuando trabajamos con objetos, entender su ciclo de vida nos permite saber cómo inicializar sus datos, cómo acceder a sus métodos y qué sucede con él una vez que el programa ya no lo necesita.

### 3.1 Creación del objeto

#### Constructores

Un constructor es un método especial que se ejecuta automáticamente al crear un objeto.

Su función principal es inicializar el objeto, asignando valores iniciales a sus atributos si es necesario.

Algunas características clave son:

- No devuelven valores (ni siquiera `void`).
- Si no defines ninguno, algunos lenguajes como C# generan un constructor vacío por defecto (`default`) y permite crear instancias sin valores iniciales.
- Si nuestra clase tiene atributos es buena práctica incluir un constructor.

**Elementos de un constructor**:

- **Nombre**: Siempre coincide con el de la clase.
- **Parámetros**: Valores que recibe para inicializar los atributos (puede no tener).
- **Cuerpo**: Contiene las instrucciones para asignar valores iniciales.
- **Nivel de acceso**: Casi siempre `public`, para poder crear objetos desde fuera de la clase.

**Ejemplo en C#**:

Aquí definimos la clase `Persona` con un constructor que recibe el `nombre` y la `edad`. Luego, en `Program`, creamos un objeto `persona1` y mostramos sus datos.

```csharp
class Persona
{
    public string nombre;
    public int edad;

    // Constructor: se ejecuta al crear el objeto
    public Persona(string pNombre, int pEdad)
    {
        nombre = pNombre;
        edad = pEdad;
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
        // Se crea un objeto Persona con valores iniciales
        Persona persona1 = new Persona("Juan", 25);

        // Se invoca el método para mostrar los datos
        persona1.MostrarInfo();  
        // Salida: Nombre: Juan, Edad: 25
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

- **`Activator.CreateInstance&lt;T&gt;()`**: Crea dinámicamente una instancia de una clase sin usar `new`. Útil cuando el tipo se desconoce en tiempo de compilación.
  
  **Ejemplo en C#**

```csharp
Persona juan = Activator.CreateInstance&lt;Persona&gt;();
```

- **`default`**: Asigna el valor predeterminado a un tipo. Para tipos de referencia, devuelve `null`. Para tipos de valor, devuelve `0`, `false` o equivalente.
  
  **Ejemplo en C#**

```csharp
Persona personaPorDefecto = default(Persona);  // null
int numero = default(int);  // 0
```

### 3.2 Uso del objeto

#### Acceso a atributos y métodos

Una vez que un objeto ha sido creado (instanciado), podemos acceder a sus atributos y métodos para realizar operaciones y manipular sus datos.

Se accede a los miembros de un objeto usando el operador punto (`.`).
Por ejemplo, si `persona1` es un objeto, `persona1.Nombre` accede al atributo `Nombre` y `persona1.MostrarInfo()` llama al método.

### 3.3 Alcance y duración del objeto

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

### 3.4 Destrucción y gestión de memoria

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

## IV. Relaciones entre clases

En sistemas POO las clases no suelen trabajar de forma aislada, sino que estas se relacionan entre sí de diversas maneras para representar interacciones, dependencias y jerarquías. Estas relaciones ayudan a estructurar el código de forma más clara, reutilizable y mantenible.

Algunas relaciones se consideran más "fuertes", ya que implican una mayor relación, mientras que otras son más "débiles", porque solo llevan a cabo una interacción temporal.

### 4.1 Dependencia - "usa"

Una clase depende de otra cuando utiliza temporalmente sus datos o comportamiento para cumplir una operación.

Se usa cuando una clase necesita ayuda de otra para ejecutar una acción puntual.

**Ejemplo en C#:**

Una `Impresora` *usa* un `Documento` mientras lo imprime, pero no lo guarda permanentemente.

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

**Diagrama de clases**:

!`Programación IV - Elementos de POO_23-08-2025.png`
### 4.2 Asociación - "conoce a" o "trabaja con"

Una clase puede referenciar a otra clase que esté separada, sin embargo esto no implica que una sea parte de la otra, por lo que ambas pueden existir por separado.

Suele usarse cuando dos clases colaboran entre sí pero sin depender mutuamente una de la otra.

**Ejemplo en C#**:

Un `Profesor` *conoce a* un `Estudiante`, es decir solo lo tiene de referencia.

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

**Diagrama de clases**:

!`Programación IV - Elementos de POO_23-08-2025-1.png`

### 4.3 Agregación - "tiene un" (Existe por separado)

Una clase se puede unir a otra para crear un objeto más complejo, pero ambas pueden existir por sí mismas.

Se puede usar para representar componentes que son parte de otros, pero que a su vez pueden existir de manera independiente.

**Ejemplo en C#**:

Una `Universidad` *tiene* `Carrera`(s), pero esas carreras podrían existir en otra universidad también.

```csharp
class Carrera
{
    public string Nombre { get; set; }
}

class Universidad
{
    public List&lt;Carrera&gt; Carreras { get; set; } = new List&lt;Carrera&gt;();
}
```

**Diagrama de clases**:

!`Programación IV - Elementos de POO_23-08-2025-2.png`

### 4.4 Composición - "tiene un" (No existe por separado)

Una clase puede poseer objetos de otras clases, pero estos no pueden existir independientemente, ya que si la clase principal desaparece, los objetos controlados también desaparecen.

Se suele usar cuando un objeto forma parte inseparable de otro y no tiene sentido que exista por si solo.

**Ejemplo en C#**:

Una `Casa` *tiene* `Habitacion`(es), pero si la casa desaparece, las habitaciones también.

```csharp
class Habitacion
{
    public int Numero { get; set; }
}

class Casa
{
    private List&lt;Habitacion&gt; habitaciones = new List&lt;Habitacion&gt;();

    public Casa()
    {
        habitaciones.Add(new Habitacion { Numero = 1 });
        habitaciones.Add(new Habitacion { Numero = 2 });
    }
}
```

**Diagrama de clases**:

!`Programación IV - Elementos de POO_23-08-2025-3.png`

### 4.5 Herencia - "es un"

Las clases pueden tener una relación jerárquica, donde una clase hereda los atributos y comportamientos de otra (Clase base y clase hija).

Se usa cuando una clase comparte funcionalidad con otra pero también necesita comportamientos especializados.

**Ejemplo en C#**:

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

**Diagrama de clases**:

!`Programación IV - Elementos de POO_23-08-2025-4.png`

## V. Tipos de clases

No todas las clases funcionan igual. Según el propósito que tengan, podemos encontrar distintos tipos de clases según su propósito, restricciones y forma de implementación. Conocerlas nos ayuda a organizar mejor el código y a usar la herramienta correcta en cada situación.

### 5.1 Clase concreta

Es la clase tradicional con la que se pueden crear (instanciar) objetos directamente. Contiene la implementación completa de todos sus métodos y puede heredar o ser heredada.

Se usa para crear objetos funcionales que representen entidades del sistema.

**Ejemplo en C#**:

Aquí, `Persona` es una clase concreta que se puede usar sin alguna restricción.

```csharp
class Persona
{
    public string Nombre { get; set; }

    public void Saludar()
    {
        Console.WriteLine($"Hola, soy {Nombre}");
    }
}

// Uso
Persona p = new Persona();
p.Nombre = "Laura";
p.Saludar(); // Muestra: Hola, soy Laura
```

### 5.2 Clase abstracta

Una clase abstracta no puede ser instanciada directamente pues está incompleta. En su lugar, sirve como clase base para otras clases, las cuales deben heredarla para completarle lo que falta.

Puede contener métodos abstractos (sin implementación) que deben ser definidos por las clases hijas, así como métodos normales.

Se usa para definir una estructura base común que otras clases deben completar y especializar.

**Ejemplo en C#**:

La clase `Animal` no se puede usar sola porque tiene un método sin código (`HacerSonido`). La clase `Perro` la completa y por eso sí podemos crear un objeto de `Perro`.

```csharp
abstract class Animal
{
    // Método abstracto: no tiene código, las clases hijas deben completarlo
    public abstract void HacerSonido();

    // Método normal: ya tiene código
    public void Dormir()
    {
        Console.WriteLine("Zzz...");
    }
}

class Perro : Animal
{
    public override void HacerSonido()
    {
        Console.WriteLine("Guau!");
    }
}

// Uso
Perro miPerro = new Perro();
miPerro.HacerSonido(); // Muestra: Guau!
miPerro.Dormir();      // Muestra: Zzz...
```

### 5.3 Clase estática

Una clase estática no puede ser instanciada ni heredada. Solo sirve para guardar métodos o datos compartidos que se usan sin tener la necesidad de crear nuevas instancias, más no trabaja con datos de objetos. Todos sus miembros también deben ser estáticos.

Se utiliza para agrupar métodos que no necesitan mantener estado, como funciones matemáticas, validaciones, conversiones, u otras herramientas.

**Ejemplo en C#**:

La clase `Calculadora` contiene métodos que se pueden usar sin necesidad de crear una instancia.

```csharp
static class Calculadora
{
    public static int Sumar(int a, int b) => a + b;
}

// Uso
int resultado = Calculadora.Sumar(2, 3);
Console.WriteLine(resultado); // Muestra: 5
```

```csharp
// Uso incorrecto
Calculadora calc = new Calculadora();
int resultado = calc.Sumar(3, 4);
```

### 5.4 Clase sellada

Una clase sellada no puede ser heredada, lo cual impide que otras clases modifiquen o extiendan su comportamiento.

Puede mejorar el rendimiento del sistema en tiempo de ejecución.

Se usa cuando se quiere proteger una clase para que nadie más la extienda o modifique, especialmente en bibliotecas, servicios, o clases críticas.

**Ejemplo en C#**:

La clase `Logger` registra los eventos en una aplicación. No queremos que alguien herede de ella y cambie la forma en que se registran los mensajes, como su formato. Por tanto, está sellada.

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

// Uso
Logger log = new Logger();
log.LogInfo("Aplicación iniciada");
log.LogError("Error de conexión");
```

### 5.5 Interfaz

Una interfaz garantiza que cualquier clase que la implemente tendrá cierto comportamiento, aunque no dice cómo deben funcionar. Esto se define mediante un conjunto de métodos y propiedades sin implementación.

Las clases que implementan la interfaz están obligadas a proporcionar su propia versión de esos miembros.

Se usa para definir contratos que distintas clases pueden implementar de manera diferente.

**Ejemplo en C#**:

La interfaz `IVehiculo` define que cualquier vehículo debe poder `Encender()`. La clase `Auto` implementa esa interfaz y cumple la promesa dando su propia versión del método.

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

// Uso
Auto miAuto = new Auto();
miAuto.Encender(); // Muestra: Auto encendido.
```

### 5.6 Clase parcial

Una clase parcial se puede dividir en varios archivos del mismo proyecto. El compilador une esos archivos en una sola clase al ejecutar el programa.

Se utiliza para organizar mejor el código, especialmente en proyectos grandes o con código generado automáticamente (como en Windows Forms), y así el programador añade lógica personalizada en otro archivo.

**Ejemplo en C#**:

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

Uso

```csharp
Persona p = new Persona();
p.Nombre = "Carlos";
p.Saludar(); // Muestra: Hola, soy Carlos
```

### 5.7 Clase genérica

Una clase genérica permite trabajar con cualquier tipo de dato sin especificarlo inicialmente. Se define con un parámetro de tipo `&lt;T&gt;`, el cual se especifica al momento de crear una instancia.

Se suele utilizar para colecciones, contenedores, utilidades y estructuras reutilizables.

**Ejemplo en C#**:

La clase `Caja&lt;T&gt;` es genérica porque puede guardar cualquier tipo de dato. En el primer caso es una caja de enteros, en el segundo una caja de texto.

```csharp
class Caja&lt;T&gt;
{
    public T Contenido { get; set; }
}

// Uso
Caja&lt;int&gt; cajaEntero = new Caja&lt;int&gt; { Contenido = 100 };
Caja&lt;string&gt; cajaTexto = new Caja&lt;string&gt; { Contenido = "Hola" };

Console.WriteLine(cajaEntero.Contenido); // Muestra: 100
Console.WriteLine(cajaTexto.Contenido);  // Muestra: Hola
```

## VI. Cardinalidad

La cardinalidad explica las relaciones entre clases, describiendo cuántos objetos de una clase pueden estar relacionados con los objetos de otra clase. Puede cambiar según los requerimientos del sistema.

- **1 a 1**: Un objeto de la primera clase está relacionado con solo un objeto de la segunda clase, y viceversa.
  Ejemplo: Una persona solo puede tener un pasaporte válido a la vez. Ese pasaporte pertenece a una sola persona.
- **1 a muchos**: Un objeto de una clase se relaciona con múltiples objetos de otra clase, pero no al revés.
  Ejemplo: Un docente puede impartir muchos cursos, pero cada curso es impartido por un solo docente.
- **Muchos a muchos**: Un objeto de la primera clase se relaciona con varios objetos de la segunda clase, y viceversa.
  Ejemplo: Un estudiante puede estar inscrito en varios cursos. Y un curso puede tener varios estudiantes.

## VII. Tipos de datos no primitivos

Los tipos de datos no primitivos son estructuras más complejas que los datos simples y se crean a partir de estos. Algunos de los tipos más comunes son:

- **Objetos**: Instancias de clases que combinan datos (atributos) y funcionalidades (métodos).
- **Arreglos (Arrays)**: Conjuntos de elementos del mismo tipo organizados de manera que cada valor se almacena en una posición específica identificada por un índice.
- **Matrices**: Son arreglos de dos o más dimensiones que organizan los datos en filas y columnas, permitiendo representar estructuras como tablas o gráficos.
- **Listas**: Son colecciones dinámicas de elementos, similares a los arreglos, pero con la diferencia de que pueden cambiar de tamaño y permiten agregar o eliminar datos con facilidad.

---

## / Más Información

- [Programación I - Algoritmos](/apuntes/programacion-i-algoritmos/)
- [Programación II - Conceptos Básicos](/apuntes/programacion-ii-conceptos-basicos/)
- [Programación III - Introducción a la Programación Orientada a Objetos](/apuntes/programacion-iii-introduccion-a-la-programacion-orientada-a-objetos/)
- [Programación IV - Elementos de POO](/apuntes/programacion-iv-elementos-de-poo/)
- [Programación V - Mecanismos de POO](/apuntes/programacion-v-mecanismos-de-poo/)
- [Programación VI - Estructuras de Datos y Algoritmos Avanzados](/apuntes/programacion-vi-estructuras-de-datos-y-algoritmos-avanzados/)
- [Programación VII - Manejo de Datos](/apuntes/programacion-vii-manejo-de-datos/)
- [Programación VIII - POO y la Programación Orientada a Eventos](/apuntes/programacion-viii-poo-y-la-programacion-orientada-a-eventos/)
- [Programación IX - Patrones de Diseño](/apuntes/programacion-ix-patrones-de-diseno/)
- [Programación - Guías Documentación y Buenas Prácticas](/apuntes/programacion-guias-documentacion-y-buenas-practicas/)

---
