# Unidad 2 · Memoria, objetos y estructuras de datos en C++

## Laboratorio integrador. Memoria, objetos y estructuras lineales en openFrameworks

### Propósito

Integrar lo aprendido sobre stack, heap, objetos, punteros y estructuras lineales en una aplicación interactiva donde el comportamiento visual dependa explícitamente de decisiones de memoria y organización de datos.

### Actividad 15: Diseña e implementa una aplicación integradora

Desarrolla una aplicación corta en openFrameworks en la que una estructura lineal controle el comportamiento del sistema. Puedes elegir uno de estos focos:

- serpiente o rastro basado en lista enlazada
- cola de trazos o partículas con desaparición progresiva
- visualización de creación y destrucción de nodos
- comparación entre almacenamiento fijo y dinámico en una escena interactiva

### Criterios del laboratorio

- La estructura elegida debe estar justificada.
- Debe existir memoria dinámica visible en el diseño.
- Debes poder explicar qué datos viven en stack, cuáles en heap y cuáles son compartidos.
- El comportamiento visual debe permitir observar inserción, recorrido o eliminación.
- La liberación de memoria debe quedar resuelta explícitamente.

### Entregables sugeridos

- Código funcional.
- Breve explicación técnica del diseño.
- Registro de pruebas realizadas.
- Reflexión sobre cómo la estructura influye en el comportamiento visual.

<aside>
📤

**Bitácora**

- Explica qué estructura implementaste y por qué.
- Dibuja el flujo de datos principal de tu aplicación.
- Identifica un momento donde tuviste que razonar sobre stack, heap o punteros para corregir un problema.
- Describe cómo verificaste que tu aplicación no dejaba memoria sin liberar.

</aside>

## Sesión 8. Evaluación de comprensión conceptual

### Autoevaluación

Responde sin consultar apuntes, internet ni herramientas de IA. La meta es recuperar y organizar lo que ya construiste durante la unidad.

#### Parte 1. Recuperación de conocimiento

1. Explica la diferencia entre paso por valor, por referencia y por puntero.
2. Describe las regiones principales del mapa de memoria de un programa en C++.
3. ¿Cuál es la diferencia entre un objeto creado en el stack y uno creado con `new`?
4. ¿Qué significa copiar un objeto en C++?
5. ¿Qué diferencia hay entre un miembro estático y un miembro de instancia?
6. Explica por qué una lista enlazada necesita nodos y punteros.
7. Explica la diferencia conceptual entre una lista enlazada y una cola FIFO.
8. ¿Qué problema aparece si un programa reserva memoria dinámica y nunca la libera?
9. ¿Por qué devolver la dirección de una variable local puede ser incorrecto?
10. ¿Qué papel cumple un destructor en una estructura dinámica?

#### Parte 2. Metacognición

1. ¿Qué actividad te ayudó más a entender la memoria: depurar, dibujar mapas, copiar objetos o implementar estructuras?
2. ¿En qué momento cambió tu modelo mental sobre lo que “es” un objeto en C++?
3. ¿Qué error o confusión fue más útil para aprender en esta unidad?
4. Si repitieras esta unidad, ¿qué harías distinto al experimentar con los programas?

### Coevaluación

Intercambia con un compañero uno de los productos del laboratorio integrador y revisa:

- si la estructura de datos elegida corresponde al comportamiento observado
- si la explicación de memoria es coherente
- si la liberación de memoria está resuelta
- si la justificación del diseño es clara

<aside>
📤

**Bitácora**

- Copia la URL o evidencia del trabajo revisado.
- Resume qué entendiste de la solución de tu compañero.
- Deja al menos una fortaleza y una recomendación concreta.
- Explica qué aprendiste al revisar otra implementación.

</aside>
