---
Date: 2025-08-08
Time: 02:10
tags:
- enciclopedia
- aprenderBD
slug: bases-de-datos-i-conceptos-basicos
title: Bases de Datos I - Conceptos Básicos
---

---

## I. Bases de datos

Una base de datos se puede percibir como un gran almacén de datos, que se utiliza al mismo tiempo por distintos usuarios.

En relevante tanto a nivel persona (permite desarrollar software sin estar en una empresa), como a nivel empresa (análisis de datos).

Un registro es una fila o dupla: Registro = Filas = Dupla
Los componentes de las bases de datos son:

- Datos
- Software
- Recursos humanos

### 1.1 Back-end

Administración de los datos en relación con la interacción con los usuarios. Es vital para el funcionamiento de las funciones de una página o programa.

### 1.2 Tipos de atributos

- **Mono-valuados**: Tienen un único valor asociado a una entidad, y que solo se puede tener uno. Ejemplo: Matrícula, Apellidos (paterno y materno)
- **Multivaluados**: Tienen un conjunto de valores para una entidad específica. Ejemplo: teléfonos, correos
- **Compuestos**: Son atributos que se pueden descomponer en elementos más pequeños. Ejemplo: Dirección, Nombre
- **Derivados**: Sus atributos se pueden obtener en base a otros atributos relacionados. Ejemplo: El atributo Edad se deriva del atributo Fecha de nacimiento y Fecha actual
- **Nulo**: Cuando una entidad no tiene un valor para un atributo. Ejemplo: Atributos opcionales que no tienen respuesta en formularios
### 1.3 Cardinalidad

Expresa las relaciones entre entidades, mediante el número de entidades a las que otra entidad puede estar relacionada. Ejemplo: (Entidad1: Docente, Entidad2: Curso. Las relaciones son la cardinalidad) Tipos:

- **1 a muchos**: 1 docente puede impartir varios cursos (1_m) o (1_asterisco)
- **1 a 1**: 1 docente puede impartir un curso (1_1)
- **muchos a muchos**: un docente puede impartir varios cursos y varios cursos pueden ser impartidos por muchos docentes (n:n) ó (n_m)

### 1.4 Tipos de bases de datos

#### Modelo de bases de datos relacionales

- Se organizan en tablas con relaciones definidas mediante claves primarias y foráneas.
- Entre sus ventajas se encuentra: Estandarizado, eficiente.

#### Modelo de datos jerárquico

- Organización en forma de árbol, con un nodo raíz y niveles
- Tienen relación padre-hijo

#### Modelo de datos en red

- Relaciones complejas no jerárquicas
- Complejo de usar

#### Modelo de datos orientado a objetos

- Se usa el encapsulamiento, donde se ocultan detalles internos, exponiendo sólo los métodos para acceder a ellos. (Público, Privado, Protegido)
- Los objetos pueden heredar propiedades y métodos, promoviendo la reutilización de código
- Los objetos se pueden comportar de diversas maneras según su tipo, aumentando la flexibilidad. El polimorfismo establece que un objeto sea abstracto, de manera que otros sean lo que lo definan

---

## / Más Información

- [Bases de Datos I - Conceptos Básicos](/apuntes/bases-de-datos-i-conceptos-basicos/)
- [Bases de Datos II - Diagramas y Documentación](/apuntes/bases-de-datos-ii-diagramas-y-documentacion/)
- [Bases de Datos III - Reglas de Normalización](/apuntes/bases-de-datos-iii-reglas-de-normalizacion/)
- [Bases de Datos IV - Álgebra Relacional](/apuntes/bases-de-datos-iv-algebra-relacional/)
- [Bases de Datos V - Microsoft SQL](/apuntes/bases-de-datos-v-microsoft-sql/)
- [Bases de Datos VI - Estructura Básica de SQL](/apuntes/bases-de-datos-vi-estructura-basica-de-sql/)
- [Bases de Datos VII - Consultas de Datos](/apuntes/bases-de-datos-vii-consultas-de-datos/)
- [Bases de Datos VIII - Automatización y Seguridad](/apuntes/bases-de-datos-viii-automatizacion-y-seguridad/)
- [Bases de Datos IX - Operaciones Avanzadas de SQL](/apuntes/bases-de-datos-ix-operaciones-avanzadas-de-sql/)

---