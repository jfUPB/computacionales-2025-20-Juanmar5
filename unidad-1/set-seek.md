# Unidad 1

## 🔎 Fase: Set + Seek



### ¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute?
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


### ¿Qué valor se almacena en la dirección de memoria 16? ¿Por qué crees que es ese valor?
Por lo que entendí, el valor se almacena en la línea 16 porque A estaba en 16 y A corresponde a Address porque así fue hecho el PC
El valor es 3 porque es el valor que tenía D


### Programa en lenguaje ensablador que sume los números 5 y 10, y almacene el resultado en la dirección de memoria 20.
``` asm
@5
D=A
@10
D=D+A
@20
M=D
```


### Diferencias ROM y RAM
En la ROM van las funciones o la receta (como en los juegos retro) mientras que en la RAM va la memoria y resultados almacenados de la ROM, que se crean o cocinan dentro de los registros
