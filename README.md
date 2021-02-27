# Organizacion de Lenguajes y Compiladores 2
Marcos Sebastian Velasquez Cabrera
201612190

# Examen Corto 2
Escribir un esquema de traducción dirigido por la sintaxis posfijo, para un analizador ascendente que reciba como entrada una expresión aritmética (\*,+,-,/ y paréntesis) y genere para esta el código de tres direcciones equivalente.
Para este ejercio se utilizaron las herramientos de Jlex y Cup para poder generar los anlizadores léxico y sintáctico.

## Analizador Léxico
El analizador léxico se elaboró en el archivo "Lexico". Se definen dos expresiones regulares, las cuales se encargan de formar tokens con los numeros y los posibles id que puedan ingresar en la expresión aritmética.
Se definen los tokens que acepta el analizdor (paréntesis, +,-,/,\*,identificadores y números) y lo que no esté definido, se considerará como un error léxico.
![lexico](https://user-images.githubusercontent.com/33238225/109378338-4c464300-7897-11eb-82c2-dab1f0194a1d.png)

## Analizador Sintáctico
El analizador sintáctico se elaboró en el archivo "Sintactico". En la sección "parser code" se define una variable global "contador" que se encargará de colocar un índica a cada sub-expresión generada. También se definen los métodos que se llaman al momento de encontrar un error sintáctico.
Posteriormente se definen los terminales y no terminales de la gramática, así como la precedencia de los operadores. La gramática iniciará con el no terminal *S*
![sintactico1](https://user-images.githubusercontent.com/33238225/109378345-5ec07c80-7897-11eb-960a-8ff213b217a1.png)

En la siguiente sección del analizador sintáctico, nos encontramos en la gramática, que es la siguiente:
<br />
![x1](https://user-images.githubusercontent.com/33238225/109378685-31290280-789a-11eb-8155-36b90ba9f9d7.png)
<br />

En cada una de las producciones se colocó el esquema de traducción para poder generar el código de tres direcciones. Para generar el codigo de tres direcciones, encada una de las operaciones, se imprime la expresión evaluada, y se retorna el índice de la misma para poder evaluarlo más adelante si es necesario.
<br />
![sintactico2](https://user-images.githubusercontent.com/33238225/109378352-6849e480-7897-11eb-81bb-5632e8c02b3d.png)
<br />
![sintactico3](https://user-images.githubusercontent.com/33238225/109378354-6da72f00-7897-11eb-8905-54e7ad68c3d5.png)
<br />

## Ejemplos de entrada
### (a + b) \* (a + c)
![a1](https://user-images.githubusercontent.com/33238225/109380806-a8f82c80-789c-11eb-9903-23015fca6563.png)

### x \* x
![a2](https://user-images.githubusercontent.com/33238225/109380828-b8777580-789c-11eb-8647-282f17e3cf9f.png)

### y \* y
![a3](https://user-images.githubusercontent.com/33238225/109380850-bf9e8380-789c-11eb-8f3f-a2aedb42dbc7.png)

### x2 + y2
![a4](https://user-images.githubusercontent.com/33238225/109380887-caf1af00-789c-11eb-843c-a6d078daf7d3.png)

### b + c + d
![a5](https://user-images.githubusercontent.com/33238225/109380893-d218bd00-789c-11eb-995b-8bcb8b24703c.png)

### a * a + b * b
![a6](https://user-images.githubusercontent.com/33238225/109380897-dcd35200-789c-11eb-859b-15e9fc7c2a18.png)

### 5 + 2 * b
![a7](https://user-images.githubusercontent.com/33238225/109380903-e65cba00-789c-11eb-9c90-9fc5b2f3eb5e.png)

### 6 + 7 * 10+5 / 1
![a8](https://user-images.githubusercontent.com/33238225/109380915-f1174f00-789c-11eb-949f-330d9714dbfd.png)

### ((7 + 9)/(((3 + 1) * (6 + 7) + 8) * 7) / 9) + 100
![a9](https://user-images.githubusercontent.com/33238225/109380922-f96f8a00-789c-11eb-9af6-2848f818e651.png)

### 7 * 9 - 89 + 63
![b1](https://user-images.githubusercontent.com/33238225/109380931-055b4c00-789d-11eb-8576-03eb32634ce7.png)
