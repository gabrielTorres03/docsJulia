En Julia, puedes crear funciones para organizar y reutilizar código. Las funciones se pueden definir de manera detallada o en una sola línea.

Definición de Funciones
Las funciones en Julia se definen usando la palabra clave function, y puedes retornar valores usando return.

# Función detallada
```Julia
function saludo(nombre)
    return "¡Hola, $nombre!"
end
```
println(saludo("Julia"))

# Función de una línea
cuadrado(x) = x^2
println(cuadrado(4))

Métodos y Sobrecarga
Julia permite la sobrecarga de funciones, es decir, puedes definir múltiples versiones de una función con el mismo nombre pero diferentes parámetros.

# Sobrecarga de función
function area(radio::Float64)
    return pi * radio^2
end

function area(largo::Float64, ancho::Float64)
    return largo * ancho
end

println(area(5.0))  # Círculo
println(area(5.0, 3.0))  # Rectángulo

