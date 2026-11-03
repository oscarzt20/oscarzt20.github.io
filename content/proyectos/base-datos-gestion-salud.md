---
title: "Base de Datos para Gestión de Salud e Historia Clínica Electrónica (SaludOP)"
date: 2024-11-26
weight: 6
slug: "base-datos-gestion-salud"
summary: "Modelado Entidad-Relación, Diseño Relacional normalizado, Diccionario de Datos (48 páginas) e implementación en SQL Server de un sistema hospitalario de Historia Clínica Electrónica con 23 tablas."
tags:
  - "SQL Server"
  - "Bases de Datos"
  - "Modelado E-R"
  - "Diccionario de Datos"
  - "Sector Salud"
categories:
  - "Bases de Datos"
cover:
  image: "/imagenes/proyectos/bd-salud-relacional.png"
  alt: "Diagrama Relacional del Sistema de Gestión de Salud SaludOP"
  relative: false
---

## Descripción del Proyecto

Este proyecto, desarrollado para la asignatura *Fundamentos de Bases de Datos* en la **Universidad Madero (UMAD)**, consiste en el análisis de requerimientos, modelado conceptual (**Entidad-Relación**), diseño lógico (**Modelo Relacional normalizado**), elaboración de **Diccionario de Datos** e implementación física en **Microsoft SQL Server (`SaludOP`)** para un sistema de **Gestión de Salud e Historia Clínica Electrónica (HCE)**.

- **Autores**: Oscar Juárez Ortiz, Pedro Emiliano Romero Osorio.
- **Asesora**: Ing. Verónica Moreno Jiménez.

---

## Requerimientos y Alcance del Sistema

El sistema fue diseñado para centralizar y estandarizar la operación médica y administrativa de hospitales y clínicas bajo criterios de integridad referencial y privacidad de datos clínicos (HIPAA / RGPD):

- **Expediente Único de Pacientes**: Datos demográficos, seguro médico, contacto de emergencia, catálogo de alergias (`AlergiasPacientes`) y condiciones preexistentes (`PacientesCondicionesPre`: Diabetes, Hipertensión, EPOC, Lupus).
- **Gestión de Cuerpo Médico e Instituciones**: Registro profesional (`noRegistroP`), horarios y días laborales (`Disponibilidades`), especialidades médicas (`MedicosEspecialidades`) y adscripción a instituciones de salud (`InstitucionesSalud`).
- **Agenda, Bitácora Diaria y Consultas**: Programación de citas (`Agendaciones`, `Citas`), control de folios en `BitacoraDiaria` y emisión de informes de evolución clínica (`Informes`, `MedicosInformes`).
- **Diagnósticos, Laboratorios, Tratamientos y Farmacia**: Vinculación de diagnósticos con pruebas de laboratorio (`Pruebas`, `DiagnosticosPruebas`, `Resultados`), prescripción de tratamientos (`Tratamientos`, `TratamientosDiagnosticos`), recetas electrónicas (`Recetas`, `Medicamentos`, `RecetasMedicamentos`) y control de stock en servicios de farmacia (`Servicios`, `Inventarios`).

---

## Modelos de Ingeniería de Datos (23 Tablas)

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/bd-salud-er.png" alt="Diagrama Entidad-Relación SaludOP">
    <figcaption>Diagrama Entidad-Relación (Modelo Conceptual) del sistema de Historia Clínica Electrónica.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/bd-salud-relacional.png" alt="Diagrama Relacional SaludOP">
    <figcaption>Diagrama Relacional (Modelo Lógico) con las 23 tablas normalizadas y sus cardinalidades.</figcaption>
  </figure>
</div>

---

## Estructura DDL en SQL Server (`SaludOP`)

```sql
CREATE DATABASE SaludOP;
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

