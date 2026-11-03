---
title: "Implementación de Servidor Web Seguro (LAMP + HTTPS/TLS + SSH + Wireshark)"
date: 2025-05-17
weight: 8
slug: "servidor-web-seguro-linux"
summary: "Diseño, configuración y auditoría de un servidor web transaccional en Ubuntu 22.04 sobre VirtualBox con Apache2 (HTTPS/TLS), MariaDB, aplicación PHP CRUD, acceso remoto OpenSSH y análisis de tráfico en Wireshark."
tags:
  - "Linux (Ubuntu Server)"
  - "Apache2 / HTTPS"
  - "MariaDB"
  - "SSH"
  - "Wireshark"
  - "Ciberseguridad"
  - "Redes"
categories:
  - "Redes, Infraestructura y Ciberseguridad"
cover:
  image: "/imagenes/proyectos/servidor-seguro-cartel.png"
  alt: "Cartel del Proyecto Servidor Web Seguro"
  relative: false
---

## Descripción del Proyecto

Proyecto individual desarrollado para la asignatura *Redes de Área Local (LAN)* en la **Universidad Madero (UMAD)**, enfocado en la construcción desde cero de una infraestructura de **servidor web seguro de bajo costo basada 100% en software libre**, garantizando la confidencialidad, integridad y disponibilidad de los datos en tránsito y en reposo.

- **Autor**: Oscar Juárez Ortiz
- **Institución**: Universidad Madero (UMAD), Puebla

![Cartel del Proyecto Servidor Web Seguro](/imagenes/proyectos/servidor-seguro-cartel.png)

---

## Arquitectura, Servicios y Seguridad Lógica

1. **Virtualización y Sistema Operativo**:
   - Despliegue de **Ubuntu 22.04 LTS** sobre **Oracle VM VirtualBox**, configurando jerarquías de grupos, permisos de usuarios y reglas de reenvío de puertos NAT (*Port Forwarding*: `8443 → 443` para HTTPS y `2222 → 22` para SSH).
2. **Servidor Web Cifrado (Apache2 + SSL/TLS)**:
   - Configuración de *VirtualHosts* en **Apache2** y generación de certificados digitales X.509 autofirmados con **OpenSSL** para habilitar comunicaciones seguras sobre **HTTPS (TLS)** en lugar de HTTP en texto plano.
3. **Base de Datos y Aplicación Web CRUD (`MariaDB` + `PHP`)**:
   - Instalación y aseguramiento de **MariaDB** con la base de datos relacional `tiendaDb` (tablas `categorias` y `productos`), conectada a un **Sistema CRUD en PHP** capaz de insertar, listar, actualizar y eliminar productos y categorías de forma segura.
4. **Administración Remota (OpenSSH) y Pruebas DDNS (No-IP)**:
   - Administración remota cifrada mediante **OpenSSH** desde el host Windows empleando **PuTTY** (`127.0.0.1:2222`).
   - Configuración del cliente **No-IP** para DNS Dinámico (DDNS) y diagnóstico técnico de las restricciones de reenvío de puertos / CGNAT impuestas por el router del proveedor de servicios de Internet (Totalplay) hacia la red WAN.
5. **Auditoría de Tráfico con Wireshark**:
   - Captura e inspección de paquetes en la interfaz *Loopback* (`\Device\NPF_Loopback`, `127.0.0.1`) verificando el flujo de segmentos TCP/SSH en el túnel `2222 ↔ 56611` y comprobando la protección criptográfica de las sesiones remotas.

---

## Topología y Auditoría de Tráfico

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/servidor-seguro-topologia.png" alt="Topología de red del servidor seguro">
    <figcaption>Diagrama de topología entre el host Windows, la máquina virtual Ubuntu Linux, el switch LAN y la frontera WAN hacia No-IP.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/servidor-seguro-wireshark.png" alt="Análisis de tráfico en Wireshark">
    <figcaption>Captura y auditoría de paquetes en Wireshark sobre el túnel local reenviado hacia el servidor Ubuntu.</figcaption>
  </figure>
</div>
