# Unidad 2 · Memoria, objetos y estructuras de datos en C++

## Archivo 2: Objetos, punteros y ciclo de vida

### Propósito
Profundizar en el comportamiento de objetos y memoria para conectar representación interna, copia, paso a funciones y duración de los datos.

### Sesiones cubiertas
- Sesión 3. Experimentos de memoria y efectos de modificar distintos segmentos.
- Sesión 4. Objetos en stack y heap; copia de objetos y paso de objetos a funciones.
- Sesión 5. Miembros de instancia, miembros estáticos y ciclo de vida de objetos.

### Resultados de aprendizaje
- Comparar efectos de modificar stack, heap y datos estáticos.
- Distinguir objetos automáticos y dinámicos.
- Explicar copia, aliasing y paso de objetos.
- Analizar el ciclo de vida de instancias y miembros estáticos.

## Sesión 3. Experimentos de memoria

### Objetivo
Observar de forma experimental cómo se comportan las distintas regiones de memoria cuando se crean, modifican y destruyen datos.

### Temas centrales
- Variables locales, globales y estáticas.
- Reserva y liberación de memoria dinámica.
- Riesgos conceptuales: referencias colgantes y fugas.
- Efecto de la salida de una función sobre el stack.

### Actividades sugeridas
- Modificar programas cortos y predecir el resultado.
- Comparar qué datos persisten y cuáles desaparecen.
- Registrar hipótesis antes de ejecutar cada experimento.

### Evidencias
- Bitácora de predicción, observación y conclusión.

## Sesión 4. Objetos en stack y heap

### Objetivo
Comprender cómo se crean, copian y comparten objetos según su forma de almacenamiento.

### Temas centrales
- Construcción de objetos automáticos.
- Creación dinámica con punteros.
- Copia superficial como problema conceptual inicial.
- Paso de objetos por valor y por referencia.

### Actividades sugeridas
- Comparar dos versiones de una misma clase: stack y heap.
- Pasar objetos a funciones y observar copias.
- Explicar cuándo dos variables refieren al mismo objeto y cuándo no.

### Evidencias
- Diagrama de objetos y referencias.
- Explicación del efecto de copiar un objeto en un caso concreto.

## Sesión 5. Miembros estáticos y ciclo de vida

### Objetivo
Relacionar la vida útil de los objetos con sus atributos, su clase y el contexto donde fueron creados.

### Temas centrales
- Miembros de instancia frente a miembros estáticos.
- Constructores y destructores como eventos observables.
- Estado compartido entre objetos de una misma clase.
- Persistencia más allá de una instancia particular.

### Actividades sugeridas
- Diseñar una clase con contador estático de instancias.
- Observar el orden de creación y destrucción.
- Comparar datos propios del objeto con datos compartidos por la clase.

### Evidencias
- Tabla de ciclo de vida por objeto.
- Reflexión sobre diseño y responsabilidad del estado compartido.
