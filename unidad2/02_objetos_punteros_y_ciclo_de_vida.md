# Unidad 2 · Memoria, objetos y estructuras de datos en C++

## Sesión 3. Experimentos sobre segmentos de memoria

### ¿Qué aprenderás en esta sesión? 💡

- Contrastar el comportamiento de distintas regiones de memoria.
- Formular hipótesis antes de ejecutar programas.
- Reconocer riesgos conceptuales como escritura inválida, referencias colgantes y fugas.
- Conectar observación experimental con el mapa de memoria.

### Actividad 5: Experimentos guiados sobre memoria

A partir del programa de la sesión anterior, realiza pequeños cambios y observa qué ocurre. No busques “hacer que funcione”; busca explicar el resultado.

#### Experimento A: variable local estática vs. no estática

```cpp
#include <iostream>
using namespace std;

void prueba() {
    static int contadorEstatico = 0;
    int contadorLocal = 0;
    contadorEstatico++;
    contadorLocal++;
    cout << contadorEstatico << ", " << contadorLocal << endl;
}

int main() {
    prueba();
    prueba();
    prueba();
}
```

#### Experimento B: reserva dinámica y liberación

```cpp
#include <iostream>
using namespace std;

int main() {
    int* p = new int(25);
    cout << *p << endl;
    delete p;
}
```

#### Experimento C: dirección de una variable local al salir de una función

```cpp
#include <iostream>
using namespace std;

int* direccionInvalida() {
    int local = 10;
    return &local;
}

int main() {
    int* p = direccionInvalida();
    cout << p << endl;
}
```

<aside>
📤

**Bitácora**

- Antes de ejecutar cada experimento, escribe tu hipótesis.
- Explica qué datos persisten entre llamadas y cuáles no.
- Describe por qué devolver la dirección de una variable local es conceptualmente peligroso.
- Resume qué diferencias observaste entre stack, datos estáticos y heap.

</aside>

## Sesión 4. Objetos en stack y heap; copia y paso de objetos

### ¿Qué aprenderás en esta sesión? 💡

- Distinguir objetos automáticos y dinámicos.
- Observar qué significa copiar un objeto en C++.
- Comparar paso por valor, referencia y puntero usando objetos.
- Relacionar constructores y destructores con el ciclo de vida de los datos.

### Actividad 6: Crear un objeto en el stack y observarlo

```cpp
#include <iostream>
using namespace std;

class Punto {
public:
    int x;
    int y;

    Punto(int _x, int _y) : x(_x), y(_y) {
        cout << "Constructor: Punto(" << x << ", " << y << ") creado." << endl;
    }

    ~Punto() {
        cout << "Destructor: Punto(" << x << ", " << y << ") destruido." << endl;
    }
};

int main() {
    Punto p(10, 20);
}
```

Ejecuta en depuración y observa:

- el momento en que se construye `p`
- la dirección de memoria de `p`
- el momento en que su destructor se ejecuta

### Actividad 7: Compara stack y heap

```cpp
#include <iostream>
using namespace std;

class Punto {
public:
    int x;
    int y;

    Punto(int _x, int _y) : x(_x), y(_y) {}
    ~Punto() {}
};

int main() {
    Punto pStack(30, 40);
    Punto* pHeap = new Punto(50, 60);
    delete pHeap;
}
```

Analiza qué es exactamente `pStack` y qué es exactamente `pHeap`.

### Actividad 8: Copia y paso de objetos

```cpp
#include <iostream>
#include <string>
using namespace std;

class Punto {
public:
    string nombre;
    int x;
    int y;

    Punto(string n, int _x, int _y) : nombre(n), x(_x), y(_y) {}
};

void cambiarNombrePorValor(Punto p, string nuevoNombre) {
    p.nombre = nuevoNombre;
}

void cambiarNombrePorReferencia(Punto& p, string nuevoNombre) {
    p.nombre = nuevoNombre;
}

void cambiarNombrePorPuntero(Punto* p, string nuevoNombre) {
    p->nombre = nuevoNombre;
}

int main() {
    Punto original("original", 70, 80);
    cambiarNombrePorValor(original, "valor");
    cambiarNombrePorReferencia(original, "referencia");
    cambiarNombrePorPuntero(&original, "puntero");
}
```

<aside>
📤

**Bitácora**

- Explica en qué caso el objeto original cambia y en cuál no.
- Dibuja el caso de copia por valor y compáralo con alias por referencia.
- Describe la diferencia entre “objeto” y “puntero a objeto”.
- Escribe una conclusión breve sobre qué significa copiar un objeto en C++.

</aside>

## Sesión 5. Miembros estáticos y ciclo de vida de los objetos

### ¿Qué aprenderás en esta sesión? 💡

- Diferenciar datos propios de cada instancia y datos compartidos por la clase.
- Observar el orden de construcción y destrucción.
- Relacionar alcance, duración y destrucción automática.
- Explicar por qué algunos objetos se destruyen al salir de un bloque y otros no.

### Actividad 9: Miembros estáticos frente a miembros de instancia

```cpp
#include <iostream>
using namespace std;

class Contador {
public:
    int valor;
    static int total;

    Contador(int v = 0) : valor(v) {
        total++;
    }

    void incrementar() {
        valor++;
    }
};

int Contador::total = 0;

int main() {
    Contador c1(5);
    Contador c2(10);
    Contador* c3 = new Contador(15);

    c1.incrementar();
    c2.incrementar();
    c3->incrementar();

    delete c3;
}
```

### Actividad 10: Ciclo de vida dentro y fuera de bloques

```cpp
#include <iostream>
using namespace std;

class Punto {
public:
    Punto(int, int) { cout << "constructor" << endl; }
    ~Punto() { cout << "destructor" << endl; }
};

int main() {
    {
        Punto pBloque(100, 200);
    }

    Punto* pDinamico = new Punto(300, 400);
    delete pDinamico;
}
```

Luego modifica el programa para declarar un puntero fuera de un bloque e inicializarlo dentro del bloque. Analiza por qué el puntero puede seguir existiendo aunque el bloque termine, y por qué eso no significa lo mismo que la vida del objeto al que apunta.

<aside>
📤

**Bitácora**

- Explica dónde vive `Contador::total` y dónde vive `valor`.
- Describe el ciclo de vida de `c1`, `c2` y el objeto apuntado por `c3`.
- Compara destrucción automática y destrucción manual.
- Explica con tus palabras qué significa que un puntero siga existiendo pero el objeto ya no exista.

</aside>
