# Proyecto [La Masia]: Métodos Numéricos para Ecuaciones No Lineales

Este repositorio presenta una biblioteca en Python, programada bajo el paradigma de Orientación a Objetos, que implementa métodos numéricos clásicos para hallar raíces de ecuaciones no lineales. Incluye los métodos de Bisección, Falsa Posición, Punto Fijo, Newton-Raphson, Brent y Secante. Cada método se entrega con documentación y demostraciones interactivas en Google Colab

## 📦 Instalación

Todas las demostraciones están diseñadas para ejecutarse directamente en Google Colab, por lo que no se requiere instalación local
---
## ⚙️ Uso Básico de la Biblioteca
Cada método está encapsulado en su propia clase Solver. Para utilizarlos, simplemente instancie la clase correspondiente y llame al método .solve()
Ejemplo (usando Newton-Raphson):

# 1. Importar las clases (asumiendo que el archivo .py está en el mismo directorio)

from newton_raphson_solver import NewtonRaphsonSolver
from sympy import symbols, lambdify

2. Definir el problema (f y f')
x = symbols('x') f_expr = x3 - x - 2 fp_expr = 3*x2 - 1

f_func = lambdify(x, f_expr, 'math') fp_func = lambdify(x, fp_expr, 'math')

3. Crear el solver y resolver
newton = NewtonRaphsonSolver(f=f_func, fp=fp_func) raiz = newton.solve(x0=2.0, tol=1e-7)

4. Reportar
print(f"La raíz encontrada es: {raiz}") print(f"Se necesitaron {newton.iterations} iteraciones.")

5. Graficar
newton.plot_results()

## 🚀 Demos de Métodos

A continuación se encuentran los notebooks de demostración para cada método solicitado.

### 1. Método [Bisección (Búsqueda Binaria)]

Un método de bracketing (cerrado) que garantiza la convergencia (lineal) al subdividir el intervalo a la mitad en cada iteración. Es el método más robusto, aunque su convergencia es lenta.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TU_USUARIO/TU_REPOSITORIO/blob/main/demo/metodo_1.ipynb)

### 2. Método [False position]

Un método de bracketing mejorado. Utiliza una interpolación lineal (una "secante") entre los puntos (a, f(a)) y (b, f(b)) para encontrar la siguiente aproximación. Generalmente converge mucho más rápido que Bisección

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TU_USUARIO/TU_REPOSITORIO/blob/main/demo/metodo_2.ipynb)

### 3. Método [Fixed Point]

El método abierto fundamental. Requiere reescribir la ecuación f(x)=0 a la forma x=g(x). La raíz se encuentra iterando $x_{i+1} = g(x_i)$. Su convergencia (lineal) no está garantizada y depende críticamente de que la derivada $|g'(x)| < 1$ cerca de la raíz.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TU_USUARIO/TU_REPOSITORIO/blob/main/demo/metodo_3.ipynb)

### 4. Método [Newton Raphson]

El método abierto más potente. Utiliza la función f(x) y su derivada f'(x) para proyectar una línea tangente en cada iteración. Es conocido por su convergencia cuadrática (extremadamente rápida), aunque requiere el cálculo analítico de la derivada.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TU_USUARIO/TU_REPOSITORIO/blob/main/demo/metodo_4.ipynb)

### 5. Método [Secant]

Una modificación del método de Newton que evita el cálculo analítico de la derivada. En su lugar, aproxima la tangente usando una línea secante entre los dos puntos anteriores ($x_i$ y $x_{i-1}$). Ofrece una convergencia superlineal, casi tan rápida como la de Newton.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TU_USUARIO/TU_REPOSITORIO/blob/main/demo/metodo_5.ipynb)

### 6. Método [Brent]

El método "patrón oro" de los buscadores de raíces. Es un método híbrido que combina la robustez de los métodos cerrados (Bisección) con la velocidad de los métodos abiertos (Secante e Interpolación Cuadrática Inversa). Comienza como un método rápido (Secante), pero monitorea activamente la convergencia. Si detecta que la convergencia es muy lenta o insegura, interviene y realiza un paso de Bisección (más lento pero 100% seguro) para garantizar el progreso.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TU_USUARIO/TU_REPOSITORIO/blob/main/demo/metodo_5.ipynb)

## 🧐 Análisis comparativo
