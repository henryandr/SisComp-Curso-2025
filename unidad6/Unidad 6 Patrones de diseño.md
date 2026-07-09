# Unidad 6: Patrones de diseño

# **Introducción 📜**

En la unidad anterior conectamos con los cursos anteriores relacionados con la programación orientada a objetos. En esta unidad conectaremos con un curso posterior a este: S***cripting***. Lo que haremos es explorar algunos patrones de diseño que ayudarán a estructurar el código de manera más eficiente y mantenible, y por tanto, facilitará el trabajo en equipo.

# **¿Qué aprenderás en esta unidad? 💡**

Vas a estudiar en detalle tres patrones de diseño: Observer, Factory y State. Estos patrones son soluciones comprobadas a problemas comunes en el diseño de software orientado a objetos.

# **Investigación 🔎**

# **Actividad 1: Enunciado**

En esta actividad inicial, configurarás y ejecutarás un caso de estudio desarrollado en openFrameworks que utiliza los patrones de diseño Observer, Factory y State. Tu objetivo es familiarizarte con la aplicación, observar su comportamiento e interactuar con ella.

Crea un nuevo proyecto en openFrameworks, adiciona el siguiente código, ejecútalo y explora la aplicación.

ofApp.h:

```cpp
#pragma once
#include "ofMain.h"
#include <string>
#include <vector>
class Observer {
public:  
		virtual ~Observer() = default;  
		virtual void onNotify(const std::string & event) = 0;
		};
class Subject {
public:  
		void addObserver(Observer * observer);  
		void removeObserver(Observer * observer);
protected:  
		void notify(const std::string & event);
private:  
		std::vector<Observer *> observers;
		};
		
class Particle;

class State {
public:  
		virtual ~State() = default;  
		virtual void update(Particle * particle) = 0;  
		virtual void onEnter(Particle * particle) { }  
		virtual void onExit(Particle * particle) { }
		};
		
class Particle : public Observer {
public:  
		Particle();  
		~Particle() override;
	  Particle(const Particle &) = delete;  
	  Particle & operator=(const Particle &) = delete;
	  void update();  
	  void draw();  
	  void onNotify(const std::string & event) override;
	  void setState(State * newState);
	  ofVec2f position;  
	  ofVec2f velocity;  
	  float size;  
	  ofColor color;
private:  
		void keepInsideWindow();  
		State * state;
		};
		
class NormalState : public State {
public:  
		void update(Particle * particle) override;  
		void onEnter(Particle * particle) override;
		};
		
class AttractState : public State {
public:  
		void update(Particle * particle) override;
		};
		
class RepelState : public State {
public:  
		void update(Particle * particle) override;
		};
		
class StopState : public State {
public:  
		void update(Particle * particle) override;
		};
class ParticleFactory {
public:  
		static Particle * createParticle(const std::string & type);
		};
class ofApp : public ofBaseApp, public Subject {
public:  
		~ofApp() override;  
		void setup() override;  
		void update() override;  
		void draw() override;  
		void keyPressed(int key) override;
private:  
	std::vector<Particle *> particles;
	};
```

ofApp.cpp:

```cpp
#include "ofApp.h"
#include <algorithm>
void Subject::addObserver(Observer * observer) {  
		if (!observer) return;  
		if (std::find(observers.begin(), observers.end(), observer) == observers.end()) {    
				observers.push_back(observer);  
				}
		}
		
void Subject::removeObserver(Observer * observer) {  
		if (!observer) return;  
		observers.erase(std::remove(observers.begin(), observers.end(), observer), observers.end());
		}
void Subject::notify(const std::string & event) {  
		for (Observer * observer : observers) {    
				observer->onNotify(event);  
				}
		}
Particle::Particle()  : state(nullptr) {  
		position = ofVec2f(ofRandomWidth(), ofRandomHeight());  
		velocity = ofVec2f(ofRandom(-0.5f, 0.5f), ofRandom(-0.5f, 0.5f));  
		size = ofRandom(2.0f, 5.0f);  
		color = ofColor(255);
	  state = new NormalState();  
	  state->onEnter(this);
	  }
	  
Particle::~Particle() {  
		if (state) {    
				state->onExit(this);    
				delete state;    
				state = nullptr;  
				}
		}
void Particle::setState(State * newState) {  
		if (state) {    
				state->onExit(this);    
				delete state;  
				}  
		state = newState;  
		if (state) {    
				state->onEnter(this);  
				}
		}
void Particle::update() {  
		if (state) {    
				state->update(this);  
				}  
		keepInsideWindow();
		}
void Particle::draw() {  
		ofPushStyle();  
		ofSetColor(color);  
		ofDrawCircle(position, size);  
		ofPopStyle();
		}
void Particle::onNotify(const std::string & event) {  
		if (event == "attract") {    
				setState(new AttractState());  
				} 
		else if (event == "repel") {    
				setState(new RepelState());  
				} 
		else if (event == "stop") {    
				setState(new StopState());  
				} 
		else if (event == "normal") {    
				setState(new NormalState());  
				}
		}
void Particle::keepInsideWindow() {  
		const float W = static_cast<float>(ofGetWidth());  
		const float H = static_cast<float>(ofGetHeight());
	  if (position.x < 0.0f) {    
			  position.x = 0.0f;    
			  velocity.x *= -1.0f;  
			  } 
		else if (position.x > W) {    
				position.x = W;    
				velocity.x *= -1.0f;  
				}  
		if (position.y < 0.0f) {    
				position.y = 0.0f;    
				velocity.y *= -1.0f;  
				} 
		else if (position.y > H) {    
				position.y = H;    
				velocity.y *= -1.0f;  
				}
		}
void NormalState::onEnter(Particle * particle) {  
		particle->velocity.set(ofRandom(-0.5f, 0.5f), ofRandom(-0.5f, 0.5f));
		}
void NormalState::update(Particle * particle) {  
		particle->position += particle->velocity;
		}
static void steer(Particle * particle, const ofVec2f & toward, float accel, float vmax, float posScale) {  
		ofVec2f dir = toward - particle->position;  
		float len = dir.length();  
		if (len > 1e-6f) {    
				dir /= len;    
				particle->velocity += dir * accel;  
				}  
		particle->velocity.limit(vmax);  
		particle->position += particle->velocity * posScale;
		}
void AttractState::update(Particle * particle) {  
		ofVec2f mouse(ofGetMouseX(), ofGetMouseY());  
		steer(particle, mouse, /*accel*/ 0.05f, /*vmax*/ 3.0f, /*posScale*/ 0.2f);
		}
void RepelState::update(Particle * particle) {  
		ofVec2f mouse(ofGetMouseX(), ofGetMouseY());  
		ofVec2f away = particle->position - mouse;  
		float len = away.length();  
		if (len > 1e-6f) {    
				away /= len;    
				particle->velocity += away * 0.05f;  
				}  
		particle->velocity.limit(3.0f);  
		particle->position += particle->velocity * 0.2f;
		}
void StopState::update(Particle * particle) {  
		particle->velocity *= 0.80f;  
		if (particle->velocity.lengthSquared() < 1e-4f) {    
				particle->velocity.set(0.0f, 0.0f);  
				}  
		particle->position += particle->velocity;
		}
Particle * ParticleFactory::createParticle(const std::string & type) {  
		Particle * particle = new Particle();
	  if (type == "star") {    
			  particle->size = ofRandom(2.0f, 4.0f);    
			  particle->color = ofColor(255, 0, 0);  
			  } 
		else if (type == "shooting_star") {    
				particle->size = ofRandom(3.0f, 6.0f);    
				particle->color = ofColor(0, 255, 0);    
				particle->velocity *= 3.0f;  
				} 
		else if (type == "planet") {    
				particle->size = ofRandom(5.0f, 8.0f);    
				particle->color = ofColor(0, 0, 255);  
				}  
		return particle;
		}
ofApp::~ofApp() {  
		for (Particle * p : particles) {    
				removeObserver(p);    
				delete p;  
				}  
		particles.clear();
		}
void ofApp::setup() {  
		ofBackground(0);  
		particles.reserve(100 + 5 + 10);
	  for (int i = 0; i < 100; ++i) {    
			  Particle * p = ParticleFactory::createParticle("star");    
			  particles.push_back(p);    
			  addObserver(p);  
			  }  
		for (int i = 0; i < 5; ++i) {    
				Particle * p = ParticleFactory::createParticle("shooting_star");    
				particles.push_back(p);    
				addObserver(p);  
				}  
		for (int i = 0; i < 10; ++i) {    
				Particle * p = ParticleFactory::createParticle("planet");    
				particles.push_back(p);    
				addObserver(p);  
				}
		}
void ofApp::update() {  
		for (Particle * p : particles) {    
				p->update();  
				}
		}
void ofApp::draw() {  
		for (Particle * p : particles) {    
				p->draw();  
				}
		}
void ofApp::keyPressed(int key) {  
		switch (key) {  
				case 's':    
						notify("stop");    
						break;  
				case 'a':    
						notify("attract");    
						break;  
				case 'r':    
						notify("repel");    
						break;  
				case 'n':    
						notify("normal");    
						break;  
				default:    
					break;  
					}
			}
```

<aside>
📤

**🧐🧪✍️ Reporta en tu bitácora**
1. ¿Cómo puedes interactuar con la aplicación? Menciona específicamente las teclas y qué efecto parecen tener sobre las partículas.
2. ¿Observas los diferentes tipos de “partículas”? ¿Se comportan todas igual inicialmente?
3. Toma algunas capturas de pantalla de la aplicación en diferentes momentos (estado inicial, después de presionar ‘a’, ‘r’, ‘s’, ‘n’) y añádelas a tu bitácora.
4. ¿Qué crees que está pasando “detrás de cámaras” cuando presionas las teclas? Formula una hipótesis inicial sobre cómo la aplicación cambia el comportamiento de las partículas.

</aside>

# **Actividad 2: Investiga el patrón observer**

**Enunciado**
En esta actividad, profundizarás en el patrón de diseño `Observer`. Analizarás su propósito, estructura y cómo está implementado en el caso de estudio que exploraste en la actividad anterior. El objetivo es que comprendas cómo este patrón permite la comunicación entre objetos de forma desacoplada.

**Concepto del Patrón Observer**

Imagina que quieres recibir notificaciones de una tienda online cuando tu producto favorito vuelve a estar en stock. En lugar de revisar la página web constantemente (polling), te suscribes a las notificaciones. Cuando el producto está disponible, la tienda (el *Sujeto* u *Observable*) envía automáticamente un mensaje a todos los *Observadores* suscritos (como tú).

El patrón Observer define una dependencia uno-a-muchos entre objetos, de manera que cuando un objeto (el Sujeto) cambia su estado, todos sus dependientes (Observadores) son notificados y actualizados automáticamente.

Componentes clave:

- **Subject (Sujeto):** mantiene una `lista de Observadores`. Proporciona métodos para agregar (`attach`/`addObserver`), eliminar (`detach`/`removeObserver`) y notificar (`notify`) a los observadores.
- **Observer (Observador):** define una interfaz de actualización (`update`/`onNotify`) que será llamada cuando el Sujeto cambie.
- **ConcreteSubject (Sujeto Concreto):** almacena el estado de interés y envía notificaciones a sus observadores cuando su estado cambia.
- **ConcreteObserver (Observador Concreto):** implementa la interfaz Observer. Almacena una referencia al Sujeto Concreto (opcional) y reacciona a la notificación actualizando su propio estado.

**Análisis del caso de estudio**

Vuelve al código del caso de estudio (`ofApp.h` y `ofApp.cpp`).

1. **Identifica los Roles:**
    - ¿Qué clase actúa como la interfaz `Observer`? ¿Qué método define?
    - ¿Qué clase actúa como `Subject`? ¿Qué métodos proporciona para gestionar observadores y notificar?
    - ¿Qué clase es el `ConcreteSubject` en esta aplicación? ¿Por qué? (Pista: ¿Quién *envía* las notificaciones?)
    - ¿Qué clase(s) actúan como `ConcreteObserver`? ¿Por qué? (Pista: ¿Quién *recibe* y *reacciona* a las notificaciones?)
2. **Sigue el flujo de notificación:**
    - Localiza el método `keyPressed` en `ofApp.cpp`. ¿Qué sucede cuando se presiona la tecla ‘a’? ¿Qué método se llama?
    - Ve al método `notify` en la clase `Subject`. ¿Qué hace este método?
    - Localiza el método que implementa la interfaz `Observer` en la clase `Particle` (`onNotify`). ¿Qué hace este método cuando recibe el evento “attract”?
3. **Registro y eliminación de observadores:**
    - ¿En qué parte del código se añaden las instancias de `Particle` como observadores de `ofApp`? (Busca dónde se llama a `addObserver`).
    - Aunque no se usa explícitamente en este ejemplo simple, ¿Dónde se eliminarían los observadores si fuera necesario (por ejemplo, si una partícula se destruyera durante la ejecución)? (Busca `removeObserver`). ¿Por qué es importante el destructor de `ofApp` en este contexto?

<aside>
📤

**🧐🧪✍️ Reporta en tu bitácora**
1. Explica con tus propias palabras el propósito del patrón Observer. ¿Qué problema resuelve?
2. Dibuja un diagrama que muestre la relación entre `Subject`, `Observer`, `ofApp` y `Particle` en el caso de estudio, indicando quién es el Sujeto y quiénes los Observadores.
3. Construye un diagrama de secuencia que muestre cómo funciona el patrón Observer al presionar una tecla.
4. ¿Qué ventajas crees que ofrece usar el patrón Observer en esta aplicación en comparación con, por ejemplo, que `ofApp::update` recorriera todas las partículas y les dijera directamente que cambien su comportamiento basado en una variable global? Piensa en términos de acoplamiento y extensibilidad.

</aside>

# **Actividad 3: Investiga el Patrón Factory Method**

**Enunciado**
Esta actividad se centra en el patrón de diseño Factory Method. Investigarás su propósito, cómo abstrae el proceso de creación de objetos y cómo se utiliza en el caso de estudio para generar diferentes tipos de partículas.

**Concepto del patrón Factory Method**

Imagina que estás construyendo un juego que necesita crear diferentes tipos de transporte (camiones, barcos, aviones). En lugar de tener código de creación (`new Camion()`, `new Barco()`) esparcido por toda tu aplicación, el patrón Factory Method propone definir una interfaz (o un método en una clase base/existente) para crear objetos, pero deja que sean las subclases (o la implementación concreta del método) quienes decidan qué clase específica instanciar.

El Factory Method es un patrón creacional que proporciona una interfaz para crear objetos en una superclase, mientras permite a las subclases alterar el tipo de objetos que se crearán. También se puede implementar como un método estático simple en una clase (a veces llamado “Simple Factory” o “Static Factory Method”, que es lo que vemos en el caso de estudio).

Propósito principal:

- **Desacoplar la creación de objetos:** el código cliente que necesita un objeto no necesita saber cómo crearlo ni qué clase concreta se está creando. Solo interactúa con la interfaz o clase base del producto.
- **Flexibilidad:** facilita la introducción de nuevos tipos de productos sin modificar el código cliente que utiliza el Factory.

**Análisis del caso de estudio**

Revisa nuevamente el código, prestando atención a la clase `ParticleFactory` y su uso en `ofApp::setup`.

1. **Identifica la Factory:**
    - ¿Qué clase actúa como la factory en este ejemplo?
    - ¿Cuál es el “método factory” específico? ¿Es un método de instancia o estático?
    - ¿Qué tipo de objeto devuelve este método fábrica?
2. **Proceso de creación:**
    - Observa el método `ParticleFactory::createParticle`. ¿Cómo decide qué tipo de partícula específica crear y configurar?
    - ¿Qué información necesita el método fábrica para realizar su trabajo?
    - ¿Qué devuelve si se le pasa un tipo desconocido? ¿Cómo podrías mejorar esto?
3. **Uso de Factory:**
    - Localiza `ofApp::setup`. ¿Cómo se utiliza la `ParticleFactory` para poblar el vector `particles`?
    - Compara esto con la alternativa: ¿Cómo se vería `ofApp::setup` si *no* usara la fábrica y tuviera que crear y configurar cada tipo de partícula (`star`, `shooting_star`, `planet`) directamente usando `new Particle()` y luego ajustando sus propiedades (`size`, `color`, `velocity`)?

<aside>
📤

**🧐🧪✍️ Reporta en tu bitácora**
1. Explica con tus propias palabras el propósito del patrón Factory Method (o Simple Factory, en este caso). ¿Qué problema principal aborda en la creación de objetos?
2. ¿Qué ventajas aporta el uso de `ParticleFactory` en `ofApp::setup` en comparación con instanciar y configurar las partículas directamente allí? Piensa en términos de organización del código (SRP - Single Responsibility Principle), legibilidad y facilidad para añadir *nuevos* tipos de partículas en el futuro.
3. Imagina que quieres añadir un nuevo tipo de partícula llamada `"black_hole"` que tiene tamaño grande, color negro y velocidad muy lenta. Describe los pasos que necesitarías seguir para implementar esto utilizando la `ParticleFactory` existente. ¿Tendrías que modificar `ofApp::setup`? ¿Por qué sí o por qué no?
4. El método `createParticle` en el ejemplo es estático. ¿Qué implicaciones (ventajas/desventajas) tiene esto comparado con tener una instancia de `ParticleFactory` y un método de instancia `createParticle()`?.

</aside>

# **Actividad 4: Investiga el patrón State**

**Enunciado**
En esta actividad, explorarás el patrón de diseño State. Analizarás cómo permite a un objeto alterar su comportamiento cuando su estado interno cambia, haciendo que el objeto parezca cambiar de clase. Identificarás su implementación en el caso de estudio y comprenderás cómo gestiona los diferentes comportamientos de las partículas.

**Concepto del patrón State**

Piensa en un reproductor de música. Puede estar en estado “Reproduciendo”, “Pausado” o “Detenido”. Las acciones (como presionar el botón “Play/Pause”) tienen diferentes efectos dependiendo del estado actual. Si está “Reproduciendo” y presionas, pasa a “Pausado”. Si está “Pausado” o “Detenido” y presionas, pasa a “Reproduciendo”.

El patrón State permite a un objeto encapsular diferentes comportamientos (estados) en objetos separados y delegar la ejecución a su objeto de estado actual. Esto evita tener grandes bloques `if/else` o `switch` en la clase principal para manejar el comportamiento dependiente del estado.

Componentes clave:

- **Context (contexto):** mantiene una instancia de una subclase de `State` que define el estado actual. Delega las solicitudes dependientes del estado al objeto de estado actual. Puede proporcionar un método para cambiar su estado. (En nuestro caso, `Particle`).
- **State (estado):** define una interfaz común para todos los estados concretos. Esta interfaz declara los métodos que representan las operaciones dependientes del estado. (En nuestro caso, la clase base `State`).
- **ConcreteState (estado concreto):** cada subclase implementa un comportamiento asociado con un estado del Contexto. (En nuestro caso, `NormalState`, `AttractState`, `RepelState`, `StopState`).

**Análisis del caso de estudio**

Examina el código (`ofApp.h`, `ofApp.cpp`) enfocándote en las clases relacionadas con el estado (`State`, `NormalState`, `AttractState`, etc.) y cómo interactúan con `Particle`.

1. **Identifica los componentes:**
    - ¿Cuál es la clase `Context`? ¿Qué miembro utiliza para mantener el estado actual?
    - ¿Cuál es la interfaz `State`? ¿Qué métodos importantes define? (Piensa en `update`, `onEnter`, `onExit`).
    - Enumera las clases `ConcreteState`. ¿Qué comportamiento específico encapsula cada una?
2. **Delegación del comportamiento:**
    - Observa el método `Particle::update()`. ¿Cómo delega la lógica de actualización al estado actual?
    - Compara el código dentro de `NormalState::update()`, `AttractState::update()`, `RepelState::update()` y `StopState::update()`. ¿Cómo encapsula cada clase un comportamiento diferente?
3. **Transiciones de estado:**
    - ¿Cómo cambia una `Particle` de un estado a otro? ¿Qué método es responsable de gestionar la transición? (Busca `setState`).
    - ¿Qué sucede dentro de `Particle::setState()`? ¿Por qué son importantes los métodos `onEnter` y `onExit` de la interfaz `State` (aunque no todos los estados concretos los usen extensivamente en este ejemplo)? ¿Qué gestionan `onEnter` y `onExit` en `NormalState`?
    - ¿Qué evento externo (mediado por el patrón Observer, que ya analizaste) desencadena la llamada a `setState` en una `Particle`?

<aside>
📤

**🧐🧪✍️ Reporta en tu bitácora**
1. Explica con tus propias palabras el propósito del patrón State. ¿Cuándo es útil aplicarlo?
2. Dibuja un diagrama de estados simple para la clase `Particle`. Muestra los diferentes estados (`Normal`, `Attract`, `Repel`, `Stop`) como nodos y las transiciones entre ellos como flechas etiquetadas con el evento que las causa (p. ej., la tecla presionada: ‘n’, ‘a’, ‘r’, ‘s’).
3. Describe las ventajas de usar el patrón State en `Particle` en lugar de tener un miembro `std::string estadoActual` y usar un gran `if/else if/else` o `switch` dentro de `Particle::update()` para cambiar el comportamiento. Piensa en cohesión, extensibilidad (añadir nuevos estados) y el Principio Abierto/Cerrado (Open/Closed Principle).
4. ¿Qué responsabilidad tienen los métodos `onEnter` y `onExit` en el patrón State? Proporciona un ejemplo de por qué podrían ser útiles (incluso si no se usan mucho en *todos* los estados de este caso de estudio). Por ejemplo, ¿Qué podrías hacer en `onEnter` para `AttractState` o en `onExit` para `StopState`?

</aside>

# **Aplicación 🛠**

# **Actividad 5**

**Enunciado**
En esta actividad modificarás el caso de estudio para añadir un nuevo tipo de partícula que utiliza los patrones Observer, Factory y State.

<aside>
📤

**🧐🧪✍️ Reporta en tu bitácora**
1. El código fuente completo de tu proyecto openFrameworks.
2. Explica cómo usaste el patrón Factory para esta nueva partícula.
3. Describe cómo implementaste el patrón Observer para esta nueva partícula.
4. Explica cómo aplicaste el patrón State a esta nueva partícula.

</aside>

# **Evidencias 🗂️**

**RUBRICA!**
• Recuerda que la bitácora se cierra el **~~fecha**~~ a las 7:49 a.m. No olvides que el aprendizaje es un proceso que se plasma en la bitácora. La bitácora no es un resultado que se llena a última hora.
• Si no realizas la autoevaluación tu nota será 0.
• Si una actividad no está COMPLETA debes multiplicar la nota de esa actividad por el porcentaje de avance que tengas.
• Si usas IA para generar código, texto o imágenes la nota en esa actividad será 0.
**Rúbrica de evaluación del proceso**
5: realicé las 5 actividades completas y la autoevaluación.
4: realicé 4 actividades completas y la autoevaluación.
3: realicé 3 actividades completas y la autoevaluación.
2: realicé 2 actividades completas y la autoevaluación.
1: realicé 1 actividad completa y la autoevaluación.
0: no realicé ninguna actividad o no realicé la autoevaluación.

**EVIDENCIAS EN BITÁCORA**
1. Realiza las actividades propuestas en esta unidad y documenta todo el proceso en tu bitácora.
2. Realiza la autoevaluación indicando:
    ◦ Tu nota propuesta.
    ◦ La defensa de esa nota para cada actividad.