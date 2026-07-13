# Unidad 3 · Programación orientada a objetos y patrones de diseño

## Sesión 5. Herencia, composición y organización de objetos

### ¿Qué aprenderás en esta sesión? 💡

- Evaluar cuándo una jerarquía aporta claridad y cuándo agrega complejidad.
- Comparar herencia con composición como decisiones de diseño.
- Relacionar diseño de clases con mantenibilidad.

### Actividad 10: Compara alternativas de modelado

Supón que tienes un sistema interactivo con entidades visuales. Diseña dos alternativas:

1. una basada en una clase base `Entity` y varias derivadas,
2. otra basada en composición de comportamientos.

Para cada alternativa responde:

- ¿qué responsabilidades quedan más claras?
- ¿qué cambios serían más fáciles de hacer?
- ¿dónde se concentra más acoplamiento?
- ¿qué opción elegirías para un sistema pequeño que luego crecerá?

## Sesión 6. Polimorfismo y despacho dinámico en colecciones

### ¿Qué aprenderás en esta sesión? 💡

- Usar una interfaz común para operar sobre objetos distintos.
- Explicar el valor del polimorfismo en sistemas extensibles.
- Analizar colecciones heterogéneas sin depender del tipo concreto.

### Actividad 11: Colección heterogénea

Analiza este fragmento:

```cpp
#include <memory>
#include <vector>
using namespace std;

class Entity {
public:
    virtual ~Entity() = default;
    virtual void update() = 0;
};

class Enemy : public Entity {
public:
    void update() override {}
};

class NPC : public Entity {
public:
    void update() override {}
};

int main() {
    vector<unique_ptr<Entity>> entities;
    entities.push_back(make_unique<Enemy>());
    entities.push_back(make_unique<NPC>());

    for (auto& entity : entities) {
        entity->update();
    }
}
```

Responde:

- ¿Qué ventaja tiene que `main` trabaje con `Entity` y no con cada clase concreta?
- ¿Qué tendrías que cambiar para añadir un nuevo tipo `Boss`?
- ¿Qué parte del código cliente permanece estable gracias al polimorfismo?

## Sesión 7. Observer, Factory y State en un mismo caso

### ¿Qué aprenderás en esta sesión? 💡

- Reconocer tres problemas clásicos de diseño.
- Elegir el patrón según el tipo de variación que quieres manejar.
- Diferenciar creación, comunicación y cambio de comportamiento.

### Actividad 12: Identifica el problema antes del patrón

Antes de nombrar patrones, relaciona cada situación con el problema que resuelve:

- Quieres avisar a varios objetos cuando cambia un evento.
- Quieres crear variantes de un objeto sin repartir `new` por todo el programa.
- Quieres que un objeto cambie su comportamiento según su estado actual.

### Actividad 13: Observer

Piensa en una aplicación donde una clase principal recibe entrada del usuario y varias entidades reaccionan a ella.

Responde:

- ¿quién sería el sujeto?
- ¿quiénes serían los observadores?
- ¿qué evento se notificaría?
- ¿qué pasaría si la clase principal tuviera que cambiar manualmente cada objeto uno por uno?

### Actividad 14: Factory

Supón que el sistema puede crear `star`, `planet` y `shooting_star`.

Responde:

- ¿qué gana el sistema si toda la construcción vive en una sola factory?
- ¿qué se modifica cuando aparece un nuevo tipo?
- ¿qué parte del código cliente no debería cambiar?

### Actividad 15: State

Imagina una partícula que puede estar en modo `normal`, `attract`, `repel` o `stop`.

Responde:

- ¿qué problema aparece si todo eso se resuelve con un `switch` enorme dentro de una sola clase?
- ¿qué cambia si cada estado se mueve a una clase diferente?
- ¿qué responsabilidad tendría el contexto y cuál tendría cada estado concreto?

<aside>
📤

**Bitácora**

- Construye una tabla comparativa entre Observer, Factory y State.
- Para cada patrón, escribe: problema, idea central, ventaja principal y ejemplo en el caso de estudio.
- Dibuja al menos un diagrama simple de interacción o de estados.
- Explica cuál de los tres patrones te parece más útil para extender un sistema interactivo y por qué.

</aside>
