# Operaciones con arreglos en MATLAB

## Introducción
MATLAB® tiene dos tipos diferentes de operaciones aritméticas: operaciones con arreglos y operaciones con matrices. Puede utilizar estas operaciones aritméticas para realizar cálculos numéricos, por ejemplo, sumar dos números, elevar los elementos de un arreglo a una determinada potencia o multiplicar dos matrices.

Las operaciones con matrices siguen las reglas del álgebra lineal. Por el contrario, las operaciones con arreglos ejecutan operaciones elemento por elemento y admiten arreglos multidimensionales. El carácter de punto (.) distingue las operaciones con arreglos de las operaciones con matrices. Sin embargo, debido a que las operaciones con matrices y arreglos son las mismas para la adición y la sustracción, los pares de caracteres .+ y .- son innecesarios.

## Operaciones con arreglos
Las operaciones con arreglos ejecutan operaciones elemento por elemento en los elementos correspondientes de los vectores, las matrices y los arreglos multidimensionales. Si los operandos tienen el mismo tamaño, cada elemento del primer operando coincide con el elemento de la misma ubicación en el segundo operando. Si los operandos tienen tamaños compatibles, cada entrada se amplía de manera implícita según sea necesario para hacer que coincida con el tamaño del otro. Para obtener más información, consulte <a href="https://la.mathworks.com/help/matlab/matlab_prog/compatible-array-sizes-for-basic-operations.html" target="_blank">Tamaños de arreglos compatibles para operaciones básicas</a>.

Como ejemplo sencillo, puede sumar dos vectores con el mismo tamaño.

```matlab
A = [1 1 1]
```
```matlab
A =

     1     1     1
```
```matlab
B = [1 2 3]
```
```matlab
B =

     1     2     3
```
```matlab
A+B
```
```matlab
ans =

     2     3     4
```

Si un operando es un escalar y el otro no, MATLAB amplía el escalar de manera implícita para que sea del mismo tamaño que el otro operando. Por ejemplo, puede calcular el producto elemento por elemento de un escalar y una matriz.

```matlab
A = [1 2 3; 1 2 3]
```

```matlab
A =

     1     2     3
     1     2     3
```

```matlab
3.*A
```

```matlab
ans =

     3     6     9
     3     6     9
```

La expansión implícita también funciona si se resta un vector de 1 por 3 de una matriz de 3 por 3, ya que los dos tamaños son compatibles. Al llevar a cabo la resta, el vector se ha ampliado de manera implícita para convertirlo en una matriz de 3 por 3.

```matlab
A = [1 1 1; 2 2 2; 3 3 3]
```

```matlab
A =

     1     1     1
     2     2     2
     3     3     3
```

```matlab
m = [2 4 6]
```

```matlab
m =

     2     4     6
```

```matlab
A - m
```

```matlab
ans =

    -1    -3    -5
     0    -2    -4
     1    -1    -3
```
Un vector fila y un vector columna tienen tamaños compatibles. Si suma un vector de 1 por 3 y un vector de 2 por 1, cada vector se amplía de manera implícita a una matriz de 2 por 3 antes de que MATLAB ejecute la suma elemento por elemento.
```matlab
x = [1 2 3]
```

```matlab
x =

     1     2     3
```

```matlab
y = [10; 15]
```

```matlab
y =

    10
    15
```

```matlab
x + y
```

```matlab
ans =

    11    12    13
    16    17    18
```

Si los tamaños de los dos operandos son incompatibles, obtiene un error.

```matlab
A = [8 1 6; 3 5 7; 4 9 2]
```

```matlab
A =

     8     1     6
     3     5     7
     4     9     2
```

```matlab
m = [2 4]
```

```matlab
m =

     2     4
```

```matlab
A - m
```

```matlab
Matrix dimensions must agree.
```

La siguiente tabla proporciona un resumen de los operadores aritméticos de arreglos en MATLAB. Para obtener información específica de la función, haga clic en el enlace a la página de referencia de la función en la última columna.

| Operador | Finalidad                         | Descripción                                                                               | Página de referencia |
|----------|-----------------------------------|-------------------------------------------------------------------------------------------|----------------------|
| +        | Adición                           | A+B suma A y B.                                                                           | <a href="https://la.mathworks.com/help/matlab/ref/plus.html" target="_blank">plus</a> |
| +        | Más unario                        | +A devuelve A.                                                                            | <a href="https://la.mathworks.com/help/matlab/ref/uplus.html" target="_blank">uplus</a> |
| -        | Sustracción                       | A-B resta B de A                                                                          | <a href="https://la.mathworks.com/help/matlab/ref/minus.html" target="_blank">minus</a> |
| -        | Menos unario                      | -A niega los elementos de A.                                                              | <a href="https://la.mathworks.com/help/matlab/ref/uminus.html" target="_blank">uminus</a> |
| .*       | Multiplicación elemento por elemento | A.*B es el producto elemento por elemento de A y B.                                        | <a href="https://la.mathworks.com/help/matlab/ref/times.html" target="_blank">times</a> |
| .^       | Potencia elemento por elemento    | A.^B es la matriz con los elementos A(i,j) a la potencia B(i,j).                           | <a href="https://la.mathworks.com/help/matlab/ref/power.html" target="_blank">power</a> |
| ./       | División derecha de arreglos      | A./B es la matriz con los elementos A(i,j)/B(i,j).                                        | <a href="https://la.mathworks.com/help/matlab/ref/rdivide.html" target="_blank">rdivide</a> |
| .\       | División izquierda de arreglos    | A.\B es la matriz con los elementos B(i,j)/A(i,j).                                        | <a href="https://la.mathworks.com/help/matlab/ref/ldivide.html" target="_blank">ldivide</a> |
| .'       | Trasposición de arreglos          | A.' es la traspuesta de arreglos de A. En matrices más complejas, esta no implica conjugación. | <a href="https://la.mathworks.com/help/matlab/ref/transpose.html" target="_blank">transpose</a> |
