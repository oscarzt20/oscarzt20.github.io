---
title: "SAP S/4HANA Fiori — Gestión de Procesos Comerciales y Logísticos (SD & MM)"
date: 2025-05-18
weight: 6
slug: "sap-s4hana-fiori-sd-mm"
summary: "Ejecución y auditoría de los ciclos empresariales Order-to-Cash (Ventas y Distribución) y Procure-to-Pay (Gestión de Materiales) integrados con contabilidad financiera en SAP S/4HANA."
tags:
  - "SAP S/4HANA"
  - "SAP Fiori"
  - "SAP SD"
  - "SAP MM"
  - "ERP"
categories:
  - "Sistemas Empresariales (ERP)"
cover:
  image: "/imagenes/proyectos/sap-fiori-sd.png"
  alt: "Flujo de documentos en SAP S/4HANA Fiori"
  relative: false
---

## Contexto y Objetivo

En las organizaciones modernas, las áreas de ventas, almacén, compras y finanzas no operan como silos independientes: cada movimiento físico de mercancía genera un impacto financiero inmediato. Este proyecto consistió en la configuración, ejecución y auditoría de **40 procesos transaccionales de punta a punta** dentro del ERP **SAP S/4HANA** mediante la interfaz **SAP Fiori** (caso de estudio *Global Bike v4.2*), validando la integración operativa y contable entre los módulos **SD (*Sales & Distribution*)**, **MM (*Materials Management*)** y **FI (*Financial Accounting*)**.

---

## 1. Ciclo Comercial *Order-to-Cash* (Módulo SD)

Se ejecutaron los **16 subprocesos** que transforman la solicitud de un cliente en un ingreso conciliado en libros contables:

| Fase del Ciclo | Operación en SAP Fiori | Documento Generado |
| :--- | :--- | :--- |
| **1. Datos Maestros (BP)** | Alta de cliente comercial y persona de contacto vinculada | `BP 1003796` / `1003797` |
| **2. Preventa** | Registro de consulta del cliente (*Inquiry*) y emisión de cotización formal (*Quotation*) | `10000258` → `20000197` |
| **3. Orden de Venta** | Generación del pedido de venta (*Standard Order*) referenciando la cotización aprobada | `212` |
| **4. Expedición y Almacén** | Creación de entrega saliente (*Outbound Delivery*), *Picking* y salida de mercancía (*Post Goods Issue*) | `80000202` (`GI 4900038704`) |
| **5. Facturación y Cobro** | Emisión de factura al cliente (*Invoice*) y contabilización del pago entrante en el Libro Mayor (G/L) | `90000151` → `JE 1400000672` |

---

## 2. Ciclo de Aprovisionamiento *Procure-to-Pay* (Módulo MM)

Se completaron los **24 subprocesos** de abastecimiento, licitación de proveedores, recepción física en múltiples entregas y liquidación de cuentas por pagar:

| Fase del Ciclo | Operación en SAP Fiori | Documento Generado |
| :--- | :--- | :--- |
| **1. Datos Maestros** | Alta de proveedor (*Mid-West Supply 329*) y creación de material comercial (*Trading Goods*) | `BP 1003893` / `CHLK1329` |
| **2. Requisición y Licitación** | Solicitud interna de compra (*Purchase Requisition*) y petición de oferta (*RFQ*) | `10000800` → `7000000237` |
| **3. Evaluación de Ofertas** | Comparativa de precios entre 3 proveedores (*Bid Evaluation*), adjudicando la oferta óptima | `8000000574` (*Awarded*) |
| **4. Orden de Compra (PO)** | Emisión de *Purchase Order* vinculada a la cotización ganadora | `4500000278` |
| **5. Recepción y Facturación** | Entrada física de mercancías en dos entregas parciales (*Goods Receipt*) y verificación de facturas | `GR 5000000439 / 458`<br>`INV 5105600694 / 695` |
| **6. Tesorería (FI-AP)** | Contabilización del pago saliente al proveedor (*Outgoing Payment*) y cierre de partidas abiertas | `1500000298 (US00)` |

---

## Documentación y Trazabilidad en SAP Fiori

El proyecto está respaldado por **dos manuales técnicos de ejecución (176 páginas en total)** elaborados en la UMAD, donde se documenta cada transacción realizada con el usuario `Learn-329`, la resolución de bloqueos logísticos y la auditoría del flujo documental (*Operational & G/L Document Flow*).

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/sap-fiori-sd.png" alt="Flujo operativo y contable en SAP Fiori SD">
    <figcaption>Trazabilidad completa (Operational &amp; G/L Document Flow) del ciclo de ventas en SAP S/4HANA SD.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/sap-fiori-mm.png" alt="Adjudicación de licitación y creación de Orden de Compra en SAP Fiori MM">
    <figcaption>Adjudicación de cotización a proveedor y generación de Orden de Compra en SAP S/4HANA MM.</figcaption>
  </figure>
</div>
