---
Date: 2026-01-14
Time: 02:41
tags:
- enciclopedia
- Programación
slug: programacion-1-introduccion-y-algoritmos
title: Programación 1 - Introducción y Algoritmos
---

---

Para un ingeniero de software, la programación es una de las principales herramientas que tenemos a nuestra disposición para la resolución de problemas. Al programar, le transmitimos nuestro razonamiento a la computadora, indicando qué acciones realizar y cómo ejecutarlas, paso a paso.

Detrás de cualquier programa existe un razonamiento lógico, diseñado para solucionar una necesidad específica; el código es simplemente el medio para alcanzar esa solución.

## I. ¿Qué es un algoritmo?

Antes de escribir código, necesitamos entender la lógica que hay detrás, y para eso los desarrolladores crean *algoritmos*.

> Un algoritmo es una secuencia ordenada de pasos que resuelven un problema o llevan a cabo una tarea específica.

En la vida diaria, operamos bajo algoritmos constantemente, como el conducir, jugar un deporte o preparar café. Sin embargo, nosotros contamos con la capacidad de inferir: podemos llenar vacíos de información usando el contexto.

En programación, esa ventaja desaparece, por tanto, los pasos a seguir deben ser mucho más precisos y sin ambigüedades, porque la computadora solo entiende instrucciones exactas.

### 1.1 Características de los algoritmos

Todo algoritmo, y por extensión todo programa, funciona bajo un esquema universal que incluye:

1. **Entrada**: Son los datos necesarios para operar, los cuales recibe del exterior (ya sea del usuario, de un archivo o de otro sistema).
2. **Proceso**: Es el conjunto de operaciones lógicas y matemáticas que transforman la entrada. Aquí es donde se aplica nuestra lógica como programadores.
3. **Salida**: Es el resultado final obtenido tras el procesamiento. Es la respuesta que el sistema entrega al usuario o a otro programa.

Podemos ver a este proceso como el encargado de transformar los datos en información útil.

#### Propiedades de un buen algoritmo

Un algoritmo válido debe cumplir con las siguientes propiedades:

- **Inicio y Final/es**: El algoritmo debe tener un alcance definido. Requiere un estado inicial (Entrada) y debe producir un resultado observable o un cambio de estado final (Salida).
- **Finito**: Todo algoritmo debe resolver el problema en un número contable de pasos. Si este no contiene una condición de término clara, genera un "bucle infinito", consumiendo recursos del sistema indefinidamente hasta colapsarlo.
- **Preciso**: Cada instrucción debe estar claramente definida.
- **Eficaz**: Buscar alcanzar la solución utilizando la menor cantidad de recursos posible.

## II. ¿Cómo representar un algoritmo?

Una vez definido el problema o tarea a realizar, pasamos a modelar la solución, y para ello utilizamos *lenguajes algorítmicos*; estas herramientas nos permiten planificar la lógica del programa, facilitar su comprensión y detectar errores antes de invertir tiempo en la programación.

Existen dos formas principales de representar algoritmos: la visual (Diagramas de Flujo) y la narrativa (Pseudocódigo).

### 2.1 Diagrama de flujo

Es una representación gráfica de un algoritmo. Utiliza distintos símbolos estandarizados (Norma ANSI/ISO), conectados por flechas para mostrar la secuencia lógica de los pasos.

Es ideal para documentar procesos y entender a simple vista el flujo que tendrá un programa.

#### Simbología básica

- **Óvalo / Elipse**: Indica el inicio o fin del algoritmo.
- **Paralelogramo**: Representa la entrada (lectura de datos) o salida (impresión de resultados) de información.
- **Rectángulo**: Expresa un proceso interno (cálculos, asignaciones).
- **Rombo**: Representa una decisión lógica. El flujo se divide en caminos de "Sí" o "No" dependiendo de una condición.
- **Flechas**: Indican el orden de la ejecución.

**Ejemplo**:

Imaginemos el diagrama para determinar si un número es par o impar.

El flujo recibiría un número (Entrada), pasaría por un Rombo de decisión (¿Al dividir el número entre 2 el residuo es 0?) y saldría por dos caminos distintos hacia el final.

![Conceptos Generales de Programación_05-06-2025-1.png](/imagenes/Conceptos%20Generales%20de%20Programaci%C3%B3n_05-06-2025-1.webp)

### 2.2 Pseudocódigo

El pseudocódigo es una descripción del algoritmo que utiliza un lenguaje híbrido entre nuestro idioma natural y las palabras clave de programación.

Su objetivo es centrarse en la lógica pura sin preocuparse por la sintaxis estricta de un lenguaje de programación.

**Ejemplo**:

Usaremos el mismo ejemplo del número par o impar.

```
1. Inicio
2. Escribir "Ingrese un número"
3. Leer numero
4. SI (numero % 2 == 0) ENTONCES
    4.1. Escribir "Es par"
5. SINO
    5.1. Escribir "Es impar"
6. Fin
```

## III. Metodología general para solucionar algoritmos

Cuando enfrentamos un problema, podemos resolverlo siguiendo estos pasos:

1. **Definir el problema**: Entender claramente qué se nos pide. El objetivo debe ser preciso.
2. **Analizar el problema**: Debemos adoptar la perspectiva del sistema y desglosar la tarea. Esto implica identificar:
	- **Entradas**: ¿Qué datos necesitamos recibir?
	- **Salidas**: ¿Qué información debemos producir?
	- **Proceso**: ¿Qué fórmulas o lógica transforman la entrada en salida?
3. **Diseñar el algoritmo**:
	- Establecer un punto de inicio y fin.
	- Ir de lo general a lo particular.
	- Asegurar que sea finito en tamaño y tiempo de ejecución.
	- Realizar la prueba de escritorio (simular la ejecución del algoritmo con datos de prueba para comprobar que funciona).

> Pueden existir múltiples caminos para resolver un mismo algoritmo.

**Ejemplo**:

Calcular el área de un triángulo. Aplicando la metodología paso a paso:

1. **Definición del problema**: Hallar el área de un triángulo a partir de su base y su altura.
2. **Análisis**:
	- **Entrada**: base, altura.
	- **Proceso**: área = base × altura ÷ 2.
	- **Salida**: área del triángulo.
3. **Diseño del algoritmo (utilizando pseudocódigo)**:
	1. Inicio
	2. Leer base y altura
	3. Calcular area = (base * altura) / 2
	4. Mostrar area
	5. Fin

---

## Ejercicios sugeridos

Resuelve los siguientes problemas aplicando la metodología general para la solución de algoritmos, haciendo uso del pseudocódigo o diagramas de flujo.

1. Diseña un algoritmo que reciba dos números diferentes y muestre cuál de los dos es el mayor.
2. Diseña un algoritmo para un sistema de votación:
	- Solicitar la edad del usuario.
	- Si la edad es mayor o igual a 18, mostrar: "Puede votar". 
	- Si es menor a 18, mostrar: "Aún no puede votar".
3. Diseña un algoritmo para calcular la edad actual de una persona mediante su fecha de nacimiento.
4. Diseña un algoritmo que simule la entrega de efectivo de un cajero:
	- El usuario pide una cantidad (ej. $1,300) y el cajero debe entregarla utilizando la menor cantidad de billetes posible.
	- Billetes disponibles: $500, $200, $100.

---

## / Más información

- 

---