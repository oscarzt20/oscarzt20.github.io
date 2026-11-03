---
title: "Procesos Empresariales End-to-End en SAP S/4HANA Fiori — Módulos SD y MM"
date: 2025-05-18
weight: 9
slug: "sap-s4hana-fiori-sd-mm"
summary: "Ejecución y documentación de 40 casos prácticos integrados en SAP S/4HANA Fiori (Global Bike v4.2) abarcando los ciclos completos Order-to-Cash (Sales & Distribution — SD) y Procure-to-Pay (Materials Management — MM)."
tags:
  - "SAP S/4HANA"
  - "SAP Fiori"
  - "ERP"
  - "SAP SD"
  - "SAP MM"
  - "Procesos de Negocio"
categories:
  - "Sistemas Empresariales (ERP)"
cover:
  image: "/imagenes/proyectos/sap-fiori-sd.png"
  alt: "Flujo de documentos en SAP S/4HANA Fiori"
  relative: false
---

## Descripción General

Proyecto práctico desarrollado en la **Universidad Madero (UMAD)** para la configuración, ejecución y auditoría de procesos empresariales integrados dentro del ERP **SAP S/4HANA** a través de la interfaz **SAP Fiori** (usuario `Learn-329`), utilizando el caso de estudio **Global Bike v4.2**. El trabajo documenta paso a paso **40 ejercicios transaccionales** que cubren los flujos comerciales, logísticos y financieros de punta a punta, incluyendo su contabilización automática en **FI (Financial Accounting / General Ledger)**.

- **Autor**: Oscar Juárez Ortiz (`Learn-329`)
- **Institución**: Universidad Madero (UMAD), Puebla

---

## 1. Módulo SD (*Sales and Distribution* — Ciclo *Order-to-Cash*)

Ejecución completa de los **16 subprocesos** del ciclo comercial, desde el alta de socios comerciales (*Business Partners*) hasta el cobro y conciliación contable:

| Etapa del Proceso SD | Actividad Ejecutada en SAP Fiori | Documento / ID Generado |
| :--- | :--- | :--- |
| **1. Datos Maestros (BP)** | Creación de Nuevo Cliente (*Create Customer*) | `1003796` |
| **2. Persona de Contacto** | Registro de Contacto y Relación BP (*Create Contact Person & BP Relationship*) | `1003797` |
| **3. Preventa (Inquiry)** | Solicitud de consulta del cliente (*Create Customer Request — Inquiry*) | `10000258` |
| **4. Cotización** | Emisión de oferta formal (*Create Customer Quotation*) | `20000197` |
| **5. Pedido de Venta** | Orden de venta referenciada a cotización (*Sales Order Referencing a Quotation*) | `212` |
| **6. Logística y Entrega** | Verificación de stock, inicio de entrega (*Start Delivery Process*), *Picking* y salida de mercancía (*Post Goods Issue*) | `80000202` (`GI 4900038704`) |
| **7. Facturación (Billing)** | Creación y contabilización de factura de cliente (*Billing Document / Invoice*) | `90000151` (`JE 90000135`) |
| **8. Cobro y Flujo (FI)** | Registro de pago entrante (*Post Receipt of Customer Payment*) y auditoría en *Document Flow* | `1400000672` |

---

## 2. Módulo MM (*Materials Management* — Ciclo *Procure-to-Pay*)

Simulación integral de los **24 subprocesos** del ciclo de aprovisionamiento, evaluación de proveedores, control de inventarios en múltiples entregas y tesorería:

| Etapa del Proceso MM | Actividad Ejecutada en SAP Fiori | Documento / ID Generado |
| :--- | :--- | :--- |
| **1. Maestro de Proveedores** | Alta de proveedor comercial (*Create New Vendor — Mid-West Supply 329*) | `1003893` |
| **2. Maestro de Materiales** | Creación y extensión de material comercial (*Trading Goods*) | `CHLK1329` |
| **3. Solicitud de Compra** | Generación interna de *Purchase Requisition* y gestión de stock | `10000800` |
| **4. Licitación (RFQ)** | Creación de petición de oferta (*Request for Quotation — RFQ*) | `7000000237` (`RFQ1329`) |
| **5. Evaluación de Ofertas** | Registro de 3 cotizaciones de proveedores y evaluación comparativa por precio (*Price Based Bid Evaluation*) | `8000000574` (`Awarded`), `8000000575`, `8000000576` |
| **6. Orden de Compra (PO)** | Emisión de *Purchase Order* referenciando la RFQ ganadora | `4500000278` |
| **7. Recepción de Mercancías (1ª y 2ª)** | Contabilización de entradas de mercancía (*Post Goods Receipt*) e inspección física | `5000000439` y `5000000458` |
| **8. Verificación de Facturas (1ª y 2ª)** | Registro contable de facturas de proveedor (*Supplier Invoices*) | `5105600694` y `5105600695` |
| **9. Pago a Proveedor y Saldos** | Contabilización de pago saliente (*Post Outgoing Payment*) y revisión de saldos/partidas | `1500000298 (2025, US00)` |

---

## Evidencias en SAP Fiori

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/sap-fiori-sd.png" alt="Flujo operativo y contable de documentos en SAP Fiori SD">
    <figcaption>Trazabilidad completa (Operational &amp; G/L Document Flow) desde el Inquiry 10000258 hasta la factura 90000151 y el cobro 1400000672 en SAP S/4HANA SD.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/sap-fiori-mm.png" alt="Adjudicación de cotización y creación de Orden de Compra en SAP Fiori MM">
    <figcaption>Cotización adjudicada (8000000574, usuario Learn-329) y generación de Orden de Compra (Purchase Order) en SAP S/4HANA MM.</figcaption>
  </figure>
</div>
