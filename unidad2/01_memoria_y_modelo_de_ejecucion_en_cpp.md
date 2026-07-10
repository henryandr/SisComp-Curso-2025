# Unidad 2 · Memoria, objetos y estructuras de datos en C++

En esta unidad comenzarás a usar C++ como laboratorio para observar cómo viven los datos en memoria, cómo cambian cuando pasan por funciones y cómo se relacionan el código, el stack, el heap y los objetos. La meta no es memorizar sintaxis aislada, sino construir un modelo mental que te permita explicar qué está ocurriendo dentro del programa mientras se ejecuta.

## Sesión 1. Entorno, depuración y formas de paso a funciones

### ¿Qué aprenderás en esta sesión? 💡

- Compilar y ejecutar un programa básico en C++.
- Usar breakpoints y ejecución paso a paso.
- Diferenciar paso por valor, referencia y puntero.
- Relacionar cada forma de paso con el cambio —o no— de la variable original.

### Actividad 1: Primer programa en C++

Vas a familiarizarte con el entorno de trabajo y con el flujo básico de compilar, ejecutar y depurar.

1. Abre Visual Studio.
2. Crea un proyecto de consola en C++.
3. Abre el archivo que contiene `main`.
4. Ejecuta el programa base y luego reemplázalo por este ejemplo:

```cpp
#include <iostream>

int sum(int a, int b) {
    return a + b;
}

int main() {
    int a = 5;
    int b = 7;
    std::cout << "La suma de " << a << " y " << b << " es " << sum(a, b) << "\n";
}
```

5. Coloca un breakpoint en la línea donde se declara `a`.
6. Ejecuta con depuración y avanza paso a paso con `F10`.
7. Observa en las ventanas `Autos` o `Locals` cómo aparecen y cambian las variables.

<aside>
📤

**Bitácora**

- Explica para qué sirve un breakpoint.
- Describe qué información te muestra la ventana `Autos`.
- Indica en qué momento entra la ejecución a la función `sum` y qué valores recibe.

</aside>

### Actividad 2: Paso por valor, referencia y puntero

Analiza y ejecuta el siguiente programa:

```cpp
#include <iostream>
using namespace std;

void modificarPorValor(int n) {
    cout << "Dentro de modificarPorValor: " << n << endl;
    n += 5;
    cout << "Modificado por valor: " << n << endl;
}

void modificarPorReferencia(int& n) {
    cout << "Dentro de modificarPorReferencia: " << n << endl;
    n += 5;
    cout << "Modificado por referencia: " << n << endl;
}

void modificarPorPuntero(int* n) {
    cout << "Dentro de modificarPorPuntero: " << *n << endl;
    *n += 5;
    cout << "Modificado por puntero: " << *n << endl;
}

int main() {
    int a = 10;
    int b = 10;
    int c = 10;

    modificarPorValor(a);
    modificarPorReferencia(b);
    modificarPorPuntero(&c);

    cout << a << ", " << b << ", " << c << endl;
}
```

Antes de ejecutarlo, predice qué valor tendrá cada variable al regresar a `main`.

### Ideas clave

- **Paso por valor:** la función trabaja con una copia.
- **Paso por referencia:** la función trabaja con un alias de la variable original.
- **Paso por puntero:** la función recibe una dirección y modifica el dato apuntado.

<aside>
📤

**Bitácora**

- Escribe tu predicción antes de ejecutar.
- Compara el resultado de `a`, `b` y `c` al final del programa.
- Explica por qué `&c` y `*n` aparecen juntos en el caso del puntero.
- Resume cuándo conviene usar cada mecanismo.

</aside>

## Sesión 2. Mapa de memoria de un programa en C++

### ¿Qué aprenderás en esta sesión? 💡

- Identificar las regiones principales de memoria de un proceso.
- Distinguir código, datos globales, stack y heap.
- Relacionar ubicación en memoria con tiempo de vida.
- Leer direcciones de variables para construir un mapa conceptual.

### Actividad 3: Dibuja el mapa de memoria de un programa

Piensa en la memoria de un programa como una organización por zonas:

```text
+-------------------------------+
| Segmento de código            |
+-------------------------------+
| Globales y estáticas          |
+-------------------------------+
| Heap                          |
| (memoria dinámica)            |
+-------------------------------+
| Stack                         |
| (variables locales)           |
+-------------------------------+
```

Ahora analiza este programa:

```cpp
#include <iostream>
using namespace std;

int global_inicializada = 42;
int global_no_inicializada;
const char* const mensaje_ro = "Hola, memoria";

void funcionConStatic() {
    static int var_estatica = 100;
    cout << "var_estatica: " << &var_estatica << endl;
}

int* crearArrayHeap(int tam) {
    int* arr = new int[tam];
    for (int i = 0; i < tam; i++) {
        arr[i] = i;
    }
    return arr;
}

int suma(int a, int b) {
    int c = a + b;
    return c;
}

int main() {
    int a = 10;
    int b = 20;
    int c = suma(a, b);
    int* arrayHeap = crearArrayHeap(5);

    cout << &a << endl;
    cout << &b << endl;
    cout << &c << endl;
    cout << &global_inicializada << endl;
    cout << &global_no_inicializada << endl;
    cout << static_cast<const void*>(mensaje_ro) << endl;
    cout << arrayHeap << endl;

    funcionConStatic();
    delete[] arrayHeap;
}
```

### Actividad 4: Observa y clasifica

Ejecuta el programa anterior y clasifica cada elemento:

- `main` y `suma`
- `global_inicializada`
- `global_no_inicializada`
- `var_estatica`
- `a`, `b`, `c`
- `arrayHeap`
- el bloque de memoria apuntado por `arrayHeap`
- el literal de texto `"Hola, memoria"`

<aside>
📤

**Bitácora**

- Construye tu propio mapa de memoria del programa.
- Explica por qué `arrayHeap` y el arreglo dinámico no están en la misma región de memoria.
- Indica qué datos desaparecen automáticamente al salir de `main` y cuáles requieren liberación explícita.
- Describe qué significa que una variable `static` “recuerde” su valor.

</aside>
