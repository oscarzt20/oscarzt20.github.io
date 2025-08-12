---
Title: Bases de Datos VI - Estructura Básica de SQL
Fecha: 2025-08-08
Hora: 02:19
tags: ['enciclopedia', 'post']
---

---

## I. Estructura y configuración inicial en SQL Server

### 1.1 Operaciones básicas de SQL

- **CREATE DATABASE**: Crea una nueva base de datos
- **USE**: Selecciona la base de datos en la que deseas trabajar. Después de ejecutar este comando, todas las operaciones de SQL se aplicarán a la base de datos seleccionada.
- **DROP DATABASE** Elimina por completo una base de datos.
- **CREATE TABLE**: Crea una nueva tabla. Al definirla, se especifican las columnas, tipos de datos y restricciones para almacenar información estructurada.
- **DROP TABLE**: Elimina la tabla que se seleccione
- **INSERT**: Permite agregar una nueva fila o registro en una tabla. Se puede especificar una lista de columnas y valores correspondientes.
- **UPDATE**: Modifica los datos de las filas en una tabla. Permite actualizar uno o más valores en registros específicos utilizando una cláusula `WHERE` para limitar las filas afectadas.
- **SELECT**: Corresponde a la operación de proyección del álgebra relacional, se utiliza para listar los atributos de una consulta.
- **FROM**: Indica la tabla o tablas desde las cuales se extraerán los datos.
- **WHERE**: Filtra los registros en función de una condición dada, similar a la operación de selección en el álgebra relacional.
- **INNER JOIN ... ON**: Combina filas de dos o más tablas en función de una condición de igualdad especificada en la cláusula ON. Solo devuelve las filas donde existe una coincidencia en ambas tablas.

### 1.2 Creación de los elementos iniciales

1. **Crear y usar la base de datos**

```
CREATE DATABASE NombreDB;
USE NombreDB;
```

2. **Crear tablas**. Aquellas que no tienen llave foránea van primero.

```
CREATE TABLE Departamentos
(
	id_departamento INT IDENTITY(1,1) PRIMARY KEY,
	atributo VARCHAR(50),
	atributo2 DATE,
	atributo3 FLOAT(9),
	atributo4 INT
);

CREATE TABLE Empleados
(
	id_empleado INT IDENTITY(1,1) PRIMARY KEY,
	atributo VARCHAR(50),
	atributo2 DATE,
	atributo3 FLOAT(9),
	atributo4 INT,
	id_departamento INT,
	FOREIGN KEY (id_departamento) REFERENCES Departamentos(id_departamento)
);
```

### 1.3  Manipulaciones de datos en tablas

#### INSERT

Insertar valores.

**Ejemplo**

```
INSERT INTO Departamentos
VALUES
('Sistemas', 2025-01-15, 50.2, 30),
('RH', 2025-03-09, 50.2, 30);

INSERT INTO Empleados
VALUES
('Ernesto', 2025-01-15, 25.5, 10, 1),
('Laura', 2025-03-09, 25.5, 10, 2);
```

#### UPDATE

Actualizar valores. **No omitir** `WHERE` ya que sino se actualizarán todos los registros de la tabla.

**Ejemplo**

```
UPDATE Productos  
SET nombreProducto = 'Frijol', precio = 19.99
WHERE id_producto = 3;
```

#### DELETE

Borra valores. **No omitir** `WHERE` ya que sino se eliminarán todos los registros de la tabla.

**Ejemplo**

```
DELETE FROM Productos  
WHERE idProducto = 5;
```

#### DROP

Eliminar una tabla. No se podrá eliminar si hay otra tabla que dependa de esta.

**Ejemplo**

```
DROP TABLE Productos;
```

Eliminar una base de datos. No se puede eliminar la base de datos si está en uso, por lo que primero se debe usar otra tabla antes.

**Ejemplo**

```
USE master;

DROP DATABASE NombreBD;
```

### 1.4 Notas generales de SQL Server

- Declarar cada FK como una variable más
- Ejecutar cada tabla, primero escribir y ejecutar las tablas de las que otras dependen
- Cada insert debe seguir la jerarquía con la que se crearon las tablas
- Si se puso una numeración automática (IDENTITY(1,1)) en el id de una tabla, cuando se inserten datos no se colocan los id. Si es foránea si se pone, para saber con quién se conecta.

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