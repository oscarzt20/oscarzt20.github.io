---
Title: Bases de Datos V - Microsoft SQL
Date: 2025-08-08
Hora: 02:18
tags: ['enciclopedia', 'aprenderBD']
---

---

## I. Microsoft SQL

El SQL (Lenguaje Estructurado de Consultas) es un lenguaje declarativo basado en el modelo relacional, es decir, se indican instrucciones y la acción que realizarán sobre una base de datos relacional.

### 1.1 Categorías de SQL

- **Lenguaje de definición de datos (DDL, Data Definition Language)**: Son instrucciones que se utilizan para crear, modificar y borrar objetos de la base de datos, como tablas, vistas, esquemas, dominios, activadores y procedimientos almacenados.
- **Lenguaje de control de datos (DCL, Data Control Language)**: Son instrucciones que permiten controlar quién o qué tiene acceso a objetos específicos de la base de datos. Dentro de estas instrucciones se pueden encontrar aquellas asociadas a la administración de usuarios, para otorgar o revocar permisos a objetos de las bases de datos.
- **Lenguaje de manipulación de datos (DML, Data Manipulation Language)**: Son instrucciones que se utilizan para recuperar, agregar, modificar y borrar datos almacenados en la base de datos.
### 1.2 Instalación y uso

1. En la página Microsoft SQL se elige la versión express, instalación personalizada, instalar, New standalone installation, aceptar e instalar
2. Quitar selección de Azure, y Machine Learning y todo next
3. Install SQL server management tools, Descargar los ssms
4. Cerrar todo y abrir SQL Server Management Studio 20
5. Colocar opcional, y conectar
6. Al abrir dar conectar
7. En la barra, New Query
8. Seleccionar primera línea (CREATE DATABASE mydb;) y Execute, lo mismo con la segunda línea (Use mydb;)

#### Notas de programar en SQL

- Declarar cada FK como una variable más
- Ejecutar cada tabla, primero escribir y ejecutar las tablas de las que otras dependen
- Cada insert debe seguir la jerarquía con la que se crearon las tablas
- Si se puso una numeración automática (IDENTITY(1,1)) en el id de una tabla, cuando se inserten datos no se colocan los id. Si es foránea si se pone, para saber con quién se conecta.

## II. Configuraciones de SQL Server

### 2.1 Creación de diagramas

1. Crear la base de datos
2. Buscar la DB dentro de la lista de la carpeta databases en el lado izquierdo y expandir
3. Expandir la carpeta de database diagram y aceptar el mensaje
4. click derecho en esa misma carpeta y seleccionar añadir
5. Seleccionar todas las tablas al mismo tiempo y seleccionar add

### 2.2 Backups

En SQL, los respaldos son una parte esencial, ya que permiten recuperar los datos en caso de fallos o pérdidas.

Existen 2 formas de generar un archivo de backup:

Mediante el gestor:

1. Crear la base de datos
2. Buscar la DB dentro de la lista de la carpeta databases en el lado izquierdo
3. Click derecho en la base de datos, Task, Backup
4. Configurar el tipo los componentes y el lugar donde se guardará, etc.

Mediante un comando:

```
BACKUP DATABASE PaleteriaLaMichoacana TO DISK = 'C:\empresa.bak';
```

### 2.3 Creación de usuarios y permisos

Dentro de SQL es posible crear usuarios y asignarle permisos según sea necesario.

**Ejemplo**:

- Creación de dos usuarios `uLectura` y `uEscritura` con diferentes contraseñas y permisos.

```
CREATE LOGIN uLectura WITH PASSWORD = 'Segura123';

USE PaleteriaLaMichoacana;

CREATE USER uLectura FOR LOGIN uLectura;

GRANT SELECT TO uLectura;
DENY INSERT, UPDATE, DELETE TO uLectura;

EXEC sp_addrolemember 'db_datareader', 'uLectura';


CREATE LOGIN uEscritura WITH PASSWORD = 'OtraSegura123';

USE PaleteriaLaMichoacana;

CREATE USER uEscritura FOR LOGIN uEscritura;

GRANT SELECT, INSERT, UPDATE, DELETE TO uEscritura;

EXEC sp_addrolemember 'db_datawriter', 'uEscritura';
```

Para utilizar los usuarios en SQL Server Management Studio 20:

1. Crear el usuario y ejecutar los comandos en la base de datos
2. Click derecho nombre de SQLEXPRESS en la barra de la izquierda, propiedades, seguridad y seleccionar SQL Server
3. En servicios de windows, buscar SQL Server (SQLEXPRESS) y reiniciar el servicio
4. Cambiar la autenticación al abrir SQL poner SQL SERVER Auth
5. Colocar login y password del usuario deseado
6. Seleccionar opcional
7. Entrar. Si hacemos uso de la BD podremos manipularla según se configuró el usuario.

### 2.4 Consideraciones de una BD en producción

1. Cada cuanto se respalda, a qué hora
2. Autenticación
3. Servidor en la nube o físico, cuidar mucho los accesos

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