# Unidad 3 · Programación orientada a objetos y patrones de diseño

## Sesión 3. Objetos en memoria, herencia y métodos virtuales

### ¿Qué aprenderás en esta sesión? 💡

- Representar mentalmente un objeto como datos y comportamiento asociado.
- Relacionar jerarquías de clases con la organización del objeto en memoria.
- Explicar el papel de los métodos virtuales en el polimorfismo.
- Usar el depurador para observar objetos reales durante la ejecución.

### Actividad 5: Dibuja un objeto derivado en memoria

Analiza este ejemplo:

```cpp
#include <iostream>
using namespace std;

class Figura {
public:
    Figura(string nombre) : nombre(nombre) {}
    virtual ~Figura() = default;
    virtual void dibujar() = 0;

protected:
    string nombre;
};

class Circulo : public Figura {
public:
    Circulo(float radio) : Figura("Circulo"), radio(radio) {}
    void dibujar() override {
        cout << nombre << endl;
    }

private:
    float radio;
};
```

Antes de ejecutar cualquier programa:

- dibuja cómo crees que se organiza un objeto `Circulo` en memoria,
- indica dónde imaginas que viven los datos heredados,
- decide si piensas que existe alguna referencia interna a los métodos virtuales.

### Actividad 6: Observa el objeto con depuración

Compila el ejemplo anterior en Visual Studio, crea una instancia de `Circulo` y detén la ejecución con un breakpoint. Luego:

1. inspecciona el objeto en `Locals` o `Autos`,
2. expande sus partes heredadas,
3. compara lo que ves con tu dibujo inicial,
4. registra qué cambió en tu modelo mental.

### Actividad 7: Predice llamadas polimórficas

Analiza este programa:

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Animal {
public:
    virtual ~Animal() = default;
    virtual void hacerSonido() = 0;
};

class Perro : public Animal {
public:
    void hacerSonido() override { cout << "Guau" << endl; }
};

class Gato : public Animal {
public:
    void hacerSonido() override { cout << "Miau" << endl; }
};

int main() {
    vector<Animal*> animales = { new Perro(), new Gato(), new Perro() };

    for (Animal* animal : animales) {
        animal->hacerSonido();
    }

    for (Animal* animal : animales) {
        delete animal;
    }
}
```

Responde antes de ejecutarlo:

- ¿Cómo sabe el programa cuál versión de `hacerSonido()` debe usar?
- ¿Qué información necesita el objeto para que eso ocurra?
- ¿Qué pasaría si `hacerSonido()` no fuera virtual?

<aside>
📤

**Bitácora**

- Incluye tu dibujo inicial del objeto derivado.
- Documenta lo que observaste en el depurador.
- Explica con tus palabras qué relación hay entre herencia, método virtual y polimorfismo.
- Escribe una hipótesis sobre qué podría ser una tabla virtual y para qué serviría.

</aside>

## Sesión 4. Encapsulamiento en compilación y observación en ejecución

### ¿Qué aprenderás en esta sesión? 💡

- Diferenciar las reglas de acceso en C++.
- Reconocer que el encapsulamiento es una restricción de interfaz y compilación.
- Contrastar lo que prohíbe el compilador con lo que aún puede observarse en memoria.
- Refinar tu idea de “ocultar” en programación orientada a objetos.

### Actividad 8: Fuerza errores de acceso

Compila y modifica este ejemplo:

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
    // ac.protectedVar = 20;
    // ac.privateVar = 30;
}
```

Haz dos pruebas:

1. compílalo tal como está,
2. descomenta los accesos prohibidos y vuelve a compilar.

Luego explica:

- qué error aparece,
- en qué momento se detecta,
- qué te dice esto sobre el encapsulamiento.

### Actividad 9: Discute el encapsulamiento frente al depurador

Vuelve a un programa con objetos e inspecciónalo en el depurador. Reflexiona:

- ¿El hecho de poder ver datos internos en depuración contradice el encapsulamiento?
- ¿Cuál es la diferencia entre acceso permitido por interfaz y observación técnica del estado?
- ¿Por qué sigue siendo valioso encapsular aunque la memoria exista físicamente?

<aside>
📤

**Bitácora**

- Copia o resume los errores de compilación que obtuviste.
- Explica con tus palabras qué protege `private`, `protected` y `public`.
- Redacta una conclusión breve sobre por qué encapsular no significa “hacer invisible la memoria”.

</aside>
