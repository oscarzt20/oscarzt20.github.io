---
title: "Rescate Animal Puebla — Base de Datos Transaccional para ONG y Veterinaria"
date: 2025-05-10
weight: 4
slug: "base-datos-ong-rescate-animal"
summary: "Diseño e implementación en SQL Server de una base de datos relacional de 21 tablas con automatización mediante triggers, procedimientos almacenados y vistas para gestionar rescates, hospital veterinario, adopciones y finanzas."
tags:
  - "SQL Server"
  - "T-SQL"
  - "Bases de Datos"
  - "Stored Procedures"
  - "Triggers"
categories:
  - "Bases de Datos"
cover:
  image: "/imagenes/proyectos/bd-ong-modelo.png"
  alt: "Modelo relacional de la base de datos RescateAnimalPuebla1"
  relative: false
---

## El Problema

Las organizaciones de rescate animal y clínicas veterinarias suelen administrar sus operativos de rescate, expedientes médicos, inventario de medicamentos, voluntariado y donaciones en registros aislados. Esto provoca pérdida de trazabilidad sobre el estado clínico de cada ejemplar, desabasto de insumos médicos y falta de control presupuestal en campañas y eventos.

El objetivo de este proyecto fue construir el motor de base de datos relacional **`RescateAnimalPuebla1` en Microsoft SQL Server**, centralizando la operación clínica, logística y financiera con reglas de negocio automatizadas desde el propio servidor de datos.

---

## Arquitectura del Modelo Relacional (21 Tablas)

El esquema se normalizó en **21 tablas relacionales** protegidas con restricciones de integridad referencial (`FOREIGN KEY`) y validaciones de dominio (`CHECK` para edades no negativas, teléfonos de 10 a 12 dígitos, códigos postales válidos, montos positivos y coherencia cronológica en fechas de tratamiento y turnos):

| Dominio del Sistema | Tablas Relacionales |
| :--- | :--- |
| **Operativos de Rescate (4)** | `Especies`, `Razas`, `Rescates`, `Animales` |
| **Hospital Veterinario (6)** | `Areas`, `Veterinarios`, `Consultas`, `Tratamientos`, `Vacunas`, `TratamientosVacunas` |
| **Adopciones y Seguimiento (2)** | `Adoptantes`, `Adopciones` |
| **Voluntariado y Acceso (3)** | `Turnos`, `Usuarios`, `Roles` |
| **Finanzas, Eventos e Insumos (6)** | `Donantes`, `Donaciones`, `Eventos`, `Asistencias`, `Gastos`, `Suministros` |

![Modelo Relacional de la Base de Datos RescateAnimalPuebla1](/imagenes/proyectos/bd-ong-modelo.png)

---

## Automatización y Lógica en T-SQL

Para evitar que la integridad de los datos dependa exclusivamente de la capa de aplicación, se programaron objetos transaccionales y analíticos directamente en **T-SQL**:

### 1. Procedimientos Almacenados (`Stored Procedures`)
- **`RegistrarRescateYActualizarAnimal`**: Registra en una sola transacción el operativo de rescate y el alta del animal utilizando `SCOPE_IDENTITY()`, asignándole automáticamente el estado `'En rehabilitación'`.
- **`AsignarTratamientoTrasConsulta`**: Cierra automáticamente los tratamientos previos abiertos del paciente (`SET fechaFin = @fechaInicio`) antes de registrar la nueva prescripción médica.
- **`ActualizarInventarioTrasAplicarVacuna`**: Verifica la existencia de dosis suficientes en `Suministros`, descuenta las unidades aplicadas y vincula el registro en `TratamientosVacunas`.
- **`CompararEstadoSaludAnimal`**: Contrasta el diagnóstico inicial frente al estado actual del ejemplar para dictaminar su evolución clínica.
- **`RegistrarAdopcion`**: Formaliza la entrega del ejemplar y actualiza su estatus en el catálogo general.
- **`VerificarDesvioPresupuestal`**: Cruza el total de donaciones recaudadas frente a los gastos ejercidos durante el periodo de un evento y emite alertas en caso de déficit.

### 2. Disparadores (`Triggers`) en Tiempo Real
- **`tr_AjustarInventarioMedicamentos`**: Al insertar un nuevo tratamiento, analiza la lista de medicamentos prescritos y descuenta automáticamente las unidades correspondientes del inventario en `Suministros`.
- **`tr_ActualizarEstadoAdopcion`**: Cambia de forma inmediata el estado del animal a `'Adoptado'` al registrarse un contrato en la tabla `Adopciones`.
- **`tr_FechaAplicacionVacuna`**: Garantiza la trazabilidad asignando `GETDATE()` cuando se registra la aplicación de una vacuna sin fecha explícita.

### 3. Vistas Analíticas y Seguridad Basada en Roles (DCL)
- **8 Vistas de Negocio (`CREATE VIEW`)**: Incluyen `Vista_Historial_Clinico`, `Vista_Animales_Disponibles`, `Vista_Donaciones_Por_Donante` y `Vista_Seguimientos_Observaciones_Criticas` (que detecta automáticamente casos post-adopción con palabras clave como `'riesgo'`, `'inadecuado'` o `'ajuste'`).
- **Control de Permisos (DCL)**: Creación de perfiles diferenciados de lectura (`uLectura` en `db_datareader` con `DENY` explícito de modificación) y operación (`uEscritura` en `db_datawriter`).

---

## Documentación y Pruebas

El proyecto está respaldado por una **documentación técnica de 51 páginas** (desarrollada en la UMAD junto con Emmanuel Baltazar López y Pedro Emiliano Romero Osorio), que incluye el diagrama relacional, los scripts DDL/DML completos y la evidencia de ejecución y prueba de cada `INNER JOIN`, vista, procedimiento almacenado y *trigger*.

---

## Fragmento de Código T-SQL

```sql
CREATE TRIGGER tr_AjustarInventarioMedicamentos
ON Tratamientos
AFTER INSERT
AS
BEGIN
    DECLARE @medicamentos VARCHAR(500), @id_tratamiento INT, @cantidadMedicamentos INT;

    SELECT @medicamentos = medicamentos, @id_tratamiento = id_tratamiento
    FROM inserted;

    IF @medicamentos IS NOT NULL AND @medicamentos <> ''
    BEGIN
        -- Calcula el número de medicamentos separados por coma y descuenta el stock
        SET @cantidadMedicamentos = LEN(@medicamentos) - LEN(REPLACE(@medicamentos, ',', '')) + 1;

        UPDATE Suministros
        SET cantidadDisponible = cantidadDisponible - @cantidadMedicamentos
        WHERE id_tratamiento = @id_tratamiento;
    END;
END;
GO

CREATE VIEW Vista_Seguimientos_Observaciones_Criticas AS
SELECT
    A.nombreAnimal,
    AD.fechaAd,
    AD.infoAdicional
FROM Adopciones AD
JOIN Animales A ON AD.id_animal = A.id_animal
WHERE AD.infoAdicional LIKE '%ajuste%'
   OR AD.infoAdicional LIKE '%inadecuado%'
   OR AD.infoAdicional LIKE '%riesgo%';
```
