# Unidad 4 · GPU, OpenGL y programación concurrente

## Archivo 1: Fundamentos de GPU y pipeline gráfico

### Propósito
Introducir el modelo de render moderno y la diferencia conceptual entre CPU y GPU como preparación para OpenGL y programación paralela.

### Sesiones cubiertas
- Sesión 1. CPU vs GPU, contexto OpenGL, framebuffer, viewport y flujo general de render.
- Sesión 2. Objetos de OpenGL: VAO, VBO, shader program y pipeline programable.

### Resultados de aprendizaje
- Diferenciar responsabilidades de CPU y GPU.
- Explicar el recorrido general de un frame.
- Reconocer los objetos básicos de OpenGL.
- Relacionar datos de vértices con el pipeline programable.

## Sesión 1. CPU, GPU y flujo de render

### Objetivo
Comprender cómo se organiza un pipeline gráfico moderno y por qué la GPU es adecuada para tareas masivamente paralelas.

### Temas centrales
- CPU como coordinadora y GPU como procesadora especializada.
- Contexto gráfico y ciclo de render.
- Framebuffer y viewport.
- Datos, comandos y presentación en pantalla.

### Actividades sugeridas
- Trazar el recorrido de un frame desde la aplicación hasta la pantalla.
- Comparar un cálculo secuencial en CPU con uno paralelo en GPU a nivel conceptual.
- Identificar qué partes del sistema viven en CPU y cuáles en GPU.

### Evidencias
- Diagrama del flujo de render.
- Explicación escrita de la diferencia CPU/GPU.

## Sesión 2. Objetos básicos de OpenGL

### Objetivo
Relacionar la organización de datos y estados de OpenGL con el pipeline gráfico programable.

### Temas centrales
- VAO como configuración de atributos.
- VBO como almacenamiento de vértices.
- Shader program como pareja de etapas programables.
- Draw calls como activación del pipeline.

### Actividades sugeridas
- Analizar un ejemplo mínimo de triángulo.
- Ubicar dónde se crean, cargan y usan VAO y VBO.
- Explicar qué pasa si falta alguno de los objetos esenciales.

### Evidencias
- Mapa del ciclo de vida de los objetos de OpenGL.
- Respuestas cortas sobre el rol de cada objeto.
