---
title: "X-Force Arena — Ingeniería y Ciclo de Vida de un Ecosistema Gamer"
date: 2025-10-14
weight: 2
slug: "arena-videojuegos-xforce-smartwear"
summary: "Proyecto integral del ciclo de vida del software para un complejo de entretenimiento inmersivo: desde la ideación de un traje háptico inteligente hasta el diseño del ERP operativo y su subsistema de estacionamiento automatizado con QR."
tags:
  - "Ciclo de Vida del Software"
  - "Ingeniería de Requerimientos"
  - "Diseño de Sistemas"
  - "UML"
  - "Design Thinking"
  - "UI/UX"
categories:
  - "Ingeniería de Software y Diseño de Sistemas"
cover:
  image: "/imagenes/proyectos/xforce-ui-home.png"
  alt: "Ecosistema de software X-Force Arena"
  relative: false
---

## Visión Integral del Proyecto

**X-Force Arena** (desarrollado para la empresa ficticia *Nexus Interactive*) es un proyecto evolutivo que consolida las etapas fundamentales del **Ciclo de Vida del Desarrollo de Software (SDLC)**. En lugar de abordar ejercicios aislados, el proyecto modela el ecosistema tecnológico completo de una arena de videojuegos inmersiva a través de tres subsistemas interconectados:

1. **El Producto Inmersivo (*SmartWear V0.3*)**: El traje háptico inteligente que los visitantes rentan dentro de la arena para vivir partidas inmersivas y eventos de cosplay.
2. **El Núcleo Operativo y Administrativo (*X-Force Live*)**: El sistema central que controla la venta de boletos, la renta y mantenimiento de los trajes *SmartWear*, los inventarios de souvenirs/alimentos, el personal y la facturación del recinto.
3. **El Subsistema de Acceso y Movilidad (*Estacionamiento QR*)**: La plataforma de kioscos físicos y aplicación móvil integrada a las zonas de estacionamiento del complejo para agilizar el ingreso y cobro automatizado de los asistentes.

---

## Etapa 1: Ideación y Design Thinking (*SmartWear V0.3*)

El ciclo inició con la definición del producto diferenciador de la arena mediante la metodología **Design Thinking**. A partir de encuestas a usuarios y el análisis de necesidades en una matriz *Point of View (POV)*, se diseñó el prototipo conceptual **SmartWear V0.3**:

- **Inmersión Visual y Háptica**: Paneles de proyección *Quantum Dot* para renderizar *skins* dinámicas generadas por IA y sensores de retroalimentación táctil para simular impactos en partida.
- **Ecosistema Conectado**: Asistente de voz integrado, sincronización grupal entre jugadores dentro de la arena, autorregulación térmica y recarga solar.

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/smartwear-v03.jpg" alt="Prototipo conceptual SmartWear V0.3">
    <figcaption>Arquitectura conceptual del traje inteligente SmartWear V0.3.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/xforce-mapa-digital.jpg" alt="Mapa arquitectónico de la Arena X-Force">
    <figcaption>Distribución de las 12 zonas operativas de la arena: taquilla, renta/entrega de trajes SmartWear, áreas de juego y estacionamientos A y B.</figcaption>
  </figure>
</div>

---

## Etapa 2: Modelado de Negocios y Diseño de Sistemas (*X-Force Live*)

Con el modelo operativo del recinto definido, se realizó el levantamiento formal de requerimientos y la arquitectura del sistema central encargado de administrar todas las áreas del mapa de la arena:

- **Ingeniería de Requerimientos y Factibilidad**: Realización de **7 minutas con *stakeholders***, definición de **120 Reglas de Negocio (`RN_01` a `RN_120`)** y evaluación de factibilidad técnica, operativa, legal y financiera (estimando 137 horas de ingeniería sobre una arquitectura MVC con PHP y MySQL).
- **Modelado Arquitectónico en UML**:
  - Control de acceso para **8 roles operativos** (*Administrador del parque, Cajero, Administrador del sistema, Gerentes de ventas, almacén y compras, Empleado y Cliente*).
  - Especificación de **10 Casos de Uso (`CU_01` a `CU_10`)** que integran la venta de accesos (General y VIP), el préstamo y restauración de los trajes *SmartWear V0.3*, el control de inventario, órdenes de compra, cierre de cajas y facturación.
  - Modelado de **Diagramas de Actividades** (flujos base y alternativos), **Diagramas de Estados** para **15 objetos de negocio**, **Diagramas de Navegación** y **Diagramas de Clases UML**.

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/xforce-ui-home.png" alt="Acceso al sistema X-Force Live">
    <figcaption>Pantalla de autenticación del sistema central X-Force Live.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/xforce-ui-sistema.png" alt="Especificación de interfaz de usuario con tipos de datos">
    <figcaption>Diseño de interfaces operativas (Altas, Bajas, Cambios y Consultas) con validación estricta de tipos y longitudes de campo.</figcaption>
  </figure>
</div>

---

## Etapa 3: Extensión de Autoservicio (*Kioscos y App de Estacionamiento QR*)

Para completar la experiencia del visitante desde su llegada a las zonas de **Estacionamiento A y B** del complejo, se diseñó un subsistema de **19 pantallas interactivas (`PA_16_01` a `PA_16_18`)** que elimina las filas de cobro manual:

- **Kioscos de Entrada y Salida**: Emisión y validación de boletos con código QR, cálculo automático de tarifa por tiempo de estancia en base de datos (`TIMESTAMPDIFF`) y pasarela de pago con tarjeta.
- **Billetera Móvil para Visitantes**: Aplicación móvil para escanear el código QR de acceso, recargar saldo digital y consultar el historial de visitas a la arena.

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/estacionamiento-kiosco-qr.png" alt="Kiosco de acceso al estacionamiento de la arena">
    <figcaption>Interfaz de kiosco en la entrada del estacionamiento de la arena (PA_16_01).</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/estacionamiento-app-movil.png" alt="Aplicación móvil de estacionamiento y saldo QR">
    <figcaption>Aplicación móvil del visitante con lector QR, gestión de saldo e historial de accesos (PA_16_09).</figcaption>
  </figure>
</div>

---

## Documentación y Entregables de Ingeniería

Uno de los pilares de este proyecto es su **rigor documental** (más de **230 páginas de especificación formal** elaboradas en equipo bajo la asesoría de la Mtra. Martha Patricia Hernández Zamora en la UMAD), demostrando dominio práctico de la ingeniería de software antes de escribir código:

- **Plan de Gestión de Configuración de Software (SCM)**: Nomenclatura estandarizada de artefactos, control de cambios y versionado documental.
- **Catálogo de Datos y Formatos**: Especificación de **18 Reportes Gerenciales (`RE_01`–`RE_18`)** y **23 Formatos Operativos (`FO_01`–`FO_23`)** (KARDEX, contratos, cartas responsivas de renta de trajes, tickets, facturas y nómina).
- **Trazabilidad Completa**:Cada pantalla de usuario está vinculada directamente con su regla de negocio, su caso de uso, su tabla relacional y sus validaciones de entrada.
