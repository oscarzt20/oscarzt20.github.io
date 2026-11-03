---
title: "Arena de Videojuegos 'X-Force', Traje Háptico 'SmartWear V0.3' y Sistema de Estacionamiento QR"
date: 2024-12-01
weight: 4
slug: "arena-videojuegos-xforce-smartwear"
summary: "Proyecto integral del Ciclo de Vida de Software ( más de 220 páginas de ingeniería): Design Thinking para el traje inteligente SmartWear V0.3, Modelado de Negocios (120 reglas de negocio), Diseño de Sistemas UML/MVC y prototipos UI/UX para la arena X-Force y su sistema de estacionamiento QR."
tags:
  - "Ingeniería de Software"
  - "Diseño de Sistemas"
  - "UML"
  - "Requerimientos"
  - "Design Thinking"
  - "UI/UX"
  - "MySQL"
categories:
  - "Ingeniería de Software y Diseño de Sistemas"
cover:
  image: "/imagenes/proyectos/xforce-ui-home.png"
  alt: "Interfaz principal de X-Force Live"
  relative: false
---

## Visión General del Proyecto

Este proyecto multidisciplinario abarca el **ciclo de vida completo de ingeniería de software** desarrollado a lo largo de tres asignaturas en la **Universidad Madero (UMAD)** (*Modelado de Negocios y Requerimientos*, *Proceso de Diseño de Sistemas* y *Sistemas de Información Gerencial*), para la empresa **Nexus Interactive** y su complejo de entretenimiento inmersivo **Arena de Videojuegos "X-Force"** (ubicado en WTC CDMX).

- **Autores**: Oscar Juárez Ortiz, José Brian Molina Nochebuena, Pedro Emiliano Romero Osorio.
- **Asesora**: Mtra. Martha Patricia Hernández Zamora.

---

## Fase 1: Design Thinking y Prototipo "SmartWear V0.3"

Mediante investigación de usuarios (encuestas estadísticas y matriz *Point of View — POV* clasificando ideas conservadoras, innovadoras y extremas), se diseñó el traje inteligente **SmartWear V0.3** para cosplay y combate inmersivo en la arena:

- **Paneles de Proyección Quantum Dot**: Proyección digital de alta fidelidad con *skins* generadas por IA, modo camuflaje/invisibilidad y respuesta háptica para simular texturas e impactos.
- **Asistente Virtual IA y Conectividad**: Control por voz, traducción instantánea y sincronización grupal con otros trajes en eventos.
- **Ergonomía y Sostenibilidad**: Recarga mediante luz solar, gorro integrado para simulación de casco/rostro y tela transpirable con autorregulación térmica.

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/smartwear-v03.jpg" alt="Prototipo SmartWear V0.3">
    <figcaption>Especificación conceptual y componentes tecnológicos del traje inteligente SmartWear V0.3.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/xforce-mapa-digital.jpg" alt="Mapa Digital de la Arena de Videojuegos X-Force">
    <figcaption>Mapa arquitectónico digital de las 12 zonas operativas de la Arena de Videojuegos (Game Zone).</figcaption>
  </figure>
</div>

---

## Fase 2: Modelado de Negocios y Diseño de Sistemas (201 Páginas)

Se elaboró la especificación formal del sistema de información gerencial y operativo de la arena bajo estándares de **Gestión de Configuración de Software (SCM)** y modelado **UML en Rational Rose 7.0**:

1. **Ingeniería de Requerimientos y Reglas de Negocio**:
   - Levantamiento de **7 minutas formales** con *stakeholders* y definición de **120 Reglas de Negocio (`RN_01` a `RN_120`)**.
   - Estudio de factibilidad técnica, económica, operativa y legal (presupuesto estimado de `$34,422.31 MXN` en 137 horas de *humanware*; arquitectura objetivo con **Yii Framework v1.1.1, PHP 5, MySQL 5.5 y WAMP Server**).
2. **Modelado Funcional y Arquitectónico**:
   - **8 Roles de Usuario** (*Administrador del parque, Cajero, Administrador del sistema, Gerente de ventas, Gerente de almacén, Gerente de compras, Empleado, Cliente*).
   - **10 Casos de Uso del Sistema (`CU_01` a `CU_10`)**: Control de acceso y menús por rol, gestión ABC de empleados y clientes, catálogo e inventario de souvenirs/alimentos, venta de boletos (General `$180` / VIP `$500`), renta y restauración de trajes inteligentes (`$2,000`), arqueo/cierre de cajas, órdenes de compra a proveedores y facturación.
   - **18 Reportes (`RE_01`–`RE_18`)** y **23 Formatos (`FO_01`–`FO_23`)** (Contratos, KARDEX, Tickets, Facturas, Cartas responsivas, Nómina y Estados de cuenta).
   - **Diagramas UML**: Diagramas de Casos de Uso, Diagramas de Actividades con carriles (*swimlanes*) para flujos base y alternativos, Diagramas de Estados para **15 objetos de negocio (`OBJ_01`–`OBJ_15`)**, Diagramas de Navegación por rol y **Diagramas de Clases UML** con multiplicidades.

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/xforce-ui-home.png" alt="Pantalla de inicio de sesión X-Force Live">
    <figcaption>Interfaz de autenticación del sistema web X-Force Live.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/xforce-ui-sistema.png" alt="Pantalla de gestión del sistema X-Force Live">
    <figcaption>Diseño de pantallas operativas (Altas, Bajas, Cambios y Consultas) con validación de campos tipados.</figcaption>
  </figure>
</div>

---

## Fase 3: Prototipo de Estacionamiento Automatizado y App Móvil QR

Como extensión de *Sistemas de Información Gerencial*, se diseñó un ecosistema de **19 pantallas interactivas (`PA_16_01` a `PA_16_18`)** que conecta los kioscos físicos de entrada/salida del estacionamiento con una aplicación móvil de billetera digital:

- **Kiosco de Entrada y Salida**: Emisión de boleto físico o código QR, validación de lectura e impresión y escaneo de salida.
- **Cálculo Tarifario en SQL**: Integración de consultas en tiempo real (`SELECT id_ticket, TIMESTAMPDIFF(HOUR, horaE, NOW()) * 15 AS montoTotal FROM TicketEstacionamiento`) y pasarela de pago con tarjeta.
- **App Móvil de Usuario**: Recarga de saldo (`$15` a `$100`), generación de QR dinámico de acceso/pago y consulta de historial de estancias (`Mis Accesos`).

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/estacionamiento-kiosco-qr.png" alt="Kiosco de estacionamiento QR">
    <figcaption>Pantalla de kiosco para emisión y escaneo de boleto QR (PA_16_01).</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/estacionamiento-app-movil.png" alt="App móvil de estacionamiento">
    <figcaption>Interfaz móvil para escaneo QR, recarga de saldo e historial de accesos (PA_16_09).</figcaption>
  </figure>
</div>

