# Unidad 1

## 🤔 Fase: Reflect

### Actividad 05

#### Parte 1

Describe con tus palabras las tres fases del ciclo Fetch-Decode-Execute. ¿Qué rol juega el Program Counter (PC) en este ciclo?
- Se toma el código para analizar
- Se lee y decodifica lo que se está intentando comunicar con cada instrucción
- Se ejecuta la instrucción
¿Cuál es la diferencia fundamental entre una instrucción-A (que empieza con @) y una instrucción-C (que involucra D, M, A, etc.) en el lenguaje ensamblador de Hack? Da un ejemplo de cada una.
- Una instrucción-A es principalmente la que almacena valores de la ROM en dirección A
``` asm
@10
```
- Una instrucción-C es la que puede almacenar valores en las direcciones A y D así como enviar valores a la memoria RAM
```
D=A
M=D
```
Explica la función de los siguientes componentes del computador Hack: el registro D, el registro A y la ALU.
- Registro A es el principal que almacena valores principalmente en la ROM su nombre significaba algo
- Registro D solo es un segundo registro que también puede almacenar en la memoria RAM, por costumbre se llama D y no B
- ALU no recuerdo qué era
¿Cómo se implementa un salto condicional en Hack? Describe un ejemplo (p. ej., saltar si el valor de D es mayor que cero).
- Con un 0;JMP al final de una instrucción
```
D=1
0;JMP
```
¿Cómo se implementa un loop en el computador Hack? Describe un ejemplo (p. ej., un loop que decremente un valor hasta que llegue a cero).
- Creo que era con D;JLT y 0;JMP con un label pero no me acuerdo lo suficiente como para dar un ejemplo
¿Cuál es la diferencia entre la instrucción D=M y la instrucción M=D?
- D=M toma el valor de la memoria RAM y se lo da al registro D, M=D Toma el valor del registro D y se lo almacena a la memoria RAM
Describe brevemente qué se necesita para leer un valor del teclado (KBD) y para “pintar” un pixel en la pantalla (SCREEN).
- Realizar un loop donde se verifique que @KBD sea distinto de cero al tomar el valor de la tecla presionada, después se ejecuta la instrucción en un bucle para rellenar toda la pantalla
