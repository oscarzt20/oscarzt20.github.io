---
Date: 2025-08-08
Time: 01:46
tags:
- enciclopedia
- aprenderProgramacion
slug: programacion-ii-conceptos-basicos
title: Programación II - Conceptos Básicos
---

---

Un lenguaje de programación es una forma estructurada de comunicarnos con la computadora para que ejecute instrucciones. Existen muchos lenguajes (C#, Java, Python, etc.), cada uno con sus ventajas y usos.

Los algoritmos se convierten en programas reales gracias a estos lenguajes.

## I. Clasificación de los lenguajes de programación

### 1.1 Niveles de abstracción

Podemos clasificar los leguajes de programación basado en lo cerca o lejos que estén del lenguaje natural humano:

- **Bajo nivel**: Aquellos lenguajes que controlan el hardware del ordenador. Ej. Lenguaje Ensamblador, Código Máquina o Binario.
- **Alto nivel**: Son los más parecidos al lenguaje natural humano y abarca el 99% de lenguajes de programación.
- **Nivel intermedio**: Puede usar elementos de los dos anteriores. Un ejemplo es el lenguaje C.

### 1.2 Ejecución del código

Según cómo se ejecuta el código, podemos clasificarlos en:

- **Lenguaje compilado**: Se toma el código de alto nivel y lo convierte en bytes, y al final nos dará un archivo ejecutable.
  Tiene mejor rendimiento al ejecutarse aunque ocupa más memoria que el interpretado.
- **Lenguaje interpretado**: Se interpreta línea a línea en tiempo real al ejecutarse (Ej. JavaScript, Python).
  Tiene un rendimiento algo más lento que el compilado pero ocupa menos memoria.
- **Lenguaje híbrido**: Algunos lenguajes combinan ambos enfoques, primero, el código es compilado a un formato intermedio llamado bytecode, luego este bytecode es ejecutado por un intérprete o máquina virtual (JVM en Java, CLR en C#) (Ej. Java, C#, Kotlin).

## II. Herramientas para programar

### 2.1 IDE's

Un IDE (Entorno de Desarrollo Integrado) es una aplicación que reúne en un mismo lugar las herramientas necesarias para programar.

En general, estos incluyen:

- **Editor de texto inteligente**: Sugiere autocompletado y detecta errores mientras escribes.
- **Depurador**: Permite ejecutar el programa paso a paso  para encontrar errores.
- **Gestor de proyectos**: organiza los archivos de manera estructurada.
- **Compilador/Intérprete**: Traduce el código y lo ejecuta.

Existen muchas opciones de IDE's, algunos ejemplos notables son:

- **Visual Studio**: Es el IDE más completo y recomendado para programar en C# y .NET.
- **Visual Studio Code (VSCode)**: Por default no es un IDE completo, sino un editor de código extensible. Es ligero, y tiene extensiones descargables que le pueden otorgar funcionalidad ampliada.
- **NetBeans**: Más usado con Java.

#### Visual Studio

Visual Studio es el IDE oficial de Microsoft para programar en C#.

**Instalación rápida:**

1. Descarga Visual Studio versión Community.
2. En el instalador, selecciona la opción **.NET desktop development**.
3. Completa la instalación y abre Visual Studio.

**Crear tu primer proyecto de consola en C#:**

1. En Visual Studio, selecciona **Crear un proyecto**.
2. Busca **Aplicación de consola**.
3. Ponle un nombre.
4. Haz click en **Siguiente**
5. Haz clic en **Crear**.

Verás un archivo `Program.cs` con algo parecido a:

```csharp
Console.WriteLine("Hello, World!");
```

- `Console.WriteLine("¡Hola, mundo!");` nos puede servir para mostrar mensajes.

Si das click en el botón verde con el ícono de play junto con el nombre del proyecto, deberías ver el mensaje. También puedes cambiar el contenido de este.

Además de mostrar mensajes, podemos solicitar datos:

```csharp
Console.WriteLine("Escribe tu nombre y presiona Enter:");

string nombre = Console.ReadLine();

Console.WriteLine("Tú nombre es: " + nombre);
```

- `Console.WriteLine("...");` Muestra un mensaje pidiendo al usuario que escriba su nombre.
- `Console.ReadLine();` Hace una pausa y espera a que el usuario escriba en la consola y presione Enter. Lo que el usuario escribió se guarda como dato.
- Usamos `Console.WriteLine` otra vez para mostrar lo que el usuario escribió.

## III. Componentes básicos de la programación

### 3.1 Tipos de datos simples

Cuando programamos, necesitamos tipos de datos para representar información. Son como las "categorías" de cosas que podemos almacenar en memoria. Algunos de los tipos de datos simples son:

- **Caracteres (char)**: Almacenan una sola letra, número o símbolo.
- **Texto (string)**: Secuencia de caracteres utilizada para representar palabras o frases.
- **Entero (int)**: Números enteros, positivos o negativos, sin decimales.
- **Decimal (double, float)**: Números con parte decimal.
- **Booleano (bool)**: Solo tiene dos valores posibles: verdadero (true) o falso (false).
- **Fecha (date, DateTime)**: Representa una fecha y, en algunos casos, también la hora.
- **Nulo (null, None, nil)**: Representa la ausencia de un valor o un objeto vacío.

La denominación de cada tipo de dato puede diferir en cada lenguaje de programación.

**Ejemplo en C#**:

Elegimos un tipo de dato, un nombre para identificarlo y le asignamos un valor.

```csharp
char inicial = 'J';
string nombre = "Juan";
int edad = 25;
double altura = 1.75;
bool esMayorDeEdad = true;
DateTime hoy = DateTime.Now;

Console.WriteLine($"Hola, soy {nombre}, tengo {edad} años y mido {altura}m.");
```

### 3.2 Atributos

#### Variable

Espacio reservado en memoria para almacenar un valor como tipo de dato. Este valor se puede modificar a lo largo del programa, y tiene un nombre.

**Ejemplo C#**:

Se declara una variable del tipo `int`, con el nombre `edad` y se le asigna el valor inicial de `25`.

```csharp
int edad = 25;
```

En la programación, el punto y coma `;` se utiliza para finalizar una sentencia en muchos lenguajes de programación.

Básicamente, indica al compilador o intérprete que la instrucción actual ha terminado y que puede pasar a la siguiente. Sin él, podrían causarse errores.

#### Constante

Es un espacio reservado en memoria para almacenar un valor como tipo de dato, el cual *NO* se puede modificar, y tiene un nombre.

**Ejemplo en C#**:

Se declara una constante del tipo `double`, con el nombre `PI` y se le asigna el valor de `3.1416`.

```csharp
const double PI = 3.1416;
```

### 3.3 Operadores

Los operadores nos permiten hacer operaciones con variables y valores.

#### Operadores aritméticos

Realizan operaciones aritméticas y definen el orden en el que se harán las operaciones dentro del código:

- **Suma (+)**
- **Resta (-)**
- **Multiplicación (\*\)**
- **División (/)**
- **Módulo (%)**: Retorna el residuo de una división entre dos números.
- **Incremento (++):** Aumenta en una unidad el valor de una variable.
- **Decremento (--):** Disminuye en una unidad el valor de una variable.

El orden es el mismo que en la aritmética: ( ) * / + - %

**Ejemplo en C#**:

Se declaran las variables `a` y `b`, y se muestra el resultado de sumar estas variables, así como el resultado del uso del módulo.

```csharp
int a = 10, b = 3;

Console.WriteLine(a + b); // 13
Console.WriteLine(a % b); // 1 (residuo)
```

#### Operadores de comparación

Expresiones que comparan dos valores y devuelven un valor booleano `true` o `false`:

- **Menor que (&lt;)**: Verifica si el valor `a` es menor que `b`.
- **Mayor que (&gt;)**: Comprueba si el valor `a` es mayor que `b`.
- **Igual a (\==)**: Determina si ambos valores son exactamente iguales, incluyendo si son del mismo tipo. *NO* confundir con \= que es el operador de asignación.
- **Diferente de (!=)**: Evalúa si dos valores son distintos.
- **Menor o igual a (&lt;=)**: Verifica si el valor `a` es menor o igual que `b`.
- **Mayor o igual a (&gt;=)**: Comprueba si el valor `a` es mayor o igual que `b`.

**Ejemplo en C#**:

Se declaran las variables `x` y `y`. Primero, se demuestra si `x` es menor que `y` lo cual resulta verdadero, y después se trata de comprobar si son iguales lo cual resulta falso.

```csharp
int x = 5, y = 8;

Console.WriteLine(x &lt; y);  // True
Console.WriteLine(x == y); // False
```

#### Operadores de asignación

Permiten actualizar las variables. Mientras que los operadores aritméticos actúan sobre valores para producir un resultado, los de asignación modifican el valor de una variable. 

- **Asignación (\=)**: Asigna o reemplaza un valor.
- **Suma y asignación (\+=)**: Suma un valor.
- **Resta y asignación (\-=)**: Resta un valor.
- **Multiplicación y asignación (\*=)**: Multiplica un valor.
- **División y asignación (\/=)**: Divide un valor.
- **Módulo y asignación (\%=)**: Calcula el residuo de la división.

**Ejemplo en C#**:

Se declara la variable `z` con el valor de 10 y después se le agrega 5.

```csharp
int z = 10;

z += 5; // z = z + 5 → 15
```

#### Operadores lógicos

Permiten combinar condiciones (expresiones que producen `true` o `false`) para tomar decisiones.

- **AND (\&&)**: Resulta verdadero si todas las expresiones conectadas son verdaderas, sino es falso.
- **OR (\||)**: Resulta verdadero si al menos una de las expresiones ligadas es verdadero, sino es falso.
- **NOT (!)**: Resulta verdadero si el valor es contrario a la expresión conectada.

**Ejemplos en C#**:

**AND (\&&)**: Una persona está en rango adulto laboral si su edad está entre 18 *y* 65 años.

```csharp
int edad = 30;

bool esAdultoLaboral = (edad &gt;= 18) && (edad &lt;= 65);

Console.WriteLine(esAdultoLaboral); // True
```

**OR (\||)**: El envío gratis si la compra es mayor o igual a 200 *o* si el cliente es Premium.

```csharp
double total = 180.0;
bool esPremium = true;

bool envioGratis = (total &gt;= 200) || esPremium;

Console.WriteLine(envioGratis); // True
```

**NOT (!)**: Se bloquea el acceso si *no* tiene permiso.

```csharp
bool tienePermiso = false;

bool accesoBloqueado = !tienePermiso; // !false → true

Console.WriteLine(accesoBloqueado); // True
```

### 3.4 Expresiones lógicas

Las expresiones lógicas combinan valores y operadores para decidir qué camino tomará un programa, es decir permiten que un programa actúe de manera diferente según las condiciones. Esto se logra evaluando si una proposición es verdadera o falsa.

Para validar estas expresiones, y al mismo tiempo lograr identificar posibles errores en el programa, podemos utilizar una tabla de verdad.

#### Tabla de verdad

Es una representación en tabla que abarca todas las posibles combinaciones de datos de entrada y el resultado final.

Se utiliza para:

- Validar que las condiciones estén bien planteadas.
- Detectar errores lógicos antes de ejecutar el programa.

Se recomienda usar los datos límite (los casos más pequeños, más grandes o extremos posibles) para validar de forma efectiva.

**Ejemplo con OR (\||)**:

Determinar si un cliente recibe entrada gratis en Cinépolis. Para esto, debe tener \>= 300 puntos o hay promoción especial.

**Código de C#**:

```csharp
int puntos = 280;
bool esPromocionEspecial = true;

if (puntos >= 300 || esPromocionEspecial)
{
    Console.WriteLine("Entrada gratis"); // Resultado
}
else
{
    Console.WriteLine("Debe pagar entrada");
}
```

Para este ejemplo, estamos utilizando la estructura `if`, la cual permite tomar una decisión en el programa, y se ejecutará si la expresión lógica que contiene es verdadera, pero de ser falsa se ejecutará la instrucción que está dentro de `else`.

**Tabla de verdad**:

| Var 1:<br>Puntos cliente frecuente | Var 2:<br>Tipo de promoción | Resultado | Salida                      |
| ---------------------------------- | --------------------------- | --------- | --------------------------- |
| 300                                | `true`                      | V         | **V**: "Entrada gratis"     |
| 425                                | `true`                      | V         | **V**: "Entrada gratis"     |
| 200                                | `true`                      | V         | **V**: "Entrada gratis"     |
| 300                                | `false`                     | V         | **V**: "Entrada gratis"     |
| 500                                | `false`                     | V         | **V**: "Entrada gratis"     |
| 80                                 | `false`                     | F         | **F**: "Debe pagar entrada" |

**Ejemplo con AND &&**:

Evaluar si una persona es acreedora a una tarjeta premium. Para ello, el ingreso debe ser \>= 50,000 y el historial de pago debe ser puntual.

**Código de C#**:

```csharp
int ingreso = 60000;
string historialCredito = "puntual";

if (ingreso >= 50000 && historialCredito == "puntual")
{
    Console.WriteLine("Aprobado para tarjeta premium"); // Resultado
}
else
{
    Console.WriteLine("Lo sentimos, no cubre con todos los requisitos");
}
```

**Tabla de verdad**:

| Var 1:<br>Ingreso | Var 2:<br>Estado de pagos | Resultado | Salida                                                  |
| ----------------- | ------------------------- | --------- | ------------------------------------------------------- |
| 50000             | "puntual"                 | V         | **V**: "Aprobado para tarjeta premium"                  |
| 60000             | "puntual"                 | V         | **V**: "Aprobado para tarjeta premium"                  |
| 40000             | "puntual"                 | F         | **F**: "Lo sentimos, no cubre con todos los requisitos" |
| 50000             | "atrasado"                | F         | **F**: "Lo sentimos, no cubre con todos los requisitos" |
| 80000             | "atrasado"                | F         | **F**: "Lo sentimos, no cubre con todos los requisitos" |
| 10000             | "atrasado"                | F         | **F**: "Lo sentimos, no cubre con todos los requisitos" |

### 3.5 Estructuras de control de flujo

Las estructuras de control permiten cambiar el orden normal de ejecución de las instrucciones. En lugar de que el programa corra de arriba a abajo, podemos hacer que tome decisiones o repita tareas.

#### Estructuras condicionales

Controla el flujo de ejecución del programa según si una o varias condiciones son verdaderas o falsas.

##### IF

Ejecuta un bloque de código si una condición es verdadera.

!`Conceptos Generales de Programación_05-06-2025-3.png`

**Ejemplo en C#**:

Un supermercado ofrece un 10% de descuento si el cliente es mayor de 60 años y muestra el descuento aplicado.

```csharp
int edad = 65;
double precio = 100.0;
double descuento = 0;

if (edad > 60)
{
    descuento = precio * 0.10;
    Console.WriteLine($"Descuento aplicado: ${descuento}");
}
```

##### ELSE

Se utiliza con `if` para ejecutar un bloque de código alternativo si la condición es falsa.

**Ejemplo en C#**:
  
Un sistema de compras decide si el envío es gratis o tiene costo dependiendo del total de la compra.

```csharp
double totalCompra = 250.0;

if (totalCompra >= 200)
{
    Console.WriteLine("¡Envío gratis!");
}
else
{
    Console.WriteLine("El costo de envío es de $50.");
}
```

##### SWITCH

Permite seleccionar uno de varios bloques de código para ejecutar, y tiene una opción de default. Es más limpio que usar muchos `else if`.

!`Conceptos Generales de Programación_05-06-2025-2.png`

**Ejemplo en C#**:

Un usuario elige su método de pago en un e-commerce.

```csharp
string metodoPago = "Tarjeta";

switch (metodoPago)
{
    case "Tarjeta":
        Console.WriteLine("Pago realizado con tarjeta.");
        break;
    case "PayPal":
        Console.WriteLine("Pago realizado con PayPal.");
        break;
    case "Transferencia":
        Console.WriteLine("Pago realizado con transferencia.");
        break;
    default:
        Console.WriteLine("Método no válido.");
        break;
}
```

#### Estructuras iterativas

Sirven para repetir un bloque de instrucciones.

##### FOR

Usado cuando sabemos de antemano cuántas veces queremos repetir un bloque de instrucciones.

!`Conceptos Generales de Programación_05-06-2025-4.png`

**Ejemplo en C#**:

Un usuario tiene varios productos en su carrito y queremos mostrar la lista.

```csharp
string[] carrito = { "Laptop", "Mouse", "Teclado" };

for (int i = 0; i &lt; carrito.Length; i++)
{
    Console.WriteLine($"Producto {i + 1}: {carrito[i]}");
}
```

##### FOR EACH

Se utiliza para recorrer los elementos de una colección (como arreglos o listas) sin necesidad de usar un índice explícito.

!`Conceptos Generales de Programación_05-06-2025-5.png`

**Ejemplo en C#**:

Recorre una lista de productos en un inventario.

```csharp
string[] productos = { "Pan", "Leche", "Huevos", "Queso" };

foreach (string producto in productos)
{
    Console.WriteLine($"Producto disponible: {producto}");
}
```

##### WHILE

Repite un bloque de instrucciones mientras la condición sea verdadera.

!`Conceptos Generales de Programación_05-06-2025-6.png`

**Ejemplo en C#**:

Un sistema de inventario descuenta unidades de un producto mientras haya stock disponible.

```csharp
int stock = 5;

while (stock &gt; 0)
{
    Console.WriteLine($"Producto vendido. Stock restante: {stock}");
    
    stock--;
}

```

##### DO WHILE

Parecido al while pero este se cumple al menos una vez, aunque la condición sea falsa.

!`Conceptos Generales de Programación_05-06-2025-7.png`

**Ejemplo en C#**:

Mostrar un menú inicial, hasta que el usuario elija salir.

```csharp
int opcion;

do
{
    Console.WriteLine("Menú:");
    Console.WriteLine("1. Ver saldo");
    Console.WriteLine("2. Retirar dinero");
    Console.WriteLine("3. Salir");
    Console.Write("Seleccione una opción: ");
    
    opcion = int.Parse(Console.ReadLine());

} while (opcion != 3);

Console.WriteLine("Programa finalizado.");
```

### 3.6 Funciones

Una función es un bloque de código con un nombre, que ejecuta una tarea específica y puede reutilizarse en un mismo programa sin tener que escribir las mismas instrucciones varias veces. Sirve para organizar mejor el código en programas más amplios.

**Ventajas de usar funciones**:

- Código más limpio y legible.
- Reutilización de código.
- Facilita el mantenimiento y depuración.
- Permite dividir problemas grandes en partes más pequeñas.

**Estructura de una función**:

```csharp
tipo_de_dato NombreDeLaFuncion(parametros)
{
    // instrucciones que hace la función
    return valor; // solo si devuelve algo
}
```

- **tipo_de_dato**: Es el tipo de resultado que la función dará. (`int`, `string`, `bool`, `void` si no devuelve nada)
- **NombreDeLaFuncion**: Es el **nombre de la función**, para poder usarla en el programa. Por ejemplo: `SumarNumeros`, `MostrarMensaje`.
- **parametros**: Son los datos que la función necesita para trabajar. Pueden ser cero, uno o varios. Por ejemplo: ``(int a, int b)`` indica que la función necesita dos números enteros.
- **Instrucciones**: Son las acciones que realiza la función usando los parámetros.
- **return valor**: Es lo que la función devuelve. Solo se usa si la función no es `void`.

**Ejemplos en C#**:

**Función sin parámetros y sin retorno (void)**: Se imprime “¡Hola! Soy una función.” en la consola.

```csharp
static void Saludar()
{
    Console.WriteLine("¡Hola! Soy una función.");
}

Saludar(); // Llamada a la función para "activarla"
```

**Función con parámetros**: Se imprime un saludo personalizado usando el nombre que se le pase.

```csharp
void SaludarA(string nombre)
{
    Console.WriteLine("Hola " + nombre);
}

SaludarA("Ana");  // Hola Ana
```

**Función con retorno**: Se suman dos números y devuelve el resultado.

```csharp
int Sumar(int a, int b)
{
    return a + b;
}

int resultado = Sumar(3, 4);
Console.WriteLine(resultado); // 7
```

**Función booleana**: Verifica si un número es par y devuelve `true` o `false`.

```csharp
bool EsPar(int numero)
{
    return numero % 2 == 0;
}

Console.WriteLine(EsPar(6)); // True
```

---

## Ejercicios

1. Crea un programa que pida la edad de una persona y diga si es mayor de edad.
2. Usa un `switch` para que, según el número del 1 al 7 ingresado, muestre el día de la semana.
3. Escribe un ciclo `for` que muestre los números del 1 al 10.
4. Crea un programa que calcule el promedio de N calificaciones usando un `while`.
5. Implementa una función que reciba un número y devuelva `true` si es par, `false` si es impar.
6. Escribe una función que calcule el área de un rectángulo (base × altura).

---

## / Más Información

Es recomendable revisar: [Programación - Guías Documentación y Buenas Prácticas](/apuntes/programacion-guias-documentacion-y-buenas-practicas/)

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
