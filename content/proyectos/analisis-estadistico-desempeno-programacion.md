---
title: "Análisis Estadístico del Desempeño y Factores de Error en la Programación"
date: 2024-12-03
weight: 10
slug: "analisis-estadistico-desempeno-programacion"
summary: "Investigación cuantitativa (n = 30 estudiantes de Ingeniería de Software en la UMAD) sobre la incidencia semanal de errores de código mediante pruebas t-Student, Z de proporciones, prueba t de Welch, regresión lineal múltiple y ANOVA."
tags:
  - "Estadística"
  - "Ciencia de Datos"
  - "Calidad de Software"
  - "Regresión Lineal"
  - "Pruebas de Hipótesis"
categories:
  - "Ciencia de Datos y Estadística"
cover:
  image: "/imagenes/proyectos/estadistica-desempeno.png"
  alt: "Resumen estadístico del estudio de desempeño en programación en la UMAD"
  relative: false
---

## Planteamiento e Investigación

En las etapas formativas de la Ingeniería de Software, comprender las causas raíz que originan defectos en el código (*errores de sintaxis, errores lógicos, errores en tiempo de ejecución y errores de omisión*) resulta esencial para elevar la calidad del software. Este estudio estadístico tuvo como objetivo cuantificar la tasa promedio de errores semanales en una muestra de **$n = 30$ estudiantes de Ingeniería de Software de la Universidad Madero (UMAD)** e identificar qué variables influyen significativamente en la precisión del programador.

- **Autores**: Oscar Juárez Ortiz, Pedro Emiliano Romero Osorio, Emmanuel Baltazar López.
- **Asignatura**: Estadística — Universidad Madero (UMAD).
- **Asesora**: Mtra. Ma. del Socorro Barrientos Camarena.

![Resumen Estadístico de Desempeño en Programación — UMAD](/imagenes/proyectos/estadistica-desempeno.png)

---

## Diseño Metodológico y Resultados de los 7 Modelos Estadísticos

A partir del levantamiento muestral ($n = 30$) y su procesamiento estadístico, se formularon y contrastaron **7 modelos de inferencia y regresión** con nivel de significancia $\alpha = 0.05$:

| # | Modelo Estadístico | Hipótesis Contrastadas ($H_0$ vs. $H_a$) | Estadísticos Obtenidos ($n = 30$) | Decisión Estadística |
| :--- | :--- | :--- | :--- | :--- |
| **1** | **Prueba $t$ para Media Muestral** | $H_0: \mu = 5$ vs. $H_a: \mu \neq 5$ errores/semana | $\bar{x} = 44.23$, $s = 95.98$<br>$t = 2.2390 > t_{\text{crít}} = 2.0452$ | **Se rechaza $H_0$** (el promedio difiere de 5 errores/semana). |
| **2** | **Prueba $Z$ de Proporción Poblacional** | $H_0: p_0 = 0.50$ vs. $H_a: p > 0.50$ ($>5$ errores/semana) | $x = 23/30$ ($\hat{p} = 76.67\%$)<br>$Z = 2.9216 > Z_{\text{crít}} = 1.6449$ | **Se rechaza $H_0$** (la mayoría supera 5 errores/semana). |
| **3** | **Inferencia por Nivel de Experiencia** | $H_0$: Independiente de experiencia vs. $H_a$: Depende de la experiencia | 5 niveles ($1\text{ a }5$), $gl = 29$<br>$s_d = 2.6458$ | La experiencia reduce la tasa de errores básicos y eleva la complejidad abordada. |
| **4** | **Prueba $t$ de Welch por Lenguaje** (`JS`, `Python`, `C#`, `Java`, `Ruby`) | $H_0$: El lenguaje no influye vs. $H_a$: El lenguaje influye significativamente | $\bar{x}_{\text{No}} = 1.75$ ($s^2 = 1.84$) vs. $\bar{x}_{\text{Sí}} = 2.26$ ($s^2 = 0.93$)<br>$t = -1.1605$, $p = 0.2619$ ($gl = 17$) | **No se rechaza $H_0$** (el lenguaje por sí solo no determina la tasa de error). |
| **5** | **Prueba $Z$ de Proporción ($<5$ errores)** | $H_0: p = 0.70$ vs. $H_a: p < 0.70$ | $\hat{p} = 0.40$, $q = 0.60$<br>$Z = -3.5857$, $p\text{-valor} = 0.00017$ | **Se rechaza $H_0$** ($p < 0.05$: menos del $70\%$ comete $<5$ errores). |
| **6** | **Regresión Lineal Simple** ($X_1$: Horas diarias vs. $Y$: Errores) | $H_0: \beta_1 = 0$ vs. $H_a: \beta_1 \neq 0$ | $R = 0.1597$, $R^2 = 0.0255$<br>$\hat{Y} = 22.1713 - 1.3790 X_1$ | Pendiente negativa ($\beta_1 = -1.38$): mayor práctica diaria reduce errores. |
| **7** | **Regresión Lineal Múltiple y ANOVA** ($X_1$: Horas, $X_2$: Exp., $X_3$: Complejidad) | $H_0: \beta_1 = \beta_2 = \beta_3 = 0$ vs. $H_a$: Al menos una variable influye | $R = 0.2627$, $R^2 = 0.0690$<br>$F = 0.6425 > F_{\text{crít}} = 0.5946$ | **Se rechaza $H_0$** (efecto conjunto significativo sobre errores detectados). |

### Ecuación del Modelo de Regresión Lineal Múltiple

$$\hat{Y} = -29.4963 - 2.1106 X_1 + 8.1430 X_2 + 14.3032 X_3$$

Donde:
- $X_1$: Horas promedio dedicadas diariamente a programar ($\beta_1 = -2.1106$, reduce la incidencia de errores).
- $X_2$: Nivel de experiencia acumulada en programación ($\beta_2 = +8.1430$, mayor capacidad para identificar y depurar defectos).
- $X_3$: Nivel de complejidad de los proyectos abordados ($\beta_3 = +14.3032$, proyectos más complejos exponen mayor volumen de defectos por semana; para $X_1 = 5$, $X_2 = 5$, $X_3 = 3$, el pronóstico es $\hat{Y} = 43.58$ errores identificados y corregidos).

---

## Hallazgos Clave y Conclusiones de Ingeniería

1. **Impacto de la Práctica Diaria**: Los estudiantes que dedican mayor número de horas diarias a programar alcanzan niveles superiores de dominio técnico y abordan proyectos de mayor complejidad arquitectónica, reduciendo la incidencia de errores de sintaxis y omisión.
2. **Correlación entre Experiencia y Complejidad**: A medida que aumenta la experiencia acumulada, el tipo de defecto migra de errores sintácticos básicos (mitigados en tiempo real por **IDEs** como VS Code o IntelliJ IDEA) hacia retos de diseño lógico en sistemas con múltiples interdependencias.
3. **Prácticas de Mitigación Recomendadas**: La adopción sistemática de **revisiones de código (*code reviews*)**, **pruebas unitarias**, **modularidad** y **estándares de código limpio (Clean Code)** demostró ser el factor determinante para contener la tasa de defectos conforme escala la complejidad de los proyectos en la carrera.
