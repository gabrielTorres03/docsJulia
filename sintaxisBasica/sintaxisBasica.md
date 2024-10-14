La ventaja de Julia ante otros lenguajes es que es bastante intuitivo y flexible. Asi que a continuacion exploraremos
el como declarar variables y como utilizar diferentes tipos de datos: 

Declaración de Variables
Las variables en Julia se declaran simplemente asignando un valor, sin necesidad de especificar el tipo.

	# Declaración de variables
nombre = "Julia"
edad = 25
pi = 3.14159
activo = true

Tipos de Datos
Julia ofrece varios tipos de datos básicos:

Numéricos: Enteros (Int), flotantes (Float), complejos (Complex).
Booleanos: Verdadero (true) y falso (false).
Strings: Texto entre comillas.
Arreglos y Tuplas: Para almacenar colecciones de valores.

Ejemplos: 

# Números
numero_entero = 42
numero_flotante = 3.14
numero_complejo = 1 + 2im

# Booleanos
es_verdadero = true
es_falso = false

# Strings
saludo = "Hola, Julia!"

# Arreglos y Tuplas
mi_arreglo = [1, 2, 3, 4, 5]
mi_tupla = (10, "Julia", false)

Operadores
Julia soporta operadores aritméticos y lógicos:

Aritméticos: +, -, *, /, ^, %
Lógicos: && (AND), || (OR), ! (NOT)
Relacionales: ==, !=, <, >, <=, >=

# Ejemplos de operadores
a = 10
b = 3

suma = a + b
division = a / b
potencia = a ^ b

# Operadores lógicos
c = true
d = false

resultado_and = c && d
resultado_or = c || d

Estructuras de Control
Las estructuras de control permiten controlar el flujo del programa:

Condicionales (if / else)
Bucles (for, while)

# Condicional
x = 7
if x > 10
    println("x es mayor que 10")
elseif x == 10
    println("x es igual a 10")
else
    println("x es menor que 10")
end

# Bucle for
for i in 1:5
    println("Iteración $i")
end

# Bucle while
contador = 1
while contador <= 5
    println("Contador: $contador")
    contador += 1
end
