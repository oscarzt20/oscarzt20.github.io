---
title: "Simulación de Parvada 3D (Boids de 4 Fuerzas) en Unity"
date: 2026-10-19
weight: 3
slug: "parvada-4-fuerzas-unity"
summary: "Implementación en C# y Unity 3D del algoritmo de comportamiento colectivo emergente (Flocking / Boids) integrando cuatro fuerzas vectoriales: Cohesión, Separación, Alineación y Reacción Dinámica al Jugador."
tags:
  - "Unity 3D"
  - "C#"
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

## Descripción General

Proyecto desarrollado en **Unity 3D** y **C#** (`Parvada_4F.cs`) que modela el comportamiento colectivo emergente de parvadas (*Flocking / Boids*) en un espacio tridimensional acotado, extendiendo el modelo clásico de Craig Reynolds con una **cuarta fuerza vectorial de interacción directa con el jugador** (atracción/persecución o repulsión/huida en tiempo real).

- **Autor**: Oscar Juárez Ortiz
- **Asignatura**: Videojuegos II — Universidad Madero (UMAD)
- **Video demostrativo**: [Ver simulación en YouTube (`youtu.be/r0ov9oKs4iM`)](https://youtu.be/r0ov9oKs4iM)

![Simulación de Parvada 4 Fuerzas en Unity 3D](/imagenes/proyectos/flock-4fuerzas-gameplay.jpg)

---

## Modelo Matemático y Vectorial (`Parvada_4F.cs`)

En cada fotograma (`Update`), cada agente calcula su aceleración combinada como la suma ponderada de cuatro vectores normalizados, sujeta a límites físicos de aceleración (`maxCombinado = 80`) y velocidad máxima (`maxDireccion = 25`):

$$\vec{F}_{\text{combinada}} = w_c \vec{F}_{\text{cohesión}} + w_s \vec{F}_{\text{separación}} + w_a \vec{F}_{\text{alineación}} + w_j \vec{F}_{\text{jugador}}$$

| Fuerza Vectorial | Peso ($w$) | Rango de Detección | Función en la Simulación |
| :--- | :--- | :--- | :--- |
| **1. Cohesión (`Cohesion()`)** | `50` | `20 unidades` | Calcula el centro de masa promedio de los vecinos cercanos y dirige al agente hacia el grupo. |
| **2. Separación (`Separacion()`)** | `80` | `6 unidades` | Genera repulsión inversamente proporcional a la distancia ($\hat{r}/\|\vec{r}\|$) para evitar colisiones entre agentes. |
| **3. Alineación (`Alineacion()`)** | `60` | `10 unidades` | Promedia y normaliza los vectores de velocidad $\vec{v}$ de los vecinos para sincronizar el rumbo de vuelo. |
| **4. Reacción al Jugador (`ReaccionJugador()`)** | `100` | `40 unidades` | Conmutable mediante `bool huir`: evade al jugador ($\vec{p}_{\text{agente}} - \vec{p}_{\text{jugador}}$) o converge hacia él ($\vec{p}_{\text{jugador}} - \vec{p}_{\text{agente}}$). |

Adicionalmente, el sistema restringe el vuelo dentro de una franja de altitud segura (`alturaMinY = 0.5f` a `alturaMaxY = 3.5f`) y aplica reflexión vectorial en las fronteras del mundo (`tamanoMundo = 48`) orientando suavemente cada entidad con `transform.LookAt(posicion + direccion)`.

---

## Implementación en C#

```csharp
// Combinamos las cuatro fuerzas
combinado = factorCohesion * Cohesion() 
          + factorSeparacion * Separacion() 
          + factorAlineacion * Alineacion() 
          + factorJugador * ReaccionJugador();

// Moderamos la fuerza vertical y limitamos la fuerza total
combinado.y = Mathf.Clamp(combinado.y, -20, 20);
combinado = Vector3.ClampMagnitude(combinado, maxCombinado);

// Actualizamos la direccion y velocidad
direccion = direccion + combinado * Time.deltaTime;
direccion.y = Mathf.Clamp(direccion.y, -5, 5);
direccion = Vector3.ClampMagnitude(direccion, maxDireccion);

// Movemos y orientamos al agente
posicion = posicion + direccion * Time.deltaTime * vel;
transform.position = posicion;
if (direccion.magnitude > 0)
    transform.LookAt(posicion + direccion);
```

