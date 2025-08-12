---
Title: Bases de Datos III - Reglas de Normalización
Fecha: 2025-08-08
Hora: 02:11
tags: ['enciclopedia', 'post']
---

---

## I. Normalización

Es la transformación del diseño de la base de datos a uno más simple y estable, sin ambigüedad.

Esto es importante para optimizar y garantizar que no haya ambigüedades (Pérdida de datos, etc.).

### 1.1 Regla/Forma 1

Una tabla está en **Primera Forma Normal (1NF)** si cumple con lo siguiente:

- **Atomicidad:** Cada celda contiene un único valor atómico (no listas, conjuntos ni estructuras anidadas).
- **Clave primaria:** Debe existir una clave primaria que identifique unívocamente cada fila.
- **Sin duplicados:** No debe haber filas duplicadas.
- **Uniformidad:** Cada columna debe contener valores de un solo tipo de dato (coherentes para cada fila).

**Recomendación:** Los datos compuestos (como nombres completos) o valores múltiples (como listas de teléfonos) deben descomponerse en datos atómicos. No se permiten rangos ni conjuntos de valores en una celda.

### 1.2 Regla/Forma 2

Una tabla está en **Segunda Forma Normal (2NF)** si:

- Está en 1NF.
- **Sin dependencias parciales** Ocurren cuando un atributo depende de parte de una clave primaria compuesta y no de la clave primaria completa. Es decir, se crean tablas independientes para conjuntos de valores que se apliquen a varios registros.
- **Llaves foráneas**: Las tablas se relacionan mediante llaves foráneas.

### 1.3 Regla/Forma 3

Una tabla está en **Tercera Forma Normal (3NF)** si:

- Está en 2NF.
- **Sin dependencias transitivas**: Los atributos no clave dependen exclusivamente de la clave primaria y no de otros atributos no clave. Es decir, al tener dos entidades conectadas de muchos a muchos, se crea una tabla intermedia que incluye las claves primarias de ambas tablas como claves foráneas y con el nombre de ambas entidades.
- **Se separan los catálogos**: Surge el catálogo, donde los datos ya están definidos, como tipos de categorías. (Dato de un atributo, que tiene un rango limitado).

### 1.4 Regla/Forma 3.5 Boyce Codd

La **Forma Normal de Boyce-Codd** es una versión más estricta de la 3NF, y se cumple si:

- Está en 3NF.
- **Cada determinante es una clave candidata**: Cada atributo que determine a otro debe ser una clave candidata, o debe dividirse la tabla si causa dependencias funcionales. Es decir, si para cada dependencia funcional X - Y en la tabla, el conjunto X es una superclave. Una superclave es un conjunto de uno o más atributos de una tabla que puede identificar de manera única todas las filas de las tablas.
- **Sin dependencias funcionales**: No deben existir relaciones entre atributos fuera de las claves candidatas.
- En general, todos los atributos tienen que depender de la superclave. Ejemplo: Si tenemos la tabla Estudiantes: id_estudiante, nombreEstudiante, nombre_curso, profesor. Los datos de curso y el profesor no van en la tabla Estudiantes ya que no dependen de la superclave (id_estudiante), por lo que se separan en otra tabla donde se conecten.

### 1.5 Regla/Forma 4

Una tabla está en **Cuarta Forma Normal (4NF)** si:

- Está en 3.5NF.
- **Sin dependencias multivaluadas:** En una tabla sólo pueden haber 2 llaves foráneas. Se puede resolver al separar la tercera tabla y conectarla con otra. Ejemplo: Se tienen varias tablas que se relacionan a una sola y esto crea muchas combinaciones posibles, que pueden confundir, como un juguete que tiene aspectos de las tablas materiales colores tamaños, venta etc..

### 1.6 Regla/Forma 5

Una tabla está en **Quinta Forma Normal (5NF)** si:

- Está en 5NF.
- **Sin dependencias de unión**: Depuración, es decir, se optimizan las tablas para eliminar redundancias entre las tablas con relaciones.
### 1.7 Notas de normalización

- Pensar en cómo interaccionan los datos con el front-end.
- Los datos generados automáticamente, o que se ponen con un menú específico en la interfaz, no se coloca como tabla. Ejemplo: Fecha, en caso de que el usuario pueda elegirla de un calendario, ya que tiene un formato estándar. Es decir, si un dato se consigue en la interfaz, mediante un algoritmo programado y no de una base de datos. Por lo tanto, no va una tabla.
#### Dependencia transitiva

Se da al romper la ambigüedad generada por dos elementos que dependen entre ellos.

#### Creación de tablas normalizadas en diagrama relacional

**¿Cuándo se separa un atributo de una tabla?**

*Depende mucho de los requerimientos pero para darse una idea inicial:*

1. ¿El valor del atributo cambia con cierta frecuencia?
	- Sí: Se separa de la tabla.
	- No:
2. ¿Varias instancias del mismo elemento podrían compartir un mismo valor?
	- Si:
	- No: Se queda en la tabla.
3. ¿El atributo se trata de un catálogo? (Datos que pueden representarse en una lista o que tienen un rango de datos ya establecido)
	- Si: Se separa de la tabla.
	- No: Se queda en la tabla. (Ejemplo: Nombre)

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