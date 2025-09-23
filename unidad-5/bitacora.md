# Bitácora de aprendizaje de la unidad 5

## 1.  **Diagnóstico inicial**
- Estoy medio olvidado y perdido con todos los temas de POO
- Creo que voy mejorando con los temas pero me confundo aún, igual, identifico mejor el polimorfismo y la encapsulación, me cuesta menos distinguirla

## 2.  **La pregunta inicial**
- ¿Cómo podré recordar los conceptos de herencia y polimorfismo para volverlos a aplicar al nuevo contexto?

## 3.  **Registro de exploración:** 
- Aquí documentas cada ciclo de pregunta -> hipótesis -> experimento -> hallazgo -> reflexión.
- Debe ser rico en evidencia visual (código, capturas del depurador con anotaciones, diagramas).

# Actividad 1

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


# Actividad 2

## ¿Qué identifiqué?

Particle Es una clase abstracta, todas las partículas deben poder tener update(), draw(), decir si están muertas (isDead()) y, en el caso de las que suben, indicar si deben explotar (shouldExplode()).

RisingParticle es la chispa que se va agrandando. Nace en la parte de abajo de la pantalla, con una velocidad que la impulsa hacia arriba., su movimiento se va frenando por la gravedad y al llegar a una altura se flaggea que ya puede explotar

Clases de explosión: (CircularExplosion, RandomExplosion, StarExplosion)

Cuando una RisingParticle explota, genera entre 20 y 30 partículas de explosión.
- CircularExplosion -> dibuja círculo
- RandomExplosion -> dibuja rectángulos
- StarExplosion -> dibuja líneas que forman una estrellita

- Con click -> crea una chispa que sube (RisingParticle).
- Con espacio -> crea 1000 partículas como de la nada
- Con tecla s -> guarda una captura de pantalla.


# Actividad 3

## dep


# Actividad 4

## Cod. 1
publicVar se puede modificar sin problema.
protectedVar y privateVar no deberían poder modificarse directamente desde main().
El compilador debería lanzar un error de acceso.
El encapsulamiento funciona en tiempo de compilación: el compilador impide que un código externo acceda a variables privadas o protegidas.


## Cod. 2
El compilador no permitirá el acceso a obj.secret1 porque es private.
error: 'int MyClass::secret1' is private within this context


## Cod. 3
Aunque secret1, secret2 y secret3 son privados, el reinterpret_cast deja caer a la memoria de obj y leerlos directamente.
El programa compila y ejecuta sin errores.


## Conclusión
El encapsulamiento NO es una barrera real en tiempo de ejecución.
En C++, un objeto es un bloque de memoria contiguo y usando punteros puedes saltarte las restricciones.
Lo que hace el compilador es proteger en el código fuente, no blindar físicamente la memoria.

## ¿Qué es el encapsulamiento?
El encapsulamiento es ocultar los atributos internos de una clase y exponer solo lo necesario a al instanciar con publics, privates y protecteds.

## ¿Por qué es importante?
Permite proteger los datos de modificaciones accidentales.
Asegura que el objeto solo se use de la forma que el programador diseñó.
Facilita el mantenimiento y la reutilización del código.


# Actividad 5

## CircularExplosion en memoria

Al inspeccionar el objeto CircularExplosion en el depurador se observa que:
- El objeto contiene los campos heredados de Particle, luego los campos añadidos por ExplosionParticle, y finalmente los propios de CircularExplosion.
- En la ventana Locals/Autos se refleja la jerarquía de clases expandida en árbol, y en Memory se ve como un bloque contiguo de direcciones.
- El primer campo corresponde al puntero a la vtable, lo que confirma el soporte de métodos virtuales.
Conclusión: la herencia se materializa en memoria como un único bloque que conecta las clases base y la clase derivada

## ¿Cómo se implementa la herencia en C++?
El compilador organiza la memoria de la clase derivada colocando primero los miembros de la clase base y luego los nuevos de la derivada.
Si existen métodos virtuales, se añade un puntero oculto a la _vtable que permite el polimorfismo.

## Experimento de herencia múltiple

Ejemplo:
``` c++
#include <iostream>
using namespace std;

class A { public: int a; A() : a(1) {} };
class B { public: int b; B() : b(2) {} };
class C : public A, public B { public: int c; C() : c(3) {} };

int main() {
    C obj;
    cout << obj.a << ", " << obj.b << ", " << obj.c << endl;
    return 0;
}


🔎 En el depurador:

El objeto obj aparece dividido en bloques: primero la parte de A, luego la parte de B, y finalmente los campos propios de C.
En memoria se ve como la concatenación de las estructuras de A, B y C.

Conclusión: en C++ la herencia múltiple se implementa agregando cada clase base como una sección distinta dentro del mismo objeto. Esto permite combinar varias jerarquías, aunque puede producir ambigüedades (por ejemplo, el problema del diamante), que se resuelven con herencia virtual.

```
