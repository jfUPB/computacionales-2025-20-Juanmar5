# Unidad 3

## 🔎 Fase: Set + Seek

### Actividad 1
##### ¿Para qué sirven los breakpoints?
- Los breakpoints se usan para pausar la ejecución del programa de línea en línea para analizarlo y verificar que los valores están bien y no hallan errores. 
##### ¿Para qué se usa la ventana de depuración Autos?
- Muestra las variables relacionadas con la línea de código que se está ejecutando, ayuda a monitorear valores de variables y ver cómo van cambiando.

### Actividad 2
##### Código
``` c++
#include <iostream>
using namespace std;

void swapPorValor(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
    cout << "Dentro de swapPorValor: a = " << a << ", b = " << b << endl;
}

void swapPorReferencia(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
    cout << "Dentro de swapPorReferencia: a = " << a << ", b = " << b << endl;
}

void swapPorPuntero(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
    cout << "Dentro de swapPorPuntero: a = " << *a << ", b = " << *b << endl;
}

int main() {
    int x = 10, y = 20;

    cout << "Valores iniciales: x = " << x << ", y = " << y << endl;

    cout << "\n== Intercambio por Valor ==" << endl;
    swapPorValor(x, y);
    cout << "Después de swapPorValor: x = " << x << ", y = " << y << endl;

    cout << "\n== Intercambio por Referencia ==" << endl;
    swapPorReferencia(x, y);
    cout << "Después de swapPorReferencia: x = " << x << ", y = " << y << endl;

    cout << "\n== Intercambio por Puntero ==" << endl;
    swapPorPuntero(&x, &y);
    cout << "Después de swapPorPuntero: x = " << x << ", y = " << y << endl;

    return 0;
}
```
##### Resultado
```
Valores iniciales: x = 10, y = 20

== Intercambio por Valor ==
Dentro de swapPorValor: a = 20, b = 10
Despu├®s de swapPorValor: x = 10, y = 20

== Intercambio por Referencia ==
Dentro de swapPorReferencia: a = 20, b = 10
Despu├®s de swapPorReferencia: x = 20, y = 10

== Intercambio por Puntero ==
Dentro de swapPorPuntero: a = 10, b = 20
Despu├®s de swapPorPuntero: x = 10, y = 20
```
Desconozco por qué la 'é' salió así

### Actividad 3
##### Mapa de memoria
+----------------------------+
| Segmento de código (Text) |
|----------------------------|
| Funciones:                |
|  - main()                 |
|  - suma()                 |
|  - funcionConStatic()     |
|  - crearArrayHeap()       |
+----------------------------+

| Variables globales y estáticas |
|-------------------------------|
| global_inicializada = 42     |
| global_no_inicializada       |
| mensaje_ro (puntero constante a char) |
| var_estatica (dentro de funcionConStatic) |
+-------------------------------+

| Heap (asignación dinámica)   |
|-------------------------------|
| arrayHeap → apunta a bloque  |
| de 10 enteros creados con     |
| new int[tam]                 |
+-------------------------------+

| Stack (pila)                 |
|-------------------------------|
| Variables locales de main(): |
|  - a, b, c                   |
| Variables locales de suma(): |
|  - c                         |
| Parámetros pasados por valor |
|  - a, b (en suma)            |
+-------------------------------+

| Segmento de solo lectura     |
|-------------------------------|
| "Hola, memoria de solo lectura" |
+-------------------------------+


### Actividad 04
##### Experimento 1:

¿Qué pasa?
- Intentar escribir allí provoca una excepción.

##### Experimento 2: 

¿Qué pasa?
- También da error, los literales de cadena están en el segmento de solo lectura.

##### Experimento 3

¿Qué pasa?
- Funciona, los valores de las variables cambian y se imprimen actualizados. Se guardan en el segmento de datos, el cual es de lectura y escritura.

##### Experimento 4:

¿Qué pasa?
- No compila, var_estatica no es visible fuera de la función, tiene ámbito local

¿Qué pasa con las variables cada que entras y sales de la función?
- Las variables locales normales se crean y destruyen cada vez que entras/sales de la función.
- Las variables estáticas locales se crean solo una vez y mantienen su valor entre llamadas.

##### Experimento 5:

¿Qué pasa?
- var_no_estatica siempre vale 100 porque se crea de nuevo en cada llamada.
- var_estatica empieza en 100 y va aumentando con cada llamada (101, 102, 103...).

¿Por qué?
- Una variable local sin static se almacena en el stack y desaparece al salir de la función.
- Una variable local con static se almacena en el segmento de globales/estáticas y conserva su valor.

##### Experimento 6

¿Qué pasa?
- Se produce comportamiento indefinido: puede imprimir basura, un número aleatorio o causar error.
- Acceder a memoria liberada es un dangling pointer

##### Preguntas

¿Diferencias entre Heap y Stack?
- Stack: automático, rápido, limitado en tamaño, variables se crean y destruyen al entrar/salir de funciones.
- Heap: manual, más flexible, se mantiene hasta que se libere con delete, pero más lento y propenso a errores.

¿Consecuencias de no liberar memoria con delete?
- Se produce una fuga de memoria (memory leak). El sistema no recupera esa memoria hasta que el programa termine.

¿Por qué usar delete[] para arreglos?
- Porque new[] reserva memoria para varios elementos consecutivos y delete[] libera correctamente todo el bloque.
- Usar solo delete en un arreglo produce comportamiento indefinido.
