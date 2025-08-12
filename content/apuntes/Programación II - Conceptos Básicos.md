---
Title: Programación II - Conceptos Básicos
Fecha: 2025-08-08
Hora: 01:46
tags: ['enciclopedia', 'post']
---

---

## I. Clasificación de los lenguajes de programación

### 1.1 Niveles de abstracción

- **Bajo nivel**: Aquellos lenguajes que controlan el hardware del ordenador. Ej. Lenguaje Ensamblador, Código Máquina o Binario.
- **Alto nivel**: Son más parecidos al lenguaje natural humano y abarca el 99% de lenguajes de programación.
- **Nivel intermedio**: Puede usar elementos de los dos anteriores. El único que lo hace es el C.

### 1.2 Lenguajes compilados e interpretados

- **Lenguaje compilado**: Se toma el código en alto nivel y lo convierte en bytes, y al final nos dará un archivo ejecutable. Tiene mejor rendimiento al ejecutarse aunque ocupa más memoria que el interpretado.
- **Lenguaje interpretado**: Se interpreta línea a línea en tiempo real al ejecutarse (Ej. JavaScript, Python). Tiene un rendimiento algo más lento que el compilado pero ocupa menos memoria.
- **Lenguaje híbrido**: Algunos lenguajes combinan ambos enfoques, primero, el código es compilado a un formato intermedio llamado bytecode, luego este bytecode es ejecutado por un intérprete o máquina virtual (JVM en Java, CLR en C#) (Ej. Java, C#, Kotlin).

## II. Componentes básicos de la programación

### 2.1 Tipos de datos simples

Algunos de los tipos de datos comunes simples son:

- **Caracteres (char)**: Almacenan una sola letra, número o símbolo.
- **Texto (string)**: Secuencia de caracteres utilizada para representar palabras o frases.
- **Entero (int)**: Números enteros, positivos o negativos, sin decimales.
- **Decimal (double, float)**: Números con parte decimal.
- **Booleano (bool)**: Solo tiene dos valores posibles: verdadero (true) o falso (false).
- **Fecha (date, datetime)**: Representa una fecha y, en algunos casos, también la hora.
- **Nulo (null, None, nil)**: Representa la ausencia de un valor o un objeto vacío.

> [!NOTE]
> La denominación de cada tipo de dato puede diferir en cada lenguaje de programación.

### 2.2 Atributos

#### Variable

Espacio reservado en memoria para almacenar un valor como tipo de dato. Este valor se puede modificar a lo largo del programa, y tiene un nombre.

**Ejemplo de declaración de variable en C#**:

```csharp
int edad = 25;  // Variable de tipo entero (int) con valor inicial de 25

```

#### Constante

Es un espacio reservado en memoria para almacenar un valor como tipo de dato, el cual *NO* se puede modificar, y tiene un nombre.

**Ejemplo de declaración de constante en C#**:

```csharp
const double PI = 3.1416; // Constante de tipo double
```

### 2.3 Operadores

#### Operadores aritméticos

Es la regla que define el orden en el que se harán las operaciones en un determinado código:

- **Suma (+)**: Realiza la adición de dos valores numéricos.
- **Resta (-)**: Calcula la diferencia entre dos valores.
- **Multiplicación ($*$)**: Multiplica dos valores numéricos.
- **División (/)**: Divide un número entre otro y devuelve el resultado.
- **Módulo (%)**: Retorna el residuo de una división entre dos números.
- **Incremento (++):** Aumenta en una unidad el valor de una variable.
- **Decremento (--):** Disminuye en una unidad el valor de una variable.

> [!NOTE]
> El orden es el mismo que en la aritmética: ( ) * / + - %

#### Operadores de comparación

Expresiones que comparan dos valores y devuelven un valor booleano:

- **Menor que (<)**: Verifica si el valor de la izquierda es menor que el de la derecha.
- **Mayor que (>)**: Comprueba si el valor de la izquierda es mayor que el de la derecha.
- **Igual a ($==$)**: Determina si ambos valores son exactamente iguales. *No confundir con `=` que es el operador de asignación.*
- **Diferente de (!=)**: Evalúa si dos valores son distintos.
- **Menor o igual a (<=)**: Verifica si el valor de la izquierda es menor o igual al de la derecha.
- **Mayor o igual a (>=)**: Comprueba si el valor de la izquierda es mayor o igual al de la derecha.

#### Operadores de asignación

- **Asignación (`=`)**: Asigna el valor de la derecha a la variable de la izquierda.
- **Suma y asignación (`+=`)**: Suma el valor de la derecha al de la variable y almacena el resultado en la misma variable.
- **Resta y asignación (`-=`)**: Resta el valor de la derecha al de la variable y almacena el resultado en la misma variable.
- **Multiplicación y asignación (`*=`)**: Multiplica la variable por el valor de la derecha y almacena el resultado en la misma variable.
- **División y asignación (`/=`)**: Divide la variable entre el valor de la derecha y almacena el resultado en la misma variable.
- **Módulo y asignación (`%=`)**: Calcula el residuo de la división entre la variable y el valor de la derecha, almacenándolo en la misma variable.

#### Operadores lógicos

Permiten realizar operaciones lógicas en valores booleanos y se apoyan de estructuras como if, while y for. Son:

- **AND (`&&`)**: Resulta verdadero si todas las expresiones conectadas son verdaderas, sino, es falso.
- **OR (`||`)**: Devuelve verdadero si al menos una de las expresiones ligadas es verdadero, sino, es falso.

### 2.4 Expresiones lógicas

Es una construcción en código que combina valores y operadores lógicos para evaluar si una proposición es verdadera o falsa. Ej. (edad >= 18).

#### Tabla de verdad

Es una representación en tabla que abarca todas las posibles combinaciones de datos de entrada en una expresión lógica, determinando si el resultado es Verdadero o Falso. Sirve para validar las expresiones lógicas. Se recomienda usar datos límite.

**Ejemplo con OR**:

Determinar si un cliente recibe entrada gratis en Cinépolis.

```csharp
if ((PuntosClienteFrecuente >= 300) || (TipoDePromocion == "boleto gratis") || (TipoDePromocion == "aniversario Cinépolis"))
{
    Console.WriteLine("Bienvenido a Cinépolis, no paga su entrada, es gratis");
}
else
{
    Console.WriteLine("Bienvenido a Cinépolis, favor de pasar a taquilla");
}

```

|**Var 1** (Puntos Cliente Frecuente)|**Var 2** (Tipo De Promocion)|**R**|**Var 3** (Tipo De Promocion)|**Salida**|
|---|---|---|---|---|
|>= 300|"boleto gratis"|V|"aniversario Cinépolis"|**V** "Bienvenido a Cinépolis, no paga su entrada, es gratis"|
|300|"boleto gratis"|V|"aniversario Cinépolis"|**V** "Bienvenido a Cinépolis, no paga su entrada, es gratis"|
|425|"muchos gratis"|F|"sin promoción"|**V** "Bienvenido a Cinépolis, no paga su entrada, es gratis"|
|200|"boleto gratis"|V|"sin promoción"|**V** "Bienvenido a Cinépolis, no paga su entrada, es gratis"|
|80|"sin promoción"|F|"sin promoción"|**F** "Bienvenido a Cinépolis, favor de pasar a taquilla"|

**Ejemplo con AND**:

Evaluar si una persona es acreedora a una tarjeta premium.

```csharp
if ((IngresoPersona >= 50000) && (IngresoPersona <= 99000) && (EstadoPagos == "puntuales"))
{
    Console.WriteLine("Eres acreedor a una tarjeta premium");
}
else
{
    Console.WriteLine("Lo sentimos, no cubre con todos los requisitos");
}
```

|**Var 1** (Ingreso Persona >= 50000)|**Var 2** (Ingreso Persona <= 99000)|**R**|**Var 3** (Estado Pagos)|**Salida**|
|---|---|---|---|---|
|50000|99000|V|"puntuales"|**V** "Eres acreedor a una tarjeta premium"|
|60000|115000|F|"atrasados"|**F** "Lo sentimos, no cubre con todos los requisitos"|
|40000|80000|V|"atrasados"|**F** "Lo sentimos, no cubre con todos los requisitos"|
|10000|20000|F|"atrasados"|**F** "Lo sentimos, no cubre con todos los requisitos"|

### 2.5 Estructuras de control de flujo

#### Estructuras condicionales

Controla el flujo de ejecución del programa según si una o varias condiciones son verdaderas o falsas.

- **IF**: Ejecuta un bloque de código si una condición es verdadera.

![Conceptos Generales de Programación_05-06-2025-3.png](/imagenes/Conceptos%20Generales%20de%20Programaci%C3%B3n_05-06-2025-3.png)


**Ejemplo en C#**:

Un supermercado ofrece un 10% de descuento si el cliente es mayor de 60 años.

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

- **ELSE**: Se utiliza con if para ejecutar un bloque de código alternativo si if resulta falso.
  
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

- **SWITCH**: Permite seleccionar uno de varios bloques de código para ejecutar y tiene una opción de default.

![Conceptos Generales de Programación_05-06-2025-2.png](/imagenes/Conceptos%20Generales%20de%20Programaci%C3%B3n_05-06-2025-2.png)

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
        Console.WriteLine("Pago realizado con transferencia bancaria.");
        break;
    default:
        Console.WriteLine("Método de pago no reconocido.");
        break;
}

```

#### Estructuras iterativas

- **FOR**: Es una estructura de control que permite ejecutar de manera repetitiva un bloque de instrucciones.

![Conceptos Generales de Programación_05-06-2025-4.png](/imagenes/Conceptos%20Generales%20de%20Programaci%C3%B3n_05-06-2025-4.png)

**Ejemplo en C#**:

Un usuario tiene varios productos en su carrito y queremos mostrar la lista.

```csharp
string[] carrito = { "Laptop", "Mouse", "Teclado" };

for (int i = 0; i < carrito.Length; i++)
{
    Console.WriteLine($"Producto {i + 1}: {carrito[i]}");
}

```

- **FOR EACH**: Se utiliza para recorrer los elementos de una colección (como arreglos o listas) sin necesidad de usar un índice explícito.

![Conceptos Generales de Programación_05-06-2025-5.png](/imagenes/Conceptos%20Generales%20de%20Programaci%C3%B3n_05-06-2025-5.png)

**Ejemplo en C#**:

Recorre una lista de productos en un inventario.

```csharp
string[] productos = { "Pan", "Leche", "Huevos", "Queso" };

foreach (string producto in productos)
{
    Console.WriteLine($"Producto disponible: {producto}");
}

```

- **WHILE**: Este validará la condición primero y de ser válida, regresará a la condición.

![Conceptos Generales de Programación_05-06-2025-6.png](/imagenes/Conceptos%20Generales%20de%20Programaci%C3%B3n_05-06-2025-6.png)

**Ejemplo en C#**:

Un sistema de inventario descuenta unidades de un producto mientras haya stock disponible.

```csharp
int stock = 5;

while (stock > 0)
{
    Console.WriteLine($"Producto vendido. Stock restante: {stock}");
    stock--;
}

```

- **DO WHILE**: Parecido al while pero este se cumple al menos una vez sin importar las condiciones.

![Conceptos Generales de Programación_05-06-2025-7.png](/imagenes/Conceptos%20Generales%20de%20Programaci%C3%B3n_05-06-2025-7.png)

**Ejemplo en C#**:

Un usuario debe ingresar su contraseña correcta para acceder al sistema.

```csharp
string contraseña;

do
{
    Console.Write("Ingrese su contraseña: ");
    contraseña = Console.ReadLine();
} 
while (contraseña != "segura123");

Console.WriteLine("¡Acceso concedido!");
```

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