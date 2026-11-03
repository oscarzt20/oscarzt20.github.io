---
title: "Plataforma Web de Tutor Virtual con IA Generativa (UMAD)"
date: 2026-05-15
weight: 1
slug: "tutor-virtual-umad"
summary: "Aplicación web interactiva de tutoría académica impulsada por Google Gemini 2.5, Node.js/Express, SQLite y avatar 2D multimodal con síntesis de voz nativa (Web Speech API) para estudiantes de Ingeniería de Software."
tags:
  - "Inteligencia Artificial"
  - "Node.js"
  - "JavaScript"
  - "SQLite"
  - "Web Speech API"
  - "Google Gemini"
  - "RAD / PSP / TSP"
categories:
  - "Desarrollo Web e IA"
cover:
  image: "/imagenes/proyectos/tutor-virtual-flujo.png"
  alt: "Diagrama de flujo y arquitectura del Tutor Virtual UMAD"
  relative: false
---

## Resumen del Proyecto

Este proyecto de investigación aplicada consistió en el diseño, desarrollo y validación de una **plataforma web de tutoría virtual impulsada por Inteligencia Artificial Generativa**, creada para la **Universidad Madero Puebla (UMAD)** y orientada a fortalecer el proceso de enseñanza-aprendizaje de los estudiantes de **Ingeniería de Software**.

- **Equipo de Desarrollo**: Oscar Juárez Ortiz (*Frontend, UI/UX e integración de Web Speech API*), Emmanuel Baltazar López (*Backend, API Gemini y Arquitectura*), Pedro Emiliano Romero Osorio (*Base de Datos SQLite, Testing y Documentación*).
- **Director de Tesis**: Mtro. Carlos Zapata Bretón.
- **Metodología**: Desarrollo Rápido de Aplicaciones (**RAD**) complementado con métricas de **PSP (Personal Software Process)** y **TSP (Team Software Process)**.

---

## Problemática y Objetivo

Los estudiantes enfrentan dificultades frecuentes para acceder a fuentes confiables, contextualizadas y oportunas que refuercen los contenidos revisados en clase, derivando en rezago académico y reprobación en asignaturas clave. A diferencia de chatbots institucionales orientados a trámites administrativos, el **Tutor Virtual UMAD** fue diseñado específicamente como un **Sistema de Tutoría Inteligente (STI)** alineado al plan de estudios de Ingeniería de Software, ofreciendo asistencia pedagógica suplementaria 24/7 con interacción multimodal (texto, voz y avatar reactivo).

---

## Arquitectura del Sistema y Stack Tecnológico

El sistema implementa una arquitectura **Cliente-Servidor basada en REST API** dividida en cuatro capas desacopladas:

1. **Capa de Presentación (Frontend Multimodal)**:
   - Desarrollada con **HTML5**, **CSS3 responsivo (Mobile-First, Flexbox y Media Queries)** y **JavaScript Vanilla**, siguiendo principios de accesibilidad **WCAG (POUR)** y heurísticas de usabilidad de Nielsen.
   - Integra un **Avatar 2D reactivo** sincronizado dinámicamente con los eventos asíncronos `onstart` y `onend` de la **Web Speech API (`SpeechSynthesis`)**, alternando sprites para simular el habla en tiempo real, acompañado de un interruptor de accesibilidad (*Toggle de Voz*) en todo momento.
2. **Capa de Lógica de Negocio (Backend Node.js + Express)**:
   - Expone los endpoints REST `/api/registro`, `/api/login`, `/api/preguntar` y `/api/historial`.
   - Implementa **enrutamiento dinámico de personalidad (Prompt Engineering)**: recupera el perfil académico del estudiante desde la base de datos e inyecta un `System Prompt` especializado antes de consultar al modelo fundacional.
   - Gestiona múltiples sesiones concurrentes mediante estructuras `Map` en memoria y protege la clave `GEMINI_API_KEY` exclusivamente en variables de entorno (`.env`) del servidor.
3. **Capa de Servicios Cognitivos**:
   - Integración con **Google Gemini 2.5 API**, con manejo explícito de excepciones, límites de cuota y *timeouts*.
4. **Capa de Persistencia Relacional (SQLite)**:
   - Base de datos incrustada (`umad_tutor.db`) con cumplimiento **ACID** y validación estricta por expresión regular (**Regex**) que restringe el registro exclusivamente a correos institucionales `@umad.edu.mx`.

### Modelo de Base de Datos Relacional

| Tabla | Campos Principales | Restricciones y Propósito |
| :--- | :--- | :--- |
| `Usuarios` | `id`, `nombre`, `correo`, `password`, `carrera` | `PK AUTOINCREMENT`, `correo UNIQUE NOT NULL` (`@umad.edu.mx`), perfil para enrutamiento de prompts |
| `Chats` | `id`, `correo_usuario`, `pregunta`, `respuesta`, `fecha` | `PK AUTOINCREMENT`, `FK Lógica` hacia `Usuarios(correo)`, `DEFAULT CURRENT_TIMESTAMP` para historial cronológico |

---

## Diagramas de Ingeniería

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/tutor-virtual-flujo.png" alt="Diagrama de flujo del caso de uso principal">
    <figcaption>Orquestación técnica del Caso de Uso Principal (Frontend → Backend Express → SQLite → Google Gemini API).</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/tutor-virtual-navegacion.png" alt="Diagrama de navegación del sistema">
    <figcaption>Diagrama de navegación y flujo de pantallas del Tutor Virtual UMAD.</figcaption>
  </figure>
</div>

---

## Resultados y Métricas de Calidad

Se implementaron el **100% de los 12 Requerimientos Funcionales (`RF-01` a `RF-12`)** y los **5 Requerimientos No Funcionales (`RNF-01` a `RNF-05`)**, gestionando el repositorio bajo **Semantic Versioning (SemVer)** y **Conventional Commits** (`feat:`, `fix:`, `refactor:`, `docs:`).

| Módulo Evaluado | Latencia Promedio | Tasa de Éxito |
| :--- | :--- | :--- |
| **Login / Autenticación (SQLite local)** | `120 ms` | `99.8%` |
| **Consultas de Historial (SQLite local)** | `85 ms` | `99.9%` |
| **API Google Gemini 2.5 (IA Generativa)** | `1,850 ms` | `97.5%` |
| **Renderizado y Voz (Web Speech API)** | `45 ms` | `100%` |

- **Calidad de Software**: 31 defectos detectados y resueltos a lo largo de las 5 fases del cronograma (0 deuda técnica acumulada al cierre).
- **Validación con Usuarios**: **95.5% de tasa de aprobación** en pruebas Alpha/Beta sobre 120 consultas académicas realizadas en el perfil de Ingeniería de Software.

