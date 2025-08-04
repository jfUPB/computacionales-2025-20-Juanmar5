# Unidad 2

## 🔎 Fase: Set + Seek

### Actividad 1

##### Programa Ensamblador
Escribe un programa que dibuje un punto negro en la esquina superior izquierda de la pantalla.
``` asm
@SCREEN
M=1
(END)
@END
0;JMP
```

##### Programa C++

``` c++
#include <iostream>
#include <cstdint>
using namespace std;

const int SCREEN = 16384;
uint16_t memory[32768];

int main() {
    memory[SCREEN] = 1;
    cout << "Pixel (0,0) encendido: " << memory[SCREEN] << endl;
    return 0;
}

```

### Actividad 2

##### Programa Ensamblador
Modifica el programa anterior para que dibuje una línea horizontal negra de 16 pixeles de largo en la esquina superior izquierda de la pantalla

``` asm
@SCREEN
M=-1
(END)
@END
0;JMP
```

##### Programa C++

```
#include <iostream>
#include <cstdint>
using namespace std;

const int SCREEN = 16384;
uint16_t memory[32768];

int main() {
    memory[SCREEN] = 0xFFFF;
    cout << "Word en SCREEN: ";
    for (int i = 15; i >= 0; --i) {
        cout << ((memory[SCREEN] >> i) & 1);
    } cout << endl;
    return 0;
}
```


