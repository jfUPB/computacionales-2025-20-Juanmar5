# Bitácora de aprendizaje de la unidad 5

## 1.  **Diagnóstico inicial**
- Estoy medio olvidado y perdido con todos los temas de POO

## 2.  **La pregunta inicial**
- ¿Cómo podré recordar los conceptos de herencia y polimorfismo para volverlos a aplicar al nuevo contexto?

## 3.  **Registro de exploración:** 
- Aquí documentas cada ciclo de pregunta -> hipótesis -> experimento -> hallazgo -> reflexión.
- Debe ser rico en evidencia visual (código, capturas del depurador con anotaciones, diagramas).

## Parte 1: recordando los conceptos (en C#)

¿Qué es el encapsulamiento para ti? Describe una situación en la que te haya sido útil o donde hayas visto su importancia.
- La encapsulación en Java es un principio que consiste en agrupar y métodos de un objeto dentro de una sola clase para poderse controlar desde una interfaz
- Recuerdo alguna vez haber utilizado encapsulamiento para determinar si los productos de un supermercado ficticio tenían tipos de clasificaciones que se pudieran cambiar o no por un método que se llamaba con input del usuario.
¿Qué es la herencia? ¿Por qué un programador decidiría usarla? Da un ejemplo simple.
- La herencia es cuando creas una clase derivada de otra clase que ya existía y esta toma sus atributos como suyos junto a otros específicos a esa sub clase. Es super útil para cosas como objetos con anomalías ligeras de una taxonomía o clasificar especies de animales por ejemplo
- Ejemplo:
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
¿Qué es el polimorfismo? Describe con tus palabras qué significa que un código sea “polimórfico”.
- Que podemos escribir código que trabaje con objetos de distintas clases de forma uniforme, sin importar su tipo específico, siempre y cuando compartan una interfaz común. Esto hace que el código sea más flexible y extensible.

## Parte 2: Análisis de código
*Encapsulamiento/

- Ejemplo de encapsulamiento:

``` public string Nombre
{
    get { return nombre; }
    protected set { nombre = value; }
}
```

Aquí nombre está declarado como private, pero se expone por la propiedad Nombre.
Esto es encapsulamiento porque el detalle interno queda oculto.

- ¿Por qué nombre es private y Nombre es public?

Porque así evitas que desde afuera se pueda cambiar libremente
La propiedad Nombre controla cómo se accede: getter público pero escritura setter solo permitido dentro de su propia clase o clases hijas.

**Herencia**

- ¿Cómo se evidencia la herencia en Circulo?

```
public class Circulo : Figura
```

El : Figura es que Circulo hereda de Figura.
Gracias a eso, Circulo puede usar el constructor de Figura (base("Círculo")) y agrega el método Dibujar().

- Además de Radio, qué datos almacena Circulo?

Gracias a heredar de Figura, también tiene el campo nombre (a través de la propiedad Nombre).
O sea, internamente un Circulo tiene:

Radio
Nombre

**Polimorfismo**

- Cómo creo que funciona por debajo:

Quizá cada clase tenga como una "tabla" interna de direcciones de memoria que le diga qué es qué y así.
Cuando llamas a Dibujar, el programa busca en esa tabla cuál es el Código o función que le debe meter al objeto de esa clase y salta a ese Código, como un indicador.

## Parte 3: Hipótesis sobre la implementación
**Memoria y herencia**
- Me imagino que el Nombre iría primero, como designante de toda la instanciación, después de sus atributos que tomarían herencia de una superclase


**Mecanismo del polimorfismo**
- Yo pensaría que si no hay variable de booleano que determine que si es rectángulo true o elseif círculo o una string, entonces quizá podría detectarlo basado en si tiene atributos de herencia "radio" o "base, altura".

**La barrera del encapsulamiento**
- Yo creo que la protección private se revisa principalmente en compilación. El compilador ya sabe qué miembros son accesibles desde dónde y te da error si intentas romper la regla.

## Parte 4: Autoevaluación y primeras preguntas

Encapsulamiento: entendí que sirve para proteger el estado interno de un objeto.
Herencia: vi cómo los objetos “heredan” no solo métodos, sino también datos.
Polimorfismo: razoné que hay algún mecanismo interno (tipo tabla de funciones) que hace posible que Dibujar() se resuelva dinámicamente.

Primera pregunta para iniciar mi ruta personal:
- ¿Cómo se ve en la memoria un objeto con herencia en C#?
