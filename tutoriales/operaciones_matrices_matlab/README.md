# Operaciones con matrices en MATLAB

## Introducción
MATLAB® tiene dos tipos diferentes de operaciones aritméticas: operaciones con arreglos y operaciones con matrices. Puede utilizar estas operaciones aritméticas para realizar cálculos numéricos, por ejemplo, sumar dos números, elevar los elementos de un arreglo a una determinada potencia o multiplicar dos matrices.

Las operaciones con matrices siguen las reglas del álgebra lineal. Por el contrario, las operaciones con arreglos ejecutan operaciones elemento por elemento y admiten arreglos multidimensionales. El carácter de punto (.) distingue las operaciones con arreglos de las operaciones con matrices. Sin embargo, debido a que las operaciones con matrices y arreglos son las mismas para la adición y la sustracción, los pares de caracteres .+ y .- son innecesarios.

## Operaciones con matrices
Las operaciones con matrices siguen las reglas del álgebra lineal y no son compatibles con arreglos multidimensionales. El tamaño y la forma necesarios de las entradas relacionadas entre sí dependen de la operación. En caso de entradas no escalares, los operadores de matrices por lo general calculan diferentes respuestas a las de sus homólogos de los operadores de arreglos.

Por ejemplo, si utiliza el operador de división derecha de matriz, /, para dividir dos matrices, estas deben tener el mismo número de columnas. Sin embargo, si utiliza el operador de multiplicación de matriz, *, para multiplicar dos matrices, las matrices deben tener una dimensión interna común. Es decir, el número de columnas de la primera entrada debe ser igual al número de filas de la segunda entrada. El operador de multiplicación de matriz calcula el producto de dos matrices con la fórmula, ![Formula](https://latex.codecogs.com/png.latex?C(i,j)=\sum_{k=1}^{n}A(i,k)B(k,j))

Para comprobarlo, puede calcular el producto de dos matrices.

```matlab
A = [1 3;2 4]
```

```matlab
A =

     1     3
     2     4
```

```matlab
B = [3 0;1 5]
```

```matlab
B =

     3     0
     1     5
```

```matlab
A*B
```

```matlab
ans =

     6    15
    10    20
```

El producto anterior de las matrices no es igual al siguiente producto elemento por elemento.

```matlab
A.*B
```

```matlab
ans =

     3     0
     2    20
```

La siguiente tabla proporciona un resumen de los operadores aritméticos de matrices en MATLAB. Para obtener información específica de la función, haga clic en el enlace a la página de referencia de la función en la última columna.

| Operador | Finalidad                         | Descripción                                                                               | Página de referencia |
|----------|-----------------------------------|-------------------------------------------------------------------------------------------|----------------------|
| *        | Multiplicación de matrices        | C = A*B es el producto algebraico lineal de las matrices A y B. El número de columnas de A debe ser igual al número de filas de B. | <a href="https://la.mathworks.com/help/matlab/ref/mtimes.html" target="_blank">mtimes</a> |
| \        | División izquierda de matrices    | x = A\B es la solución a la ecuación Ax = B. Las matrices A y B deben tener el mismo número de filas. | <a href="https://la.mathworks.com/help/matlab/ref/mldivide.html" target="_blank">mldivide</a> |
| /        | División derecha de matrices      | x = B/A es la solución a la ecuación xA = B. Las matrices A y B deben tener el mismo número de columnas. En términos del operador de división izquierda, B/A = (A'\B')'. | <a href="https://la.mathworks.com/help/matlab/ref/mrdivide.html" target="_blank">mrdivide</a> |
| ^        | Potencia de matrices              | A^B es A a la potencia B, si B es un escalar. En otros valores de B, el cálculo implica valores y vectores propios. | <a href="https://la.mathworks.com/help/matlab/ref/mpower.html" target="_blank">mpower</a> |
| '        | Traspuesta conjugada compleja     | A' es la traspuesta algebraica lineal de A. En matrices complejas, esta es la traspuesta conjugada compleja. | <a href="https://la.mathworks.com/help/matlab/ref/ctranspose.html" target="_blank">ctranspose</a> |
