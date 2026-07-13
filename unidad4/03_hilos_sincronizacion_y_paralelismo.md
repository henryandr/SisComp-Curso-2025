# Unidad 4 · GPU, OpenGL y programación concurrente

## Sesión 5. Procesos, hilos y responsividad

### ¿Qué aprenderás en esta sesión? 💡

- Diferenciar proceso, hilo, concurrencia y paralelismo.
- Explicar por qué una interfaz puede congelarse.
- Reconocer cuándo conviene mover trabajo fuera del hilo principal.
- Relacionar render en tiempo real con responsividad.

### Actividad 13: Observa una interfaz bloqueante

Analiza una aplicación interactiva donde un clic dispara una computación pesada en el mismo hilo principal.

Predice antes de ejecutarla:

- ¿la animación seguirá fluida?
- ¿la ventana seguirá respondiendo?
- ¿qué tarea deja de avanzar cuando la computación pesada empieza?

Luego ejecuta y compara tu predicción con lo observado.

### Actividad 14: Concurrencia vs paralelismo

Completa una tabla con estos conceptos:

- **Proceso**
- **Hilo**
- **Concurrencia**
- **Paralelismo**
- **Responsividad**

Después responde:

- ¿puede haber concurrencia sin paralelismo real?
- ¿por qué una aplicación gráfica suele necesitar al menos concurrencia, aunque no siempre gane velocidad total?
- ¿qué relación ves entre hilo principal, eventos y render?

### Actividad 15: Mueve el trabajo a un hilo secundario

A partir del ejemplo bloqueante, plantea una versión donde la tarea costosa ocurra en segundo plano.

Explica:

- qué parte debe seguir en el hilo principal,
- qué parte puede ir a otro hilo,
- qué mejora esperas notar en la experiencia de usuario,
- qué nuevos riesgos aparecen al compartir datos.

<aside>
📤

**Bitácora**

- Describe qué observaste en la versión bloqueante.
- Explica con tus palabras la diferencia entre concurrencia y paralelismo.
- Justifica por qué mover trabajo a un hilo secundario puede mejorar la responsividad.
- Dibuja un esquema simple con el hilo principal y el hilo de trabajo.

</aside>

## Sesión 6. Sincronización, estado compartido y condiciones de carrera

### ¿Qué aprenderás en esta sesión? 💡

- Identificar condiciones de carrera.
- Reconocer secciones críticas.
- Usar mutex como mecanismo básico de exclusión mutua.
- Evaluar el costo y el beneficio de sincronizar.

### Actividad 16: Detecta el dato compartido

Observa una versión con dos hilos donde ambos acceden a una misma variable visual, por ejemplo el tamaño de una figura o un contador.

Responde:

- ¿qué dato es compartido?
- ¿qué hilo lo lee?
- ¿qué hilo lo modifica?
- ¿por qué eso puede producir resultados inconsistentes?

### Actividad 17: Antes y después del mutex

Compara dos versiones del mismo programa:

1. una sin protección,
2. otra con `lock` y `unlock` o un `mutex` equivalente.

Documenta:

- qué comportamiento esperas de la versión sin protección,
- qué cambia al sincronizar,
- qué garantía nueva aparece,
- qué costo potencial introduces.

### Actividad 18: Analiza una condición de carrera clásica

Trabaja con un contador compartido incrementado por varios hilos.

Antes de ejecutar, responde:

- si cuatro hilos incrementan un contador el mismo número de veces, ¿el resultado final debería ser exacto?
- ¿por qué podría no coincidir si no hay sincronización?
- ¿qué parte exacta de `contador++` deja de ser segura cuando varios hilos la ejecutan a la vez?

### Actividad 19: ¿Sincronizar siempre es gratis?

Reflexiona sobre esta tensión:

- sin sincronización hay más riesgo de error,
- con sincronización puede bajar el paralelismo efectivo.

Explica:

- cuándo vale la pena pagar ese costo,
- qué datos no necesitarían protección,
- por qué un diseño con menos estado compartido suele ser más simple.

<aside>
📤

**Bitácora**

- Registra el comportamiento antes y después de sincronizar.
- Explica qué es una condición de carrera con un ejemplo propio.
- Describe qué protege el mutex y qué no resuelve por sí solo.
- Concluye qué aprendiste sobre el balance entre seguridad y rendimiento.

</aside>
