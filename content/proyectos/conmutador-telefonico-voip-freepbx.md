---
title: "Servidor PBX de Telefonía VoIP en la Nube con FreePBX y Asterisk"
date: 2025-11-23
weight: 7
slug: "conmutador-telefonico-voip-freepbx"
summary: "Despliegue en la nube (VPS Debian 12 en Hostinger) de un conmutador telefónico IP (PBX) de código abierto utilizando FreePBX 17 y Asterisk 22 con protocolo SIP/PJSIP, Firewall Inteligente y clientes Zoiper."
tags:
  - "Redes"
  - "VoIP / SIP"
  - "Linux (Debian 12)"
  - "FreePBX / Asterisk"
  - "VPS / Nube"
  - "Seguridad en Redes"
categories:
  - "Redes, Infraestructura y Ciberseguridad"
cover:
  image: "/imagenes/proyectos/voip-freepbx-cartel.png"
  alt: "Cartel técnico del Proyecto Conmutador Telefónico VoIP"
  relative: false
---

## Resumen del Proyecto

Proyecto desarrollado para la asignatura *Redes de Área Extendida (WAN)* en la **Universidad Madero (UMAD)**, enfocado en sustituir los costosos y rígidos sistemas telefónicos tradicionales (PSTN) o centrales IP propietarias mediante la implementación en la nube de un **servidor de conmutación telefónica (PBX) de código abierto** orientado a pequeñas y medianas empresas (PYMES).

- **Autores**: Oscar Juárez Ortiz, Pedro Emiliano Romero Osorio, Emmanuel Baltazar López.

![Cartel del Proyecto Conmutador Telefónico VoIP](/imagenes/proyectos/voip-freepbx-cartel.png)

---

## Arquitectura e Infraestructura Implementada

- **Infraestructura en la Nube (VPS)**: Servidor virtual privado KVM alojado en **Hostinger** (2 vCPU, 4 GB RAM, 50 GB SSD) ejecutando **Debian 12 GNU/Linux**.
- **Motor y Plataforma PBX**: **Asterisk 22.5.2** integrado con **FreePBX 17.0.21** (bajo licencia libre GPLv2+).
- **Protocolos de Señalización y Transporte**:
  - **SIP (RFC 3261)** mediante el *channel driver* **PJSIP** en el puerto `5060/UDP` para establecimiento, modificación y término de sesiones.
  - **RTP (Real-time Transport Protocol)** en los puertos dinámicos `10000–20000/UDP` para el flujo de audio en tiempo real.
- **Seguridad Perimetral**: Configuración del **Sangoma Smart Firewall (Responsive Firewall + Fail2Ban)** restringiendo el acceso administrativo y autorizando únicamente segmentos e IPs confiables.
- **Aprovisionamiento y Pruebas Multi-Sede**: Configuración de extensiones corporativas (`EXT. 101 / 1001` Área administrativa CDMX, `EXT. 102 / 1002` Gerencia Cancún, `EXT. 103 / 1003` Facturación Guadalajara), panel **UCP (User Control Panel)** y validación de llamadas simultáneas mediante el softphone **Zoiper 5**.

---

## Análisis de Costo-Beneficio y Resultados

| Indicador Evaluado | Asterisk Puro (Desde Cero) | Implementación con FreePBX 17 + Asterisk 22 |
| :--- | :--- | :--- |
| **Tiempo de despliegue** | `80 – 120 horas` (configuración manual de dialplan y NAT) | **`8 – 12 horas`** (instalación automatizada + administración GUI) |
| **Mantenimiento y Respaldo** | Manual mediante scripts personalizados | Automatizado vía panel web con validaciones y *rollback* |
| **Costo Operativo Mensual (TCO)** | Alto en soluciones comerciales (Cisco CallManager, 3CX) | **`$350 MXN / mes`** (infraestructura VPS base, `$0` en licencias) |

