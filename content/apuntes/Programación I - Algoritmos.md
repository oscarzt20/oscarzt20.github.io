---
Title: Programación I - Algoritmos
Date: 2025-08-08
Hora: 01:40
tags: ['enciclopedia', 'aprenderProgramacion']
---

---

La programación es el proceso de escribir instrucciones para que una computadora realice tareas específicas. Es decir, cuando programamos le decimos a la computadora qué hacer y cómo hacerlo, paso a paso.

Antes de escribir código, necesitamos entender la lógica detrás de los programas y para eso los desarrolladores crean algoritmos. Un algoritmo es una secuencia ordenada de pasos que resuelven un problema o llevan a cabo una tarea.

En la vida diaria usamos algoritmos sin darnos cuenta, como el seguir una receta de cocina, consultar un mapa o entender las instrucciones de un juego. La diferencia es que en programación, esos pasos deben ser mucho más precisos y sin ambigüedades, porque la computadora solo entiende instrucciones claras y exactas.

## I. Características de los algoritmos

Un buen algoritmo debe cumplir con ciertas propiedades:

- **Finito**: Un algoritmo debe terminar después de un número determinado de pasos, para evitar los bucles sin fin.
- **Preciso**: Cada instrucción debe estar claramente definida.
- **Con inicio y final/es**: Debe tener un punto de inicio y puede contener más de un final posible.
- **Eficaz en la solución del problema**: El algoritmo debe resolver el problema de manera correcta y eficiente, evitando pasos innecesarios.

### 1.1 Tipos de algoritmos

- **Cualitativos**: Emplean palabras. Ejemplo: Una receta de cocina.
- **Cuantitativos**: Utilizan cálculos numéricos. Ejemplo: resolver una ecuación de 2° grado.

## II. Lenguajes algorítmicos

Un lenguaje algorítmico es un conjunto de símbolos y reglas que permiten explicar un algoritmo. Se usan para planificar la lógica de un programa, facilitar su comprensión y ayudar a detectar errores.

### 2.1 Lenguajes algorítmicos gráficos

**Diagrama de flujo**

Es una representación gráfica de un algoritmo o proceso, utilizando distintos símbolos conectados por flechas que indican el flujo de ejecución.

Los símbolos usados son:

- **Círculo**: Indica el inicio y el fin del algoritmo.
- **Rectángulo**: Expresa una acción o proceso a realizar.
- **Rombo**: Representa una decisión (condición lógica).
- **Flechas**: Indican el flujo del proceso.

**Ejemplo**:

Diagrama de flujo de un algoritmo que determina si un número es par o impar.

![Conceptos Generales de Programación_05-06-2025-1.png](/imagenes/Conceptos%20Generales%20de%20Programaci%C3%B3n_05-06-2025-1.png)

### 2.2 Lenguajes algorítmicos no gráficos

**Pseudocódigo**

Consiste en escribir el algoritmo utilizando un lenguaje intermedio entre el lenguaje natural y un lenguaje de programación.

**Ejemplo**:

Redacción de pseudocódigo para anotar un gol en un partido de fútbol.

```
1. Inicio.
2. Entrar a la cancha de fútbol con el equipo adecuado.
3. Esperar la indicación del inicio del partido.
4. Localizar el balón.
5. Correr hacia el balón.
6. Ganar control del balón.
7. ¿Se tiene posesión del balón?
	1. Sí, continuar al paso 8.
	2. No, regresar al paso 4.
8. Localizar la portería deseada.
9. Patear la pelota levemente y repetidamente en dirección a la portería.
10. Evitar intentos del equipo contrario de arrebatar el control del balón.
11. ¿Se mantuvo el control del balón?
	1. Sí, continuar al paso 12.
	2. No, regresar al paso 4.
12. Una vez frente a la portería, a un mínimo de 5 metros de distancia, cambiar rápidamente a posición de tiro.
13. Identificar un espacio en la portería donde sea menos accesible para el portero.
14. Patear la pelota con suficiente fuerza en dirección hacia dentro de la portería, usando el empeine del pie hábil.
15. ¿Se logró anotar el gol?
	1. Sí, festejar con el equipo propio.
	2. No, regresar al paso 4.
16. Fin.
```

## III. Metodología general para solucionar algoritmos

Cuando enfrentamos un problema, podemos resolverlo siguiendo estos pasos:

1. **Definir el problema**: Debe ser claro y preciso.
2. **Analizar el problema**: Colocarse en el lugar del ordenador y buscar lo que se necesita para cumplir la tarea. Incluye:
	- Datos que necesitamos (entrada).
	- Información a producir (salida).
	- Métodos y fórmulas para analizar y procesar los datos.
3. **Diseñar el algoritmo**:
	- Debe tener un punto particular de inicio.
	- No debe ser ambiguo.
	- Debe ir de lo general a lo particular.
	- Debe ser finito en tamaño y tiempo de ejecución.
	- Debe hacerse la prueba de escritorio (simular el algoritmo con datos de ejemplo para comprobar que funciona).

**Ejemplo**:

Calcular el área de un triángulo.

1. **Definición del problema**: Hallar el área del triángulo dados base y altura.
2. **Análisis**:
	- Entrada: base, altura.
	- Proceso: área = (base × altura) ÷ 2.
	- Salida: área del triángulo.
3. **Diseño del algoritmo (utilizando pseudocódigo)**:
	1. Inicio
	2. Leer base y altura
	3. Calcular area = (base * altura) / 2
	4. Mostrar area
	5. Fin

---

## Ejercicios

1. Diseña un algoritmo que calcule el promedio de 3 calificaciones. Escríbelo usando pseudocódigo.
2. Realiza un diagrama de flujo que represente el proceso de decidir si una persona puede votar (edad ≥ 18).

---

## / Más Información

- [Programación I - Algoritmos](/apuntes/programación-i---algoritmos/)
- [Programación II - Conceptos Básicos](/apuntes/programación-ii---conceptos-básicos/)
- [Programación III - Introducción a la Programación Orientada a Objetos](/apuntes/programación-iii---introducción-a-la-programación-orientada-a-objetos/)
- [Programación IV - Conceptos Básicos de POO](/apuntes/programación-iv---conceptos-básicos-de-poo/)
- [Programación V - Mecanismos de POO](/apuntes/programación-v---mecanismos-de-poo/)
- [Programación VI - Estructuras de Datos Abstractos](/apuntes/programación-vi---estructuras-de-datos-abstractos/)
- [Programación VII - Manejo de Datos](/apuntes/programación-vii---manejo-de-datos/)
- [Programación VIII - POO y la Programación Orientada a Eventos](/apuntes/programación-viii---poo-y-la-programación-orientada-a-eventos/)
- [Programación IX - Patrones de Diseño](/apuntes/programación-ix---patrones-de-diseño/)
- [Programación - Guías Documentación y Buenas Prácticas](/apuntes/programación---guías-documentación-y-buenas-prácticas/)

---