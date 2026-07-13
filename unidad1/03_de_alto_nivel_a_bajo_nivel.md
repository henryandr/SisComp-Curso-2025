# Unidad 1 · Arquitectura del computador y programación en ensamblador

En esta etapa descubrirás cómo se traducen algunos conceptos fundamentales de la programación en alto nivel, como condicionales, ciclos, punteros y arreglos, a lenguaje ensamblador. Utilizarás el lenguaje Hack de las sesiones anteriores para implementar estos conceptos. Esta parte de la unidad sirve como puente para la siguiente unidad, donde exploraremos algunos conceptos fundamentales utilizando el lenguaje de programación C++.

Aprenderás la relación entre el lenguaje ensamblador y un lenguaje de alto nivel como C++. Aprenderás a traducir conceptos de alto nivel a bajo nivel, y viceversa. Además, desarrollarás programas que implementan estos conceptos en el lenguaje ensamblador del computador Hack. Vas a explorar estos conceptos usando el simulador del Hack. Y por favor, **SIEMPRE SIMULA** y aplica la metodología de predice, ejecuta, observa y reflexiona.

## Sesión 5. Traducción de ciclos y condicionales entre C++ y ensamblador

### Actividad integrada: Convierte un ciclo while en un ciclo for

**Enunciado**: considera el siguiente programa:

```cpp
//Adds 1+...+100.
int i=1;
int sum=0;
while(i <=100)
{
	sum += i;
	i++;
}
```

Una traducción a ensamblador es como sigue:

```nasm
// Adds1+...+100.
@i // i refers to some memory location.
M=1 // i=1
@sum // sum refers to some memory location.
M=0 // sum=0
(LOOP)
@i D=M // D=i
@100
D=D-A // D=i-100
@END
D;JGT // If(i-100)>0 goto END
@i
D=M // D=i
@sum
M=D+M // sum=sum+i
@i
M=M+1 // i=i+1
@LOOP
0;JMP // Goto LOOP
(END)
@END
0;JMP // Infinite loop
```

Vamos a transformar este programa a su equivalente usando un ciclo for:

```cpp
//Adds 1+...+100.
int sum=0;
for(int i = 1; i <=100; i++){
	sum+= i;
	}
```

- Analiza los programas con while y for asegúrate de entender por qué son equivalentes.
- Convierte la versión del for a ensamblador.
- No olvides comprobar el funcionamiento de los programas en ensamblador en el simulador.
- Compara las versiones en ensamblador del while y del for. ¿Qué puedes concluir?

<aside>
📤

**Bitácora**
Escribe en tu bitácora el programa en ensamblador y las conclusiones que has sacado de la comparación entre los dos programas.

</aside>

## Sesión 6. Punteros, arreglos y relación entre direcciones de memoria y código de alto nivel

### Actividad integrada: Punteros

Un puntero es una variable que almacena la dirección de memoria de otra variable. Observa el siguiente programa escrito en C++:

```cpp
int a = 10;
int* p;
p = &a;
*p = 20;
```

El programa anterior modifica el contenido de la variable **`a`** por medio de la variable **`p`**. **`p`**es un puntero porque almacena la dirección de memoria de la variable **`a`**. En este caso el valor de la variable **`a`** será 20 luego de ejecutar `*p = 20;`.

Ahora analiza con detenimiento:

- ¿Cómo se **declara** un puntero en C++?

`int* p;`

**p** es una variable que almacenará la dirección de otra variable. Dicha variable almacenará número enteros.

- ¿Cómo se **define** (nota que antes preguntamos cómo se **declara**) un puntero en C++?

`p = &a;.`

Definir el puntero es **inicializar** el valor del puntero, es decir, guardar la dirección de una variable. En este caso p contendrá la dirección de a o podemos decir que p apunta a **`a`**

- ¿Cómo se almacena en C++ la dirección de memoria de una variable? Con el operador **`&`**.

`p = &a;`

- ¿Cómo se escribe el contenido de la variable a la que apunta un puntero? Con el operador `*`.
- `*p = 20;`

En este caso como **`p`** contiene la dirección de **`a`**. Por tanto, se está modificando el valor de la variable **`a`** por medio de **`p`**.

Ahora vas a usar un puntero para leer la posición de memoria a la que este apunta, es decir, vas a leer por medio del puntero la variable cuya dirección está almacenada en él.

```cpp
int a = 10;
int b = 5;
int *p;
p = &a;
b = *p;
```

En este caso:

`b = *p;`

el código anterior hace que el valor de b cambie de 5 a 10 porque `p` apunta a **`a`** y con `*p` a la derecha del igual estás leyendo el contenido de la variable apuntada.

<aside>
📤

**Bitácora**
Convierte estos programas a ensamblador y realiza la simulación paso a paso. Recuerda la metodología: predice, ejecuta, observa y reflexiona.

```cpp
int a = 10;
int* p;
p = &a;
*p = 20;

int a = 10;
int b = 5;
int *p;
p = &a;
b = *p;
```

</aside>

### Actividad integrada: Experimenta con arreglos

Los arreglos son colecciones de datos en la memoria.

Considera el siguiente programa

```cpp
int arr[] = {11,233,23,77,112,61,67,98,900,810};
int sum = 0;
for (int j = 0; j < 10; j++) {
	sum = sum + arr[j];
	}
```

<aside>
📤

**Bitácora**

- Implementa el programa anterior en lenguaje ensamblador aplicando el concepto de punteros.
- Considera que los datos del arreglo están almacenados **desde** la dirección 16. Inicializa el arreglo en lenguaje ensamblador.
- Simula paso a paso el programa en ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
- Construye tu programa PASO A PASO mediante pruebas. Indica qué característica vas a implementar con cada prueba y cómo la probaste.
- Muestra el programa final y cómo lo probaste.
</aside>

## Sesión 7. Evaluación parcial teórica

### Autoevaluación

**Mirando hacia adentro: autoevaluación de conceptos y proceso**

El objetivo de esta actividad es doble. Primero, que puedas recuperar de tu memoria los conceptos fundamentales de la unidad sin ayuda de tus notas. Este proceso de “recordar” es una de las formas más efectivas de fortalecer tu memoria a largo plazo. Segundo, que reflexiones sobre *cómo* has aprendido, para que puedas identificar qué estrategias te funcionan mejor.

<aside>
📤

**Bitácora**
**Sin consultar tus apuntes**, el simulador o cualquier otro material, responde con tus propias palabras a las siguientes preguntas. ¡No te preocupes por la perfección! El objetivo es ver qué recuerdas ahora mismo.

**Parte 1: recuperación de conocimiento (retrieval practice)**
1. Describe con tus palabras las tres fases del ciclo Fetch-Decode-Execute. ¿Qué rol juega el Program Counter (PC) en este ciclo?
2. ¿Cuál es la diferencia fundamental entre una instrucción-A (que empieza con `@`) y una instrucción-C (que involucra `D`, `M`, `A`, etc.) en el lenguaje ensamblador de Hack? Da un ejemplo de cada una.
3. Explica la función de los siguientes componentes del computador Hack: el registro D, el registro A y la ALU.
4. ¿Cómo se implementa un salto condicional en Hack? Describe un ejemplo (p. ej., saltar si el valor de D es mayor que cero).
5. ¿Cómo se implementa un loop en el computador Hack? Describe un ejemplo (p. ej., un loop que decremente un valor hasta que llegue a cero).
6. ¿Cuál es la diferencia entre la instrucción `D=M` y la instrucción `M=D`?
7. Describe brevemente qué se necesita para leer un valor del teclado (`KBD`) y para “pintar” un pixel en la pantalla (`SCREEN`).
8. Explica cómo se representa y manipula un puntero en el lenguaje ensamblador de Hack. Describe las operaciones equivalentes a `p = &a` (asignar dirección) y `*p = 20` (escribir a través del puntero) usando instrucciones de ensamblador.
9. ¿Cómo implementarías el acceso a un elemento de un arreglo, como `arr[j]`, en lenguaje ensamblador? Describe el rol de la dirección base del arreglo y el índice `j` en esta operación.

**Parte 2: reflexión sobre tu proceso (metacognición)**
1. ¿Cuál fue el concepto o actividad más desafiante de esta unidad para ti y por qué?
2. La metodología de “predecir, ejecutar, observar y reflexionar” fue central en nuestras actividades. ¿En qué momento esta metodología te resultó más útil para entender algo que no tenías claro?
3. Describe un momento “¡Aha!” que hayas tenido durante esta unidad. ¿Qué estabas haciendo cuando ocurrió?
4. Pensando en la próxima unidad, ¿qué harás diferente en tu proceso de estudio para aprender de manera más efectiva?
5. ¿Cuál fue el concepto más abstracto o difícil de “traducir” de C++ a ensamblador en esta unidad (punteros, ciclos, arreglos)? ¿Qué hiciste para lograr entenderlo?
6. En la actividad de arreglos se sugirió construir el programa “PASO A PASO mediante pruebas”. ¿Cómo te ayudó este enfoque a manejar la complejidad del problema?
7. ¿Qué concepto de bajo nivel te sientes más seguro de poder identificar cuando lo veas implementado en C++?

</aside>

### Coevaluación

**Aprendiendo juntos: coevaluación constructiva**

Ahora es el momento de aprender de un compañero. La coevaluación es una herramienta poderosa que te permite ver otras perspectivas y aprender a dar retroalimentación constructiva, una habilidad clave. El objetivo no es calificar, sino ayudar a tu compañero a mejorar.

<aside>
📤

**Bitácora**
1. Encuentra un compañero de trabajo.
2. Intercambien las URLs de sus bitácoras de aprendizaje.
3. Lee las entradas de tu compañero correspondientes a los ejercicios de arquitectura, simulación del computador Hack, control de flujo y traducción de programas entre C++ y ensamblador.
4. Utilizando la rúbrica de la unidad, evalúa cada actividad y deja un comentario de retroalimentación *por cada criterio*. Recuerda ser específico y constructivo. Tu feedback debe ayudar a tu compañero a identificar sus fortalezas y áreas de oportunidad. Todos estos comentarios los dejarás en tu propia bitácora.
5. Simula paso a paso al menos uno de los programas de tu compañero y describe detalladamente qué pruebas realizaste para saber si el programa funciona correctamente.
6. Reporta los resultados de las pruebas y comparte tus comentarios con tu compañero.

</aside>
