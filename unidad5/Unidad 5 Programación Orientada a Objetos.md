# Unidad 5: Programación Orientada a Objetos

# **Introducción 📜**

En esta unidad vas a profundizar en los principios fundamentales de la Programación Orientada a Objetos (OOP) usando C++. El objetivo es profundo: no solo usarás la herencia, el polimorfismo y el encapsulamiento en C++, sino que entenderás cómo funcionan por dentro, “bajo el capó”. Este conocimiento es lo que te permitirá, en el futuro, aprender cualquier otro lenguaje orientado a objetos, porque sabrás qué buscar y cómo funcionan los principios fundamentales.

# **¿Qué aprenderás en esta unidad? 💡**

Reconozco que cada uno de ustedes llega a este punto con un bagaje distinto. Algunos se han dado por vencidos con la programación, otros han tenido experiencias frustrantes, y algunos han podido aprender. Por eso, en esta unidad, tú eliges el trayecto de aprendizaje. Te propongo dos rutas:

<aside>
💡

**Consejo**
**La ruta guiada**: un camino estructurado con actividades paso a paso que te llevarán a través de todos los conceptos clave usando arte generativo. Es ideal si prefieres tener una guía clara y un objetivo definido.

</aside>

<aside>
🔥

**Consejo**
**La ruta de exploración personal**: un camino para los curiosos, para los que quieren ir a su propio ritmo, profundizar en lo que más les interesa o **reforzar lo que más necesitan**. Aquí, el objetivo no es completar una lista de tareas, sino embarcarte en una investigación personal. ES UNA NUEVA OPORTUNIDAD para reconciliarte con la programación y descubrir su belleza.

</aside>

**¿En qué consiste la ruta de exploración personal?**

Tu misión es la misma: desentrañar los secretos de la OOP usando C++ como medio. Pero tú decides el mapa. El punto de partida es un diagnóstico.

Realizarás una breve actividad inicial. No es una prueba, es un espejo que te ayudará a ver qué conceptos manejas bien y cuáles son áreas de oportunidad.

Luego tú defines, basado en tu diagnóstico, tus propias preguntas. ¿Qué te genera más curiosidad? ¿Qué necesitas reforzar? Diseñarás tus experimentos actuando como un científico computacional. Crearás pequeños programas, usarás el depurador y buscarás la evidencia que responda a tus preguntas. **ES MUY IMPORTANTE** que sepas que en cualquiera de las dos rutas el error no es un fracaso, sino un dato valioso. No estamos apostando por el resultado final, sino por el proceso de aprendizaje.

Cada error es una oportunidad para aprender y crecer. Documenta tu Viaje en tu bitácora de aprendizaje, registrarás tu proceso. Una buena bitácora no solo muestra código, muestra pensamiento: tus preguntas, hipótesis, experimentos (con capturas de pantalla), hallazgos, y reflexiones.

# **Investigación 🔎**

# **Actividad 1:** Esta será nuestra actividad de diagnóstico inicial

**Parte 1: recordando los conceptos (en C#)**

En tus cursos anteriores has trabajado principalmente con C#. Basándote en esa experiencia, responde con tus propias palabras:

1. ¿Qué es el encapsulamiento para ti? Describe una situación en la que te haya sido útil o donde hayas visto su importancia.
2. ¿Qué es la herencia? ¿Por qué un programador decidiría usarla? Da un ejemplo simple.
3. ¿Qué es el polimorfismo? Describe con tus palabras qué significa que un código sea “polimórfico”.

**Parte 2: análisis de código (en C#)**

```csharp
using System;using System.Collections.Generic;
public abstract class Figura{    
		private string nombre;
    public string Nombre {        
		    get { return nombre;}
		    protected set { nombre = value; }    
		    }
    public Figura(string nombre)    {        
		    this.Nombre = nombre;    
		    }
    public abstract void Dibujar();
    }
public class Circulo : Figura{    
		public double Radio { get; private set; }
    public Circulo(double radio) : base("Círculo")    {        
		    this.Radio = radio;    
		    }
    public override void Dibujar()    {        
		    Console.WriteLine($"Dibujando un {Nombre} de radio {Radio}.");    
		    }
		}
public class Rectangulo : Figura{    
		public double Base { get; private set; }    
		public double Altura { get; private set; }
    public Rectangulo(double b, double h) : base("Rectángulo")    {        
		    this.Base = b;        
		    this.Altura = h;    
		    }
    public override void Dibujar()    {        
		    Console.WriteLine($"Dibujando un {Nombre} de {Base}x{Altura}.");    
		    }
		}
public class Programa{    
		public static void Main()    {        
				List<Figura> misFiguras = new List<Figura>();
        misFiguras.Add(new Circulo(5.0));        
        misFiguras.Add(new Rectangulo(4.0, 6.0));        
        misFiguras.Add(new Circulo(10.0));
        foreach (Figura fig in misFiguras) {            
		        fig.Dibujar();        
		        }    
		    }
		}
```

Ahora, responde a estas preguntas sobre el código:

**Encapsulamiento:**

- Señala una línea de código que sea un ejemplo claro de encapsulamiento y explica por qué lo es.
- ¿Por qué crees que el campo nombre es private pero la propiedad Nombre es public? ¿Qué problema se evita con esto?

**Herencia:**

- ¿Cómo se evidencia la herencia en la clase Circulo?
- Un objeto de tipo Circulo, además de Radio, ¿Qué otros datos almacena en su interior gracias a la herencia?

**Polimorfismo:**

- Observa el bucle `foreach`. La variable `fig` es de tipo Figura, pero a veces contiene un Circulo y otras un Rectangulo. Cuando se llama a `fig.Dibujar()`, el programa ejecuta la versión correcta. En tu opinión, ¿Cómo crees que funciona esto “por debajo”? No necesitas saber la respuesta correcta, solo quiero que intentes razonar cómo podría ser.

**Parte 3: hipótesis sobre la implementación**

Esta es la parte más importante. Imagina que eres un diseñador de lenguajes de programación. Tienes que decidir cómo implementar estos conceptos en la memoria y en el procesador. No hay respuestas incorrectas, solo ideas. Dibuja si te ayuda.

1. Memoria y herencia: cuando creas un objeto Rectangulo, este tiene Base, Altura y también Nombre. ¿Cómo te imaginas que se organizan esos tres datos en la memoria del computador para formar un solo objeto?
2. El mecanismo del polimorfismo: pensemos de nuevo en la llamada fig.Dibujar(). El compilador solo sabe que fig es una Figura. ¿Cómo decide el programa, mientras se está ejecutando, si debe llamar al Dibujar del Circulo o al del Rectangulo? Lanza algunas ideas o hipótesis.
3. La barrera del encapsulamiento: ¿Cómo crees que el compilador logra que no puedas acceder a un miembro private desde fuera de la clase? ¿Es algo que se revisa cuando escribes el código, o es una protección que existe mientras el programa se ejecuta? ¿Por qué piensas eso?

**Parte 4: y tu autoevaluación y primeras preguntas**

Has completado el diagnóstico. Ahora, reflexiona sobre tu propia experiencia y basado en esto te propongo dos caminos:

1. Formula la primer pregunta que comenzarás a investigar. Este será el punto de partida para tu “ruta de exploración personal”. Tu vas definiendo tus propiuas actividades.
2. Si prefieres la “ruta guiada” adelante. Comienza con la actividad 2.

# **Actividad 2: Aplicación**

En esta actividad te mostraré una aplicación para que veas aplicados todos los conceptos que estudiarás en esta unidad.

Durante la actividad te indicaré los momentos en los que debes detenerte para analizar 🧐, experimentar 🧪 y reportar ✍️ tus hallazgos en la bitácora de aprendizaje.

Crea un proyecto en `openFrameworks` y adiciona el siguiente código.

`ofApp.h`

```cpp
#pragma once
#include "ofMain.h"#include <vector>
// -------------------------------------------------
// Clase base abstracta: Particle
// -------------------------------------------------
class Particle {
		public:    
				virtual ~Particle() {}    
				virtual void update(float dt) = 0;    
				virtual void draw() = 0;    
				virtual bool isDead() const = 0;    
				// Nuevo método para saber si la partícula (tipo RisingParticle) debe explotar    
				virtual bool shouldExplode() const { return false; }    
				// Métodos para obtener posición y color, para usarlos en explosiones    
				virtual glm::vec2 getPosition() const { return glm::vec2(0, 0); }    
				virtual ofColor getColor() const { return ofColor(255); }
		};
// -------------------------------------------------
// RisingParticle: Partícula que nace en la parte inferior central y sube
// -------------------------------------------------
class RisingParticle : public Particle {
		protected:    
				glm::vec2 position;    
				glm::vec2 velocity;    
				ofColor color;    
				float lifetime; 
				// tiempo máximo antes de explotar    
				float age;    
				bool exploded;
		public:    
				RisingParticle(const glm::vec2& pos, const glm::vec2& vel, const ofColor& col, float life)
					: position(pos), velocity(vel), color(col), lifetime(life), age(0), exploded(false) {    }
		    void update(float dt) override {        
				    position += velocity * dt;        
				    age += dt;        
				    // Aumenta la desaceleración para dar sensación de recorrido largo        
				    velocity.y += 9.8f * dt * 8;        
				    // Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura        
				    float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);        
				    if (position.y <= explosionThreshold || age >= lifetime) {            
						    exploded = true;        
						    }    
						}
		    void draw() override {        
				    ofSetColor(color);        
				    // Partícula más grande        
				    ofDrawCircle(position, 10);    
				    }
		    bool isDead() const override { return exploded; }    
		    bool shouldExplode() const override { return exploded; }    
		    glm::vec2 getPosition() const override { return position; }    
		    ofColor getColor() const override { return color; }
		    };
// -------------------------------------------------
// Clase base para explosiones: ExplosionParticle
// -------------------------------------------------
class ExplosionParticle : public Particle {
		protected:    
				glm::vec2 position;    
				glm::vec2 velocity;    
				ofColor color;    
				float age;    
				float lifetime;    
				float size;  
				// tamaño de la partícula de explosión
		public:    
				ExplosionParticle(const glm::vec2& pos, const glm::vec2& vel, const ofColor& col, float life, float sz)
						: position(pos), velocity(vel), color(col), age(0), lifetime(life), size(sz) {    }
		    void update(float dt) override {        
				    position += velocity * dt;        
				    age += dt;        
				    float alpha = ofMap(age, 0, lifetime, 255, 0, true);        
				    color.a = alpha;    
				    }
		    bool isDead() const override { return age >= lifetime; 
		    }
};
// -------------------------------------------------
// CircularExplosion: Explosión en patrón circular
// -------------------------------------------------
class CircularExplosion : public ExplosionParticle {
		public:    
				CircularExplosion(const glm::vec2& pos, const ofColor& col)
						: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.2f, ofRandom(16, 32)) {        
						float angle = ofRandom(0, TWO_PI);        
						float speed = ofRandom(80, 200);        
						velocity = glm::vec2(cos(angle), sin(angle)) * speed;    
						}
		    void draw() override {        
				    ofSetColor(color);        
				    ofDrawCircle(position, size);    
				    }
				};
// -------------------------------------------------
// RandomExplosion: Explosión con direcciones aleatorias
// -------------------------------------------------
class RandomExplosion : public ExplosionParticle {
		public:    
				RandomExplosion(const glm::vec2& pos, const ofColor& col)
						: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.5f, ofRandom(16, 32)) {        
						velocity = glm::vec2(ofRandom(-200, 200), ofRandom(-200, 200));    
						}
		    void draw() override {        
				    ofSetColor(color);        
				    ofDrawRectangle(position.x, position.y, size, size);    
				    }
				};
// -------------------------------------------------
// StarExplosion: Explosión en forma de estrella
// -------------------------------------------------
class StarExplosion : public ExplosionParticle {
		public:    
				StarExplosion(const glm::vec2& pos, const ofColor& col)        
						: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.3f, ofRandom(20, 40)) {        
						float angle = ofRandom(0, TWO_PI);        
						float speed = ofRandom(90, 180);        
						velocity = glm::vec2(cos(angle), sin(angle)) * speed;    
						}
		    void draw() override {        
				    ofSetColor(color);        
				    int rays = 5;        
				    float outerRadius = size;        
				    float innerRadius = size * 0.5;        
				    ofPushMatrix();        
				    ofTranslate(position);        
				    for (int i = 0; i < rays; i++) {            
						    float theta = ofMap(i, 0, rays, 0, TWO_PI);            
						    float xOuter = cos(theta) * outerRadius;            
						    float yOuter = sin(theta) * outerRadius;            
						    float xInner = cos(theta + PI / rays) * innerRadius;            
						    float yInner = sin(theta + PI / rays) * innerRadius;            
						    ofDrawLine(0, 0, xOuter, yOuter);            
						    ofDrawLine(xOuter, yOuter, xInner, yInner);        
						    }        
						ofPopMatrix();    
						}
			};
// -------------------------------------------------
// ofApp: Manejo de la escena y eventos
// -------------------------------------------------
class ofApp : public ofBaseApp {
		public:    
				void setup();    
				void update();    
				void draw();    
				void mousePressed(int x, int y, int button);  
				void keyPressed(int key);
		    std::vector<Particle*> particles;    
		    ~ofApp();
		private:  
				void createRisingParticle();
};
```

ofApp.cpp

```cpp
#include "ofApp.h"
// --------------------------------------------------------------
void ofApp::setup() {    
		ofSetFrameRate(60);    
		ofBackground(0);
		}
// --------------------------------------------------------------
void ofApp::update() {    
		float dt = ofGetLastFrameTime();
    // Actualiza todas las partículas    
    for (int i = 0; i < particles.size(); i++) {        
		    particles[i]->update(dt);    
		    }
    // Procesa las partículas (iteración en reversa para facilitar eliminación)    
    for (int i = particles.size() - 1; i >= 0; i--) {        
		    // Si la partícula debe explotar, generamos nuevas explosiones        
		    if (particles[i]->shouldExplode()) {            
				    int explosionType = (int)ofRandom(3); 
				    // 0: Circular, 1: Random, 2: Star            
				    int numParticles = (int)ofRandom(20, 30);            
				    for (int j = 0; j < numParticles; j++) {                
						    if (explosionType == 0) {                    
								    particles.push_back(new CircularExplosion(particles[i]->getPosition(), particles[i]->getColor()));                
								    }                
								else if (explosionType == 1) {                    
										particles.push_back(new RandomExplosion(particles[i]->getPosition(), particles[i]->getColor()));                
										}                
								else {                    
										particles.push_back(new StarExplosion(particles[i]->getPosition(), particles[i]->getColor()));                
										}            
								}            
						delete particles[i];            
						particles.erase(particles.begin() + i);        
						}        
				else if (particles[i]->isDead()) {            
						delete particles[i];            
						particles.erase(particles.begin() + i);        
						}    
				}
	}
// --------------------------------------------------------------
void ofApp::draw() {    
		for (int i = 0; i < particles.size(); i++) {        
				particles[i]->draw();    
				}
		}
// --------------------------------------------------------------
void ofApp::createRisingParticle() {  
		// Genera una RisingParticle cerca del centro inferior (con variación horizontal)  
		float minX = ofGetWidth() * 0.35;  
		float maxX = ofGetWidth() * 0.65;  
		float spawnX = ofRandom(minX, maxX);  
		glm::vec2 pos(spawnX, ofGetHeight());  
		// La partícula apunta hacia un objetivo en la parte superior central  
		glm::vec2 target(ofGetWidth() / 2 + ofRandom(-300, 300), ofGetHeight() * 0.10 + ofRandom(-30, 30));  
		glm::vec2 direction = glm::normalize(target - pos);  
		// Velocidad ajustada para recorrer una mayor distancia  
		glm::vec2 vel = direction * ofRandom(250, 350);  
		ofColor col;  
		col.setHsb(ofRandom(255), 220, 255);  
		float lifetime = ofRandom(1.5, 3.5); 
		// Tiempo de vida antes de explotar  
		particles.push_back(new RisingParticle(pos, vel, col, lifetime));
		}
// --------------------------------------------------------------
void ofApp::mousePressed(int x, int y, int button) {    
		createRisingParticle();
		}
// --------------------------------------------------------------
void ofApp::keyPressed(int key) {  
		if (key == ' ') {    
				for (int i = 0; i < 1000; i++) {      
						createRisingParticle();    
						}  
				}    
		if (key == 's') {        
				ofSaveScreen("screenshot_" + ofToString(ofGetFrameNum()) + ".png");    
				}
		}
// --------------------------------------------------------------
ofApp::~ofApp() {    
		for (int i = 0; i < particles.size(); i++) {        
				delete particles[i];    
				}    
		particles.clear();
		}
```

🧐🧪✍️ Analiza el código de la aplicación y trata de explicar en tus propias palabras qué está haciendo, NO USES IA generativa. Captura pantallas de la aplicación funcionando y añádelas a la bitácora de aprendizaje.

Cuando ejecutes la aplicación deberías ver algo como esto:

![Una partícula](https://juanferfranco.github.io/computacionales-2025-20/_astro/u5a1-1.DZIJDoya_Z1EnXHv.webp)

![Una partícula- explosión](https://juanferfranco.github.io/computacionales-2025-20/_astro/u5a1-2.Pj0MOvnf_UXdUC.webp)

![Múltiples partículas](https://juanferfranco.github.io/computacionales-2025-20/_astro/u5a1-3.CEhk3xT5_ZWA6K0.webp)

![Múltiples partículas- explosión](https://juanferfranco.github.io/computacionales-2025-20/_astro/u5a1-4.BzkDgbMc_Z6f3OK.webp)

# **Actividad 3**

Ahora te guiaré en el análisis del caso de estudio anterior. En esta actividad vas a recordar y sobre todo a `redescubrir` algunos conceptos fundamentales de la programación orientada a objetos, pero esta vez lo harás desde la experimentación y la curiosidad. Quiero insistir en esto. En cursos previos ya abordaste teóricamente estos conceptos e incluso los aplicaste en ejercicios prácticos. Sin embargo, en esta actividad vas a experimentar con el caso de estudio y con el depurador de código para que puedas comprender mejor cómo se comportan los objetos en un programa y cómo se implementan algunos conceptos como la herencia, el polimorfismo y el encapsulamiento.

**Concepto de objeto**: en la programación orientada a objetos, un objeto es una instancia de una clase. Una clase define un tipo de objeto, pero **no** es un objeto en sí mismo. Pero ¿Cómo se ve un objeto en la memoria?

Considera el caso de estudio. Usa el depurador para encontrar la instancia de la clase ofApp. Recuerda que debes usar el depurador porque `el objeto solo estará en la memoria mientras la aplicación esté corriendo`.

Antes de comenzar el experimento observa la clase ofApp:

```cpp
class ofApp : public ofBaseApp {
		public:    
				void setup();    
				void update();    
				void draw();    
				void mousePressed(int x, int y, int button);    
				void keyPressed(int key);
		    std::vector<Particle*> particles;    
		    ~ofApp();
		private:    
				void createRisingParticle();
};
```

🧐🧪✍️ Antes de ejecutar el experimento, ¿Qué esperas ver en memoria (hipótesis)? Ejecuta el código y muestra una captura de pantalla del objeto en la memoria. ¿Qué puedes observar? ¿Qué información te proporciona el depurador? ¿Qué puedes concluir?

🧐🧪✍️ Usa de nuevo el depurador para capturar un objeto de tipo `CircularExplosion`. Es posible que tengas que hacer modificaciones mínimas en el código para que puedas capturar este objeto más fácilmente. Observa con el depurador la ventana de Auto o Locals y la ventana de Memory 1. Trata de buscar en memoria todas las partes que componen al objeto tipo `CircularExplosion` ¿Qué puedes observar en la memoria? ¿Qué información te proporciona el depurador? ¿Qué puedes concluir? NO OLVIDES tener a la mano toda la jerarquía de clases que componen a `CircularExplosion`. De esta manera podrás identificar cada parte del objeto en memoria.

**Concepto de los métodos virtuales**: observa de nuevo en memoria un objeto de tipo `CircularExplosion`. Nota que el primer campo en memoria del objeto es un `ExplosionParticle`. Abren el objeto `ExplosionParticle` y observa que el primer campo en memoria es un `Particle`. Abre el objeto `Particle` y observa que el primer campo en memoria es `_vtable`. ¿Qué es eso? Es un puntero a una tabla de funciones virtuales. Observa detenidamente la tabla de funciones.

🧐🧪✍️ Captura la _vtable de un objeto `CircularExplosion`, pega la imagen en tu bitácora, pero observa detenidamente la tabla de funciones. ¿Qué puedes observar?

Te voy a mostrar un ejemplo, en mi caso, de cómo se ve la tabla de funciones:

![vtable CircularExplosion](https://juanferfranco.github.io/computacionales-2025-20/_astro/u5a2-1.PmxPK7o0_83Hk8.webp)

🧐🧪✍️ Ahora, captura en memoria la _vtable de un objeto `StarExplosion`, pega la imagen en tu bitácora y observa detenidamente la tabla de funciones.

Te muestro de nuevo el ejemplo, en mi caso, de cómo se ve la tabla de funciones:

![vtable StarExplosion](https://juanferfranco.github.io/computacionales-2025-20/_astro/u5a2-2.BbQUVlVo_Z24HXs0.webp)

🧐🧪✍️ Observa de nuevo ambas tablas y compara. ¿Qué puedes ver? ¿Qué puedes concluir? ¿Qué relación existe entre la tabla de funciones y los métodos virtuales? Esta pregunta que te voy a hacer no es fácil y la idea de hacerla es prepararte mentalmente para lo viene ¿Para qué crees que pueda servir una tabla de funciones virtuales? Para responder esta pregunta trata de pensar en el polimorfismo con interfaces y clases abstractas que viste al estudiar C#, por ejemplo, con interfaces:

```cpp
using System;
interface IAnimal{    
		void HacerSonido();
		}
class Perro : IAnimal{    
		public void HacerSonido()    {        
				Console.WriteLine("El perro ladra: ¡Guau, guau!");    
				}
		}
class Gato : IAnimal{    
		public void HacerSonido()    {        
				Console.WriteLine("El gato maúlla: ¡Miau, miau!");    		
				}
		}
class Program{    
		static void Main()    {        
				// Polimorfismo: Usamos la interfaz para tratar diferentes tipos de animales        
				IAnimal[] animales = new IAnimal[]{            
						new Perro(),            
						new Gato()        
						};
        foreach (IAnimal animal in animales){            
		        animal.HacerSonido(); 
		        // Llamada polimórfica        
		        }    
		    }
}
```

Nota que el método `HacerSonido` se llama dos veces, una vez para el perro y otra vez para el gato. ¿Cómo se logra esto? ¿Qué relación existe entre los métodos virtuales y el polimorfismo? Al llamar `HacerSonido` cómo sabe esta función sobre cuál objeto debe actuar?

Dejemos por ahora este experimento hasta este punto, pero un rato lo vamos retomar.

# **Actividad 4**

**Concepto de encapsulamiento**: el encapsulamiento es un concepto fundamental en la programación orientada a objetos. En C++ el encapsulamiento se logra mediante el uso de modificadores de acceso. Te voy a proponer un experimento que puedes implementar creando un proyecto de consola de C++ en Visual Studio.

```cpp
class AccessControl {
private:    
		int privateVar;
protected:    
		int protectedVar;
public:    
		int publicVar;    
		AccessControl() : privateVar(1), protectedVar(2), publicVar(3) {}
		};
int main() {    
		AccessControl ac;    
		ac.publicVar = 10; 
		// Válido    
		// ac.protectedVar = 20; 
		// Error de compilación    
		// ac.privateVar = 30; 
		// Error de compilación    
		return 0;
		}
```

Ejecuta este código. Luego, **descomenta** las líneas que están comentadas y vuelve a compilar. ¿Qué sucede? ¿Por qué sucede esto? ¿Qué puedes concluir?

Ahora quiero que notes algo. El encapsulamiento solo lo podemos garantizar en tiempo de compilación. Sin embargo, en tiempo de ejecución podemos acceder a los campos privados de un objeto. Analiza el siguiente programa:

```cpp
#include <iostream>
class MyClass {
private:    
		int secret1;    
		float secret2;    
		char secret3;
public:    
		MyClass(int s1, float s2, char s3) : secret1(s1), secret2(s2), secret3(s3) {}
    void printMembers() const {        
		    std::cout << "secret1: " << secret1 << "\n";        
		    std::cout << "secret2: " << secret2 << "\n";        
		    std::cout << "secret3: " << secret3 << "\n";    
		    }
		};

int main() {    
		MyClass obj(42, 3.14f, 'A');    
		// Esta línea causará un error de compilación    
		std::cout << obj.secret1 << std::endl;
    obj.printMembers();  
    // Método público para mostrar los valores    
    return 0;
    }
```

🧐🧪✍️ Compila el programa. ¿Qué pasa?

Ahora prueba con este programa:

```cpp
#include <iostream>
class MyClass {
private:    
		int secret1;    
		float secret2;    
		char secret3;
public:    
		MyClass(int s1, float s2, char s3) : secret1(s1), secret2(s2), secret3(s3) {}
    void printMembers() const {        
		    std::cout << "secret1: " << secret1 << "\n";        
		    std::cout << "secret2: " << secret2 << "\n";        
		    std::cout << "secret3: " << secret3 << "\n";    
		    }
		};
int main() {    
		MyClass obj(42, 3.14f, 'A');
    // Usando reinterpret_cast para violar el encapsulamiento    
    int* ptrInt = reinterpret_cast<int*>(&obj);    
    float* ptrFloat = reinterpret_cast<float*>(ptrInt + 1);    
    char* ptrChar = reinterpret_cast<char*>(ptrFloat + 1);
    // Accediendo y mostrando los valores privados    
    std::cout << "Accediendo directamente a los miembros privados:\n";    
    std::cout << "secret1: " << *ptrInt << "\n";       
    // Accede a secret1    
    std::cout << "secret2: " << *ptrFloat << "\n";     
    // Accede a secret2    
    std::cout << "secret3: " << *ptrChar << "\n";      
    // Accede a secret3
    return 0;
    }
```

🧐🧪✍️ Compila el programa y ejecuta. ¿Qué puedes concluir?

🧐🧪✍️ En tus palabras, ¿Qué es el encapsulamiento? ¿Por qué es importante?

# **Actividad 5**

**Concepto de herencia**: la herencia es otro concepto fundamental en la programación orientada a objetos. Observa de nuevo en ofApp.h la clase `CircularExplosion`. Observa que esta clase hereda de la clase `ExplosionParticle` que a su vez hereda de la clase `Particle`.

🧐🧪✍️ captura de nuevo la memoria que ocupa el objeto `CircularExplosion` compara la jerarquía de clases con los campos en memoria del objeto. ¿Qué puedes observar? ¿Qué información te proporciona el depurador? ¿Qué puedes concluir?

🧐🧪✍️ ¿Cómo se implementa la herencia en C++?

🧐🧪✍️ C++ permite hacer algo que C# no: herencia múltiple. Realiza un experimento que te permita ver cómo se objeto en memoria cuya clase base tiene herencia múltiple.

# **Actividad 6**

**Concepto de polimorfismo**: recuerdas que ya analizaste el concepto de los métodos virtuales y su relación con la tabla de funciones virtuales. Ahora quiero que pienses en el polimorfismo.

Observa en ofApp.cpp en el método `update()` esta parte del código:

```cpp
    // Actualiza todas las partículas    
    for (int i = 0; i < particles.size(); i++) {        
		    particles[i]->update(dt);    
		    }
```

el método update de la clase `Particle` es un método virtual. Usa el depurador para analizar cómo se comporta este método en tiempo de ejecución. Realiza esta verificación cuando particles tenga varios objetos de diferentes tipos de partículas. ¿Qué puedes observar? ¿Qué información te proporciona el depurador?

Nota que update se comporta de manera diferente para cada tipo de partícula. A esto se le llama polimorfismo en tiempo de ejecución.

🧐🧪✍️ Realiza un dibujo con el cuál expliques cómo se implementa el polimorfismo en tiempo de ejecución. Utiliza el concepto de métodos virtuales y la tabla de funciones virtuales. ¿Qué puedes concluir?

🧐🧪✍️ ¿Qué relación existe entre los métodos virtuales y el polimorfismo?

# **Aplicación 🛠**

# **Actividad 7**

Aplica lo aprendido. Vas a evaluar lo aprendido en la fase anterior modificando el caso de estudio.

⚠️ **IMPORTANTE**: si usas IA generativa no le pidas respuestas. La idea de esta sección es que apliques lo aprendido. Si no sabes cómo hacerlo, quiere decir que aún tienes vacíos en tu aprendizaje y debes regresar a la fase anterior o solicitar ayuda al profesor antes de continuar.

**¿Qué harás?**

1. Agrega dos nuevos tipos de Particle diferentes a **RisingParticle**.
2. Implementar un nuevo modo de explosión.

Reporta en tu bitácora de aprendizaje:

1. ¿Cómo y por qué de la implementación de cada una de las extensiones solicitadas al caso de estudio?
2. ¿Cómo y por qué de la implementación de los conceptos de encapsulamiento, herencia y polimorfismo en tu código?
3. Explica cómo verificaste que cada una de las extensiones funciona correctamente, muestra capturas de pantalla del depurador donde evidencias lo anterior, en particular el polimorfismo en tiempo de ejecución.

# **Evidencias 🗂️**

**RUBRICA!**

- Recuerda que la bitácora se cierra el **miércoles 8 de abril a las 18.00**. No olvides que el aprendizaje es un proceso que se plasma en la bitácora. La bitácora no es un resultado que se llena a última hora.
- Si no realizas la sección de consolidación, autoevaluación y cierre, tu nota será 0.

| Criterio | Inicial (0.0 - 1.9) | En desarrollo (2.0 - 3.4) | Logrado (3.5 - 4.4) | Excelente (4.5 - 5.0) |
| --- | --- | --- | --- | --- |
| 1. Profundidad de la Indagación | Las preguntas son superficiales o ausentes. No se define una dirección clara para la exploración. | Se formulan preguntas relevantes, pero se enfocan principalmente en el “qué” y el “cómo” de los conceptos de manera aislada. | Se formulan preguntas que conectan los conceptos (ej. “¿Cómo se relaciona la herencia con la vtable?”). La investigación sigue una línea lógica y demuestra una intención clara de entender los mecanismos. | Se formulan preguntas que demuestran una síntesis conceptual. Las preguntas exploran el “porqué” del diseño y las interdependencias (ej. “¿Cómo garantiza el encapsulamiento la integridad del polimorfismo a nivel de la vtable?“). |
| 2. Calidad de la Experimentación | Los experimentos son una simple ejecución del código base, sin modificaciones ni análisis. | Se realizan modificaciones sencillas al código y se usa el depurador para observar valores, pero sin un análisis sistemático. | Se diseñan y ejecutan experimentos efectivos para verificar el funcionamiento de cada concepto (herencia, polimorfismo, encapsulamiento). Se usa el depurador de forma correcta para recolectar evidencia. | Se diseñan experimentos precisos y elegantes que no solo verifican el funcionamiento, sino que aíslan y demuestran las implicaciones y sutilezas de la interacción entre los conceptos. El uso del depurador es experto y sirve para construir argumentos sólidos. |
| 3. Análisis y Reflexión | La bitácora es un registro de acciones sin análisis. Las conclusiones son incorrectas o no están respaldadas por evidencia. | La bitácora describe los resultados de los experimentos, pero la reflexión es superficial. Se identifican los conceptos, pero no se explican con profundidad. | La bitácora conecta claramente la evidencia de los experimentos con la explicación teórica de cada concepto. Se analizan los errores como parte del aprendizaje y se llega a conclusiones correctas y bien fundamentadas. | La bitácora demuestra una reflexión profunda que va más allá de la simple verificación. Se analiza por qué los mecanismos funcionan como lo hacen, se evalúan sus implicaciones en el diseño de software y se construye un modelo mental coherente que integra todos los hallazgos. |
| 4. Apropiación y Articulación de Conceptos | La bitácora muestra una definición incorrecta o copiada de los conceptos. No se demuestra comprensión personal. | La bitácora explica los conceptos de forma básica. La comprensión parece fragmentada y dependiente de la memorización. | La bitácora demuestra una comprensión clara y correcta de cada concepto por separado. Se utilizan palabras propias y analogías adecuadas para explicar cómo funciona la herencia, el polimorfismo y el encapsulamiento. | La bitácora demuestra una maestría conceptual. Se explican los conceptos como un sistema interdependiente. Se articula con total claridad y con lenguaje propio cómo el encapsululamiento, la herencia y el polimorfismo colaboran para lograr el comportamiento orientado a objetos. La explicación es robusta y transferible. |

## 📤 **EVIDENCIAS EN BITÁCORA**

**Estructura de la bitácora de aprendizaje**
Debe contener:

1. **Diagnóstico inicial:** tus reflexiones sobre la actividad de diagnóstico.
2. **Plan de exploración:** la pregunta inicial que guiará tu trabajo, luego en el camino seguirás formulando más preguntas.
3. **Registro de exploración:** el cuerpo principal de tu bitácora. Aquí documentas cada ciclo de pregunta -> hipótesis -> experimento -> hallazgo -> reflexión. Debe ser rico en evidencia visual (código, capturas del depurador con anotaciones, diagramas).
4. **Consolidación, autoevaluación y cierre:** esta sección es OBLIGATORIA y central para tu evaluación.