---
Title: Bases de Datos II - Diagramas y Documentación
Date: 2025-08-08
Hora: 02:11
tags: ['enciclopedia', 'aprenderBD']
---

---

## I. Diagramas representativos

### 1.1 Diagrama de entidad relación

Es la representación gráfica de cada uno de los requerimientos representados en entidades, atributos y relaciones.

- Entidad: Es un objeto o una cosa del mundo real que es distinguible de los demás objetos. Ejemplo: Mesa
- Atributos: Son las características de a entidad. Ejemplo: Material
- Relaciones: Cardinalidad

| **Figura** | **Representación**                                                                                     |
| ---------- | ------------------------------------------------------------------------------------------------------ |
| Rectángulo | Entidades. Ejemplo: Cliente, Proveedores...                                                            |
| Elipse     | Atributos: Puntuado derivadas, doble para multivaluado, subrayado es clave primaria. Ejemplo: Teléfono |
| Rombo      | Conjunto de Relaciones. Ejemplo: Compra, Vende, Atiende...                                             |

### 1.2 Diagrama relacional

Es una representación en forma de tablas que representa una base de datos relacional, donde sus columnas (atributos) y las relaciones entre ellas mediante llaves foráneas y primarias.

- Una base de datos es un conjunto de tablas.
- Una tabla está compuesta por registros denominados también como filas o duplas.
- Un registro está compuesto por campos a los que también se llaman columnas o atributos.
- Las claves nos permiten acceder a los registros de una tabla.
- Una clave candidata es un campo o una combinación de campos que identifican un atributo de forma exclusiva.
- Una clave primaria es una clave candidata que ha sido designada para identificar de forma única los registros de una tabla.
- Las bases de datos relacionales son aquellas en las que cualquier tabla puede relacionarse con otra tabla a través de claves.

Notas: Si cambian los datos, pueden tener su tabla aparte.

#### Tipos de claves en un diagrama relacional

##### Claves primarias (llaves primarias)

Atributo que garantiza que cada entidad es única. Las claves candidatas son aquellas que pueden cumplir este propósito. Las claves primarias son las elegidas. Ejemplo: Matrícula, CURP, RFC

- Cada entidad debe tener una clave primaria.
- Las claves primarias van subrayadas.

##### Claves candidatas

Son aquellas llaves que son candidatas a ser clave primaria.

##### Claves foráneas

Una clave foránea o externa se compone de uno o varios atributos, que forman una clave primaria en otra tabla a la cual se desea relacionar.

- Se puede cambiar el nombre de la clave foránea, no necesariamente debe ser la misma que la clave primaria de la tabla con la que se relaciona.

## II. Diccionario de datos

Es un repositorio descentralizado de información sobre los datos que se utilizan en un sistema de gestión de bases de datos o en una aplicación.

Contiene descripciones detalladas en forma de tabla, de las variables, tablas, atributos y relaciones dentro de un sistema de base de datos.

Se debe considerar el front-end.

### 2.1 Datos del diccionario

- Nombre del campo o atributo
- Tipo de dato
- Tamaño del campo
- Descripción que explique el dato
- Valor permitido válido para ese atributo (Dominio)
- Relaciones del dato con otros (Claves foráneas, etc.)
- Reglas de validación para verificar que el dato sea correcto (Ejemplo: no se permiten valores negativos)

### 2.2 Importancia

- Análisis de requerimientos. Ayuda a comprender los datos necesarios para una solución
- Diseño de bases de datos
- Desarrollo
- Mantenimiento

---

## / Más Información

- [Bases de Datos I - Conceptos Básicos](/apuntes/bases-de-datos-i---conceptos-básicos/)
- [Bases de Datos II - Diagramas y Documentación](/apuntes/bases-de-datos-ii---diagramas-y-documentación/)
- [Bases de Datos III - Reglas de Normalización](/apuntes/bases-de-datos-iii---reglas-de-normalización/)
- [Bases de Datos IV - Álgebra Relacional](/apuntes/bases-de-datos-iv---álgebra-relacional/)
- [Bases de Datos V - Microsoft SQL](/apuntes/bases-de-datos-v---microsoft-sql/)
- [Bases de Datos VI - Estructura Básica de SQL](/apuntes/bases-de-datos-vi---estructura-básica-de-sql/)
- [Bases de Datos VII - Consultas de Datos](/apuntes/bases-de-datos-vii---consultas-de-datos/)
- [Bases de Datos VIII - Automatización y Seguridad](/apuntes/bases-de-datos-viii---automatización-y-seguridad/)
- [Bases de Datos IX - Operaciones Avanzadas de SQL](/apuntes/bases-de-datos-ix---operaciones-avanzadas-de-sql/)

---