# Unidad 4 · GPU, OpenGL y programación concurrente

## Archivo 3: Hilos, sincronización y paralelismo

### Propósito
Introducir concurrencia y paralelismo como herramientas para mejorar responsividad y rendimiento, conectándolas con problemas reales de estado compartido.

### Sesiones cubiertas
- Sesión 5. Procesos, hilos, concurrencia vs paralelismo y responsividad de interfaces.
- Sesión 6. Condiciones de carrera, mutex, sincronización y estado compartido.

### Resultados de aprendizaje
- Diferenciar proceso, hilo, concurrencia y paralelismo.
- Explicar por qué una interfaz puede congelarse.
- Identificar condiciones de carrera.
- Aplicar mecanismos básicos de sincronización a un caso concreto.

## Sesión 5. Procesos, hilos y responsividad

### Objetivo
Comprender por qué dividir trabajo en hilos puede mejorar la experiencia de usuario y cómo esa decisión cambia la organización del sistema.

### Temas centrales
- Proceso frente a hilo.
- Concurrencia frente a paralelismo.
- Trabajo de fondo y responsividad de interfaz.
- Distribución de tareas de cómputo y render.

### Actividades sugeridas
- Analizar una aplicación bloqueante y una responsiva.
- Clasificar tareas como seriales o candidatas a ejecución paralela.
- Relacionar render en tiempo real con necesidad de fluidez.

### Evidencias
- Explicación comparativa entre concurrencia y paralelismo.
- Justificación de una estrategia de separación de tareas.

## Sesión 6. Sincronización y estado compartido

### Objetivo
Reconocer los riesgos de compartir datos entre hilos y usar mecanismos de sincronización para proteger consistencia.

### Temas centrales
- Condición de carrera.
- Sección crítica.
- Mutex y exclusión mutua.
- Balance entre seguridad, simplicidad y costo de sincronización.

### Actividades sugeridas
- Observar resultados incorrectos en un ejemplo con estado compartido.
- Introducir protección con mutex y comparar comportamiento.
- Identificar qué datos requieren sincronización y cuáles no.

### Evidencias
- Registro de comportamiento antes y después de sincronizar.
- Explicación del problema y de la solución aplicada.
