Para organizar mejor el código, Julia permite la creación de módulos. Los módulos permiten agrupar funciones, tipos y constantes.

Crear un Módulo
Para crear un módulo, usa la palabra clave module. Define el código dentro del módulo y usa export para declarar las funciones y variables que estarán disponibles fuera del módulo.

# Definir un módulo en un archivo llamado `MiModulo.jl`
module MiModulo

export saludar, cuadrado

function saludar(nombre)
    return "¡Hola desde el módulo, $nombre!"
end

cuadrado(x) = x^2

end

Usar un Módulo
Para usar un módulo, carga el archivo con include() y luego usa using para importar el módulo.

# Usar el módulo
include("MiModulo.jl")
using .MiModulo

println(saludar("Mundo"))
println(cuadrado(7))

