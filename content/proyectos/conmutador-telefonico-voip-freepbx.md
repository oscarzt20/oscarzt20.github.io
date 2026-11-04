---
title: "Central Telefónica VoIP en la Nube — Telefonía IP para PyMEs"
date: 2025-11-23
weight: 7
slug: "conmutador-telefonico-voip-freepbx"
summary: "Despliegue en la nube de un conmutador telefónico IP (PBX) basado en software libre con Debian 12, FreePBX 17 y Asterisk 22 para interconectar sucursales corporativas a bajo costo."
tags:
  - "VoIP / SIP"
  - "Linux (Debian 12)"
  - "FreePBX / Asterisk"
  - "Nube / VPS"
  - "Redes"
categories:
  - "Redes, Infraestructura y Ciberseguridad"
cover:
  image: "/imagenes/proyectos/voip-freepbx-cartel.png"
  alt: "Cartel técnico del Proyecto Conmutador Telefónico VoIP"
  relative: false
---

## El Problema

Muchas pequeñas y medianas empresas (PyMEs) continúan dependiendo de líneas telefónicas convencionales (PSTN) o centrales propietarias cuyos costos de licenciamiento y cableado físico dificultan escalar la comunicación entre diferentes sucursales. El objetivo de este proyecto fue desplegar en la nube un **conmutador telefónico IP (PBX) de código abierto** que permitiera comunicar sedes remotas a través de Internet con alta disponibilidad, seguridad perimetral y una reducción drástica en costos operativos.

![Cartel del Proyecto Conmutador Telefónico VoIP](/imagenes/proyectos/voip-freepbx-cartel.png)

---

## Arquitectura e Implementación en la Nube

La solución se construyó sobre una infraestructura virtualizada en la nube, eliminando la necesidad de hardware dedicado en sitio:

1. **Servidor VPS y Sistema Base**: Instancia KVM alojada en **Hostinger** (2 vCPU, 4 GB RAM, 50 GB SSD) ejecutando **Debian 12 GNU/Linux**.
2. **Motor de Conmutación y Gestión**: Integración de **Asterisk 22** como motor de telefonía junto con **FreePBX 17** para la administración centralizada de rutas, extensiones y políticas de llamada.
3. **Señalización y Transporte Multimedia**:
   - **Protocolo SIP (RFC 3261)** mediante el controlador **PJSIP** (`5060/UDP`) para el registro de terminales y establecimiento de sesiones.
   - **Protocolo RTP** (`10000–20000/UDP`) para la transmisión de audio en tiempo real entre sedes.
4. **Seguridad Perimetral**: Configuración del **Sangoma Smart Firewall** y reglas adaptativas para autorizar únicamente clientes legítimos y bloquear intentos de intrusión por fuerza bruta.
5. **Interconexión Multi-Sede**: Aprovisionamiento y validación de llamadas simultáneas con el softphone **Zoiper 5** simulando tres sedes operativas (*Administración CDMX — Ext. 101*, *Gerencia Cancún — Ext. 102* y *Facturación Guadalajara — Ext. 103*).

---

## Documentación e Impacto Financiero

El proyecto cuenta con una **tesina técnica de 21 páginas** (desarrollada en la UMAD junto con Pedro Emiliano Romero Osorio y Emmanuel Baltazar López) que incluye el estudio de factibilidad legal y financiera, el análisis de protocolos de red y el manual paso a paso de implementación.

| Indicador Evaluado | Asterisk Puro (Manual) | Solución Desplegada (FreePBX 17 + Asterisk 22) |
| :--- | :--- | :--- |
| **Tiempo de puesta en marcha** | `80 – 120 horas` (configuración manual en consola) | **`8 – 12 horas`** (despliegue automatizado + gestión web) |
| **Administración y respaldos** | Scripts manuales propensos a errores de sintaxis | Panel centralizado con validación y *rollback* |
| **Costo operativo mensual** | Alto en centrales comerciales (licencias por usuario) | **`$350 MXN / mes`** (solo costo del VPS, `$0` en licencias) |
