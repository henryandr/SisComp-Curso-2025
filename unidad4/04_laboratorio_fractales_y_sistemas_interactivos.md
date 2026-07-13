# Unidad 4 · GPU, OpenGL y programación concurrente

## Laboratorio integrador. Sistemas visuales con cómputo intensivo

### Propósito

Integrar GPU/OpenGL con concurrencia y paralelismo en una aplicación donde el reparto de trabajo, la interactividad y la sincronización sean visibles y justificables.

### Actividad 20: Diseña e implementa un laboratorio aplicado

Desarrolla una aplicación visual con uno de estos enfoques:

- visualización del conjunto de Mandelbrot,
- Julia interactivo con parámetros manipulables,
- sistema de flocking con separación entre simulación y visualización,
- comparación entre una versión secuencial y una versión concurrente de un mismo problema gráfico.

### Criterios del laboratorio

- Debe existir una carga de trabajo suficientemente costosa como para justificar análisis de rendimiento o responsividad.
- Debe quedar claro qué parte corre principalmente en CPU y cuál depende del pipeline gráfico.
- Debe explicarse si el paralelismo ocurre en CPU, en GPU o en ambos niveles.
- Si hay estado compartido entre hilos, debe justificarse cómo se protege o cómo se evita compartirlo.
- La aplicación debe conservar un nivel de interacción razonable para observar el sistema en funcionamiento.

### Preguntas guía para el diseño

Antes de implementar, responde:

- ¿qué parte del problema vas a paralelizar o separar del hilo principal?
- ¿qué datos cambian cada frame?
- ¿qué datos deben llegar a la GPU?
- ¿qué métricas o comparaciones usarás para argumentar mejora o costo?

### Entregables sugeridos

- Código funcional o prototipo explicativo.
- Capturas o video corto del sistema funcionando.
- Diagrama del reparto de trabajo entre CPU, GPU e hilos.
- Comparación breve entre dos enfoques de implementación.

<aside>
📤

**Bitácora**

- Explica qué problema visual elegiste y por qué.
- Justifica dónde ocurre el trabajo pesado.
- Describe cómo mantuviste la aplicación interactiva.
- Explica si necesitaste sincronización y qué decisión tomaste.
- Resume qué evidencia usaste para comparar rendimiento, fluidez o costo de sincronización.

</aside>

## Sesión 8. Evaluación de comprensión conceptual

### Autoevaluación

Responde sin consultar apuntes, internet ni herramientas de IA. La meta es recuperar y reorganizar lo aprendido.

#### Parte 1. Recuperación de conocimiento

1. Explica la diferencia entre CPU y GPU en una aplicación gráfica.
2. ¿Qué función cumple el contexto OpenGL?
3. ¿Para qué sirven VBO, VAO y shader program?
4. ¿Qué diferencia hay entre vertex shader y fragment shader?
5. ¿Qué es un uniform y cómo se diferencia de un atributo por vértice?
6. ¿Qué significa que una interfaz sea responsiva?
7. ¿Cuál es la diferencia entre proceso e hilo?
8. ¿Cuál es la diferencia entre concurrencia y paralelismo?
9. ¿Qué es una condición de carrera?
10. ¿Qué resuelve un mutex y qué costo puede introducir?
11. ¿Cómo se relacionan render, cómputo y sincronización en un sistema interactivo?

#### Parte 2. Metacognición

1. ¿Qué actividad te ayudó más a entender el pipeline gráfico y por qué?
2. ¿Qué experimento te ayudó más a entender los hilos y por qué?
3. ¿Qué confusión tuviste sobre GPU, shaders o paralelismo y cómo la resolviste?
4. Si repitieras esta unidad, ¿qué medirías o compararías con más cuidado?

### Coevaluación

Intercambia con un compañero el resultado de su laboratorio y revisa:

- si el problema elegido justifica el uso de concurrencia o paralelismo,
- si la explicación CPU/GPU es coherente,
- si el reparto de trabajo está claramente descrito,
- si el manejo del estado compartido es claro,
- si la comparación entre enfoques está bien argumentada.

<aside>
📤

**Bitácora**

- Copia la evidencia del trabajo revisado.
- Resume qué entendiste de la solución de tu compañero.
- Señala una fortaleza y una recomendación concreta.
- Explica qué aprendiste al comparar otra estrategia de diseño o paralelización.

</aside>
