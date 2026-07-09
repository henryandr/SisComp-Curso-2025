# Unidad 3 · Programación orientada a objetos y patrones de diseño

## Archivo 3: Patrones Observer, Factory y State

### Propósito
Presentar patrones de diseño como soluciones reutilizables para organizar variación, comunicación y cambio de comportamiento dentro de un mismo sistema.

### Sesiones cubiertas
- Sesión 5. Herencia simple/múltiple y organización de objetos en memoria.
- Sesión 6. Polimorfismo en tiempo de ejecución y despacho dinámico.
- Sesión 7. Patrones Observer, Factory y State aplicados a un mismo sistema.

### Resultados de aprendizaje
- Analizar cómo la herencia reorganiza la representación de objetos.
- Usar polimorfismo para desacoplar comportamiento.
- Reconocer problemas de diseño que justifican patrones.
- Comparar Observer, Factory y State dentro de un caso compartido.

## Sesión 5. Herencia y memoria

### Objetivo
Observar cómo cambia la organización del objeto cuando se extiende una clase y cómo esa decisión impacta diseño y mantenimiento.

### Temas centrales
- Herencia simple y múltiple como conceptos de modelado.
- Atributos heredados y atributos agregados.
- Riesgos de complejidad innecesaria.
- Relación entre jerarquía y claridad del sistema.

### Actividades sugeridas
- Comparar varias alternativas de jerarquía.
- Dibujar objetos base y derivados en memoria.
- Discutir cuándo una relación de herencia es apropiada.

### Evidencias
- Propuesta razonada de jerarquía.
- Esquema comparativo de organización en memoria.

## Sesión 6. Polimorfismo y despacho dinámico

### Objetivo
Usar polimorfismo para expresar comportamientos variables bajo una interfaz común.

### Temas centrales
- Sustitución de objetos derivados por referencias a base.
- Despacho dinámico.
- Colecciones heterogéneas de objetos.
- Extensibilidad sin modificar código cliente central.

### Actividades sugeridas
- Analizar una colección de entidades con comportamiento distinto.
- Predecir el resultado de una llamada polimórfica.
- Justificar por qué el cliente no necesita conocer la clase concreta.

### Evidencias
- Explicación del flujo polimórfico en un ejemplo.
- Tabla de comportamientos por tipo concreto.

## Sesión 7. Patrones de diseño aplicados

### Objetivo
Aplicar tres patrones clásicos a un único caso de estudio para diferenciar claramente el problema que resuelve cada uno.

### Temas centrales
- Observer para notificación entre objetos.
- Factory para creación desacoplada.
- State para cambio de comportamiento según estado interno.
- Comparación entre comunicación, creación y control de estados.

### Actividades sugeridas
- Extender un sistema con eventos, tipos de entidades y modos de comportamiento.
- Ubicar cada patrón en el punto del sistema donde más valor aporta.
- Comparar una versión ad hoc con una versión basada en patrones.

### Evidencias
- Explicación del rol de cada patrón en el sistema.
- Diagrama simple de interacción entre objetos.
