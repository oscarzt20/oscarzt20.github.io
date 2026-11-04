---
title: "SaludOP — Arquitectura de Datos para Historia Clínica Electrónica"
date: 2024-11-26
weight: 5
slug: "base-datos-gestion-salud"
summary: "Modelado conceptual Entidad-Relación, diseño lógico normalizado, diccionario de datos e implementación en SQL Server de un sistema hospitalario de 23 tablas para expedientes clínicos electrónicos."
tags:
  - "SQL Server"
  - "Modelado de Datos"
  - "Diccionario de Datos"
  - "Bases de Datos"
categories:
  - "Bases de Datos"
cover:
  image: "/imagenes/proyectos/bd-salud-relacional.png"
  alt: "Diagrama Relacional del sistema clínico SaludOP"
  relative: false
---

## El Reto

En clínicas y hospitales, la fragmentación de la información médica entre consultas, laboratorios y farmacia dificulta el seguimiento integral del paciente y compromete la precisión de los diagnósticos. El objetivo del proyecto **SaludOP** fue diseñar desde cero la arquitectura de base de datos para un sistema de **Historia Clínica Electrónica (HCE)** capaz de centralizar expedientes, agendas médicas, resultados de laboratorio, recetas e inventario farmacéutico bajo estándares de integridad y privacidad.

---

## Diseño Conceptual y Lógico (23 Tablas Normalizadas)

El diseño de la base de datos siguió rigurosamente las etapas de ingeniería de datos para evitar redundancias y anomalías de actualización:

1. **Expediente Único del Paciente**: Identificación demográfica, seguro médico, contactos de emergencia y tablas asociativas para el control de **alergias** (`AlergiasPacientes`) y **condiciones preexistentes** (`PacientesCondicionesPre`).
2. **Gestión del Cuerpo Médico e Instituciones**: Registro de cédulas profesionales, adscripción a unidades hospitalarias (`InstitucionesSalud`), control de especialidades (`MedicosEspecialidades`) y bloques de horario laboral (`Disponibilidades`).
3. **Trazabilidad Clínica y Farmacéutica**: Vinculación completa desde la cita agendada (`Agendaciones`, `Citas`, `BitacoraDiaria`) hasta la emisión de diagnósticos (`Diagnosticos`), órdenes y resultados de laboratorio (`Pruebas`, `Resultados`), tratamientos (`Tratamientos`), prescripción de recetas (`Recetas`, `RecetasMedicamentos`) y existencias en farmacia (`Servicios`, `Inventarios`).

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/bd-salud-er.png" alt="Diagrama Entidad-Relación SaludOP">
    <figcaption>Modelo Conceptual Entidad-Relación (E-R) con entidades, atributos y relaciones.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/bd-salud-relacional.png" alt="Diagrama Relacional SaludOP">
    <figcaption>Modelo Lógico Relacional normalizado con las 23 tablas, llaves primarias (PK) y foráneas (FK).</figcaption>
  </figure>
</div>

---

## Documentación Técnica y Diccionario de Datos

El proyecto incluye una **especificación técnica de 48 páginas** (elaborada en la UMAD junto con Pedro Emiliano Romero Osorio), que documenta:

- **Análisis de Requerimientos**: Reglas de negocio hospitalarias y lineamientos de seguridad y confidencialidad de datos clínicos.
- **Diccionario de Datos Exhaustivo**: Definición formal de cada una de las 23 tablas, especificando nombre del atributo, tipo de dato en SQL Server, longitud, restricciones (`PRIMARY KEY`, `FOREIGN KEY`, `IDENTITY`) y descripción funcional de cada columna.
- **Implementación DDL y DML**: Scripts de creación del esquema e inserción de catálogos y registros clínicos de prueba.

---

## Implementación DDL en SQL Server (`SaludOP`)

```sql
CREATE DATABASE SaludOP;
GO
USE SaludOP;

CREATE TABLE Pacientes (
    id_paciente INT IDENTITY(1,1) PRIMARY KEY,
    nombre VARCHAR(80),
    apellidoP VARCHAR(80),
    apellidoM VARCHAR(80),
    fechaNacimiento DATE,
    calle VARCHAR(80),
    noExterior INT,
    colonia VARCHAR(80),
    cp INT,
    telefono VARCHAR(80),
    correo VARCHAR(80),
    seguroM VARCHAR(80),
    contactoE VARCHAR(80),
    id_sexo INT,
    FOREIGN KEY (id_sexo) REFERENCES Sexos(id_sexo)
);

CREATE TABLE Diagnosticos (
    id_diagnostico INT IDENTITY(1,1) PRIMARY KEY,
    tipoDiagnostico VARCHAR(80),
    descripcion VARCHAR(80),
    id_medico INT,
    FOREIGN KEY (id_medico) REFERENCES Medicos(id_medico)
);

CREATE TABLE Recetas (
    id_receta INT IDENTITY(1,1) PRIMARY KEY,
    folio INT,
    dosis VARCHAR(80),
    frecuencia VARCHAR(80),
    id_tratamiento INT,
    FOREIGN KEY (id_tratamiento) REFERENCES Tratamientos(id_tratamiento)
);
```
