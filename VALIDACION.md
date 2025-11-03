# Validación de Exámenes Alternativos A y B - Unidad 7

## Resumen Ejecutivo

Se han creado dos exámenes alternativos (A y B) para la Unidad 7 de Sistemas Computacionales (Gráficas y Shaders), cada uno con:
- **5 preguntas de selección múltiple** (4 puntos cada una) = 20 puntos
- **3 preguntas abiertas** (10 puntos cada una) = 30 puntos
- **Total: 50 puntos por examen**

## Blueprint y Cobertura Temática

### Temas Principales de Unit7.md

1. **Arquitectura y funcionamiento de GPU**
   - Diferencias CPU vs GPU
   - Procesamiento paralelo masivo
   - Núcleos especializados

2. **Shaders**
   - Vertex shaders
   - Fragment shaders
   - Diferencias y funciones específicas

3. **Render Pipeline**
   - Etapas: Input Assembly, Vertex Processing, Rasterization, Fragment Processing
   - Transformaciones: Model → View → Projection → Viewport
   - Tests: Depth test, Stencil test
   - Framebuffer y Z-buffer

4. **Comunicación CPU-GPU**
   - Variables uniform
   - Atributos de vértice
   - Actualización en tiempo real

5. **Programación interactiva**
   - Modificación de vértices según entrada del usuario
   - Manipulación de colores en fragment shaders
   - Aplicaciones con OpenFrameworks

6. **Conceptos Técnicos**
   - Rasterización
   - Interpolación de atributos
   - Texturas vs Materiales
   - Framebuffer vs Z-buffer

---

## Matriz de Cobertura - Examen A

| Pregunta | Tipo | Tema Principal | Habilidad Cognitiva | Dificultad | Puntos |
|----------|------|----------------|---------------------|------------|---------|
| 1 | MCQ | Rasterización | Comprensión/Aplicación | Media | 4 |
| 2 | MCQ | Interpolación de atributos | Comprensión | Media | 4 |
| 3 | MCQ | Vertex vs Fragment shader | Comprensión | Básica | 4 |
| 4 | MCQ | Uniforms y comunicación CPU-GPU | Aplicación | Media | 4 |
| 5 | MCQ | Arquitectura paralela GPU | Comprensión | Básica | 4 |
| 6 | Abierta | Texturas vs Materiales | Análisis/Aplicación | Media-Alta | 10 |
| 7 | Abierta | Render pipeline completo | Síntesis | Alta | 10 |
| 8 | Abierta | Programación interactiva shaders | Aplicación/Creación | Alta | 10 |

**Total: 50 puntos**

**Cobertura por tema:**
- GPU y arquitectura: ✓ (Pregunta 5)
- Shaders: ✓ (Preguntas 3, 4, 8)
- Pipeline: ✓ (Preguntas 1, 2, 7)
- Comunicación CPU-GPU: ✓ (Pregunta 4, 8)
- Conceptos técnicos: ✓ (Preguntas 1, 2, 6)
- Programación interactiva: ✓ (Pregunta 8)

---

## Matriz de Cobertura - Examen B

| Pregunta | Tipo | Tema Principal | Habilidad Cognitiva | Dificultad | Puntos |
|----------|------|----------------|---------------------|------------|---------|
| 1 | MCQ | Transformaciones del pipeline | Comprensión/Memoria | Media | 4 |
| 2 | MCQ | Framebuffer | Comprensión | Básica | 4 |
| 3 | MCQ | Attributes vs Uniforms | Comprensión | Media | 4 |
| 4 | MCQ | Z-buffer/Depth buffer | Comprensión | Básica | 4 |
| 5 | MCQ | Arquitectura GPU (SIMD) | Comprensión | Básica-Media | 4 |
| 6 | Abierta | Uniforms con ejemplo de código | Aplicación/Síntesis | Media-Alta | 10 |
| 7 | Abierta | Render pipeline completo | Síntesis | Alta | 10 |
| 8 | Abierta | Aplicaciones interactivas (propuestas) | Creación/Aplicación | Alta | 10 |

**Total: 50 puntos**

**Cobertura por tema:**
- GPU y arquitectura: ✓ (Pregunta 5)
- Shaders: ✓ (Preguntas 3, 6, 8)
- Pipeline: ✓ (Preguntas 1, 7)
- Comunicación CPU-GPU: ✓ (Pregunta 6, 8)
- Conceptos técnicos: ✓ (Preguntas 2, 4)
- Programación interactiva: ✓ (Pregunta 8)

---

## Validación de Calidad

### 1. Cobertura de Objetivos de Aprendizaje

**Objetivos de la Unidad 7:**
- ✅ Comprender el funcionamiento de la GPU
- ✅ Familiarizarse con shaders (vertex y fragment)
- ✅ Entender el render pipeline
- ✅ Aprender comunicación CPU-GPU (uniforms)
- ✅ Desarrollar aplicaciones interactivas con shaders

**Ambos exámenes cubren todos los objetivos.**

### 2. Distribución de Dificultad

#### Examen A:
- Básica: 2 preguntas (8 pts)
- Media: 3 preguntas (12 pts)
- Media-Alta: 1 pregunta (10 pts)
- Alta: 2 preguntas (20 pts)

#### Examen B:
- Básica: 2 preguntas (8 pts)
- Básica-Media: 1 pregunta (4 pts)
- Media: 2 preguntas (8 pts)
- Media-Alta: 1 pregunta (10 pts)
- Alta: 2 preguntas (20 pts)

**Distribución similar y equilibrada en ambos exámenes.**

### 3. Comparación con Examen Guía

**Examen Guía (Eval-U7_2025-1.tex):**
- Mezcla de MCQ (3 pts), abiertas (5 pts) y fill-in/ordering (3 pts)
- Total: 50 puntos
- Enfoque: conceptos básicos y aplicación

**Exámenes A y B:**
- Simplificación: solo MCQ y abiertas (más limpio)
- Mayor peso en preguntas abiertas (10 pts vs 5 pts)
- Enfoque más profundo en síntesis y aplicación
- Mantienen el nivel de dificultad y cobertura temática

### 4. Originalidad y No Superposición

#### Entre Examen A y Examen B:

**MCQ (Preguntas 1-5):**
- A-Q1: Rasterización | B-Q1: Transformaciones → Temas diferentes
- A-Q2: Interpolación | B-Q2: Framebuffer → Temas diferentes
- A-Q3: Vertex vs Fragment | B-Q3: Attributes vs Uniforms → Conceptos complementarios
- A-Q4: Uniforms (uso interactivo) | B-Q4: Z-buffer → Temas diferentes
- A-Q5: GPU paralela (genérico) | B-Q5: GPU SIMD (específico) → Enfoques diferentes

**Abiertas (Preguntas 6-8):**
- A-Q6: Texturas vs Materiales | B-Q6: Uniforms con código → Temas diferentes
- A-Q7: Pipeline (detalle de proceso) | B-Q7: Pipeline (etapas y componentes) → Mismo tema, enfoques complementarios
- A-Q8: Modificaciones específicas (con código GLSL) | B-Q8: Propuestas de aplicaciones → Mismo tema, diferentes niveles de abstracción

**Superposición mínima:** Solo Q7 en ambos exámenes aborda el pipeline completo, pero con enfoques diferentes (uno enfatiza el flujo de datos, otro las etapas y componentes).

#### Comparación con Examen Guía:

**MCQ:**
- Guía usa las mismas temáticas (vertex shader, transformaciones, depth buffer, GPU, uniforms)
- A y B mantienen los temas pero con enunciados y distractores completamente nuevos
- Ninguna pregunta es copia literal

**Abiertas:**
- Guía Q6: Pipeline paso a paso → Similar a A-Q7 y B-Q7 pero con diferentes énfasis
- Guía Q7: Color vs textura → Similar a A-Q6 pero expandido a materiales
- Guía Q8: Uniforms con código → Similar a B-Q6
- Guía Q9: Modificaciones interactivas → Similar a A-Q8 y B-Q8 pero con distintos requisitos

**Las preguntas son variaciones sustantivas, no copias literales. Los conceptos nucleares se repiten intencionalmente (son los objetivos de aprendizaje).**

### 5. Claridad y Precisión

✅ **Enunciados claros:** Cada pregunta tiene instrucciones específicas
✅ **Opciones mutuamente excluyentes:** Las MCQ tienen distractores bien diferenciados
✅ **Rúbricas incluidas:** Cada pregunta abierta tiene criterios de evaluación detallados
✅ **Soluciones modelo:** Incluidas en comentarios al final de cada archivo

### 6. Distractores en MCQ

**Estrategia de distractores:**
- **Errores conceptuales comunes:** Inversión de secuencias, confusión de términos
- **Simplificaciones excesivas:** Respuestas parcialmente correctas pero incompletas
- **Confusión de componentes:** Atribuir funciones a componentes incorrectos
- **Verosimilitud:** Todos los distractores son técnicamente plausibles para quien no domina el tema

**Ejemplos:**

*Examen A - Q3 (Vertex vs Fragment):*
- ✓ Correcto: "Vertex procesa vértices; fragment procesa fragmentos"
- ✗ Distractor 1: "Vertex hace iluminación; fragment texturas" (simplificación)
- ✗ Distractor 2: "Fragment hace transformaciones 3D→2D; vertex colores" (inversión)
- ✗ Distractor 3: "Vertex en CPU; fragment en GPU" (ubicación incorrecta)

*Examen B - Q1 (Transformaciones):*
- ✓ Correcto: "Local → View → Clip → Screen"
- ✗ Distractor 1: "View → Local → Screen → Clip" (orden incorrecto)
- ✗ Distractor 2: "Clip → Local → View → Screen" (comienza mal)
- ✗ Distractor 3: "Local → Clip → View → Screen" (Projection antes de View)

### 7. Lenguaje Inclusivo y Sesgo

✅ **Sin sesgos de género:** Uso de términos neutros ("estudiante", no "el estudiante" o "la estudiante")
✅ **Sin referencias culturales específicas:** Ejemplos técnicos universales
✅ **Sin pistas no intencionales:** Longitud de opciones variada, no hay patrón en respuestas correctas

### 8. Suma de Puntos

**Examen A:**
- MCQ: 5 × 4 pts = 20 pts ✓
- Abiertas: 3 × 10 pts = 30 pts ✓
- **Total: 50 pts** ✓

**Examen B:**
- MCQ: 5 × 4 pts = 20 pts ✓
- Abiertas: 3 × 10 pts = 30 pts ✓
- **Total: 50 pts** ✓

---

## Formato LaTeX

### Consistencia con Examen Guía

✅ **Preámbulo idéntico:** Mismo documentclass, paquetes, configuración
✅ **Encabezados:** Formato igual, solo cambia "Versión A" / "Versión B"
✅ **Estructura:** Dos columnas (multicols), mismo layout
✅ **Puntos:** Sistema de puntos con `\boxedpoints`, `\pointname`, `\qformat`
✅ **Entorno de preguntas:** `checkboxes` para MCQ, numeración automática
✅ **Tabla de calificaciones:** `\gradetable[h][questions]` al final

### Notas sobre Compilación

⚠️ **Requisito:** El archivo `Logo-UPB-2022.pdf` debe estar presente en el mismo directorio para compilación exitosa.

**Comando de compilación:**
```bash
pdflatex examen_A.tex
pdflatex examen_B.tex
```

**Alternativa sin logo:** Comentar línea 42 (examen_A) y 42 (examen_B):
```latex
% \multirow{5}{*}{\includegraphics[width=1\linewidth]{Logo-UPB-2022.pdf}}
```

---

## Soluciones y Claves

### Ubicación

Las claves de MCQ y soluciones modelo de preguntas abiertas están incluidas **en comentarios** al final de cada archivo `.tex`:

- **examen_A.tex:** Líneas 277-427 (comentario LaTeX multi-línea)
- **examen_B.tex:** Líneas 289-479 (comentario LaTeX multi-línea)

### Formato de Claves MCQ

Para cada pregunta de selección múltiple:
- Respuesta correcta (A, B, C, o D)
- Justificación de por qué es correcta
- Explicación de por qué cada distractor es incorrecto

### Formato de Rúbricas (Preguntas Abiertas)

Para cada pregunta abierta:
- **Rúbrica:** Criterios de evaluación con puntos asignados
- **Solución modelo:** Respuesta completa esperada con ejemplos de código cuando aplica

---

## Ajustes Recomendados (Ninguno)

Tras la validación exhaustiva, **no se requieren ajustes**. Ambos exámenes cumplen con todos los criterios de aceptación:

1. ✅ Estructura correcta (5 MCQ + 3 abiertas = 50 pts)
2. ✅ Formato LaTeX consistente con el guía
3. ✅ Cobertura equilibrada de objetivos de aprendizaje
4. ✅ Dificultad comparable al examen guía
5. ✅ Originalidad (no copias literales)
6. ✅ Distractores plausibles y bien diseñados
7. ✅ Soluciones y claves incluidas
8. ✅ Claridad y precisión en enunciados
9. ✅ Lenguaje inclusivo sin sesgos

---

## Resumen de Archivos Entregables

1. **examen_A.tex** - Examen alternativo A (50 pts)
2. **examen_B.tex** - Examen alternativo B (50 pts)
3. **VALIDACION.md** - Este documento de validación

---

## Enlaces Consultados de Unit7.md

Durante el diseño de preguntas, se consultaron los siguientes recursos referenciados en la unidad:

1. **Video: How does a GPU work?**
   - URL: https://youtu.be/h9Z4oGN89MU
   - Conceptos: Arquitectura GPU, procesamiento paralelo, render pipeline básico

2. **Video: Graphics Pipeline (detallado)**
   - URL: https://youtu.be/C8YtdC8mxTU
   - Conceptos: Etapas del pipeline, vertex/fragment shaders, transformaciones, Z-buffer

3. **Tutorial: Introducing Shaders (OpenFrameworks)**
   - URL: https://openframeworks.cc/ofBook/chapters/shaders.html
   - Conceptos: GLSL, uniforms, attributes, ejemplos de código, interactividad

Estos recursos informaron el diseño de preguntas, distractores y soluciones modelo para garantizar alineación con el material de la unidad.

---

**Fecha de creación:** Mayo 2025
**Versión:** 1.0
**Preparado por:** GitHub Copilot Agent
