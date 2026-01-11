---
Date: 2025-08-08
Time: 01:52
tags:
- enciclopedia
- aprenderProgramacion
slug: programacion-iii-introduccion-a-la-programacion-orientada-a-objetos
title: Programación III - Introducción a la Programación Orientada a Objetos
---

---

La programación orientada a objetos es una forma de organizar el código en "objetos", los cuales representan cosas del mundo real o conceptos abstractos. Cada uno tiene su propia información (*atributos*) y comportamientos (*métodos*), y permiten aplicar reglas, las cuales evitan que se pueda acceder a estos datos de manera no controlada.

Por ejemplo: Un objeto `Auto` puede tener atributos como `Color` y `Velocidad`, y métodos como `Arrancar()` o `Frenar()`.

**Los beneficios y objetivos de POO son**:

- **Natural**: Se parece a cómo pensamos en el mundo real.
- **Confiable**: Un programa bien diseñado y codificado va a funcionar como es esperado sin importar el tamaño, y el testing se vuelve más sencillo.
- **Reusable**: Una vez un problema es resuelto se puede volver a usar la solución.
- **Fácil de mantener**: Un bug se puede resolver corrigiendo una sola parte del código. Se estima que del 60%-80% del trabajo en un programa es el mantenimiento, el 20% es el desarrollo.
- **Extensible**: Podemos añadir nuevas funciones sin muchas dificultades.
- **Oportuno**: Varios programadores pueden trabajar en paralelo.

### I. Diferencias entre POO y la programación estructurada

A diferencia de la programación estructurada, donde el código se escribe en *funciones* que resuelven un problema lógico y este se ejecuta en orden de arriba hacia abajo, en POO el código se organiza en *clases* y *objetos*. No importa el orden en que se escriban, lo importante es cómo se relacionan.

Algunos lenguajes como Python o JavaScript no usan archivos de clase de la misma manera que Java o C#, pero siguen permitiendo la programación orientada a objetos. En su lugar, organizan el código en módulos, lo que ayuda a manejar proyectos grandes de manera ordenada.

**Ejemplo en C#**:

Vamos a mostrar un mensaje cuando un auto se enciende.

**Programación estructurada**:

```csharp
void Encender()
{
    Console.WriteLine("El auto está encendido");
}

Encender();
```

- Aquí simplemente tenemos una función que imprime el mensaje. No existe un concepto de "auto", solo instrucciones.

**Programación Orientada a Objetos**:

```csharp
class Auto
{
    public void Encender()
    {
        Console.WriteLine("El auto está encendido");
    }
}

Auto miAuto = new Auto();
miAuto.Encender();
```

- Aquí, agrupamos el comportamiento dentro de una clase que representa al objeto `Auto`.
- Dentro de `Auto`, definimos un método `Encender()` que describe lo que puede hacer.
- Finalmente, podemos generar copias de `Auto` en cualquier parte del programa y ejecutar su comportamiento, sin necesidad de volver a escribir el mismo código.

Este ejemplo todavía no aprovecha todas las ventajas de la POO, pero nos sirve para ver la diferencia de enfoque.

Desde aquí se recomienda usar proyectos de **Aplicación de consola (.NET Framework)** en Visual Studio, ya que generan automáticamente una clase inicial que facilita organizar y ejecutar los ejemplos de POO. Además, se utilizarán herramientas del Framework de (.NET).

### II. Los principios de POO

- **Encapsulación**: Consiste en agrupar los datos (atributos) y los comportamientos (métodos) dentro de un mismo objeto, el cual solo debe permitir el acceso a su información a otros objetos con los que va a interactuar.
- **Abstracción**: Permite mostrar solo los detalles importantes de un objeto al usuario final, ocultando los internos.
- **Herencia**: Permite que una clase aproveche los atributos y métodos de una ya existente sin tener que repetir el código, sino únicamente adicionando lo que le falte.
- **Polimorfismo**: Es la capacidad que tiene un método para comportarse de distintas maneras según el objeto que lo esté usando.
- **(+) Composición**: Aunque no es un principio oficial de POO la composición es un concepto importante, que establece que un objeto puede estar formado por otros objetos, formando una relación de dependencia entre ellos.

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