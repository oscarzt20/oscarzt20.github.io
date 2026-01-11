---
Date: 2025-08-08
Time: 02:00
tags:
- enciclopedia
- aprenderProgramacion
slug: programacion-v-mecanismos-de-poo
title: Programación V - Mecanismos de POO
---

---

## I. Mecanismos de POO

### 1.1 Encapsulación y acceso

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

### 1.2 Abstracción e interfaces propias

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

### 1.3 Herencia y especialización

La herencia es una característica esencial en la reutilización de código, ya que permite que una clase herede el contenido de otra, es decir, permite que una clase aproveche los atributos y métodos de una ya existente sin tener que repetir el código, sino únicamente adicionando lo que le falte.

Al aplicar la herencia, se define primero la *clase principal*, que será la más abstracta, es decir, la que establece la estructura general sin implementar todos los detalles. Por su parte, las *clases heredadas*, más concretas, se encargan de implementar los detalles específicos del objeto.

Algunos lenguajes permiten la *herencia múltiple*, donde una clase hereda de más de una clase principal. Sin embargo, puede generar conflictos y aumentar la complejidad, por lo que lenguajes como C# y Java no la admiten y usan *interfaces* en su lugar.

#### Jerarquía de clases

- **Superclase (Clase padre)**: Contiene todos los atributos y métodos que son comunes a las clases que descienden de ella. *Ej.* Persona.
- **Subclase (Clase hija)**: Es una extensión de la superclase, donde toma toda su información de esta y adiciona lo propio. *Ej.* Persona --> Empleado.

La relación "es-un" describe cómo se establece la herencia entre clases, ya que una clase hija hereda características y comportamientos de una clase padre.

### 1.4 Polimorfismo dinámico y estático

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

Vamos a sobrecargar el operador \+ para que pueda sumar dos objetos `Punto`, combinando sus coordenadas `x` e `y`. Sin esta sobrecarga, `PuntoA + PuntoB` daría error, pero al definir su comportamiento, podemos hacer que devuelva un nuevo punto con la suma de las coordenadas.

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

- **\+ (suma)** → Puede sumar dos objetos, como combinar coordenadas de dos puntos o concatenar información personalizada.
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
- ** \&lt; y  \&gt; (menor o mayor que)** → Permiten comparar objetos según un criterio específico.
  **Ejemplo**: `EmpleadoA > EmpleadoB` podría significar que gana más salario.

###### Sobrecarga de operadores de incremento/decremento

- **\++ (incremento)** → Puede aumentar el valor de un objeto.
  **Ejemplo**: `Nivel++` podría aumentar el nivel de un personaje en un juego.
- **`--` (decremento)** → Puede reducir el valor de un objeto.
  **Ejemplo**: `Cupo--` podría disminuir la cantidad de espacios disponibles en un evento.

###### Sobrecarga de operadores de conversión

- **`explicit` / `implicit`** → Permiten convertir un objeto en otro tipo.
  **Ejemplo**: `Producto` podría convertirse en `string` para mostrar su nombre en una factura.

### 1.5 Composición

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