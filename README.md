# Convolución de señales en tiempo continuo

**Trabajo 1 – Sistemas Lineales y Señales**  
Universidad de Cuenca, Facultad de Ingeniería

**Autor:** Jostin Aucancela

---

## Descripción

Programa en **Julia** (notebook de [Pluto.jl](https://plutojl.org/)) que calcula y visualiza la convolución entre dos señales en tiempo continuo.

$$y(t) = x(t) * h(t) = \int_{-\infty}^{\infty} x(\tau)\ * h(t-\tau)\ d\tau$$

El programa muestra cómo `h(t - τ)` (la señal reflejada) se desplaza sobre `x(τ)` y cómo se va construyendo progresivamente la señal de salida `y(t)`.

## Contenido del notebook

1. **Definición y gráfica de las señales** `x(t)` y `h(t)`, con sus intervalos de existencia y amplitudes.
2. **Implementación de la integral de convolución** con `SymPy`, por tramos según la superposición de las señales.
3. **Gráfica de la señal resultante** `y(t)`.
4. **Visualización interactiva** con un control deslizante para modificar `t`.
5. **Video** (`convolucion.mp4`) con la construcción progresiva de `y(t)`.

## Resultado de la convolución

Resuelta por tramos:

| Intervalo | y(t) |
|-----------|------|
| t ≤ 0 | 0 |
| 0 < t < 3 | t² / 2 |
| 3 < t < 6 | 3t − 9/2 |
| 6 < t < 9 | −t²/2 + 3t + 27/2 |
| t ≥ 9 | 0 |

El valor máximo es y(6) = 13.5.

## Visualización interactiva

La interfaz tiene tres gráficas que cambian al mover el slider de `t`:

- **Superposición:** `x(τ)` y `h(t - τ)` juntas.
- **Producto:** `x(τ)·h(t - τ)` con el área sombreada. Esa área es el valor de `y(t)` en ese instante, calculada numéricamente con una suma de Riemann.
- **Salida:** `y(t)` construida hasta el valor actual de `t`.

## Cómo ejecutarlo

1. Instalar [Julia](https://julialang.org/downloads/).
2. Abrir Julia e instalar y lanzar Pluto:
   ```julia
   using Pkg
   Pkg.add("Pluto")
   using Pluto
   Pluto.run()
   ```
3. Desde la página de Pluto, abrir el archivo `ConvoluciónSeñalesContinuas.jl`.
4. Pluto instala solo los paquetes necesarios la primera vez (`Plots`, `SymPy`, `PlutoUI`). Puede tardar unos minutos.
5. Mover el slider para ver la animación interactiva. La celda final genera el video `convolucion.mp4` en la carpeta del notebook.

## Estructura del repositorio

```
├── ConvoluciónSeñalesContinuas.jl   # Notebook de Pluto con todo el código
├── convolucion.mp4                  # Video de la convolución
└── README.md
```
