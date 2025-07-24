# Unidad 1

## 🔎 Fase: Set + Seek

### Actividada 1 

¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute?
En la PC en cuestión hay dos registros, A (de Address) y D  
``` asm
0 -> A se vuelve 1;
1 -> D obtiene el valor de A
2 -> A se vuelve 2
3 -> D obtiene el valor de la suma de sí mismo con A (3)
4 -> A pasa a 16
5 -> La memoria guarda el valor de D en la dirección RAM correspondiente al valor de A (RAM 16 = 3)
6 -> A se vuelve el valor de END (7)
Se crea una etiqueta o label arriba de la línea final marcándola como "END", como es la instrucción 7 entonces toma ese valor
7 -> Antes del ";" genera un cero en la calculadora aritmeticológica pero no lo usa, después genera una función JUMP que hace un salto incondicional al valor que tenga la A (que es 7), el 0 solo es parte del formato de la función JUMP
```


¿Qué valor se almacena en la dirección de memoria 16? ¿Por qué crees que es ese valor?
Por lo que entendí, el valor se almacena en la línea 16 porque A estaba en 16 y A corresponde a Address porque así fue hecho el PC
El valor es 3 porque es el valor que tenía D


Programa en lenguaje ensablador que sume los números 5 y 10, y almacene el resultado en la dirección de memoria 20.
``` asm
@5
D=A
@10
D=D+A
@20
M=D
```

### Actividada 2


Diferencias ROM y RAM
En la ROM van las funciones o la receta (como en los juegos retro) mientras que en la RAM va la memoria y resultados almacenados de la ROM, que se crean o cocinan dentro de los registros


Instrucción ALU

```
M=M-1
```
Usa la ALU para restar 1 al valor almacenamiento de la dirección actual



Registro PC Para qué es
Guarda la dirección de la siguiente instrucción que se va a ejecutar


Diferencias @i y @READKEYBOARD
@i es una variable declarada que toma el valor de memoria de 16 mientras que @READKEYBOARD es una etiqueta o label que guarda la posición de la orden


Para leer el teclado
en el registro KBD se guarda el valor de la tecla presionada y se busca que sea distinto de 0


Identifica un bucle
``` asm
(READKEYBOARD)
@READKEYBOARD
0;JMP
```
El programa ejecuta la instrucción y salta a la instrucción en la que estaba el label


Identifica una condición
``` asm
@KBD
D=M
@KEYPRESSED
D;JNE
```
El valor de KBD se guarda en D y se busca que sea distinto de cero, si sí, salta a la etiqueta de KEYPRESSED
