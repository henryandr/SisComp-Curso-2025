# Unidad 4: Estructuras de datos

# **Introducción 📜**

En esta unidad vas a aprender sobre estructuras de datos. Las estructuras de datos son formas de organizar y almacenar datos en una computadora para que puedan ser utilizados de manera eficiente. Inicialmente, vamos a analizar juntos cómo se implementa la estructura de datos llamada lista enlazada. Luego te propondré un problema con una nueva estructura de datos que tendrás que analizar por cuenta propia y luego implementar con esta una aplicación creativa interactiva.

# **¿Qué aprenderás en esta unidad? 💡**

Aprenderás sobre estructuras de datos y cómo puedes aplicarlas para construir aplicaciones creativas interactivas.

Seguirás trabajando con C++, pero esta vez utilizarás un framework de programación creativa llamado openFrameworks.

# **Investigación 🔎**

# **Actividad 1: Visualizando listas enlazadas con openFrameworks**

En esta actividad vamos a analizar juntos una aplicación creativa interactiva que utiliza una lista enlazada para solucionar un reto creativo.

Puedes descargar openFrameworks desde [**este enlace](https://openframeworks.cc/download/).**

El código de nuestro caso de estudio es este:

`ofApp.cpp`:

```cpp
#include "ofApp.h"
//--------------------------------------------------------------
void ofApp::setup() {    
		backgroundHue = 0;
    // Inicializa la serpiente con varios nodos en el centro    
    for (int i = 0; i < 20; i++) {        
		    snake.emplace_back(ofGetWidth() / 2, ofGetHeight() / 2);    
		    }
		}
//--------------------------------------------------------------
void ofApp::update() {
    glm::vec2 target = glm::vec2(ofGetMouseX(), ofGetMouseY());    
    float interpolationFactor = 0.2;  
    // controla la velocidad de movimiento (0-1)
    for (auto& pos : snake) {        
		    pos = glm::mix(glm::vec3(pos, 0.0f), glm::vec3(target, 0.0f), 0.2); 
		    // Se mueve gradualmente        
		    target = pos;  
		    // Cada nodo sigue al anterior    
		    }
    backgroundHue = fmod(backgroundHue + 0.1, 255);
    }
//--------------------------------------------------------------
void ofApp::draw() {    
		// Fondo dinámico con gradiente    
		ofColor color1 = ofColor::fromHsb(backgroundHue, 150, 240);    
		ofColor color2 = ofColor::fromHsb(fmod(backgroundHue + 128, 255), 150, 240);    
		ofBackgroundGradient(color1, color2, OF_GRADIENT_LINEAR);

    // curva suave conectando los nodos    
    if (snake.size() > 1) {        
		    ofMesh mesh;        
		    mesh.setMode(OF_PRIMITIVE_LINE_STRIP);        
		    int index = 0;        
		    for (const auto& pos : snake) {            
				    float hue = ofMap(index++, 0, snake.size() - 1, 0, 255);            
				    mesh.addColor(ofColor::fromHsb(hue, 200, 255));            
				    mesh.addVertex(glm::vec3(pos, 0.0f));        
				    }        
				ofSetLineWidth(2);        
				mesh.draw();    
				}
    // Círculos con tamaño y color variable    
    int index = 0;    
    ofNoFill();    
    ofSetLineWidth(2);    
    for (const auto& pos : snake) {        
		    float hue = ofMap(index, 0, snake.size() - 1, 0, 255);        
		    ofSetColor(ofColor::fromHsb(hue, 220, 255));        
		    float radius = ofMap(index++, 0, snake.size() - 1, 20, 5);        
		    ofDrawCircle(pos.x, pos.y, radius);    
		    }
}
//--------------------------------------------------------------
void ofApp::keyPressed(int key) {    
		if (key == 'c') {        
				snake.clear();    
				}    
		else if (key == 'a') {        
				snake.emplace_back(ofRandomWidth(), ofRandomHeight());  
				}  
		else if (key == 'r') {        
				if (!snake.empty()) {            
						snake.pop_back();        
						}
			  }  
	  else if (key == 's') {    
			  ofSaveFrame();  
			  }
		}
```

`ofApp.h`:

```cpp
#pragma once
#include "ofMain.h"
#include <list>
class ofApp : public ofBaseApp {
		public:    
				std::list<glm::vec2> snake;    
				float backgroundHue;
		    void setup();    
		    void update();    
		    void draw();    
		    void keyPressed(int key);
		    };
```

`main.cpp`:

```cpp
#include "ofMain.h"
#include "ofApp.h"
//========================================================================
int main( ){
		//Use ofGLFWWindowSettings for more options like multi-monitor fullscreen  
		ofGLWindowSettings settings;  
		settings.setSize(1024, 768);  
		settings.windowMode = OF_WINDOW; //can also be OF_FULLSCREEN
	  auto window = ofCreateWindow(settings);
	  ofRunApp(window, make_shared<ofApp>());  
	  ofRunMainLoop();
}
```

# **Actividad 2: Implementación de la lista en enlazada**

En la actividad anterior te mostré cómo se utiliza una lista enlazada, en esta actividad la vamos a implementar de cero para que veas cómo funciona.

`ofApp.h`:

```cpp
#pragma once
#include "ofMain.h"
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
		    ~LinkedList() {        
				    clear();    
				    }
		    void push_back(glm::vec2 pos) {        
				    Node* newNode = new Node(pos);        
				    if (head == nullptr) {            
						    head = tail = newNode;        
						    }        
						else {            
								tail->next = newNode;            
								tail = newNode;        
								}        
						size++;    
						}
    void pop_back() {        
		    if (head == nullptr) 
				    return;
        if (head == tail) { 
		        // Si solo hay un elemento            
		        delete head;            
		        head = tail = nullptr;        
		        }        
		    else {            
				    Node* temp = head;            
				    while (temp->next != tail) {                
						    temp = temp->next;            
						    }            
						delete tail;            
						tail = temp;            
						tail->next = nullptr;        
						}        
				size--;    
				}
    void clear() {        
		    Node* current = head;        
		    while (current != nullptr) {            
				    Node* nextNode = current->next;            
				    delete current;            
				    current = nextNode;        
				    }        
				head = tail = nullptr;        
				size = 0;    
				}
		};

class ofApp : public ofBaseApp {
		public:    
				LinkedList snake;    
				float backgroundHue;
		    void setup();    
		    void update();    
		    void draw();    
		    void keyPressed(int key);
		    };
```

`ofApp.cpp`:

```cpp
#include "ofApp.h"
//--------------------------------------------------------------
void ofApp::setup() {    
		backgroundHue = 0;
    // Inicializa la serpiente con varios nodos en el centro    
    for (int i = 0; i < 20; i++) {        
		    snake.push_back(glm::vec2(ofGetWidth() / 2, ofGetHeight() / 2));    
		    }
		}
//--------------------------------------------------------------
void ofApp::update() {    
		if (snake.head == nullptr) 
				return;
    glm::vec2 target = glm::vec2(ofGetMouseX(), ofGetMouseY());    
    float interpolationFactor = 0.2;
    Node* current = snake.head;    
    while (current != nullptr) {        
		    // glm::mix(x, y, a)        
		    // mix performs a linear interpolation x and y using a to weight between them.    
		    // The value is computed as x * (1 - a) + y * a.        
		    current->position = glm::mix(glm::vec3(current->position, 0.0f), glm::vec3(target, 0.0f), interpolationFactor);        
		    target = current->position;        current = current->next;    
		    }
    backgroundHue = fmod(backgroundHue + 0.1, 255);
    }
//--------------------------------------------------------------
void ofApp::draw() {    
		ofColor color1 = ofColor::fromHsb(backgroundHue, 150, 240);    
		ofColor color2 = ofColor::fromHsb(fmod(backgroundHue + 128, 255), 150, 240);    
		ofBackgroundGradient(color1, color2, OF_GRADIENT_LINEAR);
    if (snake.head == nullptr) 
		    return;
    ofMesh mesh;    
    mesh.setMode(OF_PRIMITIVE_LINE_STRIP);    
    Node* current = snake.head;    
    int index = 0;
    while (current) {        
		    float hue = ofMap(index++, 0, snake.size - 1, 0, 255);        
		    mesh.addColor(ofColor::fromHsb(hue, 200, 255));        
		    mesh.addVertex(glm::vec3(current->position, 0.0f));        
		    current = current->next;    
		    }
    ofSetLineWidth(2);    
    mesh.draw();
    // Círculos con tamaño y color variable    
    current = snake.head;    
    index = 0;    
    ofNoFill();    
    ofSetLineWidth(2);
    while (current) {        
		    float hue = ofMap(index, 0, snake.size - 1, 0, 255);        
		    ofSetColor(ofColor::fromHsb(hue, 220, 255));        
		    float radius = ofMap(index++, 0, snake.size - 1, 20, 5);        
		    ofDrawCircle(current->position.x, current->position.y, radius);        
		    current = current->next;    
		    }
		}
//--------------------------------------------------------------
void ofApp::keyPressed(int key) {    
		if (key == 'c') {        
				snake.clear();    
				}    
		else if (key == 'a') {        
				snake.push_back(glm::vec2(ofRandomWidth(), ofRandomHeight()));    
				}    
		else if (key == 'r') {        
				snake.pop_back();    
				}    
		else if (key == 's') {        
				ofSaveFrame();    
				}
		}
```

Para entender mejor el código anterior te voy a proponer que veas un par de simulaciones.

Para esta parte:

```cpp
Node* current = snake.head;
while (current != nullptr) {    
		current->position = glm::mix(glm::vec3(current->position, 0.0f), glm::vec3(target, 0.0f), interpolationFactor);    
		target = current->position;    
		current = current->next;
		}
```

[https://editor.p5js.org/hhenrya/full/iYRvvhm-c](https://editor.p5js.org/hhenrya/full/iYRvvhm-c)

Y para entender mejor el manejo del color:

Tono (H)

Saturación (S)

Brillo (B)

[https://editor.p5js.org/hhenrya/full/le5Ocxbba](https://editor.p5js.org/hhenrya/full/le5Ocxbba)

# **Actividad 3**

Ahora te voy a pedir que regreses a la actividad anterior y experimentes con ella. La idea es que uses el depurador y observes cómo funcionan las diferentes partes del código. A medida que tengas dudas me puedes llamar para que discutamos juntos.

# **Aplicación 🛠**

# **Actividad 4:** En esta actividad te toca a ti analizar una estructura de datos e implementarla.

Implementarás una cola (FIFO - First In, First Out) para crear un efecto de pintura dinámica en la pantalla. Cada vez que el usuario mueve el mouse, se agregará un trazo en la pantalla, pero los trazos más antiguos en la cola tendrán menos opacidad.

Te preguntarás ¿Cómo funciona una FIFO? Puedes pensar en una fila para comprar el almuerzo en la cafetería. La primera persona en llegar es la primera en ser atendida. De manera similar, en una cola FIFO, los elementos se procesan en el orden en que fueron añadidos. Los primeros en ingresar son los primeros en salir, son los más antiguos.

Tu tarea es implementar la estructura de datos BrushQueue y completar el código de ofApp.cpp donde faltan fragmentos clave. ¿Cómo? Lo primero es que analices de nuevo cómo implementamos la lista enlazada y luego transfieras ese conocimiento a la implementación de la cola FIFO. No olvides que el primer dato en entrar es el primero en salir (FIFO).

## **REQUISITOS**

1. Implementar una cola (`BrushQueue`) desde cero **sin usar** `std::queue` ni `std::list`. La idea es que implementes desde cero la estructura de datos.
2. Cada nodo de la cola debe almacenar:
    - La posición (x, y) del trazo.
    - El radio del trazo.
    - El color del trazo.
    - La opacidad del trazo.
3. Funciones obligatorias en `BrushQueue`:
    - `enqueue(x, y, radius, color, opacity)`: agregar un nuevo trazo.
    - `dequeue()`: eliminar el trazo más antiguo cuando se alcance el tamaño máximo.
    - `clear()`: eliminar todos los trazos.
    - `isEmpty()`: indicar si la cola está vacía.
4. Comportamiento del programa:
    - Cuando el usuario mueve el mouse, se debe agregar un nuevo trazo con un color aleatorio.
    - Cuando el usuario presiona ‘c’, se deben borrar todos los trazos de la pantalla.
    - Cuando el usuario presiona ‘a’, se debe alternar entre una cola de tamaño 50 y 100.
5. Debes gestionar correctamente la memoria para evitar fugas.

**Código base (con fragmentos faltantes)**:

ofApp.h:

```cpp
#pragma once
#include "ofMain.h"
// Nodo de la cola
struct Node {    
		float x, y;    
		float radius;    
		ofColor color;    
		float opacity;    
		Node* next;
    Node(float _x, float _y, float _radius, ofColor _color, float _opacity): x(_x), y(_y), radius(_radius), color(_color), opacity(_opacity), next(nullptr) {    }
    };
// Implementación manual de una cola (FIFO)
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
		    bool isEmpty();};

// Constructor
BrushQueue::BrushQueue(int _maxSize) : front(nullptr), rear(nullptr), size(0), maxSize(_maxSize) {}
// Destructor
BrushQueue::~BrushQueue() {    
		clear();
		}
// Implementa aquí `enqueue()`
void BrushQueue::enqueue(float x, float y, float radius, ofColor color, float opacity) {    
		// TODO: crear un nuevo nodo y agregarlo al final de la cola.    
		// Si la cola supera `maxSize`, eliminar el nodo más antiguo con `dequeue()`.
		}
// Implementa aquí `dequeue()`
void BrushQueue::dequeue() {    
		// TODO: eliminar el nodo más antiguo si la cola no está vacía.
		}
// Implementa aquí `clear()`
void BrushQueue::clear() {    
		// TODO: eliminar todos los nodos de la cola.
		}
// Implementa aquí `isEmpty()`
bool BrushQueue::isEmpty() {    
		// TODO: retornar si la cola está vacía.
		}

class ofApp : public ofBaseApp {
		public:    
				BrushQueue strokes; // Cola de trazos    
				float backgroundHue = 0;
		    ofApp() : strokes(50) {} // Tamaño máximo de la cola
		    void setup();    
		    void update();    
		    void draw();    
		    void keyPressed(int key);
		    };
```

ofApp.cpp:

```cpp
#include "ofApp.h"
//--------------------------------------------------------------
void ofApp::setup() {    
		ofBackground(0);
		}
//--------------------------------------------------------------
void ofApp::update() {    
		backgroundHue += 0.2;    
		if (backgroundHue > 255) 
				backgroundHue = 0;
    // TODO: agregar un nuevo trazo si el mouse está presionado.    
    // Usa strokes.enqueue(x, y, radius, color, opacity);
    }
//--------------------------------------------------------------
void ofApp::draw() {    
		// Fondo con gradiente dinámico    
		ofColor color1, color2;    
		color1.setHsb(backgroundHue, 150, 240);    
		color2.setHsb(fmod(backgroundHue + 128, 255), 150, 240);    
		ofBackgroundGradient(color1, color2, OF_GRADIENT_LINEAR);
    // TODO: dibujar los trazos almacenados en la cola.    
    // Recorre los nodos desde strokes.front hasta nullptr y usa ofDrawCircle().
    }
//--------------------------------------------------------------
void ofApp::keyPressed(int key) {    
		if (key == 'c') {        
				// TODO: limpiar la cola de trazos.    
				}    
		if (key == 'a') {        
				// TODO: alternar entre 50 y 100 trazos.    
				}    
		else if (key == 's') {        
				// TODO: guardar el frame actual.    
				}
		}
```

**Resultado esperado**:

maxSize = 50

![maxSize 50](https://juanferfranco.github.io/computacionales-2025-20/_astro/u4a3-1.gn4iFGJa_ZJwWvq.webp)

maxSize = 100

![maxSize 100](https://juanferfranco.github.io/computacionales-2025-20/_astro/u4a3-2.NLf5x_AB_SynTO.webp)

En este video puedes ver cómo debería funcionar la aplicación:

[**Video de demostración**](https://youtu.be/VRDRZTKPTx8)

# **Evidencias 🗂️**

**RUBRICA!**
• El plazo máximo de entrega es el **viernes 13 de marzo hasta las 18.00** momento en el cual se se procede a realizar la evaluación por parte del profesor. Pasado ese momento, si no entregas la nota es 0. En este espacio es fundamental tu asistencia para realizar la evaluación de tu trabajo con el profesor.
• Debe estar todo el código que permita ejecutar la aplicación en cualquier momento. Si tu código no reproduce lo que se muestra en el video la nota será 0.
• Si no se entrega un video de la aplicación la nota es 0, aunque se entregue el código que lo reproduzca.
• Si el video no abre o no es visible la nota es 0.

| **Escala de evaluación** | **Nota** |
| --- | --- |
| El código cumple con todo, implementa la FIFO sin bibliotecas y gestiona correctamente la memoria | 5 |
| El código cumple con todo e implementa la FIFO sin bibliotecas | 4 |
| El código cumple con todo, pero se implementa CON bibliotecas la FIFO | 3 |
| El código funciona pero no lograste reproducir la funcionalidad solicitada | 2 |
| El código reproduce parcialmente la funcionalidad solicitada1El código no compila o no lo entregas | 0 |

**EVIDENCIAS EN BITÁCORA**
Debes entregar un enlace, OJO un enlace, a un video no lista de youtube con las siguientes restricciones:

1. La calidad mínima del video debe ser 1080p.
2. Inicia mostrando que tu aplicación compila sin errores.
3. Ejecuta la aplicación y demuestra el cambio de tamaño de la cola, borrar los trazos y salvar un frame.
4. Debes rellenar en el archivo bitacora.md los códigos de `ofApp.cpp`, `ofApp.h` y `main.cpp`:
Es importante que verifiques que el código que entregas en la bitácora funciona de nuevo si creas un nuevo proyecto en openFrameworks y copias y pegas el código.

# **¿Qué aprendiste? 🤔**

Una vez termines esta unidad invierte en ti unos minutos para reflexionar sobre tu proceso de aprendizaje.

1. En una hoja de papel construye un diagrama donde coloques todos los conceptos que aprendiste en esta unidad y en las unidades anteriores. Relaciona los conceptos nuevos entre ellos y con los anteriores. Este es un ejercicio de práctica de recuperación que te servirá para fortalecer tu memoria a largo plazo.
2. ¿Qué hiciste bien en esta unidad que debes continuar haciendo?
3. ¿Qué deberías comenzar a hacer para mejorar tu proceso?