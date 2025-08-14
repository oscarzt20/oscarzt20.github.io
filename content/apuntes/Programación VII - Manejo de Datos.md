---
Title: Programación VII - Manejo de Datos
Date: 2025-08-08
Hora: 02:04
tags: ['enciclopedia', 'aprenderProgramacion']
---

---

## I. Manejo de datos en POO

Es común que los objetos contengan información importante que debe conservarse incluso después de que el programa finaliza. Para lograr esto se aplican técnicas como la serialización, que permiten guardar y recuperar el estado de los objetos desde archivos. Esto hace posible mantener configuraciones o datos entre ejecuciones, así como permitir que la información se comparta fácilmente entre distintos sistemas o plataformas.

### 1.1 Persistencia

En POO, la persistencia se refiere a guardar el estado de un objeto para luego reconstruirlo cuando se necesite. Es decir, permite que los datos de un programa no se pierdan cuando el programa finaliza.

### 1.2 Serialización Binaria (POO)

La serialización binaria convierte un objeto en una secuencia de bytes, que puede almacenarse en un archivo o enviarse a través de la red. Posteriormente, puede recuperarse mediante deserialización, restaurando el estado exacto del objeto.

Solo puede ser interpretado por sistemas que conozcan su estructura interna, ya que no está en un formato legible.
### 1.3 Serialización con XML (Programación estructurada)

La serialización XML convierte un objeto en texto legible, utilizando etiquetas `<xml>`. Es una forma estructurada y estandarizada, útil para la portabilidad con otros sistemas o lenguajes.

La desventaja es que cualquiera puede abrir el archivo y modificarlo, por lo que tiene menor seguridad por default.

#### Serialización normal con XML

Este tipo de serialización toma un objeto único y lo transforma en un archivo XML plano. Solo se guarda el estado de una instancia y no incluye relaciones con otros objetos.
#### Serialización por composición con XML

Este enfoque permite serializar un objeto compuesto por otros objetos, reflejando sus relaciones en POO.

### 1.4 Deserialización

La deserialización es el proceso inverso: convertir los datos almacenados (binarios o XML) de nuevo en objetos en memoria. Esto permite recuperar el estado original del objeto y seguir trabajando con él en el programa.


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