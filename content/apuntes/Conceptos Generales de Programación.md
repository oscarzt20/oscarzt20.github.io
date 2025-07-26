---
Title: Conceptos Generales de Programación
Fecha: 2025-06-02
Hora: 1085
tags: ['programacion', 'enciclopedia', 'post']
---

---

La programación es el proceso de escribir instrucciones para que una computadora realice tareas específicas. Antes de empezar a programar, es importante conocer los fundamentos necesarios para entender cómo funciona la programación.

## I. Algoritmos

Para programar, los desarrolladores crean algoritmos, que son secuencias ordenadas de pasos que resuelven un problema o llevan a cabo una tarea.

### 1.1 Características de los algoritmos

- **Finito**: Un algoritmo debe terminar después de un número determinado de pasos. Se evitan los bucles sin fin.
- **Preciso**: No debe haber interpretaciones subjetivas sobre lo que se debe hacer en cada instrucción.
- **Con inicio y final/es**: Debe tener un inicio y puede contener más de un final.
- **Eficaz en la solución del problema**: El algoritmo debe resolver el problema de manera correcta y óptima, evitando pasos innecesarios o ineficientes.

### 1.2 Tipos de algoritmos

- **Cualitativos**: Emplean palabras, ej. receta de cocina.
- **Cuantitativos**: Utilizan cálculos numéricos, ej. resolver una ecuación de 2° grado.

### 1.3 Lenguajes algorítmicos

Conjunto de símbolos y reglas que permiten explicar un proceso.

#### Lenguajes algorítmicos gráficos

- **Diagrama de flujo**: Es una representación gráfica de un algoritmo o proceso, utilizando distintos símbolos conectados por flechas que indican el flujo de ejecución. Se usa para facilitar la comprensión del programa y ayudar a detectar errores. Los símbolos usados son:
	- **Círculo**: Indica el inicio y el fin del algoritmo.
	- **Rectángulo**: Expresa una acción o proceso a realizar.
	- **Rombo**: Representa una decisión (condición lógica).
	- **Flechas**: Indican el flujo del proceso.

**Ejemplo de diagrama de flujo**:

Algoritmo que determina si un número es par o impar.

![Conceptos Generales de Programación_05-06-2025-1.png](/imagenes/Conceptos%20Generales%20de%20Programaci%C3%B3n_05-06-2025-1.png)

#### Lenguajes algorítmicos no gráficos

- **Pseudocódigo**: Es una forma de representar algoritmos utilizando un lenguaje intermedio entre el lenguaje natural y un lenguaje de programación. Sirve para planificar la lógica de un programa y facilitar su comprensión antes de escribir código.

**Ejemplo de pseudocódigo**:

Algoritmo para anotar un gol en un partido de fútbol.

```
1. Inicio.
2. Entrar a la cancha de fútbol con el equipo adecuado.
3. Esperar la indicación del inicio del partido.
4. Localizar el balón.
5. Correr hacia el balón.
6. Ganar control del balón.
7. ¿Se tiene posesión del balón?
	1. Sí, continuar al paso 8.
	2. No, regresar al paso 4.
8. Localizar la portería deseada.
9. Patear la pelota levemente y repetidamente en dirección a la portería.
10. Evitar intentos del equipo contrario de arrebatar el control del balón.
11. ¿Se mantuvo el control del balón?
	1. Sí, continuar al paso 12.
	2. No, regresar al paso 4.
12. Una vez frente a la portería, a un mínimo de 5 metros de distancia, cambiar rápidamente a posición de tiro.
13. Identificar un espacio en la portería donde sea menos accesible para el portero.
14. Patear la pelota con suficiente fuerza en dirección hacia dentro de la portería, usando el empeine del pie hábil.
15. ¿Se logró anotar el gol?
	1. Sí, festejar con el equipo propio.
	2. No, regresar al paso 4.
16. Fin.
```

### 1.4 Metodología general para solucionar algoritmos

1. **Definición del problema**: Debe ser clara y precisa.
2. **Análisis del problema**: Colocarse en el lugar del ordenador y buscar lo que se necesita para cumplir la tarea. Lleva:
	- Datos de entrada.
	- Información a producir (salida)
	- Métodos y fórmulas para analizar datos.
3. **Diseño del algoritmo**:
	- Debe tener un punto particular de inicio.
	- No debe ser ambiguo.
	- Debe ir de lo general a lo particular.
	- Debe ser finito en tamaño y tiempo de ejecución.
	- Debe hacerse la prueba de escritorio (se toman datos límite de entrada y se sigue el algoritmo para validarlo).

## II. Clasificación de los lenguajes de programación

### 2.1 Niveles de abstracción

- **Bajo nivel**: Aquellos lenguajes que controlan el hardware del ordenador. Ej. Lenguaje Ensamblador, Código Máquina o Binario.
- **Alto nivel**: Son más parecidos al lenguaje natural humano y abarca el 99% de lenguajes de programación.
- **Nivel intermedio**: Puede usar elementos de los dos anteriores. El único que lo hace es el C.

### 2.2 Lenguajes compilados e interpretados

- **Lenguaje compilado**: Se toma el código en alto nivel y lo convierte en bytes, y al final nos dará un archivo ejecutable. Tiene mejor rendimiento al ejecutarse aunque ocupa más memoria que el interpretado.
- **Lenguaje interpretado**: Se interpreta línea a línea en tiempo real al ejecutarse (Ej. JavaScript, Python). Tiene un rendimiento algo más lento que el compilado pero ocupa menos memoria.
- **Lenguaje híbrido**: Algunos lenguajes combinan ambos enfoques, primero, el código es compilado a un formato intermedio llamado bytecode, luego este bytecode es ejecutado por un intérprete o máquina virtual (JVM en Java, CLR en C#) (Ej. Java, C#, Kotlin).

## III. Componentes básicos de la programación

### 3.1 Tipos de datos simples

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

### 3.2 Atributos

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

### 3.3 Operadores

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

### 3.4 Expresiones lógicas

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

### 3.5 Estructuras de control de flujo

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

## IV. Guía de nomenclatura en programación

Las convenciones ampliamente aceptadas en la industria para la nomenclatura en programación son:

| **Elemento**                   | **Convención**                                                                                                        | **Ejemplo**                                    |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| **Nombre del proyecto**        | `PascalCase` o `kebab-case` Usa nombres claros, únicos y profesionales.                                               | MiProyecto, mi-proyecto                        |
| **Organización de carpetas**   | `lowercase` o `kebab-case`                                                                                            | controllers/, user-data/                       |
| **Variables**                  | `camelCase` Nombres significativos, evita abreviaciones ambiguas. Singular para datos únicos, plural para colecciones | userName, totalItems                           |
| **Constantes**                 | `UPPER_SNAKE_CASE`                                                                                                    | PI, API_BASE_URL                               |
| **Funciones y Métodos**        | `camelCase` o `PascalCase` Usa verbos                                                                                 | getUser(), ProcessOrder()                      |
| **Clases y Objetos**           | `PascalCase` con sustantivos para clases, `kebab-case` para archivos con sufijos descriptivos                         | ShoppingCart, user-profile.js, cart.service.js |
| **Propiedades**                | Se toma el nombre del atributo y se pasa a `PascalCase`                                                               | public int Edad { get {  } set {  } }          |
| **Assets (Recursos)**          | `kebab-case` o `snake_case`, agrupados en carpetas                                                                    | icon-home.svg, assets/images/, assets/fonts/   |
| **Commits**                    | `<tipo>(área): descripción breve` Tipos: feat, fix, docs, test                                                        | feat(auth): add login feature                  |
| **Configuración del Proyecto** | `Ramas` y `versiones organizadas`                                                                                     | feature/login-page, v1.0.0                     |
| **Bases de Datos y Eventos**   | Tablas/campos en `snake_case`y eventos en `verbo-nombre`                                                              | user_profiles, created_at, user-logged-in      |

> [!NOTE]
> Siempre evitar utilizar las palabras reservadas de cada lenguaje.

## V. Paradigmas de programación

Un paradigma de programación es una forma de pensar o estilo de programación que define cómo se estructuran y organizan los programas. Los paradigmas afectan la forma en que se diseñan, implementan y mantienen los programas, influyendo en factores como la legibilidad, escalabilidad y eficiencia del código.

- **Programación estructurada o imperativa**: Es el estilo más simple, donde el código se ejecuta de arriba hacia abajo en un único archivo o función principal. Se usa para aprender los fundamentos de la programación.
- **Programación orientada a objetos**: Organiza el código en clases y objetos que representan entidades del mundo real. Facilita la reutilización y mantenimiento del código.
- **Programación funcional**: Se basa en funciones matemáticas puras y evita modificar variables globales. Es ideal para programación concurrente y análisis de datos.
- **Programación orientada a eventos**: Es un paradigma en el que el flujo de ejecución del programa está determinado por eventos, como interacciones del usuario (clics, teclas presionadas), mensajes del sistema o respuestas de otros programas. En lugar de ejecutarse secuencialmente, el programa reacciona a eventos mediante manejadores o listeners que se activan cuando ocurre un evento específico.

## VI. Tips

**Antes de programar**:
1. Definir bien los requisitos del programa.
2. Escribir el pseudocódigo.
3. Identificar las variables que se van a utilizar.
4. Describir los posibles escenarios.
5. Realizar el diagrama de actividades.
6. Realizar la prueba de escritorio.
7. Escribir el programa en C#.

---

## / Más Información

- **Anterior**: `[[Principios de la Ingeniería de Software]]`
- **Siguiente**: [Programación Orientada a Objetos](/apuntes/programación-orientada-a-objetos/)

### Lenguajes de programación

- `[[C Sharp]]`
- `[[Java]]`
- `[[JavaScript]]`
- `[[Python]]`

---