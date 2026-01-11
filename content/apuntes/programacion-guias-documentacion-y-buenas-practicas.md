---
Date: 2025-08-08
Time: 02:07
tags:
- enciclopedia
- aprenderProgramacion
slug: programacion-guias-documentacion-y-buenas-practicas
title: Programación - Guías Documentación y Buenas Prácticas
---

---

## I. Guía de nomenclatura en programación

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

> Siempre evitar utilizar las palabras reservadas de cada lenguaje.

## II. Documentación y buenas prácticas

### 2.1 Recomendaciones

**Antes de programar**:

1. Definir bien los requisitos del programa.
2. Escribir el pseudocódigo.
3. Identificar las variables que se van a utilizar.
4. Describir los posibles escenarios.
5. Realizar el diagrama de actividades.
6. Realizar la prueba de escritorio.
7. Escribir el programa en C#.

**Al programar en POO:**

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

### 2.2 Documentación del código

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

### 2.3 Diagrama de clases

Se usa para modelar la estructura de clases en la programación orientada a objetos. Muestra las clases, sus atributos, métodos y relaciones (herencia, asociación, composición, etc.).

![Plataformas Abiertas 1_05-06-2025-7.png](/imagenes/Plataformas%20Abiertas%201_05-06-2025-7.webp)

Las relaciones entre clases se representan de diferente manera:

| **Relación**    | **Significado**                     | **Representación**                        |
| --------------- | ----------------------------------- | ----------------------------------------- |
| **Dependencia** | "Usa"                               | Línea punteada con flecha abierta `---->` |
| **Asociación**  | "Conoce a" / "Trabaja con"          | Línea continua con flechas abiertas `──>` |
| **Agregación**  | "Tiene un" (existe por separado)    | Línea con rombo blanco `----◊`            |
| **Composición** | "Tiene un" (no existe por separado) | Línea con rombo negro `----◆`             |
| **Herencia**    | "Es un"                             | Línea con flecha triangular vacía `──▷`   |

![Programación Orientada a Objetos_21-07-2025.png](/imagenes/Programaci%C3%B3n%20Orientada%20a%20Objetos_21-07-2025.webp)

## III. Excepciones y manejo de errores

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