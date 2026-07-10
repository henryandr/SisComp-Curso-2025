# Unidad 3 · Programación orientada a objetos y patrones de diseño

En esta unidad vas a retomar conceptos de programación orientada a objetos que ya has usado en cursos anteriores, pero ahora los estudiarás con una pregunta nueva: **¿cómo se traducen esas ideas a memoria, compilación y ejecución en C++?** La meta no es repetir definiciones de memoria, sino usar ejemplos, depuración y un caso de estudio para construir un modelo mental más preciso.

## Sesión 1. Diagnóstico y repaso de POO

### ¿Qué aprenderás en esta sesión? 💡

- Recuperar tus ideas previas sobre encapsulamiento, herencia y polimorfismo.
- Identificar clases, objetos, atributos y responsabilidades.
- Comparar una lectura conceptual con una lectura estructural del código.
- Formular preguntas de investigación para el resto de la unidad.

### Actividad 1: Diagnóstico inicial desde tu experiencia previa

Antes de abrir C++, escribe con tus propias palabras:

1. ¿Qué es una clase?
2. ¿Qué diferencia hay entre una clase y un objeto?
3. ¿Qué significa encapsular y por qué podría ser útil?
4. ¿Qué problema intenta resolver la herencia?
5. ¿Qué entiendes por polimorfismo?

### Actividad 2: Analiza una jerarquía simple

Lee este ejemplo y úsalo como base para tu diagnóstico:

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Figura {
public:
    Figura(string nombre) : nombre(nombre) {}
    virtual ~Figura() = default;
    virtual void dibujar() = 0;

    string getNombre() const { return nombre; }

private:
    string nombre;
};

class Circulo : public Figura {
public:
    Circulo(float radio) : Figura("Circulo"), radio(radio) {}

    void dibujar() override {
        cout << "Dibujando " << getNombre() << " de radio " << radio << endl;
    }

private:
    float radio;
};

class Rectangulo : public Figura {
public:
    Rectangulo(float base, float altura)
        : Figura("Rectangulo"), base(base), altura(altura) {}

    void dibujar() override {
        cout << "Dibujando " << getNombre()
             << " de " << base << " x " << altura << endl;
    }

private:
    float base;
    float altura;
};

int main() {
    vector<Figura*> figuras;
    figuras.push_back(new Circulo(5.0f));
    figuras.push_back(new Rectangulo(4.0f, 6.0f));

    for (Figura* figura : figuras) {
        figura->dibujar();
    }

    for (Figura* figura : figuras) {
        delete figura;
    }
}
```

Responde:

- ¿Qué partes del código muestran encapsulamiento?
- ¿Dónde se evidencia la herencia?
- ¿Por qué el `for` puede recorrer figuras distintas con una misma interfaz?
- ¿Qué datos crees que tiene internamente un `Rectangulo` además de `base` y `altura`?
- ¿Qué preguntas te deja este ejemplo sobre memoria, compilación o ejecución?

<aside>
📤

**Bitácora**

- Escribe tus definiciones iniciales de encapsulamiento, herencia y polimorfismo.
- Señala una línea del código donde identifiques cada concepto.
- Formula al menos dos preguntas que quieras investigar durante la unidad.

</aside>

## Sesión 2. Caso de estudio: POO en un sistema interactivo

### ¿Qué aprenderás en esta sesión? 💡

- Reconocer cómo la POO organiza un sistema real.
- Distinguir responsabilidades entre clases.
- Relacionar estructura del código con comportamiento visible.
- Preparar el terreno para estudiar memoria, virtualidad y patrones.

### Actividad 3: Observa un caso de estudio en openFrameworks

Trabaja con un sistema interactivo que tenga:

- una clase base abstracta,
- varias clases derivadas,
- una colección heterogénea de objetos,
- actualización y dibujo polimórficos.

Puedes apoyarte en una estructura como esta:

```cpp
class Particle {
public:
    virtual ~Particle() = default;
    virtual void update(float dt) = 0;
    virtual void draw() = 0;
};

class RisingParticle : public Particle {
public:
    void update(float dt) override;
    void draw() override;
};

class ExplosionParticle : public Particle {
public:
    void update(float dt) override;
    void draw() override;
};
```

Al ejecutar el caso de estudio, enfócate en estas preguntas:

- ¿Qué hace común la clase base?
- ¿Qué varía entre las clases derivadas?
- ¿Qué responsabilidades están en cada clase y cuáles están en la aplicación principal?
- ¿Qué cambios podrías hacer sin reescribir todo el sistema?

### Actividad 4: Mapa de responsabilidades

Construye una tabla o esquema con estas columnas:

- **Clase**
- **Qué sabe**
- **Qué hace**
- **De quién depende**
- **Qué podrías extender**

Incluye por lo menos:

- la clase principal de la aplicación,
- la clase base,
- dos clases derivadas,
- una colección o estructura que almacene objetos.

<aside>
📤

**Bitácora**

- Describe el comportamiento observable del sistema.
- Explica cómo se reparten las responsabilidades entre al menos cuatro clases.
- Señala una decisión de diseño que haga al sistema más fácil de extender.
- Propón una extensión pequeña que todavía no implementarás, pero que te gustaría desarrollar al final de la unidad.

</aside>
