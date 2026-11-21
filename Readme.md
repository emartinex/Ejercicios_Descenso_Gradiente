# Ejercicios de Descenso de Gradiente

Repositorio con la solución en Python (Jupyter Notebooks) de los 6 ejercicios de descenso de gradiente para la materia de **Matemáticas para Inteligencia Artificial**.

Los ejercicios están divididos en dos partes según las instrucciones de la actividad:
- **Ejercicios 1 al 3:** además del desarrollo a mano, aquí se comprueba que las primeras tres iteraciones ($x_1$, $x_2$ y $x_3$) coinciden con las tablas calculadas manualmente y se deja correr el algoritmo hasta cumplir el criterio de paro $\|\nabla f(x_i)\| < 10^{-6}$.
- **Ejercicios 4 al 6:** resueltos completamente en Python. Como no se daban valores iniciales, en cada notebook se documentan las pruebas que hice para elegir $\gamma$, $x_0$ y (cuando aplica) el momento $\alpha$.

## Contenido del repositorio

| Archivo | Descripción | Parámetros usados | Resultado principal |
| :--- | :--- | :--- | :--- |
| `[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github.com/emartinex/Ejercicios_Descenso_Gradiente/blob/main/Ejercicio_1_Descenso_Gradiente.ipynb)` | Función cuadrática en 2 variables en forma matricial y analítica. | $\gamma = 0.15$, $x_0 = (0, 0)$ | Converge en 24 iteraciones a $x^* = (-2, 1)$ con $f(x^*) = -13$. |
| `Ejercicio_2_Descenso_Gradiente.ipynb` | Función cuadrática en 3 variables en forma matricial y analítica. | $\gamma = 0.25$, $x_0 = (1, 0, 1)$ | Converge en 53 iteraciones a $x^* = (-3, 2, -2)$ con $f(x^*) = -20.5$. |
| `Ejercicio_3_Descenso_Gradiente_Momento.ipynb` | Descenso con momento en una variable para $f(x) = \frac{1}{4}x^4 - 2x^2$. | $\gamma = 0.05$, $\alpha = 0.5$, $x_0 = 1$ | Converge en 46 iteraciones al mínimo en $x^* = 2$ con $f(x^*) = -4$. |
| `Ejercicio_4_Descenso_Gradiente.ipynb` | Optimización en 4 variables con selección heurística de parámetros. | $\gamma = 0.03$, $x_0 = (0, 0, 0, 0)$ | Converge en 36 iteraciones a $x^* = (1, 1, 1, 1)$ con $f(x^*) = -30$. |
| `Ejercicio_5_Descenso_Gradiente_Momento.ipynb` | Función de Rosenbrock. Comparación directa con momento vs. sin momento. | $\gamma = 0.001$, $\alpha = 0.95$, $x_0 = (-1.2, 1.0)$ | Llega a $x^* = (1, 1)$ en 1,324 iteraciones con momento, frente a 32,076 sin momento. |
| `Ejercicio_6_Descenso_Gradiente.ipynb` | Búsqueda del mínimo global probando distintos puntos iniciales. | $\gamma = 0.04$, varios $x_0$ | Mínimo global en $x^* \approx (-2.06, -2.06)$ ($f \approx -20.06$) y mínimo local en $(1.93, 1.93)$ ($f \approx -12.06$). |

## Notas rápidas sobre los resultados

- En los **ejercicios 1, 2 y 3**, las tablas generadas con `pandas` para las iteraciones $x_0$ a $x_3$ coinciden con el cálculo hecho a mano.
- En el **ejercicio 4**, valores de $\gamma$ de $0.04$ en adelante hacen que el método oscile o diverja rápido por el término cúbico del gradiente; con $\gamma = 0.03$ baja de forma estable.
- En el **ejercicio 5**, el momento hace toda la diferencia por la forma estrecha del valle de Rosenbrock: reduce las iteraciones en más del 95% usando exactamente la misma tasa de aprendizaje y punto inicial.
- En el **ejercicio 6**, el resultado depende de dónde empiece el algoritmo. Probando varios puntos iniciales y revisando las raíces del gradiente se confirma que solo hay dos mínimos y un punto silla, por lo que el pozo en $x_1 < 0$ es el mínimo global.

## Requisitos y ejecución

El código está escrito de forma sencilla usando Python 3 y tres librerías básicas:

- `numpy`
- `pandas`
- `matplotlib`

Si no las tienes instaladas, puedes instalarlas junto con Jupyter ejecutando:

```bash
pip install numpy pandas matplotlib notebook
```

Después, clona el repositorio y abre Jupyter desde la carpeta del proyecto:

```bash
git clone <URL-de-tu-repositorio>
cd <nombre-de-la-carpeta>
jupyter notebook
```

Cada archivo `.ipynb` es independiente, así que puedes abrir y ejecutar cualquiera en el orden que prefieras.
