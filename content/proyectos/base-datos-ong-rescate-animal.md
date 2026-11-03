---
title: "Sistema de Base de Datos para ONG de Rescate Animal y Veterinaria (SQL Server)"
date: 2025-05-10
weight: 5
slug: "base-datos-ong-rescate-animal"
summary: "Diseño e implementación en Microsoft SQL Server (T-SQL) de una base de datos relacional de 21 tablas para gestionar rescates de fauna, clínica veterinaria, vacunaciones, adopciones, voluntariado, eventos y finanzas de una ONG."
tags:
  - "SQL Server"
  - "T-SQL"
  - "Bases de Datos"
  - "Stored Procedures"
  - "Triggers"
  - "Modelado de Datos"
categories:
  - "Bases de Datos"
cover:
  image: "/imagenes/proyectos/bd-ong-modelo.png"
  alt: "Modelo relacional de la base de datos de Rescate Animal y Veterinaria"
  relative: false
---

## Descripción del Proyecto

Proyecto desarrollado para la asignatura *Programación para Bases de Datos* en la **Universidad Madero (UMAD)**, cuyo objetivo fue diseñar, implementar y auditar una base de datos relacional completa en **Microsoft SQL Server (`RescateAnimalPuebla1`)** para administrar las operaciones clínicas, logísticas y financieras de una **ONG de rescate animal y hospital veterinario**.

- **Autores**: Oscar Juárez Ortiz, Emmanuel Baltazar López, Pedro Emiliano Romero Osorio.
- **Asesora**: Ing. Verónica Moreno Jiménez.

![Modelo Relacional de la Base de Datos RescateAnimalPuebla1](/imagenes/proyectos/bd-ong-modelo.png)

---

## Arquitectura del Esquema Relacional (21 Tablas)

El modelo garantiza la integridad referencial y de dominio mediante llaves primarias autoincrementables (`IDENTITY(1,1)`), llaves foráneas (`FOREIGN KEY`) y restricciones de validación (`CHECK` en edades, rangos telefónicos de 10 a 12 dígitos, códigos postales positivos, montos financieros e intervalos de fechas y turnos):

| Dominio Operativo | Tablas Implementadas (21 en Total) |
| :--- | :--- |
| **Rescate y Fauna (4)** | `Especies`, `Razas`, `Rescates`, `Animales` |
| **Clínica Veterinaria (6)** | `Areas`, `Veterinarios`, `Consultas`, `Tratamientos`, `Vacunas`, `TratamientosVacunas` |
| **Adopciones y Seguimiento (2)** | `Adoptantes`, `Adopciones` |
| **Capital Humano y Seguridad (3)** | `Turnos`, `Usuarios` (Voluntarios), `Roles` |
| **Finanzas, Eventos y Logística (6)** | `Donantes`, `Donaciones`, `Eventos`, `Asistencias`, `Gastos`, `Suministros` |

---

## Programación en T-SQL: Vistas, Procedimientos, Triggers y Seguridad

### 1. Consultas Multitabla (`INNER JOIN` y Agregaciones)
- Trazabilidad de animales rescatados por ubicación y tipo de siniestro (urbano, silvestre, incendio forestal, tráfico ilegal).
- Historial clínico completo vinculando `Animales → Consultas → Veterinarios → Tratamientos → TratamientosVacunas → Vacunas`.
- Análisis financiero de gastos operativos agrupados por categoría (`SUM(montoGasto)`).

### 2. Vistas Analíticas (`CREATE VIEW`)
- `Vista_Animales_Disponibles`: Catálogo con especie, raza, edad, estado de salud y descripción del animal.
- `Vista_Historial_Clinico`: Expediente médico unificado por paciente, fecha de consulta, veterinario y diagnóstico.
- `Vista_Adopciones_Confirmadas`: Cruce de animales adoptados con información del adoptante y especie.
- `Vista_Animales_Vacunados`: Subconsultas correlacionadas para identificar animales con esquemas de vacunación múltiples (`COUNT(*) > 1`).
- `Vista_Usuarios_Horas_Acumuladas1`: Totalización de horas de voluntariado (`SUM(horasT)`) agrupadas por voluntario y área operativa.
- `Vista_Donaciones_Por_Donante`: Desglose de aportaciones individuales y monto acumulado histórico por donante.
- `Vista_Eventos_Alta_Participacion`: Filtrado de campañas y eventos solidarios con aforo completo de asistentes.
- `Vista_Seguimientos_Observaciones_Criticas`: Detección automatizada (`LIKE '%riesgo%'`, `'%inadecuado%'`, `'%ajuste%'`) de adopciones que requieren seguimiento prioritario.

### 3. Procedimientos Almacenados (`CREATE PROCEDURE`)
- `RegistrarRescateYActualizarAnimal`: Registra en una sola transacción el evento en `Rescates` y el expediente en `Animales` utilizando `SCOPE_IDENTITY()`, actualizando su estado a `'En rehabilitación'`.
- `AsignarTratamientoTrasConsulta`: Cierra automáticamente los tratamientos activos previos del paciente (`SET fechaFin = @fechaInicio`) e inserta el nuevo tratamiento médico.
- `CompararEstadoSaludAnimal`: Evalúa el diagnóstico clínico anterior frente al estado de salud actual del animal para dictaminar si presenta mejoría (`@mejora = 1`).
- `RegistrarAdopcion`: Inserta el contrato en `Adopciones` y actualiza el estado del ejemplar en `Animales` a `'Adoptado'`.
- `ActualizarInventarioTrasAplicarVacuna`: Verifica la disponibilidad en `Suministros`, descuenta las dosis requeridas (`TRY_CAST`) y asocia el registro en `TratamientosVacunas`.
- `VerificarDesvioPresupuestal`: Compara las donaciones recaudadas frente a los gastos ejercidos durante el periodo de un evento y emite alertas de desviación presupuestal.

### 4. Disparadores (`CREATE TRIGGER`) y Seguridad DCL
- `tr_ActualizarEstadoAdopcion` (`AFTER INSERT ON Adopciones`): Actualiza automáticamente el `estadoSalud` del animal a `'Adoptado'`.
- `tr_FechaAplicacionVacuna` (`AFTER INSERT ON Vacunas`): Asigna `GETDATE()` cuando se registra una vacuna sin fecha explícita.
- `tr_AjustarInventarioMedicamentos` (`AFTER INSERT ON Tratamientos`): Cuenta los medicamentos prescritos en la cadena separada por comas y descuenta automáticamente el stock en `Suministros`.
- **Seguridad Basada en Roles (DCL)**: Aprovisionamiento de logins y usuarios (`uLectura`, `uEscritura`) con permisos diferenciados (`GRANT SELECT`, `DENY INSERT, UPDATE, DELETE`) e integración en roles fijos (`db_datareader`, `db_datawriter`).

---

## Fragmento de Código T-SQL (`RescateAnimalPuebla1`)

```sql
CREATE PROCEDURE RegistrarRescateYActualizarAnimal
    @fechaR DATE,
    @ubicacion VARCHAR(500),
    @tipoR VARCHAR(50),
    @nombreResponsable VARCHAR(50),
    @nombreAnimal VARCHAR(100),
    @edad INT,
    @genero VARCHAR(100),
    @estadoSalud VARCHAR(100),
    @descripcionAnimales VARCHAR(150),
    @id_especie INT
AS
BEGIN
    DECLARE @id_rescate INT, @id_animal INT;

    INSERT INTO Rescates (fechaR, ubicacion, tipoR, nombreResponsable)
    VALUES (@fechaR, @ubicacion, @tipoR, @nombreResponsable);
    SET @id_rescate = SCOPE_IDENTITY();

    INSERT INTO Animales (nombreAnimal, edad, genero, estadoSalud, descripcionAnimales, id_especie, id_rescate)
    VALUES (@nombreAnimal, @edad, @genero, @estadoSalud, @descripcionAnimales, @id_especie, @id_rescate);
    SET @id_animal = SCOPE_IDENTITY();

    UPDATE Animales
    SET estadoSalud = 'En rehabilitación'
    WHERE id_animal = @id_animal;
END;
GO

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
        SET @cantidadMedicamentos = LEN(@medicamentos) - LEN(REPLACE(@medicamentos, ',', '')) + 1;

        UPDATE Suministros
        SET cantidadDisponible = cantidadDisponible - @cantidadMedicamentos
        WHERE id_tratamiento = @id_tratamiento;
    END;
END;
```
