---
title: "Servidor Web Seguro en Linux — Infraestructura Cifrada con Software Libre"
date: 2025-05-17
weight: 8
slug: "servidor-web-seguro-linux"
summary: "Configuración y aseguramiento desde cero de un servidor Ubuntu con Apache2 (HTTPS/TLS), base de datos MariaDB, sistema CRUD en PHP, administración remota por SSH y auditoría de paquetes en Wireshark."
tags:
  - "Linux (Ubuntu Server)"
  - "Apache2 / HTTPS"
  - "MariaDB"
  - "SSH"
  - "Wireshark"
  - "Ciberseguridad"
categories:
  - "Redes, Infraestructura y Ciberseguridad"
cover:
  image: "/imagenes/proyectos/servidor-seguro-cartel.png"
  alt: "Cartel del Proyecto Servidor Web Seguro"
  relative: false
---

## El Reto

Desplegar aplicaciones web sin controles de cifrado ni segmentación de privilegios expone las credenciales y transacciones de los usuarios a ataques de interceptación en la red. Este proyecto individual consistió en diseñar, configurar y auditar una infraestructura de **servidor web transaccional segura basada 100% en herramientas de código abierto**, comprobando que es posible proteger los datos en tránsito y en reposo sin recurrir a licencias comerciales costosas.

![Cartel del Proyecto Servidor Web Seguro](/imagenes/proyectos/servidor-seguro-cartel.png)

---

## Arquitectura e Implementación de Servicios

La infraestructura se construyó sobre una máquina virtual con **Ubuntu 22.04 LTS** en **Oracle VM VirtualBox**, aplicando controles de seguridad en cada capa del servidor:

1. **Control de Acceso y Sistema Operativo**: Configuración de jerarquías de grupos y usuarios con privilegios mínimos, deshabilitando accesos innecesarios y estableciendo reglas de reenvío de puertos NAT (*Port Forwarding*: `8443 → 443` para tráfico web cifrado y `2222 → 22` para administración remota).
2. **Cifrado Web con SSL/TLS (Apache2 + OpenSSL)**: Generación de certificados digitales X.509 autofirmados y configuración de *VirtualHosts* en **Apache2** para forzar la comunicación mediante **HTTPS**, protegiendo la integridad de las peticiones entre el navegador y el servidor.
3. **Persistencia y Aplicación CRUD (`MariaDB` + `PHP`)**: Implementación de la base de datos relacional `tiendaDb` (tablas `categorias` y `productos`) conectada a un **sistema web CRUD en PHP** para gestionar el catálogo e inventario de una tienda.
4. **Administración Remota (`OpenSSH`) y Diagnóstico WAN (`No-IP`)**: Gestión del servidor desde el host Windows mediante túneles cifrados en **PuTTY**, complementada con pruebas de DNS dinámico (**No-IP**) que permitieron diagnosticar las restricciones de *Port Forwarding* / CGNAT impuestas por el proveedor de Internet en la frontera WAN.
5. **Auditoría de Red con Wireshark**: Captura e inspección de tramas en la interfaz local para verificar el establecimiento de las sesiones TCP/SSH y comprobar que la carga útil viaja cifrada.

---

## Documentación Técnica y Evidencias

El trabajo incluye una **tesina de ingeniería de 31 páginas** (con 42 ilustraciones técnicas paso a paso elaboradas en la UMAD), abarcando desde el análisis de factibilidad y marco teórico (estándares IEEE 802.3, TLS y SSH) hasta el manual completo de instalación, pruebas y auditoría de paquetes.

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/servidor-seguro-topologia.png" alt="Topología de red del servidor seguro">
    <figcaption>Topología de red entre el host cliente, la máquina virtual Ubuntu Server, el switch LAN y la salida WAN.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/servidor-seguro-wireshark.png" alt="Auditoría de tráfico en Wireshark">
    <figcaption>Inspección de paquetes en Wireshark validando el flujo cifrado en el túnel hacia el servidor.</figcaption>
  </figure>
</div>
