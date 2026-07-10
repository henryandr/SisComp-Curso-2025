# Unidad 1 · Arquitectura del computador y programación en ensamblador

El objetivo de esta unidad es que puedas comprender la arquitectura de un computador digital moderno. Para ello usaremos como caso de estudio un computador simple, pero didáctico llamado computador Hack. Programarás este computador utilizando su lenguaje ensamblador y desarrollarás programas simples, pero interactivos que harán uso de operaciones de entrada/salida.

## Sesión 1. Arquitectura básica del computador

### ¿Qué aprenderás en esta sesión? 💡

- Comprender la arquitectura de un computador.
- Conocer el lenguaje ensamblador.
- Desarrollar programas interactivos simples.
- Manipular la memoria.
- Realizar operaciones aritmético-lógicas.
- Controlar el flujo de un programa.
- Manejar la entrada y salida de datos.

### Actividad 1: el curso Nand2Tetris

El curso **Nand2Tetris** es un proyecto educativo creado por **Noam Nisan** y **Shimon Schocken** en el que los estudiantes construyen, paso a paso, una computadora completa a partir de compuertas lógicas básicas (`“nand”`) hasta llegar a ejecutar programas y juegos (`“tetris”`). A lo largo del curso se diseñan el hardware, el lenguaje de máquina, el ensamblador, el sistema operativo mínimo y un lenguaje de alto nivel, proporcionando una visión integral de cómo funcionan realmente las computadoras por dentro. Su objetivo principal es **cerrar la brecha entre la teoría y la práctica**, ofreciendo una experiencia de aprendizaje concreta y gradual que permite entender de forma profunda y accesible los fundamentos de la computación.

En esta primera actividad nos vamos a centrar en el Proyecto 4 del curso. Exploremos juntos este proyecto. Ingresa a este [**link**](https://www.nand2tetris.org/) y revisemos la documentación.

![Figura 1. Página principal del curso Nand2Tetris](image.png)

Figura 1. Página principal del curso Nand2Tetris

## Arquitectura de un computador moderno

En un computador moderno, como el Hack del curso Nand2Tetris, la **CPU** es el “cerebro” que ejecuta instrucciones realizando operaciones aritméticas y lógicas, y controlando el flujo del programa. Observa la figura 2 como referencia.

![Figura 2. Arquitectura de un computador. Fuente: Nand to Tetris / [www.nand2tetris.org](http://www.nand2tetris.org/) / Chapter 4 / Copyright © Noam Nisan and Shimon Schocken](image%201.png)

Figura 2. Arquitectura de un computador. Fuente: Nand to Tetris / [www.nand2tetris.org](http://www.nand2tetris.org/) / Chapter 4 / Copyright © Noam Nisan and Shimon Schocken

La CPU se comunica con la **memoria** (donde se almacenan tanto los datos como el programa) a través de **buses de datos** y **buses de direcciones**: los primeros transportan los valores que se leen o escriben, y los segundos indican en qué posición de memoria se realiza esa operación. Estos mismos buses conectan a la CPU y la memoria con los **periféricos de entrada y salida**, como el teclado (entrada) y la pantalla (salida) en Hack, permitiendo que el computador reciba información del exterior y muestre resultados. En conjunto, la arquitectura se basa en que la CPU lee instrucciones y datos desde memoria, los procesa y se comunica mediante los buses con los periféricos para interactuar con el usuario.

## Sesión 2. Modelo Hack y ciclo fetch-decode-execute

### Actividad 2: Ciclo fetch-decode-execute

El siguiente programa está escrito en el lenguaje ensamblador del computador Hack. Este computador no es un computador comercial, sino un computador didáctico que te permitirá acercarte a los conceptos fundamentales de manera amigable.

Analiza el siguiente programa (está en lenguaje ensamblador).

```nasm
			@1
			D=A
			@2
			D=D+A
			@16
			M=D
(END)
			@END
			0;JMP
```

**¿Qué crees que haga este programa?**

Para responder a esta pregunta vamos a analizarlo paso a paso usando un simulador de la CPU Hack que está [**aquí**](https://nand2tetris.github.io/web-ide/cpu).

Para ejecutar este programa la CPU realiza un **ciclo** constante llamado Fetch-Decode-Execute.

El ciclo Fetch-Decode-Execute describe cómo la CPU ejecuta instrucciones de un programa. Aquí está explicado de forma breve y simple:

**Fetch (buscar):** la CPU obtiene (lee) la siguiente instrucción desde la memoria. El contador de programa (PC) indica dónde se encuentra esa instrucción en la memoria ROM.

**Decode (decodificar):** la CPU interpreta la instrucción que acaba de leer. Esto significa entender qué operación debe realizarse y qué datos o recursos necesita.

**Execute (ejecutar):** la CPU realiza la operación indicada. Por ejemplo, puede ser una operación matemática, mover datos entre registros, o acceder a la memoria.

Este ciclo se repite continuamente mientras la computadora esté encendida, procesando instrucciones una tras otra. Es la base del funcionamiento de cualquier procesador.

<aside>
🧐

**🧪✍️ Experimento**
Ahora es tu turno. Crea un archivo llamado `program.asm` y copia el código del programa anterior. Ejecuta el programa en el simulador de la CPU Hack y observa cómo se comporta. ¿Qué sucede? ¿Qué valor se almacena en la dirección de memoria 16? ¿Por qué crees que es ese valor? ¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute? ¿Qué cambios observas en el contenido de la memoria y los registros? ¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute?

</aside>

<aside>
🧐

**🧪✍️ Experimento**
Escribe un programa en lenguaje ensablador que sume los números 5 y 10, y almacene el resultado en la dirección de memoria 20. Utiliza el simulador de la CPU Hack para ejecutar tu programa y verifica que el resultado es correcto.

</aside>

<aside>
📤

**Bitácora**
Reporta tus observaciones para cada experimento en tu bitácora de aprendizaje.
¿Qué diferencia hay entre los datos almacenados en la memoria ROM y en la RAM?

</aside>
