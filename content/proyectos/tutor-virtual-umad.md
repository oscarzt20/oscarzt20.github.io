---
title: "Tutor Virtual UMAD — Asistente Académico con IA Generativa"
date: 2026-05-15
weight: 1
slug: "tutor-virtual-umad"
summary: "Plataforma web de tutoría inteligente que resuelve dudas académicas 24/7 mediante IA generativa contextualizada al plan de estudios, síntesis de voz y un avatar interactivo."
tags:
  - "Node.js"
  - "JavaScript"
  - "SQLite"
  - "Google Gemini API"
  - "Web Speech API"
  - "RAD / PSP / TSP"
categories:
  - "Desarrollo Web e IA"
cover:
  image: "/imagenes/proyectos/tutor-virtual-flujo.png"
  alt: "Arquitectura de flujo del Tutor Virtual UMAD"
  relative: false
---

## El Reto

Fuera del horario de clases, los estudiantes universitarios suelen recurrir a fuentes genéricas o respuestas de IA descontextualizadas que no coinciden con el enfoque pedagógico de sus asignaturas. A diferencia de los chatbots institucionales orientados únicamente a trámites administrativos, el objetivo de este proyecto fue construir un **Sistema de Tutoría Inteligente (STI)** alineado al plan de estudios de **Ingeniería de Software en la UMAD**, capaz de brindar acompañamiento académico confiable en cualquier momento.

- **Mi rol principal**: Diseño e implementación del Frontend responsivo (HTML5/CSS3/JS), experiencia de usuario (UI/UX) e integración multimodal de síntesis de voz y animación del avatar.
- **Trabajo colaborativo**: Desarrollado en equipo junto con Emmanuel Baltazar López (*Backend y API*) y Pedro Emiliano Romero Osorio (*Base de Datos y Pruebas*), bajo la dirección del Mtro. Carlos Zapata Bretón.

---

## Arquitectura de la Solución

El sistema se diseñó bajo una arquitectura **Cliente-Servidor desacoplada vía REST API**, estructurada en cuatro capas con responsabilidades claramente definidas:

### 1. Interfaz Multimodal y Accesibilidad (Frontend)
- Construida con **HTML5**, **CSS3 (*Mobile-First*)** y **JavaScript nativo**, aplicando los principios de accesibilidad **WCAG (POUR)** y las heurísticas de usabilidad de Nielsen.
- Incorpora un **Avatar 2D reactivo** sincronizado en tiempo real con los eventos `onstart` y `onend` de la **Web Speech API (`SpeechSynthesis`)**, permitiendo que el estudiante reciba explicaciones tanto en texto como por voz, con un control de silenciamiento disponible en todo momento.

### 2. Lógica de Negocio e Ingeniería de Prompts (Backend)
- Servidor en **Node.js y Express** que gestiona los endpoints `/api/registro`, `/api/login`, `/api/preguntar` y `/api/historial`.
- Implementa **enrutamiento dinámico de contexto**: antes de enviar una consulta al modelo de IA, el servidor recupera el perfil académico del alumno e inyecta un *System Prompt* especializado en Ingeniería de Software para asegurar respuestas pertinentes al temario universitario.
- Protege las credenciales (`GEMINI_API_KEY`) en variables de entorno y administra sesiones concurrentes en memoria.

### 3. Servicios Cognitivos y Persistencia Relacional
- Conexión asíncrona con **Google Gemini 2.5 API** con control de *timeouts* y manejo de cuotas.
- Base de datos relacional **SQLite (`umad_tutor.db`)** con cumplimiento **ACID**, restringiendo el acceso mediante expresiones regulares exclusivamente a correos institucionales (`@umad.edu.mx`).

| Tabla Relacional | Atributos Clave | Propósito en el Sistema |
| :--- | :--- | :--- |
| `Usuarios` | `id`, `nombre`, `correo`, `password`, `carrera` | Control de acceso institucional (`UNIQUE`) y perfil para contextualizar prompts. |
| `Chats` | `id`, `correo_usuario`, `pregunta`, `respuesta`, `fecha` | Trazabilidad histórica de sesiones de estudio por alumno (`DEFAULT CURRENT_TIMESTAMP`). |

---

## Ingeniería de Software y Documentación

El proyecto se ejecutó bajo la metodología de **Desarrollo Rápido de Aplicaciones (RAD)**, respaldada por una tesina técnica de 74 páginas que documenta todo el ciclo de ingeniería:

- **Especificación de Requerimientos**: Definición y trazabilidad de **12 Requerimientos Funcionales (`RF-01` a `RF-12`)** y **5 Requerimientos No Funcionales (`RNF-01` a `RNF-05`)**.
- **Modelado del Sistema**: Diagramas de navegación, diagramas de clases, diagramas de estados y flujo de orquestación del caso de uso principal.
- **Gestión de Configuración y Calidad**: Control de versiones con **Semantic Versioning (SemVer)**, **Conventional Commits** y seguimiento cuantitativo de tiempos y defectos mediante **PSP (Personal Software Process)** y **TSP (Team Software Process)**.

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/tutor-virtual-flujo.png" alt="Flujo arquitectónico del caso de uso principal">
    <figcaption>Orquestación entre la interfaz web, el servidor Express, SQLite y la API de Google Gemini.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/tutor-virtual-navegacion.png" alt="Diagrama de navegación del Tutor Virtual">
    <figcaption>Mapa de navegación y validación de acceso de la plataforma.</figcaption>
  </figure>
</div>

---

## Resultados e Impacto

- **Cumplimiento del 100%** de los requerimientos funcionales y no funcionales a lo largo de 5 fases iterativas, cerrando con **0 deuda técnica** tras detectar y corregir 31 bugs durante el desarrollo.
- **95.5% de tasa de aprobación** en pruebas Alpha/Beta sobre 120 consultas reales del plan de estudios de Ingeniería de Software.

| Componente Evaluado | Latencia Promedio | Tasa de Éxito |
| :--- | :--- | :--- |
| **Autenticación local (SQLite)** | `120 ms` | `99.8%` |
| **Consulta de historial (SQLite)** | `85 ms` | `99.9%` |
| **Inferencia en Google Gemini 2.5 API** | `1,850 ms` | `97.5%` |
| **Síntesis de voz (Web Speech API)** | `45 ms` | `100%` |
