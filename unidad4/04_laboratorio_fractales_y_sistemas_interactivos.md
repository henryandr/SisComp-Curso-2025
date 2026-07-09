# Unidad 4 · GPU, OpenGL y programación concurrente

## Archivo 4: Laboratorio de fractales y sistemas interactivos

### Propósito
Integrar GPU/OpenGL con concurrencia y paralelismo en problemas visuales donde la relación entre cómputo, render y responsividad sea clara.

### Sesiones cubiertas
- Sesión 7. Paralelismo aplicado: Mandelbrot, análisis de flocking y Julia interactivo.
- Sesión 8. Evaluación sobre GPU/OpenGL, hilos, sincronización y paralelismo aplicado.

### Resultados de aprendizaje
- Aplicar paralelismo a un problema visual intensivo.
- Relacionar render, cómputo y actualización de estado.
- Justificar decisiones de sincronización en un sistema interactivo.

## Sesión 7. Laboratorio aplicado

### Objetivo
Resolver un problema visual que requiera integrar representación gráfica con cómputo intensivo y control de interacción.

### Posibles ejes del laboratorio
- Fractal de Mandelbrot como carga paralelizable.
- Julia interactivo con control de parámetros.
- Análisis de flocking con separación entre simulación y visualización.
- Comparación entre versión secuencial y versión concurrente.

### Criterios de desarrollo
- Debe observarse claramente el beneficio o el costo del paralelismo.
- La aplicación debe mantener una interacción razonable.
- El estudiante debe explicar dónde ocurre el trabajo principal y cómo se sincroniza.

### Evidencias
- Demostración funcional.
- Breve análisis del reparto de trabajo y del estado compartido.
- Comparación de comportamiento entre enfoques.

## Sesión 8. Evaluación

### Enfoque de evaluación
- CPU vs GPU y pipeline gráfico.
- VAO, VBO, shaders y uniforms.
- Procesos, hilos, concurrencia y paralelismo.
- Condiciones de carrera y mutex.
- Aplicaciones paralelas a problemas gráficos.

### Productos esperados
- Evaluación conceptual.
- Interpretación de un fragmento de programa gráfico o concurrente.
