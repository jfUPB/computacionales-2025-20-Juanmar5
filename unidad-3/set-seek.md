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

### Actividad 3 (temporal, no final)
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
