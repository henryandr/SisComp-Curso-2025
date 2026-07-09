# Unidad 1 · Arquitectura del computador y programación en ensamblador

## Archivo 2: Programación en ensamblador e entrada/salida

### Propósito
Profundizar en el lenguaje ensamblador de Hack para modelar control de flujo, operaciones con la ALU y acceso a memoria mapeada para interacción básica.

### Sesiones cubiertas
- Sesión 3. Instrucciones, ALU, registros, saltos y control de flujo en Hack.
- Sesión 4. Memoria mapeada, pantalla, teclado y programas interactivos simples.

### Resultados de aprendizaje
- Interpretar instrucciones A y C en Hack.
- Relacionar la ALU con operaciones aritméticas, lógicas y comparaciones.
- Implementar ciclos y condicionales con saltos.
- Usar `SCREEN` y `KBD` para leer y escribir en periféricos.

## Sesión 3. Instrucciones y control de flujo

### Objetivo
Construir programas en ensamblador que usen registros, ALU y saltos para resolver problemas básicos.

### Temas centrales
- Formato y función de las instrucciones A y C.
- Registros A y D.
- Destino, cómputo y salto.
- Etiquetas y organización del flujo.
- Bucles y condiciones en lenguaje ensamblador.

### Actividades sugeridas
- Analizar programas que comparan valores y almacenan resultados.
- Reescribir un cálculo aritmético usando distintas secuencias de instrucciones.
- Identificar dónde actúa la ALU en un programa dado.
- Simular un ciclo y explicar la condición de salida.

### Evidencias
- Programa resuelto con condición y salto.
- Explicación del papel de cada instrucción en el flujo completo.

## Sesión 4. Memoria mapeada y programas interactivos

### Objetivo
Entender cómo la pantalla y el teclado se representan en memoria y cómo esa representación permite construir programas interactivos simples.

### Temas centrales
- Memoria mapeada para entrada/salida.
- Dirección base de `SCREEN` y `KBD`.
- Escritura de palabras de pantalla.
- Lectura del teclado desde memoria.
- Interacción básica mediante un bucle de sondeo.

### Actividades sugeridas
- Dibujar un punto o una línea en pantalla escribiendo en `SCREEN`.
- Detectar pulsaciones de tecla y modificar el estado del programa.
- Explicar por qué la entrada/salida puede verse como memoria.
- Comparar una versión no interactiva y una interactiva del mismo programa.

### Evidencias
- Programa interactivo simple en Hack.
- Registro de observaciones sobre pantalla, teclado y control del bucle principal.

## Recursos sugeridos
- Simulador CPU de Hack.
- Documentación de memoria mapeada del computador Hack.
