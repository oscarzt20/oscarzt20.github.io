---
Title: Programación VIII - POO y la Programación Orientada a Eventos
Date: 2025-08-08
Hora: 02:05
tags: ['enciclopedia', 'aprenderProgramacion']
---

---

## I. POO y la programación orientada a eventos

La Programación Orientada a Eventos (POE) es un paradigma que se basa en la interacción con eventos, es decir, acciones que ocurren en el sistema, como hacer clic en un botón, mover el mouse, o recibir una notificación externa.

Cuando se combina con la Programación Orientada a Objetos (POO), permite crear aplicaciones interactivas donde los objetos pueden reaccionar a eventos. Este enfoque es común en interfaces gráficas de usuario y en sistemas donde las acciones del usuario determinan el flujo del programa como videojuegos.

### 1.1 Interfaces gráficas y eventos

En las interfaces gráficas, los eventos son disparados por acciones del usuario (clicks, teclas, movimientos), y se puede programar la reacción del sistema usando manejadores de eventos.

#### Eventos

Un evento es un mecanismo que permite que un objeto notifique a otros objetos cuando algo relevante ocurre.

En C#, los eventos se basan en delegados. Un evento necesita:

- **Un delegado** que define la firma del método que responderá al evento.
- **Un evento** declarado con la palabra clave event.
- **Uno o varios manejadores (handlers)** que se suscriben al evento.

#### Delegados

Un delegado es una especie de puntero a función, que define qué tipo de métodos se pueden invocar a través del evento.

#### Handlers

Un handler es un método que responde a un evento. Se suscribe a un evento y se ejecuta automáticamente cuando ese evento ocurre.

#### Sinks

Un sink es un término técnico usado para referirse al objeto que recibe el evento. Es decir, es el receptor del evento. También se puede considerar sink a la clase que contiene los handlers suscritos al evento.

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