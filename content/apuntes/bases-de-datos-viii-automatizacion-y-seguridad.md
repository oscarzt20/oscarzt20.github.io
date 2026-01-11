---
Date: 2025-08-08
Time: 02:22
tags:
- enciclopedia
- aprenderBD
slug: bases-de-datos-viii-automatizacion-y-seguridad
title: Bases de Datos VIII - Automatización y Seguridad
---

---

## I. Automatización y seguridad

### 1.1 Procedimientos almacenados

Los stored procedures permiten agilizar los procesos de consulta de datos, aumentar la seguridad, reutilizar código y permiten un desarrollo de software más ágil. Dentro de SQL Server se les considera como un grupo de una o varias instrucciones Transact-SQL, mientras que en Microsoft .NET Framework se trata de una referencia a un método de Common Runtime Language (CLR).

Los SP contienen instrucciones de programación que realizan operaciones en la base de datos, como llamar a otros procedimientos, devolver un valor de estado o realizar una llamada para indicar si la operación se ha realizado correctamente o se han producido errores y el motivo de estos.

**Ejemplos**

- SP que inserta un registro en la tabla `Personas`

```
CREATE PROCEDURE sp_createPersona
(
	@nombrePersona VARCHAR(100),
	@apellidoP VARCHAR(100),
	@apellidoM VARCHAR(100),
	@genero VARCHAR(100),
	@correo VARCHAR(100),
	@puesto VARCHAR(100),
	@telefono VARCHAR(10),
	@edad INT,
	@sueldo INT,
	@id_departamento INT
)
AS
BEGIN
INSERT INTO Personas
VALUES (@nombrePersona, @apellidoP, @apellidoM, @genero, @correo, @puesto, @telefono, @edad, @sueldo, @id_departamento);
END

EXECUTE sp_createPersona 'Hernán', 'Lopez', 'Cortés', 'Masculino', 'hernan@gmail.com', 'Sistemas', '2255487887', 38, 27000, 2;
```

- SP que actualiza un registro en la tabla `Personas`

```
CREATE PROCEDURE sp_updatePersona
(
	@id_persona INT,
	@nombrePersona VARCHAR(100),
	@apellidoP VARCHAR(100),
	@apellidoM VARCHAR(100),
	@genero VARCHAR(100),
	@correo VARCHAR(100),
	@puesto VARCHAR(100),
	@telefono VARCHAR(10),
	@edad INT,
	@sueldo INT,
	@id_departamento INT
)
AS
BEGIN
UPDATE Personas
SET
	nombrePersona = @nombrePersona,
	apellidoP = @apellidoP,
	apellidoM = @apellidoM,
	genero = @genero,
	correo = @correo,
	puesto = @puesto,
	telefono = @telefono,
	edad = @edad,
	sueldo = @sueldo,
	id_departamento = @id_departamento
WHERE id_persona = @id_persona;
END

EXECUTE sp_updatePersona 2, 'Laura', 'Sierra', 'Cayo', 'Femenino', 'laura@gmail.com', 'Administrador', '2255489741', 32, 20000, 1;
```

- SP que consulta por el nombre de una persona y además muestra el departamento y estados con el que está relacionada mediante un `INNER JOIN`

```
CREATE PROCEDURE sp_searchPersona
(
	@nombrePersona VARCHAR(100)
)
AS
BEGIN
SELECT Personas.nombrePersona, Departamentos.nombreDepartamento, Estados.nombreEstado
FROM Personas INNER JOIN Departamentos
ON Personas.id_departamento = Departamentos.id_departamento INNER JOIN DepartamentosEstados
ON Departamentos.id_departamento = DepartamentosEstados.id_departamento INNER JOIN Estados
ON DepartamentosEstados.id_estado = Estados.id_estado
WHERE Personas.nombrePersona = @nombrePersona;
END

EXECUTE sp_searchPersona 'Ernesto';
```

- Eliminar un stored procedure

```
DROP sp_nombre;
```


### 1.2 Checks

El `CHECK` es una restricción que se utiliza para definir reglas en la inserción de valores de una tabla, asegurando que los valores insertados cumplan ciertas condiciones. Ayuda a mantener la integridad de los datos dentro de la tabla.

**Ejemplos**

- Creación de una tabla con checks para que el género sea Masculino o Femenino, que la edad sea igual o mayor a 18, que el sueldo sea mayor o igual a 0 después de agregar el IVA del 16% y que el puesto solo sea en Sistemas, Administrador o Contador, Psicología.

```
CREATE TABLE Personas
(
	id_persona INT IDENTITY(1,1) PRIMARY KEY,
	nombrePersona VARCHAR(100),
	apellidoP VARCHAR(100),
	apellidoM VARCHAR(100),
	genero VARCHAR(100),
	correo VARCHAR(100),
	puesto VARCHAR(100),
	telefono VARCHAR(10),
	edad INT,
	sueldo INT,
	id_departamento INT,
	FOREIGN KEY (id_departamento) REFERENCES Departamentos(id_departamento),
	CHECK(genero IN('Masculino', 'Femenino')),
	CHECK(edad >= 18),
	CHECK(sueldo * 1.16 >= 0),
	CHECK(puesto IN('Sistemas', 'Administrador', 'Contador', 'Psicología'))
);

-- Inserción correcta
INSERT INTO Personas VALUES
	('Ernesto', 'Silva', 'Ramos', 'Masculino', 'ernesto@gmail.com', 'Sistemas', '2255489090', 38, 27000, 2);

-- Inserción incorrecta por el puesto
INSERT INTO Personas VALUES
	('Raúl', 'Lopez', 'Ramos', 'Masculino', 'raul@gmail.com', 'Redes', '2255489090', 38, 27000, 2);

```

- Tabla donde el estado sea igual a activo y la fecha de salida esté nulo o que el estado sea inactivo y la fecha de salida no esté nulo.

```
CREATE TABLE Empleados
(
	id_empleado INT IDENTITY(1,1) PRIMARY KEY,
	nombre VARCHAR(100) NOT NULL,
	estado VARCHAR(100),
	fecha_salida DATE,
	CHECK(estado = 'activo' AND fecha_salida IS NULL OR estado = 'inactivo' AND fecha_salida IS NOT NULL)
);
```

- Tabla donde se verifica que la fecha de nacimiento del empleado sea menor que su fecha de contratación.

```
CREATE TABLE Empleados
(
	id_empleado INT IDENTITY(1,1) PRIMARY KEY,
	nombre VARCHAR(100) NOT NULL,
	estado VARCHAR(100),
	fecha_nacimiento DATE,
	fecha_contratacion DATE,
	CHECK(fecha_nacimiento &lt; fecha_contratacion)
);
```

- Tabla que verifica que el cargo del empleado no sea de Gerente o que el salario sea menos de 5000.

```
CREATE TABLE Empleados
(
	id_empleado INT IDENTITY(1,1) PRIMARY KEY,
	nombre VARCHAR(100) NOT NULL,
	estado VARCHAR(100),
	cargo VARCHAR(100),
	salario DECIMAL(10, 2),
	CHECK(cargo != 'Gerente' OR salario &gt; 5000)
);
```

- Tabla que verifica que el salario total sea mayor o igual al salario base `*` 0.75

```
CREATE TABLE Empleados
(
	id_empleado INT IDENTITY(1,1) PRIMARY KEY,
	nombre VARCHAR(100) NOT NULL,
	estado VARCHAR(100),
	salario_base DECIMAL(10, 2),
	salario_total DECIMAL(10, 2),
	CHECK(salario_total >= salario_base * 0.75)
);
```

### 1.3 Triggers

Un Trigger o disparador es un script que desencadena determinadas acciones de forma automática en las tablas de la base de datos cuando se insertan, modifican y se añaden nuevos datos, lo cual nos ayuda a mejorar la gestión de la BD y aumenta la integridad de la información.

**Ventajas**:

- **Generación automática de datos:** Pueden rellenar valores automáticamente al insertar o actualizar registros.
- **Integridad referencial:** Ayudan a mantener relaciones correctas entre tablas (como validar claves foráneas).
- **Registro de actividad:** Guardan información de quién hizo qué y cuándo, útil para rastrear acciones.
- **Auditoría:** Permiten monitorear y registrar cambios importantes en los datos.
- **Replicación en tiempo real:** Copian datos automáticamente entre tablas cuando hay cambios.
- **Control de seguridad:** Aplican reglas de acceso o validaciones antes de modificar datos.
- **Prevención de errores:** Bloquean transacciones que no cumplen ciertas condiciones.

#### Tipos de triggers

1. **Disparadores de fila (Row Triggers):** Se activan una vez por cada fila afectada en la tabla.
   *Por ejemplo*, si una acción modifica 5 filas, el trigger se ejecuta 5 veces, una por cada fila.
2. **Disparadores de sentencia (Statement Triggers):** Se ejecutan una sola vez por operación, sin importar cuántas filas se vean afectadas.
   *Por ejemplo*, si se actualizan 100 filas, el trigger se dispara solo una vez.

#### Tipos de errores en los triggers

RAISERROR se utiliza para generar un mensaje de error desde un procedimiento almacenado, una función o un lote de comandos.

```
RAISERROR ('Mensaje de error', #, #)
```

Los números que contiene tienen un significado específico.

**Primer parámetro**: "qué tan grave el error"

- `-1` Devuelve el valor de gravedad asociado al error.
- `16` Es el nivel de gravedad del error. Este nivel va de 0 a 25, donde 0 es un error grave y 25 es un error menor. El nivel 16 indica un error grave, pero uno que no detiene la ejecución o de la instrucción actual.
- `10` Indica un error informativo que no afecta la ejecución del lote o la instrucción.
- `20` Indica un error crítico que finaliza la conexión de usuario actual.
- `25` Indica un error grave que detiene la ejecución del servidor de SQL Server.
- `0` Permite a los desarrolladores generar mensajes personalizados sin impacto en la ejecución del lote o instrucción.

**Segundo parámetro**: "Estado del error"

- `-1` Devuelve el valor de gravedad asociado al error.
- `1` El estado es un número de 1 a 127 que proporciona información adicional sobre el error. Puede ser util para distinguir diferentes causas de un mismo error.
- `Estado 1`: Se utiliza para un error de división por cero.
- `Estado 2`: Se utiliza para un error de validación de entrada.
- `Estado 3`: Se utiliza para un error de violación de restricción (por ejemplo, edad no válida).
- `Estado 4`: Se utiliza para un error de clave duplicada al intentar insertar registros en una tabla.

**Ejemplos**:

- Trigger al **tratar de eliminar o alterar** una tabla con **RAISERROR**

```
CREATE TRIGGER TriggerSeguridadD1
ON DATABASE FOR Drop_Table, Alter_Table
AS
BEGIN
RAISERROR ('No se tiene permitido modificar o eliminar una tabla', -1, -1)
ROLLBACK TRANSACTION
END

-- Se prueba el trigger
DROP TABLE Productos;
```

- Trigger al **insertar y actualizar**

```
CREATE TRIGGER actualizarEInsertarDatosDisparador
ON Estados
AFTER INSERT, UPDATE
AS RAISERROR ('Se actualizaron o insertaron los datos', 16, 10);

-- Se prueba el trigger
INSERT INTO Estados
VALUES ('Guadalajara', 4500000);
```

#### Ejecución de los triggers

Los **triggers** se activan automáticamente cuando ocurre una acción en una tabla, como:

- **INSERT** (cuando se insertan datos)
- **UPDATE** (cuando se actualizan datos)
- **DELETE** (cuando se eliminan datos)

Y pueden ejecutarse en dos momentos:

- **BEFORE (antes):** El trigger se ejecuta antes de que se realice la acción (útil para validar o modificar datos antes del cambio).
- **AFTER (después):** El trigger se ejecuta después de que se realiza la acción.

**Ejemplos**:

- Trigger al **insertar**

```
CREATE TRIGGER insertarDatosDisparador
ON Estados
AFTER INSERT
AS PRINT ('Se insertó un registro a la tabla de Estados.');

-- Se prueba el trigger
INSERT INTO Estados
VALUES ('Yuacatán', 1500000);
```

- Trigger al **actualizar**

```
CREATE TRIGGER actualizarDatosDisparador
ON Estados
AFTER UPDATE
AS PRINT ('Se actualizó un registro de la tabla de Estados.');

-- Se prueba el trigger
UPDATE Estados
SET nombreEstado = 'Monterrey', noHabitantes = 5800000
WHERE id_estado = 4;
```

- Trigger al **eliminar**

```
CREATE TRIGGER eliminarDatosDisparador
ON Estados
AFTER DELETE
AS PRINT ('Se eliminó un registro de la tabla de Estados.');

-- Se prueba el trigger
DELETE FROM Estados
WHERE id_estado = 2;
```

- Trigger que **reemplaza** el nombre del estado por la palabra 'new'

```
CREATE TRIGGER triggerAfterInsertar
ON Estados
AFTER INSERT
AS
BEGIN
UPDATE Estados
SET nombreEstado = 'New'
WHERE id_estado IN (SELECT id_estado FROM INSERTED)
END

-- Se prueba el trigger
INSERT INTO Estados
VALUES ('Guerrero', 4500000);
```

- Trigger de **Insert** de paletas con **variables**

```
CREATE TRIGGER tr_InsertarPaleta
ON Paletas
AFTER INSERT
AS
BEGIN
    DECLARE @nombre VARCHAR(100);
    SELECT @nombre = nombrePaleta FROM INSERTED;

    PRINT 'Se ha insertado una nueva paleta: ' + @nombre;
END;

-- Se prueba el trigger
INSERT INTO Paletas VALUES
('Paleta Chocomil', '50', 1.50, 0.80, 1);
```

- **Consultar** los trigger de una DB

```
USE Disparadores
SELECT OBJECT_NAME(parent_id)
AS Parent_Object_Name, *
FROM sys.triggers
```

- **Borrar** un trigger

```
DROP TRIGGER IF EXISTS nombreTrigger;
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