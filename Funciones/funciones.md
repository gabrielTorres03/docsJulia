En Julia, una función es un objeto que asigna una tupla de valores de argumentos a un valor de retorno. Las funciones de Julia no son funciones matemáticas puras, ya que pueden modificarse y verse afectadas por el estado global del programa. La sintaxis básica para definir funciones en Julia es:
```Julia
julia> function f(x, y)
           x + y
       end
f (generic function with 1 method)
```
Esta función acepta dos argumentos xy ydevuelve el valor de la última expresión evaluada, que es x + y.

Existe una segunda sintaxis más concisa para definir una función en Julia. La sintaxis de declaración de 
función tradicional que se muestra arriba es equivalente a la siguiente "forma de asignación" compacta:
```Julia
julia> f(x, y) = x + y
f (generic function with 1 method)
```

En la forma de asignación, el cuerpo de la función debe ser una expresión única, aunque puede ser una expresión compuesta (consulte Expresiones compuestas ). Las definiciones de funciones breves y simples son comunes en Julia. La sintaxis de función breve es, por lo tanto, bastante idiomática, lo que reduce considerablemente tanto el ruido de escritura como el visual.

Una función se llama utilizando la sintaxis de paréntesis tradicional:
```Julia
julia> f(2, 3)
5
```
Sin paréntesis, la expresión f se refiere al objeto de función y puede pasarse como cualquier otro valor:
```Julia
julia> g = f;

julia> g(2, 3)
5
```
Al igual que con las variables, Unicode también se puede utilizar para nombres de funciones:
```Julia
julia> ∑(x, y) = x + y
∑ (generic function with 1 method)

julia> ∑(2, 3)
5
```
