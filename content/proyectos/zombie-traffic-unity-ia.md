---
title: "Zombie Traffic — Inteligencia Artificial y Comportamiento Colectivo en 3D"
date: 2026-11-02
weight: 3
slug: "zombie-traffic-unity-ia"
summary: "Videojuego 3D de supervivencia en Unity y C# donde las hordas enemigas y la manada de perros aliados toman decisiones autónomas mediante Máquinas de Estados Finitos, algoritmos de parvada y física de partículas."
tags:
  - "C#"
  - "Unity 3D"
  - "Inteligencia Artificial"
  - "Máquinas de Estados (FSM)"
  - "Algoritmo Boids"
  - "Videojuegos"
categories:
  - "Videojuegos y Simulación"
cover:
  image: "/imagenes/proyectos/zombie-traffic-gameplay.jpg"
  alt: "Escena de juego Zombie Traffic en Unity 3D"
  relative: false
---

## El Concepto

**Zombie Traffic** es un videojuego 3D de supervivencia urbana desarrollado individualmente en **Unity 6** y **C#**. En lugar de recurrir al combate tradicional con armas de fuego, el jugador está desarmado y debe cruzar una ciudad infestada de zombies para llevar alimento a su mascota. Su única defensa consiste en explorar las calles para **reclutar perros aliados**, quienes forman un perímetro de escolta dinámico, ahuyentan a las hordas cercanas y atacan de manera coordinada.

- **Video demostrativo**: [Ver funcionamiento en YouTube (`youtu.be/cZBsPuGksNY`)](https://youtu.be/cZBsPuGksNY)

![Escena de Zombie Traffic en Unity 3D](/imagenes/proyectos/zombie-traffic-gameplay.jpg)

---

## Ingeniería de Inteligencia Artificial

El comportamiento emergente del juego se construyó desde cero en C# mediante dos **Máquinas de Estados Finitos (MEF)** independientes que interactúan en tiempo real con el entorno urbano:

### 1. IA de las Hordas Enemigas (`MEF_Zombie.cs`)
Cada zombie evalúa su entorno en cada fotograma y cambia su color para reflejar su estado activo:

| Estado | Indicador | Lógica de Movimiento | Condición de Transición |
| :--- | :--- | :--- | :--- |
| **Parvada (`Flock`)** | Verde | Desplazamiento grupal aplicando fuerzas de **Cohesión**, **Separación** y **Alineación**, con aceleración `1.25x` para individuos rezagados. | • Sin vecinos por `>12s` → **Patrullar**<br>• Detecta al jugador → **Perseguir**<br>• Detecta perros → **Huir** |
| **Patrullaje (`Patrullar`)** | Amarillo | Recorrido autónomo mediante secuencias de vectores (`SMovimiento`: rotación, tiempo y velocidad). | • Encuentra `>=2` vecinos tras `8s` → **Parvada**<br>• Detecta al jugador → **Perseguir**<br>• Detecta perros → **Huir** |
| **Persecución (`Perseguir`)** | Rojo | Detección por distancia (`25m`) y cono de visión (`55°`); emite una **alerta en cadena** a los zombies dentro de un radio de `14m`. | • Jugador se aleja `>40m` → **Parvada**<br>• Detecta perros → **Huir** |
| **Huida (`Huir`)** | Azul | Estado de máxima prioridad. El radio de pánico escala dinámicamente según el tamaño de la jauría (`7m + 3m × perros`). | • Sin perros cercanos por `>1.5s` → **Parvada** |

### 2. IA de la Jauría Aliada (`MEF_Perro.cs`)
- **Reclutamiento y Escolta (`Esperar` → `Seguir`)**: Al detectar al jugador, cada perro se integra a la manada y calcula su posición de escolta empleando el **potencial de Lennard-Jones**, logrando una formación envolvente que evita colisiones entre aliados sin perder cohesión.
- **Ataque Coordinado (`Atacar`)**: Cuando un zombie entra en rango de amenaza, la jauría abandona la formación de escolta y rodea al objetivo por los flancos hasta alejarlo a más de `22m`.

### 3. Navegación Urbana y Evasión con Raycasting
Para evitar el uso de mallas precalculadas estáticas, ambos tipos de agentes lanzan rayos (`Physics.Raycast` y `SphereCast`) y calculan **vectores tangentes** a la normal de impacto para rodear edificios, muros y vehículos de forma fluida, incorporando además detección automática de atascos.

---

## Documentación Técnica y Diagramas de Estados

El proyecto cuenta con una memoria técnica de **73 páginas** que documenta la arquitectura de clases, los diagramas de transición de estados, las fórmulas matemáticas empleadas y el código fuente comentado bajo estándares de Ingeniería de Software en la UMAD.

<div class="portfolio-gallery">
  <figure>
    <img src="/imagenes/proyectos/zombie-traffic-mef-1.png" alt="Diagrama de estados MEF Zombie">
    <figcaption>Máquina de Estados Finitos de la horda de zombies.</figcaption>
  </figure>
  <figure>
    <img src="/imagenes/proyectos/zombie-traffic-mef-2.png" alt="Diagrama de estados MEF Perro">
    <figcaption>Máquina de Estados Finitos de la jauría de perros aliados.</figcaption>
  </figure>
</div>

---

## Fragmento de Código (`MEF_Zombie.cs`)

```csharp
/// Evalúa el estado actual del agente y ejecuta las transiciones prioritarias
void Update()
{
    tiempoEnEstado += Time.deltaTime;

    // La supervivencia ante la jauría de perros tiene prioridad sobre cualquier estado
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
