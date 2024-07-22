# Operaciones con arreglos en MATLAB

# Introducción
MATLAB® tiene dos tipos diferentes de operaciones aritméticas: operaciones con arreglos y operaciones con matrices. Puede utilizar estas operaciones aritméticas para realizar cálculos numéricos, por ejemplo, sumar dos números, elevar los elementos de un arreglo a una determinada potencia o multiplicar dos matrices.

Las operaciones con matrices siguen las reglas del álgebra lineal. Por el contrario, las operaciones con arreglos ejecutan operaciones elemento por elemento y admiten arreglos multidimensionales. El carácter de punto (.) distingue las operaciones con arreglos de las operaciones con matrices. Sin embargo, debido a que las operaciones con matrices y arreglos son las mismas para la adición y la sustracción, los pares de caracteres .+ y .- son innecesarios.

# Operaciones con arreglos
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