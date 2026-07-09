# Unidad 2: De Alto Nivel a Ensamblador

# **Introducción 📜**

En esta unidad descubrirás cómo se traducen algunos conceptos fundamentales de la programación en alto nivel, como condicionales, ciclos, punteros y arreglos, a lenguaje ensamblador. Utilizarás el lenguaje Hack de la unidad anterior para implementar estos conceptos. Esta unidad servirá como puente para la siguiente unidad, donde exploraremos algunos conceptos fundamentales utilizando el lenguaje de programación C++.

# **¿Qué aprenderás en esta unidad? 💡**

En esta unidad aprenderás la relación entre el lenguaje ensamblador y un lenguaje de alto nivel como C++. Aprenderás a traducir conceptos de alto nivel a bajo nivel, y viceversa. Además, desarrollarás programas que implementan estos conceptos en el lenguaje ensamblador del computador Hack. Vas a explorar estos conceptos usando el simulador del Hack. Y por favor, **SIEMPRE SIMULA** y aplica la metodología de predice, ejecuta, observa y reflexiona.

# **Actividad 1: Dibujando un punto en la pantalla**

Vamos a resolver juntos este problema:

La pantalla del computador Hack se controla a través de un mapa de memoria que comienza en la dirección 16384 (SCREEN). Cada bit en este mapa de memoria representa un pixel en la pantalla (1 = negro, 0 = blanco). Escribe un programa que dibuje un punto negro en la esquina superior izquierda de la pantalla. (Recuerda que la esquina superior izquierda corresponde al primer bit del primer word en la dirección SCREEN).

Traduce este programa a lenguaje C++ para que relaciones cómo los conceptos de alto nivel se traducen a bajo nivel.

<aside>
📤

**Bitácora**

- Escribe tu mismo ambos programas.
- Simula paso a paso el programa en ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
</aside>

# **Actividad 2: Dibujando una línea horizontal**

Vamos a resolver juntos este problema:

Modifica el programa anterior para que dibuje una línea horizontal negra de 16 pixeles de largo en la esquina superior izquierda de la pantalla. (Recuerda que cada word en la memoria representa 16 pixeles).

Traduce este programa a lenguaje C++ para que relaciones cómo los conceptos de alto nivel se traducen a bajo nivel.

<aside>
📤

**Bitácora**

- Escribe tu mismo los programas.
- Simula paso a paso el programa ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
</aside>

# **Actividad 3: Entrada salida interactiva**

Modifica el programa de la actividad anterior de tal manera que puedas mover la línea horizontal de derecha a izquierda usando las teclas **d** e **i** respectivamente. Tu programa no tiene que verificar si la línea se sale de la pantalla.

Traduce este programa a lenguaje C++ para que relaciones cómo los conceptos de alto nivel se traducen a bajo nivel.

<aside>
📤

**Bitácora**

- Escribe los programas.
- Simula paso a paso en lenguaje ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
</aside>

# **Investigación 🔎**

# **Actividad 4: Convierte un ciclo while en un ciclo for**

**Enunciado**: considera el siguiente programa:

```cpp
//Adds 1+...+100. int i=1; int sum=0;
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

# **Actividad 5: Punteros**

Un puntero es una variable que almacena la dirección de memoria de otra variable. Observa el siguiente programa escrito en C++:

```cpp
int a = 10;
int* p;
p = &a;
*p = 20;
```

El programa anterior modifica el contenido de la variable **`a`** por medio de la variable **`p`**. **`p`**es un puntero porque almacena la dirección de memoria de la variable **`a`**. En este caso el valor de la variable **`a`** será 20 luego de ejecutar `*p = 20;`.

Ahora analiza con detenimiento:

- ¿Cómo se **declara** un puntero en C++?

`int* p;`

**p** es una variable que almacenará la dirección de otra variable. Dicha variable almacenará número enteros.

- ¿Cómo se **define** (nota que antes preguntamos cómo se **declara**) un puntero en C++?

`p = &a;.`

Definir el puntero es **inicializar** el valor del puntero, es decir, guardar la dirección de una variable. En este caso p contendrá la dirección de a o podemos decir que p apunta a **`a`**

- ¿Cómo se almacena en C++ la dirección de memoria de una variable? Con el operador **`&`**.

`p = &a;`

- ¿Cómo se escribe el contenido de la variable a la que apunta un puntero? Con el operador `*`.
- `p = 20;`

En este caso como **`p`** contiene la dirección de **`a`**. Por tanto, se está modificando el valor de la variable **`a`** por medio de **`p`**.

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

el código anterior hace que el valor de b cambie de 5 a 10 porque `p` apunta a **`a`** y con `*p` a la derecha del igual estás leyendo el contenido de la variable apuntada.

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

# **Aplicación 🛠**

# **Actividad 6: Experimenta con arreglos**

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
- Considera que los datos del arreglo están almacenados **desde** la dirección 16. Inicializa el arreglo en lenguaje ensamblador.
- Simula paso a paso el programa en ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
- Construye tu programa PASO A PASO mediante pruebas. Indica qué característica vas a implementar con cada prueba y cómo la probaste.
- Muestra el programa final y cómo lo probaste.
</aside>

# **Consolidación y metacognición 🤔**

# **Actividad 7: Autoevaluación**

**Mirando hacia adentro: autoevaluación de conceptos y proceso**

El objetivo de esta actividad es que recuperes de tu memoria los conceptos que conectan la programación de alto nivel con el lenguaje ensamblador. Al forzarte a recordar sin ver tus notas (práctica de recuperación), estás fortaleciendo las conexiones neuronales de ese conocimiento. Además, reflexionarás sobre tu proceso para convertirte en un aprendiz más consciente y estratégico.

<aside>
📤

**Bitácora**
Sin consultar tus apuntes, código previo o el simulador, responde a las siguientes preguntas con tus propias palabras. La meta es el esfuerzo por recordar, no la perfección.
**Parte 1: recuperación de conocimiento (Retrieval Practice)**
1. Explica cómo se representa y manipula un puntero en el lenguaje ensamblador de Hack. Describe las operaciones equivalentes a `p = &a` (asignar dirección) y `*p = 20` (escribir a través del puntero) usando instrucciones de ensamblador.
2. ¿Cómo implementarías el acceso a un elemento de un arreglo, como `arr[j]`, en lenguaje ensamblador? Describe el rol de la dirección base del arreglo y el índice `j` en esta operación.
**Parte 2: reflexión sobre tu proceso (Metacognición)**
1. ¿Cuál fue el concepto más abstracto o difícil de “traducir” de C++ a ensamblador en esta unidad (punteros, ciclos, arreglos)? ¿Qué hiciste para lograr entenderlo?
2. En la Actividad 06 se sugirió construir el programa “PASO A PASO mediante pruebas”. ¿Cómo te ayudó este enfoque a manejar la complejidad del problema?
3. Esta unidad fue el “puente” hacia C++. ¿Qué concepto de bajo nivel te sientes más seguro de poder identificar cuando lo veas implementado en C++?

</aside>

# **Actividad 8: Coeveluación**

**Aprendiendo juntos: coevaluación constructiva**

En esta actividad vas a revisar la actividad 06 de tu compañero. Vas a simular paso a paso su programa y dejarle comentarios constructivos. Recuerda que todo lo harás en tu propia bitácora de aprendizaje y luego compartirás lo que registraste con tu compañero.

<aside>
📤

**Bitácora**

- Copia la url de la bitácora revisada.
- Copia el programa de tu compañero.
- Describe detalladamente qué pruebas vas a realizar para saber si el programa funciona correctamente.
- Reporta los resultados de las pruebas.
</aside>