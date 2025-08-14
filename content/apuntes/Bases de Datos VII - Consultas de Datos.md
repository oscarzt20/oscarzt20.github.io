---
Title: Bases de Datos VII - Consultas de Datos
Date: 2025-08-08
Hora: 02:21
tags: ['enciclopedia', 'aprenderBD']
---

---

## I. Consultas

### 1.1 Consultas básicas

Se usa `SELECT` para iniciar, `*` para hacer una selección global o se especifican los datos para especificar la búsqueda. Adicionalmente se usa `FROM` para especificar la tabla y `WHERE` para especificar una condición.

**Ejemplos**

- Consulta todos los archivos y sus características

```
SELECT * FROM sys.master_files;
```

- Consulta todas las bases de datos

```
SELECT * FROM sys.databases;
```

- Consulta las tablas, se cambia el nombre de la DB que se quiere ver

```
SELECT object_id, '['+SCHEMA_NAME(schema_id)+'].['+name+']'
AS [schema_table], max_column_id_used, type, type_desc, create_date, modify_date, lock_escalation_desc
FROM sys.tables;
```

- Consulta e texto o código fuente de un objeto en la base de datos, como una vista, procedimiento almacenado, función o disparador

```
sp_helpText contarDepartamentos;
```

- Consulta todo de los clientes con apellido paterno 'Martinez'

```
SELECT * FROM Clientes WHERE apellidoP = 'Martinez';
```

- Consulta el precio y las ventas de los productos de color 'azul'

```
SELECT precio, ventas FROM Productos WHERE color = 'azul';
```

### 1.2 Uso de JOIN

#### INNER JOIN

Combina filas de dos o más tablas en función de una condición de igualdad especificada en la cláusula `ON`. Solo devuelve las filas donde existe una coincidencia en ambas tablas. Se toma en cuenta la llave primaria y la foránea.

![Conceptos y Programación de Bases de Datos_26-07-2025.png](/imagenes/Conceptos%20y%20Programaci%C3%B3n%20de%20Bases%20de%20Datos_26-07-2025.png)

**Sintaxis**

```
SELECT columnas FROM TablaA INNER JOIN TablaB ON TablaA.id_tablaA = TablaB.id_tablaA WHERE columna9 = 'valor'
```

**Ejemplos**

- Consulta los nombres de los clientes y las fechas de los pedidos

```
SELECT Clientes.nombre, Pedidos.fecha FROM Clientes INNER JOIN Pedidos ON Clientes.id_cliente = Pedidos.id_cliente;
```

- Consulta el nombre del producto, la cantidad, la fecha y el nombre del cliente en 4 tablas

```
SELECT p.nombreProducto, dp.cantidad, pe.fecha, cl.nombre FROM Productos p INNER JOIN DetallesPedidos dp ON p.id_producto = dp.id_producto INNER JOIN Pedidos pe ON dp.id_pedido = pe.id_pedido INNER JOIN Clientes cl ON pe.id_pedido = cl.id_cliente;
```

#### LEFT JOIN

EI `LEFT JOIN` devuelve todas las filas de la tabla de la izquierda (en
este caso `clientes`), y las filas coincidentes de la tabla de la derecha
(`pedidos`). Si no hay coincidencia, el resultado mostrará `NULL` en las
columnas de la tabla de la derecha.

**Sintaxis**

```
SELECT columnas FROM TablaA LEFT JOIN TablaB ON TablaA.id_tablaA = TablaB.id_tablaA WHERE columna9 = 'valor'
```

**Ejemplo**

- En este caso la consulta de Promedio de ventas por cliente muestra únicamente los datos que se especifican y que coinciden en la tabla de la izquierda y pone en NULL las de la derecha que no.

```
SELECT Clientes.nombre, AVG(totalVenta) AS promedioVenta FROM Clientes LEFT JOIN Ventas ON Clientes.id_cliente = Ventas.id_cliente GROUP BY nombre;
```

#### RIGHT JOIN

EI `RIGHT JOIN` es lo contrario al `LEFT JOIN`. Devuelve todas las filas de
la tabla de la derecha (`pedidos`), y las filas coincidentes de la tabla de
la izquierda (`clientes`). Si no hay coincidencia, se mostrarán `NULL` en
las columnas de la tabla de la izquierda.

**Sintaxis**

```
SELECT columnas FROM TablaA RIGHT JOIN TablaB ON TablaA.id_tablaA = TablaB.id_tablaA WHERE columna9 = 'valor'
```

**Ejemplo**

- En este caso la consulta de Promedio de ventas por cliente muestra únicamente los datos que se especifican y que coinciden en la tabla de la derecha y pone en NULL las de la izquierda que no.

```
SELECT Clientes.nombre, AVG(totalVenta) AS promedioVenta FROM Clientes RIGHT JOIN Ventas ON Clientes.id_cliente = Ventas.id_cliente GROUP BY nombre;
```

#### FULL JOIN

FULL JOIN Devuelve filas cuando hay una coincidencia en una de las tablas, o ambas.

**Sintaxis**

```
SELECT columnas FROM TablaA FULL JOIN TablaB ON TablaA.id_tablaA = TablaB.id_tablaA WHERE columna9 = 'valor'
```

**Ejemplo**

- En este caso se muestra tanto lo que coincide como lo que no

```
SELECT Clientes.nombre, AVG(totalVenta) AS promedioVenta FROM Clientes FULL JOIN Ventas ON Clientes.id_cliente = Ventas.id_cliente GROUP BY nombre;
```

#### CROSS JOIN

Devuelve el producto cartesiano de ambas tablas, es decir, todas las combinaciones posibles de filas.

**Sintaxis**

```
SELECT * FROM Tabla1 CROSS JOIN Tabla2;
```

**Ejemplo**

- En este caso se muestra el producto cartesiano de todos los datos de Clientes y Ventas

```
SELECT * FROM Clientes CROSS JOIN Ventas;
```

### 1.3 Funciones

#### CONCAT(X, Y)

Concatena dos cadenas de texto.

**Ejemplo**

- Selecciona el `id` de `empleado` y el `nombre` con `apellido` y mostrar como `nombreCompleto`, de la tabla `empleados`

```
SELECT id_empleado, CONCAT(nombre, ' ', apellido) AS nombreCompleto FROM Empleados;
```

#### LENGTH(X)

Devuelve la longitud de la cadena X.

**Ejemplo**

- Muestra el nombre y el número de caracteres

```
SELECT id_empleado, nombre, LEN(nombre) AS longitudNombre FROM Empleados;
```

#### SUBSTRING(X, Start, Length)

Extrae una sub-cadena de X a partir de la posición Start con la longitud indicada.

**Ejemplo**

- Muestra el nombre y la versión en sub-cadena

```
SELECT id_empleado, nombre, SUBSTRING(nombre, 1, 3) AS subcadena FROM Empleados;
```

#### UPPER(X) / LOWER(X)

Convierte X a mayúsculas o minúsculas, respectivamente.

**Ejemplos**

- Muestra el nombre y en mayúsculas

```
SELECT id_empleado, nombre, UPPER(nombre) AS nombreMayusculas FROM Empleados;
```

- Muestra el nombre y en minúsculas

```
SELECT id_empleado, nombre, LOWER(nombre) AS nombreMinusculas FROM Empleados;
```

#### DATE

**Ejemplos**

- Obtener la fecha

```
SELECT GETDATE() AS fechaHoraActual;
```

- Agregar a la fecha 5 días

```
SELECT DATEADD(DAY, 5, '2025-02-03') AS nuevaFecha;
```

- Obtiene la diferencia en días de una fecha menos otra

```
SELECT DATEDIFF(DAY, '2025-01-01', '2025-02-03') AS diferenciaDias;
```

- Obtiene el año, mes y día separándolos de la fecha deseada

```
SELECT
YEAR('2025-02-03') AS anio,
MONTH('2025-02-03') AS mes,
DAY('2025-02-03') AS dia;
```

- Obtiene la diferencia en años de una fecha menos otra

```
SELECT DATEDIFF(DAY, '2020-01-01', '2025-02-03')/365.25 AS diferenciaAnios;
```

- Añade 10 días y resta 3 meses a la fecha deseada

```
SELECT
DATEADD(DAY, 10, '2025-02-03') AS nuevaFechaConDias,
DATEADD(MONTH, -3, '2025-02-03') AS nuevaFechaConMes;
```

### 1.4 Operaciones

#### COUNT(`*`)

Cuenta el número total de registros de una tabla.

**Ejemplo**

- Cuenta los registros en empleados.

```
SELECT COUNT(*) AS totalEmpleados FROM Empleados;
```

#### SUM(columna)

Suma los valores de una columna numérica. Se pueden usar otros operadores para hacer operaciones dentro. Funciona mejor con INT.

**Ejemplo**

- Suma los montos de ventas

```
SELECT SUM(monto) AS totalVentasMonto FROM Ventas;
```

#### AVG(columna)

Calcula el promedio de los valores de una columna numérica.

**Ejemplo**

- Promedia los montos de las ventas

```
SELECT AVG(monto) AS promedioMonto FROM Ventas;
```

#### MIN(columna)

Devuelve el valor mínimo en una columna.

**Ejemplo**

- Obtiene el monto más bajo de las ventas.

```
SELECT MIN(monto) AS montoMinimoVenta FROM Ventas;
```

#### MAX(columna)

Devuelve el valor máximo en una columna.

**Ejemplo**

- Obtiene el monto más alto de las ventas.

```
SELECT MAX(monto) AS montoMinimoVenta FROM Ventas;
```

#### Uso de GROUP BY

Agrupa registros por una columna y cuenta cuántos existen en cada grupo. Se usa cuando se requieren dos o más registros.

**Ejemplo**

- Obtiene las ventas por producto

```
SELECT nombre, COUNT(*) AS cantidadVentas FROM Productos GROUP BY nombre;
```

Dependiendo del elemento con el que se agrupa, se mostrarán diferentes resultados, y es posible agrupar por varios filtros (Se separan con una coma). Si se agrupa por `id` se mostrará solo una vez cada registro con ese `id` aunque aparezcan varias veces.

#### Uso de ORDER BY

El `ORDER BY` se usa para ordenar los resultados de una consulta según una o varias columnas. Se puede especificar el orden:

- **ASC**: ascendente, por defecto.
- **DESC**: descendente.

**Ejemplos**

- Obtiene la lista de productos ordenada alfabéticamente:

```
SELECT nombre, precio
FROM Productos
ORDER BY nombre ASC;
```

- Obtiene los productos más caros primero:

```
SELECT nombre, precio
FROM Productos
ORDER BY precio DESC;
```

##### Relación con GROUP BY

Cuando se usa `GROUP BY`, el `ORDER BY` permite ordenar los grupos generados según los valores agregados.

**Ejemplo**

- Obtiene las ventas por producto y las ordena de mayor a menor:

```
SELECT nombre, COUNT(*) AS cantidadVentas  
FROM Productos  
GROUP BY nombre  
ORDER BY cantidadVentas DESC;
```

### 1.5 Vistas

Las vistas en SQL son objetos virtuales que nos permiten acceder y manipular datos almacenados en una o varias tablas como si fueran tablas individuales. Sus ventajas son:

- Se simplifican las consultas
- Se organizan los datos y mejora el rendimiento.
- Son más seguras porque ya no se ve el join con los datos, solo se verá el nombre de la vista.

#### Sintaxis básica de una vista

- **Crear una vista**

```
CREATE VIEW nombre_vista
AS consulta_deseada;
```

- **Consultar una vista**

```
SELECT * FROM nombre_vista;
```

- **Modificar una vista**

```
CREATE VIEW nombre_vista
AS consulta_deseada;

ALTER VIEW nombre_vista
AS consulta_nueva;
```

**Ejemplo**

- Vista que muestra todos los empleados del departamento de sistemas y de Puebla

```
CREATE VIEW empleadosSistemasPuebla
AS
SELECT Personas.nombrePersona
FROM Personas INNER JOIN Departamentos
ON Personas.id_departamento = Departamentos.id_departamento INNER JOIN DepartamentosEstados
ON Departamentos.id_departamento = DepartamentosEstados.id_departamento INNER JOIN Estados
ON DepartamentosEstados.id_estado = Estados.id_estado
WHERE Departamentos.nombreDepartamento = 'Sistemas' AND Estados.nombreEstado = 'Puebla';

SELECT * FROM empleadosSistemasPuebla;
```

#### Cifrado de vistas

El cifrado de vistas se usa para mantener la confidencialidad del código, especialmente si se contiene lógica o procesos sensibles.

**Ejemplo**

- Se crea una nueva vista con cifrado

```
CREATE VIEW nombre_vista WITH ENCRYPTION
AS consulta_deseada;
```

- Se modifica una vista para que tenga cifrado

```
CREATE VIEW nombre_vista
AS consulta_deseada;

ALTER VIEW nombre_vista WITH ENCRYPTION
AS consulta_nueva;
```

Para comprobar si está cifrada, se utiliza `sp_helpText`.

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