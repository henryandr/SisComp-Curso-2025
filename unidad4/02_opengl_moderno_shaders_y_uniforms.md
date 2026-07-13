# Unidad 4 · GPU, OpenGL y programación concurrente

## Sesión 3. Vertex shader, fragment shader y flujo de datos

### ¿Qué aprenderás en esta sesión? 💡

- Explicar qué hace el vertex shader.
- Explicar qué hace el fragment shader.
- Relacionar atributos de vértice con posiciones, colores o coordenadas.
- Seguir el recorrido de un triángulo desde sus datos hasta sus fragmentos.

### Actividad 7: Lee un shader mínimo

Analiza un ejemplo como este:

```glsl
#version 330 core
layout(location = 0) in vec3 aPos;

void main() {
    gl_Position = vec4(aPos, 1.0);
}
```

```glsl
#version 330 core
out vec4 FragColor;

void main() {
    FragColor = vec4(1.0, 0.5, 0.2, 1.0);
}
```

Responde:

- ¿qué dato entra al vertex shader?
- ¿qué salida produce?
- ¿qué responsabilidad tiene el fragment shader?
- ¿por qué el color final no se decide en el mismo lugar donde se reciben los vértices?

### Actividad 8: Sigue el recorrido de un triángulo

Toma un triángulo definido por tres vértices y describe el camino completo:

1. cómo se almacenan sus datos,
2. cómo llegan al vertex shader,
3. cómo se transforman en posiciones de clip space,
4. cómo se convierten en fragmentos,
5. cómo se obtiene el color final.

### Actividad 9: Atributos por vértice

Imagina que cada vértice tiene posición y color.

Responde:

- ¿qué significa que el color sea un atributo por vértice?
- ¿qué esperas ver en pantalla entre un vértice rojo y otro azul?
- ¿qué diferencia hay entre un valor que cambia por vértice y uno que permanece igual para toda la figura?

<aside>
📤

**Bitácora**

- Explica con tus palabras la diferencia entre vertex shader y fragment shader.
- Dibuja el flujo de datos entre CPU, buffers, vertex shader y fragment shader.
- Describe qué ocurre con un atributo como el color cuando pasa de los vértices a los fragmentos.
- Registra una duda conceptual que te haya quedado sobre rasterización o interpolación.

</aside>

## Sesión 4. Uniforms e interactividad visual

### ¿Qué aprenderás en esta sesión? 💡

- Usar uniforms como puente entre CPU y GPU.
- Distinguir atributos por vértice de parámetros globales del draw call.
- Relacionar tiempo, entrada del usuario y cambio visual.
- Construir una primera escena interactiva sencilla.

### Actividad 10: Controla una variable global del render

Toma un ejemplo mínimo y agrega una variable uniforme para modificar alguno de estos aspectos:

- color,
- desplazamiento horizontal o vertical,
- escala,
- tiempo.

Antes de implementarlo, predice:

- qué parte del programa debe cambiar en C++,
- qué parte debe cambiar en el shader,
- qué comportamiento visual esperas observar.

### Actividad 11: Atributos vs uniforms

Compara estas dos ideas:

- cada vértice tiene su propio color,
- toda la figura recibe un solo color enviado como uniform.

Luego responde:

- ¿cuál de los dos cambia con mayor granularidad?
- ¿cuál conviene usar para animar todo un objeto a la vez?
- ¿cómo cambia el diseño del shader en cada caso?

### Actividad 12: Diseña una variación interactiva

Propón una modificación pequeña al triángulo base:

- cambio de color con teclado,
- oscilación con tiempo,
- desplazamiento con mouse,
- escalado con una variable animada.

Debes explicar:

- qué dato se calcula en CPU,
- qué dato se envía como uniform,
- qué transformación o efecto se resuelve en GPU.

<aside>
📤

**Bitácora**

- Incluye el shader o fragmento clave que modificaste.
- Explica qué información envías como uniform y por qué.
- Describe la diferencia entre un cambio por vértice y un cambio global.
- Registra capturas o evidencia del comportamiento interactivo logrado.

</aside>
