---
title: "Zombie Traffic — IA con Máquinas de Estados Finitos y Parvadas en Unity 3D"
date: 2026-11-02
weight: 2
slug: "zombie-traffic-unity-ia"
summary: "Videojuego 3D de supervivencia urbana en Unity y C# con inteligencia artificial basada en Máquinas de Estados Finitos (MEF), algoritmo de parvada terrestre (Boids), evasión de obstáculos por raycasting y formación de escolta con potencial de Lennard-Jones."
tags:
  - "Unity 3D"
  - "C#"
  - "Inteligencia Artificial"
  - "Videojuegos"
  - "Máquinas de Estados (FSM)"
  - "Algoritmo Boids"
categories:
  - "Videojuegos y Simulación"
cover:
  image: "/imagenes/proyectos/zombie-traffic-gameplay.jpg"
  alt: "Escena de juego Zombie Traffic en Unity 3D"
  relative: false
---

## Descripción del Proyecto

**Zombie Traffic** es un videojuego 3D de supervivencia urbana desarrollado en **Unity** con **C#** para la asignatura *Videojuegos II* en la Universidad Madero (UMAD). A diferencia de los títulos de acción convencionales basados en armas de fuego, el jugador se encuentra desarmado y debe cruzar una ciudad infestada de hordas de zombies para llevar alimento a su mascota, explorando el entorno para **reclutar perros aliados** que lo escoltan en formación, intimidan a las hordas y ejecutan ataques coordinados.

- **Autor**: Oscar Juárez Ortiz
- **Video demostrativo**: [Ver demostración en YouTube (`youtu.be/cZBsPuGksNY`)](https://youtu.be/cZBsPuGksNY)

![Escena de Zombie Traffic en Unity 3D](/imagenes/proyectos/zombie-traffic-gameplay.jpg)

---

## Arquitectura de Inteligencia Artificial

El núcleo técnico del proyecto reside en dos **Máquinas de Estados Finitos (MEF)** autónomas (`MEF_Zombie.cs` y `MEF_Perro.cs`) que interactúan en tiempo real sobre el plano urbano:

### 1. Máquina de Estados Finitos de Zombies (`MEF_Zombie.cs`)

Cada agente zombie opera bajo 4 estados con retroalimentación visual cromática y transiciones automáticas:

| Estado Actual | Color Visual | Comportamiento Técnico | Condición de Transición |
| :--- | :--- | :--- | :--- |
| **E1: Parvada (`Flock`)** | Verde | Movimiento colectivo en suelo combinando fuerzas de **Cohesión** (`peso 40`, `rango 16m`), **Separación** (`peso 70`, `rango 3.5m`) y **Alineación** (`peso 50`, `rango 8m`), con aceleración `1.25x` para rezagados. | • Si `t > 12s` y `vecinos == 0` → **E2 Patrullar**<br>• Si `VeJugador()` → **E3 Perseguir**<br>• Si `hayPerros` → **E4 Huir** |
| **E2: Patrullaje (`Patrullar`)** | Amarillo | Ejecuta secuencias deterministas de pasos (`struct SMovimiento`: ángulo de rotación, duración y velocidad). | • Si `t > 8s` y `vecinos >= 2` → **E1 Parvada**<br>• Si `VeJugador()` → **E3 Perseguir**<br>• Si `hayPerros` → **E4 Huir** |
| **E3: Persecución (`Perseguir`)** | Rojo | Detección por distancia (`rangoVision = 25m`) y cono de visión (`FOV = 55°`); emite alerta en cadena a zombies vecinos dentro de `14m`. | • Si `distanciaJugador > 40m` → **E1 Parvada**<br>• Si `hayPerros` → **E4 Huir** |
| **E4: Huida (`Huir`)** | Azul | Prioridad máxima de supervivencia. Calcula un **radio de miedo acumulativo** (`radioMiedo = 7m + 3m * perrosCercanos`). | • Si `!hayPerros` y `t > 1.5s` → **E1 Parvada** |

### 2. Máquina de Estados Finitos de Perros Aliados (`MEF_Perro.cs`)

- **E1: Espera (`Esperar`)**: Permanece en posición hasta detectar al jugador dentro del radio de reclutamiento (`VeJugador() == true`).
- **E2: Escolta (`Seguir`)**: Se distribuye en ranuras alrededor del jugador empleando la **fórmula de potencial de Lennard-Jones** entre agentes caninos para mantener una distancia de escolta uniforme sin colapsar ni dispersarse.
- **E3: Ataque Coordinado (`Atacar`)**: Al detectar un `zombieCercano != null`, la jauría toma posiciones frontales, laterales y de cerco hasta neutralizar o alejar la amenaza (`dist > 22m`).

### 3. Navegación y Evasión de Obstáculos con Raycasting

- Implementación de un sistema de rayos (`Physics.Raycast` / `SphereCast`) lanzados a la altura de las rodillas con cálculo de **tangentes laterales** respecto a la normal de impacto para rodear muros, autos y esquinas urbanas sin atascarse.
- Sistema de detección y recuperación anti-atascos (`posRevision`, `tiempoEscape`) y reaparición automática ante caídas fuera del mapa (`VerificarCaida()`).

---

## Diagramas de Estados (MEF)

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/zombie-traffic-mef-1.png" alt="Diagrama de estados MEF Zombie">
    <figcaption>Diagrama de transiciones de la Máquina de Estados Finitos para la horda de Zombies.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/zombie-traffic-mef-2.png" alt="Diagrama de estados MEF Perro">
    <figcaption>Diagrama de transiciones de la Máquina de Estados Finitos para la jauría de Perros Aliados.</figcaption>
  </figure>
</div>

---

## Fragmento Destacado de Código (`MEF_Zombie.cs`)

```csharp
/// Ejecuta el estado actual de la MEF y revisa las transiciones
void Update()
{
    tiempoEnEstado += Time.deltaTime;

    // Huir de los perros tiene prioridad sobre cualquier otro estado
    Vector3 huidaPerros = CalcularHuidaPerros();
    bool hayPerros = huidaPerros.sqrMagnitude > 0;

    if (hayPerros && estado != (int)estadosZombie.Huir)
        CambiarEstado((int)estadosZombie.Huir);

    if (estado == (int)estadosZombie.Parvada)
    {
        MoverEnParvada();

        if (VeJugador() == true)
        {
            AlertarVecinos();
            CambiarEstado((int)estadosZombie.Perseguir);
        }
        else if (tiempoEnEstado > 12 && ObtieneVecinos(rangoCohesion).Count == 0)
            CambiarEstado((int)estadosZombie.Patrullar);
    }
    else if (estado == (int)estadosZombie.Patrullar)
    {
        Patrullar();

        if (VeJugador() == true)
        {
            AlertarVecinos();
            CambiarEstado((int)estadosZombie.Perseguir);
        }
        else if (tiempoEnEstado > 8 && ObtieneVecinos(rangoCohesion).Count >= 2)
            CambiarEstado((int)estadosZombie.Parvada);
    }
}
```

