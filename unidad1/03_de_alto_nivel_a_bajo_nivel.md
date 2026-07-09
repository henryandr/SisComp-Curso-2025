# Unidad 1 · Arquitectura del computador y programación en ensamblador

## Archivo 3: De alto nivel a bajo nivel

### Propósito
Usar la traducción entre C++ y ensamblador como puente conceptual entre estructuras de alto nivel y su representación en memoria e instrucciones.

### Sesiones cubiertas
- Sesión 5. Traducción de ciclos y condicionales entre C++ y ensamblador.
- Sesión 6. Punteros, arreglos y relación entre direcciones de memoria y código de alto nivel.
- Sesión 7. Evaluación parcial teórica.

### Resultados de aprendizaje
- Traducir estructuras de control sencillas entre C++ y Hack.
- Explicar el significado operacional de punteros y arreglos.
- Relacionar direcciones de memoria con variables y acceso indirecto.
- Integrar arquitectura, ensamblador y abstracciones de alto nivel.

## Sesión 5. Traducción de ciclos y condicionales

### Objetivo
Reconocer cómo las construcciones de control de C++ se implementan mediante comparaciones, saltos y etiquetas en ensamblador.

### Temas centrales
- `if`, `while` y `for` en C++.
- Comparaciones y saltos condicionales.
- Variables de control y acumuladores.
- Equivalencias entre forma legible y forma ejecutable.

### Actividades sugeridas
- Traducir un `while` y un `for` equivalentes a Hack.
- Comparar distintas versiones ensamblador del mismo algoritmo.
- Señalar dónde inicia, se verifica y se actualiza un ciclo.

### Evidencias
- Ejercicio de traducción comentado.
- Conclusiones sobre similitudes y diferencias entre ambos niveles.

## Sesión 6. Punteros, arreglos y direcciones

### Objetivo
Relacionar el acceso indirecto y los arreglos en C++ con direcciones explícitas y operaciones de memoria en Hack.

### Temas centrales
- Dirección de memoria como dato.
- Lectura y escritura indirecta.
- Acceso secuencial a arreglos.
- Desplazamientos y recorrido de memoria.

### Actividades sugeridas
- Analizar ejemplos de punteros simples en C++.
- Implementar acceso indirecto equivalente en ensamblador.
- Recorrer un arreglo desde una dirección base.
- Explicar por qué un puntero modifica el valor original.

### Evidencias
- Traducción de ejercicios con punteros y arreglos.
- Esquema de memoria con variables, direcciones y valores.

## Sesión 7. Evaluación parcial teórica

### Enfoque de evaluación
- Arquitectura básica del computador.
- Diferencia entre ROM, RAM, registros y periféricos.
- Lectura e interpretación de instrucciones Hack.
- Control de flujo, ALU, memoria mapeada y traducción alto/bajo nivel.

### Productos esperados
- Prueba escrita o cuestionario estructurado.
- Análisis de un programa corto con justificación del comportamiento esperado.
