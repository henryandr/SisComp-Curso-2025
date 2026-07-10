# Unidad 2 · Memoria, objetos y estructuras de datos en C++

## Sesión 6. Listas enlazadas como objetos dinámicos en memoria

### ¿Qué aprenderás en esta sesión? 💡

- Comprender la estructura de una lista enlazada.
- Relacionar nodos, punteros y memoria dinámica.
- Implementar operaciones básicas sobre una lista.
- Observar una estructura lineal en un contexto visual.

### Actividad 11: Analiza una lista enlazada en una aplicación interactiva

En esta sesión usarás openFrameworks para observar cómo una colección dinámica puede controlar un comportamiento visual. Analiza este fragmento:

```cpp
#include <list>

std::list<glm::vec2> snake;

for (int i = 0; i < 20; i++) {
    snake.emplace_back(ofGetWidth() / 2, ofGetHeight() / 2);
}
```

Y luego este recorrido:

```cpp
glm::vec2 target = glm::vec2(ofGetMouseX(), ofGetMouseY());
for (auto& pos : snake) {
    pos = glm::mix(glm::vec3(pos, 0.0f), glm::vec3(target, 0.0f), 0.2);
    target = pos;
}
```

Preguntas guía:

- ¿Por qué cada nodo “sigue” al anterior?
- ¿Qué representa cada elemento de `snake`?
- ¿Qué ventaja tiene una estructura dinámica frente a un arreglo fijo en este caso?

### Actividad 12: Implementa la lista enlazada manualmente

Ahora reemplaza `std::list` por una implementación propia:

```cpp
class Node {
public:
    glm::vec2 position;
    Node* next;

    Node(glm::vec2 pos) : position(pos), next(nullptr) {}
};

class LinkedList {
public:
    Node* head;
    Node* tail;
    int size;

    LinkedList() : head(nullptr), tail(nullptr), size(0) {}
    ~LinkedList() { clear(); }

    void push_back(glm::vec2 pos);
    void pop_back();
    void clear();
};
```

Implementa y prueba al menos estas operaciones:

- `push_back`
- `pop_back`
- `clear`
- recorrido desde `head` hasta `nullptr`

<aside>
📤

**Bitácora**

- Dibuja la lista después de agregar 1, 2 y 3 nodos.
- Explica qué cambia en memoria cuando insertas al final.
- Explica qué enlaces cambian cuando eliminas el último nodo.
- Justifica por qué el destructor de la lista debe liberar memoria.

</aside>

## Sesión 7. Colas FIFO y comportamiento interactivo

### ¿Qué aprenderás en esta sesión? 💡

- Diferenciar lista enlazada y cola FIFO.
- Implementar `enqueue`, `dequeue`, `clear` e `isEmpty`.
- Aplicar una estructura lineal a una experiencia visual.
- Diseñar una política de entrada y salida de datos en el tiempo.

### Actividad 13: Implementa una cola de trazos

Construirás una cola (`BrushQueue`) para generar una pintura dinámica: cada nuevo trazo entra al final y, cuando se supera un tamaño máximo, el más antiguo sale primero.

Requisitos mínimos:

1. Implementar la cola sin `std::queue` ni `std::list`.
2. Cada nodo debe almacenar posición, radio, color y opacidad.
3. La aplicación debe:
   - agregar trazos cuando el usuario interactúa
   - limpiar la cola con una tecla
   - alternar entre dos tamaños máximos
4. Debes gestionar correctamente la memoria.

Estructura sugerida:

```cpp
struct Node {
    float x, y;
    float radius;
    ofColor color;
    float opacity;
    Node* next;
};

class BrushQueue {
public:
    Node* front;
    Node* rear;
    int size;
    int maxSize;

    BrushQueue(int _maxSize);
    ~BrushQueue();
    void enqueue(float x, float y, float radius, ofColor color, float opacity);
    void dequeue();
    void clear();
    bool isEmpty();
};
```

### Actividad 14: Compara dos políticas de estructura

Compara tu lista enlazada de la sesión anterior con la cola FIFO de esta sesión.

- ¿En cuál operación está centrada cada estructura?
- ¿Qué datos necesitas conservar para que `enqueue` y `dequeue` sean simples?
- ¿Qué comportamiento visual cambia si quitas el elemento más nuevo en lugar del más antiguo?

<aside>
📤

**Bitácora**

- Explica con tus palabras la regla FIFO.
- Muestra el pseudocódigo de `enqueue` y `dequeue`.
- Justifica por qué `front` y `rear` simplifican la implementación.
- Describe cómo comprobaste que no quedaban nodos sin liberar.

</aside>
