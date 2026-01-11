---
Date: 2025-08-08
Time: 02:06
tags:
- enciclopedia
- aprenderProgramacion
slug: programacion-ix-patrones-de-diseno
title: Programación IX - Patrones de Diseño
---

---

Un patrón de diseño es una solución reutilizable, comprobada y estructurada a un problema común que aparece constantemente al diseñar sistemas orientados a objetos.

Básicamente, son guías o plantillas que ayudan a resolver un problema específico de diseño.

**Sus elementos son**

- **Nombre**: Forma de referirse al patrón de diseño.
- **Problema**: Explica cuándo debe usarse el patrón.
- **La solución**: Describe la estructura general, las clases involucradas, las relaciones entre ellas y cómo colaboran para resolver el problema.
- **Las consecuencias**: Analiza el impacto del patrón, tomando en cuenta el costo/beneficio, espacio/tiempo, lenguaje, impacto en flexibilidad, extensión y portabilidad.

Los patrones de diseño se agrupan en tres categorías, según el tipo de problema que ayudan a resolver.
## I. Patrones de creación

Se enfocan en cómo se crean los objetos. Permiten crear instancias de forma flexible.

- **Fábrica abstracta**: Permite crear objetos relacionados sin especificar sus clases concretas.
- **Método fábrica**: Delega la creación de objetos a una subclase.
- **Prototipo**: Clona objetos a partir de una instancia de prototipo existente.
- **Singleton**: Asegura que solo exista una instancia de una clase y provee un punto de acceso global.

## II. Patrones de estructura

Ayudan a organizar las clases u objetos en estructuras más grandes sin perder flexibilidad. Mejoran la reutilización de componentes.

- **Adaptador**: Convierte la interfaz de una clase en otra esperada por el cliente.
- **Puente**: Separa una abstracción de su implementación para que ambas puedan variar.
- **Decorador**: Añade funcionalidades a un objeto de forma dinámica sin modificar su clase.
- **Fachada**: Proporciona una interfaz simplificada a un conjunto complejo de clases.
- **Proxy**: Controla el acceso a un objeto, actuando como intermediario.

## III. Patrones de comportamiento

Ayudan a definir la comunicación entre objetos en el sistema y cómo es controlado el flujo.

### Patrón Estrategia

Este se forma con una familia de algoritmos que están encapsulados. El objetivo es hacer esos algoritmos intercambiables y usar el mejor para cada caso.

**Características**:

- El usuario selecciona que algoritmo usar.
- Si tenemos un problema que provee una funcionalidad, pero existen varias formas de llevarla a cabo, se puede usar este patrón.
- Puede hacerse vía herencia o con implementación de interfaz.

**Diagrama de clases**:

![Patrones Orientados a Objetos_18-08-2025.png](/imagenes/Patrones%20Orientados%20a%20Objetos_18-08-2025.webp)

**Ejemplos**:

- Guardado de archivos en diferentes formatos.
- Compresión con diferentes algoritmos.
- Formas de representar información.


- **Comando**: Encapsula una solicitud como un objeto, permitiendo parametrizar y deshacer operaciones.
- **Interprete**: Define una gramática y un intérprete para entender y procesar expresiones.
- **Iterador**: Permite recorrer una colección sin exponer su implementación interna.
- **Observador**: Notifica automáticamente a múltiples objetos cuando el estado de otro cambia.
- **Estrategia**: Permite definir una familia de algoritmos y seleccionarlos dinámicamente.

### 1.4 Anti-patrones

Los anti-patrones representan malas soluciones que se aplican comúnmente a problemas de diseño, pero que resultan en malos resultados.

- Muestran prácticas que parecen buenas al inicio, pero fallan a largo plazo.
- También incluyen recomendaciones sobre cómo salir de una mala implementación hacia una solución más adecuada.


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