# Unidad 3 · Programación orientada a objetos y patrones de diseño

## Archivo 2: Objetos en memoria y polimorfismo

### Propósito
Relacionar la POO con la memoria, la compilación y la ejecución para que el estudiante entienda qué ocurre internamente cuando se usan jerarquías y métodos virtuales.

### Sesiones cubiertas
- Sesión 3. Objeto en memoria, jerarquía de clases, métodos virtuales y vtable.
- Sesión 4. Encapsulamiento en compilación y observación de datos en ejecución.

### Resultados de aprendizaje
- Explicar cómo se representa un objeto en memoria.
- Describir el rol de métodos virtuales y despacho dinámico.
- Relacionar encapsulamiento con restricciones de compilación.
- Observar atributos y referencias durante la ejecución.

## Sesión 3. Representación de objetos y polimorfismo

### Objetivo
Comprender cómo una jerarquía de clases se traduce a objetos concretos y llamadas dinámicas en tiempo de ejecución.

### Temas centrales
- Distribución de atributos en memoria.
- Clase base y clases derivadas.
- Tabla virtual como modelo conceptual.
- Referencias o punteros a base con objetos derivados.

### Actividades sugeridas
- Comparar objetos de distintas clases derivadas.
- Predecir qué método se invoca en casos polimórficos.
- Dibujar una representación conceptual de memoria para una jerarquía.

### Evidencias
- Esquema de objetos en memoria.
- Explicación de una llamada virtual en un ejemplo concreto.

## Sesión 4. Encapsulamiento en compilación y ejecución

### Objetivo
Vincular las reglas de acceso de la POO con lo que puede observarse en el compilador y el depurador.

### Temas centrales
- `public`, `private` y `protected`.
- Fronteras de acceso entre clases y usuarios.
- Inspección de estado en tiempo de ejecución.
- Diferencia entre lo permitido por la interfaz y lo visible durante depuración.

### Actividades sugeridas
- Forzar errores de acceso para interpretar mensajes del compilador.
- Observar objetos encapsulados desde el depurador.
- Debatir por qué encapsular no significa ocultar físicamente la memoria.

### Evidencias
- Ejemplos de acceso correcto e incorrecto.
- Reflexión sobre diseño de interfaces y control de estado.
