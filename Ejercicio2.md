# EJERCICIO #2

## Simulación de Sistema de Ecuaciones Diferenciales con el Método de Runge-Kutta

Este ejercicio consiste en resolver un sistema de ecuaciones diferenciales ordinarias usando el método de Runge-Kutta de cuarto orden (RK4). Resolverás un sistema que modela el movimiento de un péndulo doble, que es un sistema no lineal con comportamiento caótico.

### Instrucciones

1. Define las ecuaciones diferenciales que describen el movimiento del péndulo doble.
2. Implementa el método de Runge-Kutta de cuarto orden.
3. Grafica la trayectoria de cada masa en el péndulo doble.

```julia
using Plots

# Parámetros del péndulo doble
m1, m2 = 1.0, 1.0  # masas
L1, L2 = 1.0, 1.0  # longitudes
g = 9.81           # gravedad

# Definir el sistema de ecuaciones diferenciales
function pendulo_doble!(du, u, t)
    θ1, ω1, θ2, ω2 = u
    Δθ = θ2 - θ1

    # Ecuaciones de movimiento para el péndulo doble
    du[1] = ω1
    du[2] = (-g * (2m1 + m2) * sin(θ1) - m2 * g * sin(θ1 - 2θ2) - 
             2sin(Δθ) * m2 * (ω2^2 * L2 + ω1^2 * L1 * cos(Δθ))) / 
             (L1 * (2m1 + m2 - m2 * cos(2Δθ)))
    du[3] = ω2
    du[4] = (2sin(Δθ) * (ω1^2 * L1 * (m1 + m2) + g * (m1 + m2) * cos(θ1) + 
             ω2^2 * L2 * m2 * cos(Δθ))) / 
             (L2 * (2m1 + m2 - m2 * cos(2Δθ)))
end

# Método de Runge-Kutta de cuarto orden
function runge_kutta4!(f, u0, tspan, dt)
    t0, tf = tspan
    t = t0:dt:tf
    u = copy(u0)
    traj = [copy(u)]
    
    for ti in t[2:end]
        k1 = dt * f(u)
        k2 = dt * f(u + 0.5 * k1)
        k3 = dt * f(u + 0.5 * k2)
        k4 = dt * f(u + k3)
        u += (k1 + 2k2 + 2k3 + k4) / 6
        push!(traj, copy(u))
    end
    return t, traj
end

# Condiciones iniciales
u0 = [π / 2, 0, π / 4, 0]
tspan = (0.0, 20.0)
dt = 0.01

# Simular
t, traj = runge_kutta4!(pendulo_doble!, u0, tspan, dt)

# Graficar trayectoria
x1 = [L1 * sin(θ1) for θ1 in traj[:,1]]
y1 = [-L1 * cos(θ1) for θ1 in traj[:,1]]
x2 = [L1 * sin(θ1) + L2 * sin(θ2) for (θ1, θ2) in traj[:, (1,3)]]
y2 = [-L1 * cos(θ1) - L2 * cos(θ2) for (θ1, θ2) in traj[:, (1,3)]]

plot(x1, y1, label="Masa 1", legend=:topright)
plot!(x2, y2, label="Masa 2", legend=:topright)
xlabel!("X")
ylabel!("Y")
title!("Trayectoria de un péndulo doble")
```

Este ejercicio muestra la simulación de un sistema caótico y cómo se puede implementar el método de Runge-Kutta en Julia para resolver sistemas de ecuaciones diferenciales complejos.