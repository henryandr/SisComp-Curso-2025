# Unidad 4 · GPU, OpenGL y programación concurrente

En esta unidad vas a conectar dos preguntas que suelen estudiarse por separado: **cómo se dibuja una escena en la GPU** y **cómo se organiza el trabajo cuando un programa necesita responder, renderizar y calcular al mismo tiempo**. Empezaremos por el lado gráfico: CPU, GPU, contexto, pipeline, buffers y el flujo de un frame.

## Sesión 1. CPU, GPU y flujo general de render

### ¿Qué aprenderás en esta sesión? 💡

- Diferenciar el rol de la CPU y el de la GPU.
- Explicar qué es un contexto gráfico y por qué hace falta.
- Describir el recorrido general de un frame.
- Relacionar actualización, dibujo y presentación en pantalla.

### Actividad 1: Traza el viaje de un frame

Piensa en una aplicación gráfica interactiva. Sin escribir código todavía, describe qué ocurre desde que el programa inicia hasta que aparece una imagen en la ventana.

Incluye al menos estas piezas:

- creación de ventana,
- creación de contexto gráfico,
- datos de la escena,
- envío de comandos,
- trabajo de la GPU,
- framebuffer,
- presentación en pantalla.

### Actividad 2: CPU vs GPU

Completa una tabla comparativa con estas columnas:

- **Componente**
- **Qué tipo de trabajo realiza mejor**
- **Qué tan flexible es**
- **Qué tan paralela es su ejecución**
- **Ejemplo en una aplicación visual**

Luego responde:

- ¿por qué no tendría sentido pedirle a la CPU que hiciera todo el render moderno por sí sola?
- ¿por qué la GPU no reemplaza completamente a la CPU?
- ¿qué tipo de coordinación debe seguir haciendo la CPU aunque la GPU dibuje?

### Actividad 3: ¿Qué es un contexto OpenGL?

Lee un ejemplo mínimo con GLFW o openFrameworks e identifica en qué momento se crea el contexto gráfico.

Reflexiona:

- ¿por qué OpenGL necesita una ventana o una superficie asociada?
- ¿qué información crees que guarda el contexto?
- ¿qué podría salir mal si intentaras usar OpenGL antes de crear ese contexto?

<aside>
📤

**Bitácora**

- Dibuja el flujo general de un frame desde la aplicación hasta la pantalla.
- Explica con tus palabras la diferencia entre CPU y GPU.
- Redacta una definición propia de contexto OpenGL.
- Formula al menos dos preguntas que quieras investigar sobre el pipeline gráfico.

</aside>

## Sesión 2. Objetos básicos de OpenGL y pipeline programable

### ¿Qué aprenderás en esta sesión? 💡

- Reconocer las piezas mínimas de un pipeline gráfico moderno.
- Distinguir VAO, VBO y shader program.
- Relacionar datos de vértices con etapas de procesamiento.
- Entender qué activa realmente una draw call.

### Actividad 4: Caso mínimo del triángulo

Trabaja con un ejemplo de triángulo simple y ubica estas piezas:

- arreglo de vértices,
- VBO,
- VAO,
- vertex shader,
- fragment shader,
- llamada de dibujo.

No memorices nombres todavía; trata de responder **qué problema resuelve cada objeto**.

### Actividad 5: Identifica el rol de cada objeto

Completa este mapa conceptual:

- **VBO:** ¿qué datos guarda?
- **VAO:** ¿qué configuración recuerda?
- **Shader program:** ¿qué comportamiento define?
- **Draw call:** ¿qué ordena hacer?

Después responde:

- ¿qué diferencia hay entre almacenar datos y definir cómo interpretarlos?
- ¿por qué el VAO y el VBO no son lo mismo?
- ¿qué pasaría si tuvieras datos de vértices pero ningún shader activo?

### Actividad 6: Reconstruye el pipeline en orden

Ordena conceptualmente estas etapas:

- carga de datos,
- procesamiento de vértices,
- ensamblaje primitivo,
- rasterización,
- cálculo de color final,
- escritura en framebuffer.

Luego explica en qué parte del proceso interviene más claramente la CPU y en cuál la GPU.

<aside>
📤

**Bitácora**

- Señala en el ejemplo dónde aparecen VAO, VBO, shaders y draw call.
- Explica el rol de cada objeto con tus propias palabras.
- Construye un diagrama del pipeline programable.
- Resume qué parte del proceso te resultó menos intuitiva y por qué.

</aside>
