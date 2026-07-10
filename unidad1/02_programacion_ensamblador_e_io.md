# Unidad 1 · Arquitectura del computador y programación en ensamblador

## Sesión 3. Instrucciones, ALU, registros, saltos y control de flujo en Hack

### Actividad 3: Explorando la arquitectura del computador Hack

Ahora vamos a analizar juntos el siguiente programa. Este programa tendrá todos los conceptos que vamos investigar en la siguiente fase de la unidad de manera más profunda. En qué nos enfocaremos:

- Las partes del computador Hack.
- El modelo de programación de la CPU.
- La diferencia entre memoria RAM y registros.
- Los tipos de instrucciones del lenguaje ensamblador.
- Cómo leo el teclado y muestro en pantalla.
- Cómo implemento un bucle.
- Cómo implemento una condición.
- ¿Qué es la ALU y qué operaciones realiza?

En [**“este”**](https://www.nand2tetris.org/_files/ugd/44046b_7ef1c00a714c46768f08c459a6cab45a.pdf) enlace está la documentación del computador Hack.

```nasm
@SCREEN
D=A
@i
M=D

(READKEYBOARD)
@KBD
D=M
@KEYPRESSED
D;JNE
@i
D=M
@SCREEN
D=D-A
@READKEYBOARD
D;JLE
@i
M=M-1
A=M
M=0
@READKEYBOARD
0;JMP

(KEYPRESSED)
@i
D=M
@KBD
D=D-A
@READKEYBOARD
D;JGE
@i
A=M
M=-1
@i
M=M+1
@READKEYBOARD
0;JMP
```

<aside>
🧐

**🧪✍️ Experimento**
Ahora experimenta.

Crea un archivo llamado `program.asm` y copia el código del programa anterior. Ejecuta paso a paso el programa en el [**simulador**](https://nand2tetris.github.io/web-ide/cpu) así:

- Carga el programa en el simulador.
- Antes de ejecutar cada instrucción vas a predecir qué crees que va a suceder. Es muy importante que hagas esto, de esta manera tu mismo puedes saber si estás entendiendo el programa.
- Luego, ejecuta la instrucción y observa el resultado.
- Si te equivocas, reflexiona sobre por qué tu predicción no fue correcta.
</aside>

<aside>
📤

**Bitácora**
Reporta en tu bitácora de aprendizaje:

- Identifica una instrucción que use la ALU y explica qué hace.
- ¿Para qué sirve el registro PC?
- ¿Cuál es la diferencia entre @i y @READKEYBOARD?
- Describe qué se necesita para leer el teclado y mostrar información en la pantalla.
- Identifica un bucle en el programa y explica su funcionamiento.
- Identifica una condición en el programa y explica su funcionamiento.
</aside>

### Actividad 4: Control de flujo con saltos

Vamos a resolver juntos este problema:

Escribe un programa que compare el valor almacenado en la dirección de memoria 5 con el valor 10. Si el valor es menor que 10, guarda el valor 1 en la dirección 7. Si el valor es mayor o igual a 10, guarda el valor 0 en la dirección 7.

<aside>
📤

**Bitácora**

- Escribe tu mismo el programa.
- Simula paso a paso. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
</aside>

## Sesión 4. Memoria mapeada, pantalla, teclado y programas interactivos simples

### Actividad 5: Implementando un ciclo simple

Vamos a resolver juntos este problema:

“Crea un programa que use un ciclo para sumar los números del 1 al 5 y guarde el resultado en la dirección de memoria 12.”

<aside>
📤

**Bitácora**

- Escribe tu mismo el programa.
- Simula paso a paso. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
</aside>

### Actividad integrada: Dibujando un punto en la pantalla

Vamos a resolver juntos este problema:

La pantalla del computador Hack se controla a través de un mapa de memoria que comienza en la dirección 16384 (SCREEN). Cada bit en este mapa de memoria representa un pixel en la pantalla (1 = negro, 0 = blanco). Escribe un programa que dibuje un punto negro en la esquina superior izquierda de la pantalla. (Recuerda que la esquina superior izquierda corresponde al primer bit del primer word en la dirección SCREEN).

Traduce este programa a lenguaje C++ para que relaciones cómo los conceptos de alto nivel se traducen a bajo nivel.

<aside>
📤

**Bitácora**

- Escribe tu mismo ambos programas.
- Simula paso a paso el programa en ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
</aside>

### Actividad integrada: Dibujando una línea horizontal

Vamos a resolver juntos este problema:

Modifica el programa anterior para que dibuje una línea horizontal negra de 16 pixeles de largo en la esquina superior izquierda de la pantalla. (Recuerda que cada word en la memoria representa 16 pixeles).

Traduce este programa a lenguaje C++ para que relaciones cómo los conceptos de alto nivel se traducen a bajo nivel.

<aside>
📤

**Bitácora**

- Escribe tu mismo los programas.
- Simula paso a paso el programa ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
</aside>

### Actividad integrada: Entrada salida interactiva

Modifica el programa de la actividad anterior de tal manera que puedas mover la línea horizontal de derecha a izquierda usando las teclas **d** e **i** respectivamente. Tu programa no tiene que verificar si la línea se sale de la pantalla.

Traduce este programa a lenguaje C++ para que relaciones cómo los conceptos de alto nivel se traducen a bajo nivel.

<aside>
📤

**Bitácora**

- Escribe los programas.
- Simula paso a paso en lenguaje ensamblador. Recuerda la metodología: predice, ejecuta, observa y reflexiona.
</aside>
