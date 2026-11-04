---
title: "Boids 3D — Simulación Vectorial de Parvadas en Unity"
date: 2026-10-19
weight: 9
slug: "parvada-4-fuerzas-unity"
summary: "Implementación matemática en C# y Unity 3D del algoritmo de comportamiento colectivo emergente, combinando cohesión, separación, alineación y reacción dinámica ante el jugador."
tags:
  - "C#"
  - "Unity 3D"
  - "Algoritmo Boids"
  - "Simulación"
  - "Videojuegos"
categories:
  - "Videojuegos y Simulación"
cover:
  image: "/imagenes/proyectos/flock-4fuerzas-gameplay.jpg"
  alt: "Simulación de parvada de 4 fuerzas en Unity 3D"
  relative: false
---

## Objetivo del Proyecto

En el desarrollo de videojuegos y simulaciones interactivas, animar grupos numerosos de criaturas mediante rutas pregrabadas produce movimientos rígidos y poco naturales. Este proyecto implementa en **C# y Unity 3D** una extensión del algoritmo clásico de *Boids* (Craig Reynolds), logrando que decenas de agentes autónomos vuelen de forma orgánica y reaccionen en tiempo real a la presencia del jugador a partir de reglas vectoriales simples.

- **Video demostrativo**: [Ver simulación en YouTube (`youtu.be/r0ov9oKs4iM`)](https://youtu.be/r0ov9oKs4iM)

![Simulación de Parvada 4 Fuerzas en Unity 3D](/imagenes/proyectos/flock-4fuerzas-gameplay.jpg)

---

## Modelo Vectorial de 4 Fuerzas (`Parvada_4F.cs`)

En cada ciclo de actualización (`Update`), cada agente consulta a sus vecinos cercanos y calcula su vector de aceleración sumando cuatro fuerzas ponderadas, acotadas por límites físicos de aceleración (`maxCombinado = 80`) y velocidad (`maxDireccion = 25`):

$$\vec{F}_{\text{combinada}} = w_c \vec{F}_{\text{cohesión}} + w_s \vec{F}_{\text{separación}} + w_a \vec{F}_{\text{alineación}} + w_j \vec{F}_{\text{jugador}}$$

| Fuerza Vectorial | Peso ($w$) | Radio de Percepción | Comportamiento Generado |
| :--- | :--- | :--- | :--- |
| **1. Cohesión (`Cohesion()`)** | `50` | `20 unidades` | Calcula el centro de masa de los vecinos cercanos e impulsa al agente hacia el interior del grupo. |
| **2. Separación (`Separacion()`)** | `80` | `6 unidades` | Aplica repulsión inversamente proporcional a la distancia para impedir que los agentes colisionen entre sí. |
| **3. Alineación (`Alineacion()`)** | `60` | `10 unidades` | Promedia los vectores de velocidad de los vecinos para unificar la dirección y ritmo de vuelo. |
| **4. Reacción al Jugador (`ReaccionJugador()`)** | `100` | `40 unidades` | Alternable en tiempo real (`bool huir`): permite que la parvada evada al jugador o converja hacia su posición. |

Adicionalmente, el algoritmo mantiene el vuelo dentro de una franja de altitud controlada (`0.5m` a `3.5m`), aplica rebote vectorial suave en los límites del escenario (`tamanoMundo = 48`) y orienta cada entidad en la dirección de su vector de velocidad.

---

## Implementación en C#

```csharp
// Suma ponderada de las cuatro fuerzas vectoriales
combinado = factorCohesion * Cohesion() 
          + factorSeparacion * Separacion() 
          + factorAlineacion * Alineacion() 
          + factorJugador * ReaccionJugador();

// Control de fuerza vertical y límite de aceleración máxima
combinado.y = Mathf.Clamp(combinado.y, -20, 20);
combinado = Vector3.ClampMagnitude(combinado, maxCombinado);

// Integración de velocidad y restricción de magnitud
direccion = direccion + combinado * Time.deltaTime;
direccion.y = Mathf.Clamp(direccion.y, -5, 5);
direccion = Vector3.ClampMagnitude(direccion, maxDireccion);

// Actualización de posición y orientación espacial del agente
posicion = posicion + direccion * Time.deltaTime * vel;
transform.position = posicion;
if (direccion.magnitude > 0)
    transform.LookAt(posicion + direccion);
```
