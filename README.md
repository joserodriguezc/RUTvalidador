# RUTvalidador
Función para validar un número de RUT/RUN

En Chile el dígito verificador es único para cada RUT, éste se calcula con un algoritmo conocido como “módulo 11”

Módulo 11 
Se basa en aplicar un factor de chequeo ponderado a cada dígito del número original. El cálculo se realiza como sigue:

1. A cada dígito del número base se le asigna un factor de chequeo ponderado. Dicho factor será 2 para el dígito menos significativo (el que está más a la derecha) y, en orden, 3, 4, 5, 6, 7 para los siguientes. Si hubiera más de 6 dígitos la secuencia se repetiría de modo que el séptimo dígito se multiplicaría por 2, el octavo por 3, etc.
2. Cada dígito del número base se multiplica por el factor de chequeo asignado.
3. Se suman los resultados de todas las multiplicaciones.
4. Al resultado de la suma se le calcula el módulo 11 (de ahí el nombre del método), es decir, el resto de la división entera entre 11.
5. A 11 se le resta el módulo calculado en el punto anterior. Si el resultado de la resta es < 10, dicho resultado es el dígito de control que buscábamos. Si el resultado es 11 el dígito de control es 0 y si el resultado es 10 el dígito de control resultante es 1.

El siguiente esquema desarrolla un ejemplo de cálculo:

Número ejemplo: 41261533-?

Pasos 1 y 2  
 = 4x3 + 1x2 + 2x7 + 6x6 + 1x5 + 5x4 + 3x3 + 3x2   

Paso 3   12 + 2 + 14 + 36 + 5 + 20 + 9 + 6 = 104

Paso 4   104 mod 11 = 5 

Paso 5   11 - 5 = 6

Resultado = 41261533-6

A veces se usan variantes, como sustituir el resultado por una letra cuando el resultado es 10. Por ejemplo, en Chile el Rol Único Nacional (RUN) y el Rol Único Tributario (RUT) utilizan este sistema y cuando el resultado del algoritmo es 10 el carácter de control es la letra "K".
