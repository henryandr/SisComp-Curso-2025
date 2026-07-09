# Unidad 4 · GPU, OpenGL y programación concurrente

## Archivo 2: OpenGL moderno, shaders y uniforms

### Propósito
Profundizar en la parte programable del pipeline y usar shaders y uniforms para construir una primera escena interactiva.

### Sesiones cubiertas
- Sesión 3. Vertex shader, fragment shader, atributos, draw calls y triángulo base.
- Sesión 4. Uniforms e interactividad: color, posición y tiempo en OpenGL.

### Resultados de aprendizaje
- Explicar el papel de vertex y fragment shaders.
- Conectar atributos de vértice con transformación y rasterización.
- Usar uniforms para modificar una escena desde la CPU.
- Construir un ejemplo gráfico mínimo e interactivo.

## Sesión 3. Vertex y fragment shaders

### Objetivo
Entender cómo la GPU transforma vértices y calcula fragmentos usando programas especializados.

### Temas centrales
- Entradas de vértices.
- Salidas del vertex shader.
- Rasterización y generación de fragmentos.
- Cálculo de color final en el fragment shader.

### Actividades sugeridas
- Leer y explicar un shader mínimo.
- Relacionar atributos con posiciones o colores.
- Describir el recorrido de un triángulo desde datos hasta pixels.

### Evidencias
- Explicación de un programa mínimo de shaders.
- Diagrama del flujo de datos entre etapas.

## Sesión 4. Uniforms e interactividad

### Objetivo
Controlar variables globales del render para producir cambios visuales dependientes del tiempo o de la entrada del usuario.

### Temas centrales
- Uniforms como datos enviados desde CPU.
- Color, traslación, escala y tiempo.
- Vinculación entre loop de actualización y loop de dibujo.
- Primeras experiencias de interactividad visual.

### Actividades sugeridas
- Modificar color y posición mediante teclado, mouse o tiempo.
- Comparar atributos por vértice con uniforms globales.
- Diseñar una variación simple del triángulo base.

### Evidencias
- Escena interactiva mínima.
- Explicación de qué datos cambian por vértice y cuáles por uniform.
