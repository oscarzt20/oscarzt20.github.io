---
title: "Calidad en el Código — Estudio Estadístico sobre Factores de Error en Programación"
date: 2024-12-03
weight: 10
slug: "analisis-estadistico-desempeno-programacion"
summary: "Investigación cuantitativa sobre los factores que influyen en la aparición y detección de bugs en estudiantes de Ingeniería de Software, aplicando pruebas de hipótesis, regresión lineal múltiple y ANOVA."
tags:
  - "Estadística"
  - "Calidad de Software"
  - "Regresión Lineal"
  - "Pruebas de Hipótesis"
  - "Ciencia de Datos"
categories:
  - "Ciencia de Datos y Estadística"
cover:
  image: "/imagenes/proyectos/estadistica-desempeno.png"
  alt: "Resumen estadístico del estudio de desempeño en programación en la UMAD"
  relative: false
---

## El Objetivo

Mejorar la calidad del software requiere entender con datos reales qué factores provocan o reducen la introducción de defectos (*bugs* de sintaxis, lógica, ejecución y omisión) durante el desarrollo. En este estudio se encuestó y analizó una muestra de **$n = 30$ estudiantes de Ingeniería de Software de la UMAD** para evaluar estadísticamente cómo influyen las horas de práctica diaria, el nivel de experiencia, el lenguaje utilizado y la complejidad de los proyectos en la tasa semanal de errores.

![Resumen Estadístico de Desempeño en Programación — UMAD](/imagenes/proyectos/estadistica-desempeno.png)

---

## Modelos de Inferencia Estadística Evaluados

Se plantearon y contrastaron **7 modelos estadísticos** con un nivel de significancia $\alpha = 0.05$, procesando los datos muestrales y residuales en hojas de cálculo estructuradas:

| # | Prueba Estadística | Hipótesis Evaluada | Resultado Muestral ($n = 30$) | Conclusión |
| :--- | :--- | :--- | :--- | :--- |
| **1** | **$t$-Student (Media Muestral)** | ¿El promedio semanal es igual a 5 errores? ($H_0: \mu = 5$) | $\bar{x} = 44.23$, $s = 95.98$<br>$t = 2.2390 > t_{\text{crít}} = 2.0452$ | **Se rechaza $H_0$**: el volumen real de errores identificados supera ampliamente la referencia de 5 por semana. |
| **2** | **Prueba $Z$ de Proporción** | ¿Más del 50% supera los 5 errores por semana? ($H_a: p > 0.50$) | $23/30$ alumnos ($\hat{p} = 76.67\%$)<br>$Z = 2.9216 > Z_{\text{crít}} = 1.6449$ | **Se rechaza $H_0$**: existe evidencia significativa de que la mayoría supera dicho umbral durante sus prácticas. |
| **3** | **Diferencia por Experiencia** | ¿La tasa de error depende de los semestres de experiencia? | 5 niveles evaluados ($gl = 29$, $s_d = 2.6458$) | Conforme avanza el estudiante, disminuyen los errores básicos y aumentan los retos de lógica. |
| **4** | **Prueba $t$ de Welch por Lenguaje** (`C#`, `Java`, `Python`, `JS`, `Ruby`) | ¿El lenguaje de programación por sí solo determina la cantidad de errores? | $\bar{x}_{\text{No}} = 1.75$ vs. $\bar{x}_{\text{Sí}} = 2.26$<br>$t = -1.1605$, $p = 0.2619$ ($gl = 17$) | **No se rechaza $H_0$**: la tasa de defectos no depende del lenguaje elegido, sino de los hábitos del programador. |
| **5** | **Prueba $Z$ de Cola Inferior** | ¿Al menos el 70% comete menos de 5 errores semanales? ($H_0: p = 0.70$) | $\hat{p} = 0.40$, $Z = -3.5857$<br>$p\text{-valor} = 0.00017 < 0.05$ | **Se rechaza $H_0$**: solo el 40% reporta menos de 5 errores semanales. |
| **6** | **Regresión Lineal Simple** | Relación entre horas de práctica diaria ($X_1$) y errores ($Y$) | $\hat{Y} = 22.1713 - 1.3790 X_1$<br>($R = 0.1597$) | La pendiente negativa ($\beta_1 = -1.38$) confirma que dedicar más horas diarias reduce la incidencia de fallos. |
| **7** | **Regresión Múltiple y ANOVA** | Efecto conjunto de Horas ($X_1$), Experiencia ($X_2$) y Complejidad ($X_3$) | $F = 0.6425 > F_{\text{crít}} = 0.5946$<br>($R = 0.2627$) | **Se rechaza $H_0$**: la combinación de las tres variables explica significativamente la detección de errores. |

### Modelo de Regresión Lineal Múltiple

$$\hat{Y} = -29.4963 - 2.1106 X_1 + 8.1430 X_2 + 14.3032 X_3$$

El modelo multifactorial revela una dinámica clave en la formación de un Ingeniero de Software:
- **Las horas de práctica diaria ($X_1$, $\beta_1 = -2.11$)** reducen directamente la generación de defectos.
- **La experiencia ($X_2$, $\beta_2 = +8.14$) y la complejidad del proyecto ($X_3$, $\beta_3 = +14.30$)** incrementan la capacidad del desarrollador para abordar sistemas más grandes y **detectar y corregir** un mayor número de defectos durante sus revisiones semanales.

---

## Conclusiones Aplicadas a la Ingeniería de Software

1. **El lenguaje no sustituye a las buenas prácticas**: La prueba de Welch demostró que cambiar entre C#, Java, Python o JavaScript no reduce por sí mismo los errores; la diferencia radica en la aplicación de **código limpio (*Clean Code*)**, modularidad y estándares de nomenclatura.
2. **Transición de errores sintácticos a lógicos**: Mientras los entornos de desarrollo modernos (IDEs) corrigen en tiempo real los errores de sintaxis en etapas tempranas, los proyectos de semestres avanzados exigen **pruebas unitarias** y **revisiones de código (*code reviews*)** para contener los defectos de diseño lógico.
