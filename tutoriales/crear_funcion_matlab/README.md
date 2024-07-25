# ¿Cómo crear una función en MATLAB?

## Sintaxis
**function [y1,...,yN] = myfun(x1,...,xM)**

## Descripción
**function [y1,...,yN] = myfun(x1,...,xM)** declara una función llamada myfun que acepta entradas x1,...,xM y devuelve salidas y1,...,yN. Esta instrucción de declaración debe ser la primera línea ejecutable de la función. Los nombres de función válidos comienzan con un carácter alfabético y pueden contener letras, números o guiones bajos.

Puede guardar la función:
- En un archivo de función que solo contenga definiciones de funciones. El nombre del archivo debe coincidir con el nombre de la primera función del archivo.
- En un archivo de script que contenga comandos y definiciones de funciones. Las funciones deben estar al final del archivo. Los archivos de script no pueden tener el mismo nombre que una función del archivo. Las funciones son compatibles con los scripts a partir de la versión R2016b.

Los archivos pueden incluir varias funciones locales o funciones anidadas. Para facilitar la lectura, utilice la palabra clave end para indicar el final de cada función en un archivo. La palabra clave end es obligatoria cuando:
- Una función del archivo contiene una función anidada.
- La función es una función local dentro de un archivo de función, y cualquier función local del archivo utiliza la palabra clave *end*.
- La función es una función local dentro de un archivo de script.

## Ejemplos

### Función con una salida
Defina una función en un archivo llamado `calculateAverage.m` que acepte un vector de entrada, calcule la media de los valores y devuelva un único resultado.

```matlab
function ave = calculateAverage(x)
    ave = sum(x(:))/numel(x); 
end
```
Llame a la función desde la línea de comandos.
```matlab
z = 1:99;
ave = calculateAverage(z)

ave =
    50
```
### Función con varias salidas
Defina una función en un archivo llamado `stat.m` que devuelva la media y la desviación estándar de un vector de entrada.
```matlab
function [m,s] = stat(x)
    n = length(x);
    m = sum(x)/n;
    s = sqrt(sum((x-m).^2/n));
end
```
Llame a la función desde la línea de comandos.
```matlab
values = [12.7, 45.4, 98.9, 26.6, 53.1];
[ave,stdev] = stat(values)
ave =
   47.3400
stdev =
   29.4124
```
### Función en un archivo de script
Defina un script en un archivo llamado `integrationScript.m` que calcule el valor del integrando en $2\pi/3$ y calcule el área bajo la curva de 0 a $\pi$. Incluya una función local que defina el integrando $y = \sin(x)^3$.

**Nota:** La inclusión de funciones en los scripts requiere MATLAB® R2016b o posterior.
```matlab
% Compute the value of the integrand at 2*pi/3.
x = 2*pi/3;
y = myIntegrand(x)
% Compute the area under the curve from 0 to pi.
xmin = 0;
xmax = pi;
f = @myIntegrand;
a = integral(f,xmin,xmax)
function y = myIntegrand(x)
    y = sin(x).^3;
end
```
```matlab
y =

    0.6495

a =

    1.3333
```
### Varias funciones en un archivo de función
Defina dos funciones en un archivo llamado `stat2.m`, donde la primera función llame a la segunda.
```matlab
function [m,s] = stat2(x)
    n = length(x);
    m = avg(x,n);
    s = sqrt(sum((x-m).^2/n));
end

function m = avg(x,n)
    m = sum(x)/n;
end
```
La función *avg* es una función local. Las funciones locales solo están disponibles para otras funciones del mismo archivo.

Llame a la función *stat2* desde la línea de comandos.
```matlab
values = [12.7, 45.4, 98.9, 26.6, 53.1];
[ave,stdev] = stat2(values)
```
```matlab
ave =
   47.3400
stdev =
   29.4124
```
### Función con validación de argumentos
Defina una función que restrinja la entrada a un vector numérico que no contenga elementos *Inf* ni *NaN*. Esta función utiliza la palabra clave *arguments*, que es válida para la versión R2019b de MATLAB® y posteriores.
```matlab
function [m,s] = stat3(x)
    arguments
        x (1,:) {mustBeNumeric, mustBeFinite}
    end
    n = length(x);
    m = avg(x,n);
    s = sqrt(sum((x-m).^2/n));
end

function m = avg(x,n)
    m = sum(x)/n;
end
```
En el bloque de código *arguments, (1,:)* indica que *x* debe ser un vector. Las funciones de validación, *{mustBeNumeric, mustBeFinite}*, restringen los elementos de *x* a valores numéricos que no son *Inf* ni *NaN*. Para obtener más información, consulte <a href="https://la.mathworks.com/help/matlab/matlab_prog/function-argument-validation-1.html" target="_blank">Function Argument Validation</a>.

Llamar a la función con un vector que contiene un elemento *NaN* infringe la declaración del argumento de entrada. Esta infracción provoca un error de la función de validación <a href="https://la.mathworks.com/help/matlab/ref/mustbefinite.html" target="_blank">mustBeFinite</a>.