# Exámenes Alternativos - Unidad 7: Gráficas y Shaders

Este directorio contiene dos exámenes alternativos (A y B) para la Unidad 7 del curso de Sistemas Computacionales.

## Archivos Incluidos

1. **examen_A.tex** - Examen alternativo versión A
2. **examen_B.tex** - Examen alternativo versión B  
3. **VALIDACION.md** - Documento de validación completo con matrices de cobertura y análisis de calidad
4. **Unit7.md** - Material de referencia de la unidad (original)
5. **Eval-U7_2025-1.tex** - Examen guía utilizado como referencia de formato (original)

## Estructura de Cada Examen

Cada examen tiene un total de **50 puntos** distribuidos así:

### Preguntas de Selección Múltiple (20 pts)
- 5 preguntas
- 4 puntos cada una
- 4 opciones (A-D) con una sola correcta
- Distractores basados en errores conceptuales comunes

### Preguntas Abiertas (30 pts)
- 3 preguntas
- 10 puntos cada una
- Requieren desarrollo, análisis o aplicación de conceptos
- Incluyen rúbricas detalladas para evaluación

## Temas Cubiertos

Los exámenes cubren los siguientes temas de la Unidad 7:

- **Arquitectura de GPU**: Procesamiento paralelo, diferencias CPU vs GPU
- **Shaders**: Vertex shaders, fragment shaders, diferencias y funciones
- **Render Pipeline**: Etapas, transformaciones (Model-View-Projection-Viewport)
- **Comunicación CPU-GPU**: Variables uniform, attributes, actualización en tiempo real
- **Conceptos Técnicos**: Rasterización, interpolación, framebuffer, Z-buffer
- **Texturas y Materiales**: Diferencias y aplicaciones
- **Programación Interactiva**: Modificación de vértices y fragmentos con shaders

## Compilación LaTeX

### Requisitos

- LaTeX distribution (TeX Live, MiKTeX, etc.)
- Paquetes requeridos (todos estándar):
  - exam, inputenc, babel, times, graphicx, tcolorbox, listings, multicol, etc.
- Archivo `Logo-UPB-2022.pdf` en el mismo directorio (o comentar línea 42 en ambos archivos)

### Comandos de Compilación

```bash
# Compilar Examen A
pdflatex examen_A.tex

# Compilar Examen B
pdflatex examen_B.tex
```

### Compilación sin Logo

Si no dispone del archivo `Logo-UPB-2022.pdf`, comente la línea 42 en ambos archivos:

```latex
% \multirow{5}{*}{\includegraphics[width=1\linewidth]{Logo-UPB-2022.pdf}}
```

## Soluciones y Claves de Respuesta

Las soluciones están incluidas **en comentarios** al final de cada archivo `.tex`:

### Examen A (líneas 181-288)
- Claves de MCQ con justificaciones
- Explicación de cada distractor
- Rúbricas detalladas para preguntas abiertas
- Soluciones modelo con ejemplos de código GLSL

### Examen B (líneas 181-332)
- Claves de MCQ con justificaciones
- Explicación de cada distractor
- Rúbricas detalladas para preguntas abiertas
- Soluciones modelo con ejemplos de código

### Formato de Claves MCQ

```
Pregunta X: [Letra] (Descripción breve)
Justificación: Por qué es correcta
Distractores: Por qué cada opción incorrecta es errónea
```

### Formato de Rúbricas

```
Pregunta X: [Tema]
Rúbrica:
- Criterio 1: X pts
- Criterio 2: X pts
...

Solución modelo:
[Respuesta completa esperada con detalles y código si aplica]
```

## Diferenciación entre Examen A y B

Los exámenes A y B:

- ✅ Cubren los mismos objetivos de aprendizaje
- ✅ Tienen dificultad equivalente
- ✅ Utilizan preguntas diferentes (mínima superposición)
- ✅ Mantienen el mismo formato y estructura
- ✅ Pueden aplicarse simultáneamente sin riesgo de copia

### Ejemplos de Diferenciación

**MCQ:**
- A-Q1: Rasterización → B-Q1: Transformaciones
- A-Q2: Interpolación → B-Q2: Framebuffer
- A-Q3: Vertex vs Fragment → B-Q3: Attributes vs Uniforms

**Abiertas:**
- A-Q6: Texturas vs Materiales → B-Q6: Uniforms con código
- A-Q8: Modificaciones específicas con GLSL → B-Q8: Propuestas de aplicaciones

## Validación de Calidad

El documento **VALIDACION.md** incluye:

- ✅ Matrices de cobertura temática
- ✅ Análisis de distribución de dificultad
- ✅ Verificación de originalidad
- ✅ Evaluación de distractores
- ✅ Checklist de claridad y lenguaje inclusivo
- ✅ Comparación con examen guía
- ✅ Trazabilidad de objetivos de aprendizaje

## Uso Recomendado

### Para Aplicar los Exámenes

1. **Compilar los PDFs** con los comandos indicados
2. **Asignar aleatoriamente** versión A o B a cada estudiante
3. **Usar las rúbricas** incluidas para evaluación consistente
4. **Consultar soluciones modelo** para casos ambiguos

### Para Crear Nuevos Exámenes

Los archivos `.tex` pueden usarse como **plantillas** para futuras variantes:

- Mantener el preámbulo y estructura
- Reemplazar contenido de preguntas
- Actualizar soluciones en comentarios
- Ajustar puntos si es necesario (modificar `\question[X]`)

## Contacto y Soporte

Para preguntas sobre el contenido de los exámenes:
- **Preparado por:** Henry Andrade, IEo, Ph.D.
- **Curso:** Sistemas Computacionales
- **Programa:** Ingeniería en Diseño de Entretenimiento Digital
- **Institución:** Universidad Pontificia Bolivariana - Sede Medellín

---

**Fecha de creación:** Mayo 2025  
**Versión:** 1.0  
**Repositorio:** henryandr/SisComp-Curso-2025
