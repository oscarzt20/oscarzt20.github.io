---
Title: Programación VI - Estructuras de Datos Abstractos
Date: 2025-08-08
Hora: 02:01
tags: ['enciclopedia', 'aprenderProgramacion']
---

---

## I. Estructuras de datos abstractos

En POO, son modelos que permiten organizar y gestionar datos de manera eficiente. Estas estructuras permiten almacenar objetos y manipularlos según ciertas reglas de acceso y recorrido.

### 1.1 Estructuras de datos lineales

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

### 1.2 Estructura de datos no lineales

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