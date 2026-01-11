---
Date: 2025-08-08
Time: 02:16
tags:
- enciclopedia
- aprenderBD
slug: bases-de-datos-iv-algebra-relacional
title: Bases de Datos IV - Álgebra Relacional
---

---

## I. Álgebra relacional

Las bases de datos relacionales requieren de un conjunto de operaciones que permiten manipular la base de datos. Date (2001) menciona que el álgebra relacional es un conjunto de operadores que toman sus relaciones como sus operandos y regresan una relación como resultado.
### 1.1 Operadores relacionales

- **σ (sigma)**: Representa la **operación de selección**, que filtra las filas de una relación basándose en una condición.
- **π (pi)**: Representa la **operación de proyección**, que selecciona columnas específicas de una relación.
- **∪ (unión)**: Representa la **unión** de dos relaciones.

### 1.2 Operadores de condición

- **< (Menor que)**: Compara si un valor es menor que otro.
- **> (Mayor que)**: Compara si un valor es mayor que otro.
- **<= (Menor o igual a que)**: Compara si un valor es menor o igual a otro.
- **>= (Mayor o igual a que)**: Compara si un valor es mayor o igual a otro.
- **= (Igual a)**: Verifica si dos valores son iguales.

### 1.3 Representación de una expresión

Se puede representar de 3 maneras:

- **Texto**: Descripción.
> Muestra *todos* los datos de *empleados* que tengan un *salario de 4000*
- **Álgebra Relacional**: Expresión Relacional.
$$\sigma({\pi\text{salario} = 4000} (\text{Empleados})) $$
- **Código SQL**: Código.
```
SELECT * FROM Empleados WHERE salario = 4000;
```

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