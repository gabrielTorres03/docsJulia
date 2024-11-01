# EJERCICIO #1

## Descomposición de Valores Singulares (SVD) para Reducción de Dimensionalidad en Análisis de Imágenes

En este ejercicio, usarás la descomposición de valores singulares (SVD) para reducir la dimensionalidad de una imagen en escala de grises. Este tipo de análisis es útil en la compresión de imágenes, donde queremos conservar la mayor parte de la información con menos datos.

### Instrucciones

1. Carga una imagen en escala de grises.
2. Convierte la imagen en una matriz y calcula su SVD.
3. Reconstruye la imagen usando solo los primeros k valores singulares.
4. Muestra la imagen original y las versiones comprimidas con diferentes valores de k.

```julia
using Images, LinearAlgebra, Plots

# Cargar la imagen en escala de grises
img = Gray.(load("ruta/de/tu/imagen.jpg"))
img_matrix = Float64.(img)

# Calcular la SVD
U, S, V = svd(img_matrix)

# Función para reconstruir imagen usando k valores singulares
function reconstruir_img(U, S, V, k)
    return U[:, 1:k] * Diagonal(S[1:k]) * V[:, 1:k]'
end

# Visualizar la imagen original y las versiones comprimidas
ks = [5, 20, 50, 100]
plot(img, title="Imagen original", size=(300,300))
for k in ks
    img_reducida = reconstruir_img(U, S, V, k)
    plot(Gray.(img_reducida), title="k = $k", size=(300,300))
end
```

En este ejercicio, experimentarás cómo la compresión afecta la calidad de la imagen a medida que reduces los valores singulares. Cuanto mayor sea k, más detalles tendrá la imagen reconstruida.