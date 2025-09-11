# Bitácora de aprendizaje de la unidad 5

## 1.  **Diagnóstico inicial**

## 2.  **La pregunta inicial**

## 3.  **Registro de exploración:** 
> Aquí documentas cada ciclo de pregunta -> hipótesis -> experimento -> hallazgo -> reflexión.
> Debe ser rico en evidencia visual (código, capturas del depurador con anotaciones, diagramas).

Parte 1: recordando los conceptos (en C#)

¿Qué es el encapsulamiento para ti? Describe una situación en la que te haya sido útil o donde hayas visto su importancia.
> La encapsulación en Java es un principio que consiste en agrupar y métodos de un objeto dentro de una sola clase para poderse controlar desde una interfaz
> Recuerdo alguna vez haber utilizado encapsulamiento para determinar si los productos de un supermercado ficticio tenían tipos de clasificaciones que se pudieran cambiar o no por un método que se llamaba con input del usuario.
¿Qué es la herencia? ¿Por qué un programador decidiría usarla? Da un ejemplo simple.
> La herencia es cuando creas una clase derivada de otra clase que ya existía y esta toma sus atributos como suyos junto a otros específicos a esa sub clase. Es super útil para cosas como objetos con anomalías ligeras de una taxonomía o clasificar especies de animales por ejemplo
> Ejemplo:
``` C++
#include <iostream>
using namespace std;

// Clase base
class Animal {
public:
    void comer() {
        cout << "El animal está comiendo." << endl;
    }

    void dormir() {
        cout << "El animal está durmiendo." << endl;
    }
};

// Clase derivada
class Perro : public Animal {
public:
    void ladrar() {
        cout << "El perro está ladrando." << endl;
    }
};

int main() {
    Perro miPerro;

    // Métodos heredados de Animal
    miPerro.comer();
    miPerro.dormir();

    // Método propio de Perro
    miPerro.ladrar();

    return 0;
}
```
¿Qué es el polimorfismo? Describe con tus palabras qué significa que un código sea “polimórfico”.]
> Que podemos escribir código que trabaje con objetos de distintas clases de forma uniforme, sin importar su tipo específico, siempre y cuando compartan una interfaz común. Esto hace que el código sea más flexible y extensible.


## 4.  **Consolidación, autoevaluación y cierre:**
> [!CAUTION]
> Esta sección es OBLIGATORIA y central para tu evaluación
