# Proyecto [La Masia]: Métodos Numéricos para Ecuaciones No Lineales

Este repositorio presenta una biblioteca en Python, programada bajo el paradigma de Orientación a Objetos, que implementa métodos numéricos clásicos para hallar raíces de ecuaciones no lineales. Incluye los métodos de Bisección, Falsa Posición, Punto Fijo, Newton-Raphson, Brent y Secante. Cada método se entrega con documentación y demostraciones interactivas en Google Colab

## 📦 Instalación

Todas las demostraciones están diseñadas para ejecutarse directamente en Google Colab, por lo que no se requiere instalación local
---
## ⚙️ Estructura del Software (en cada Notebook)

Dado que cada método se entrega como un notebook (.ipynb) autocontenido, la "biblioteca" y la "demostración" conviven en el mismo archivo.

La estructura de cada notebook es la siguiente:

Celda 1: Código Base (El Software)

Esta es la celda superior que contiene todas las importaciones (numpy, matplotlib, etc.) y la definición completa de la clase Solver (ej. class NewtonRaphsonSolver:).

Esta celda es, en efecto, nuestro software propuesto.

Celda 2: Solucionador Interactivo (La Demo)

Esta es la celda que contiene el script interactivo (input(), reportes, etc.) que utiliza la clase definida en la Celda 1.

Cómo Utilizar el Software
Para ejecutar o probar el software con nuevos datos, simplemente:

Abra el notebook deseado en Google Colab usando los enlaces de la sección "Demos".

Ejecute la Celda 1 (la que define la clase) una sola vez para cargar el solver en memoria.

Ejecute la Celda 2 (la interactiva) y proporcione los datos solicitados (función, intervalo, etc.).

## 🚀 Demos de Métodos

A continuación se encuentran los notebooks de demostración para cada método solicitado.

### 1. Método [Bisección (Búsqueda Binaria)]

Un método de bracketing (cerrado) que garantiza la convergencia (lineal) al subdividir el intervalo a la mitad en cada iteración. Es el método más robusto, aunque su convergencia es lenta.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j-matheus10/msenl/blob/main/demo/bisection_method.ipynb)

### 2. Método [False position]

Un método de bracketing mejorado. Utiliza una interpolación lineal (una "secante") entre los puntos (a, f(a)) y (b, f(b)) para encontrar la siguiente aproximación. Generalmente converge mucho más rápido que Bisección

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j-matheus10/msenl/blob/main/demo/false_position_method.ipynb)

### 3. Método [Fixed Point]

El método abierto fundamental. Requiere reescribir la ecuación f(x)=0 a la forma x=g(x). La raíz se encuentra iterando $x_{i+1} = g(x_i)$. Su convergencia (lineal) no está garantizada y depende críticamente de que la derivada $|g'(x)| < 1$ cerca de la raíz.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j-matheus10/msenl/blob/main/demo/fixed_point_method.ipynb)

### 4. Método [Newton Raphson]

El método abierto más potente. Utiliza la función f(x) y su derivada f'(x) para proyectar una línea tangente en cada iteración. Es conocido por su convergencia cuadrática (extremadamente rápida), aunque requiere el cálculo analítico de la derivada.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j-matheus10/msenl/blob/main/demo/newton_raphson_method.ipynb)

### 5. Método [Secant]

Una modificación del método de Newton que evita el cálculo analítico de la derivada. En su lugar, aproxima la tangente usando una línea secante entre los dos puntos anteriores ($x_i$ y $x_{i-1}$). Ofrece una convergencia superlineal, casi tan rápida como la de Newton.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j-matheus10/msenl/blob/main/demo/secant_method.ipynb)

### 6. Método [Brent]

El método "patrón oro" de los buscadores de raíces. Es un método híbrido que combina la robustez de los métodos cerrados (Bisección) con la velocidad de los métodos abiertos (Secante e Interpolación Cuadrática Inversa). Comienza como un método rápido (Secante), pero monitorea activamente la convergencia. Si detecta que la convergencia es muy lenta o insegura, interviene y realiza un paso de Bisección (más lento pero 100% seguro) para garantizar el progreso.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j-matheus10/msenl/blob/main/demo/brent_method.ipynb)

## 🧐 Análisis comparativo

### Bisection v/s False position
f(x): x**3 - x - 2
a : 1
b : 2
Iter: Tolerancia: 1e-7 (fija para ambos)
#### False position
<img width="975" height="780" alt="image" src="https://github.com/user-attachments/assets/799472bb-866b-49f4-9623-9d6b72b02777" />

#### Bisection
<img width="951" height="784" alt="image" src="https://github.com/user-attachments/assets/c7fa6298-0ccd-4cb3-aebb-d1b09e1936f7" />

### Fixed Point v/s Secant
Problema: Resolver f(x) = e^{-x} - x 
Método Fixed Point: Usa g(x) = exp(-x)
Método Secant: Usa f(x) = exp(-x) - x$

Suposición inicial (x0): 0.5
Suposición inicial (x1): 0.6

#### Fixed Point
<img width="959" height="713" alt="image" src="https://github.com/user-attachments/assets/74aafb66-76d0-4e75-9168-66db2ed1fef2" />

#### Secant
<img width="954" height="743" alt="image" src="https://github.com/user-attachments/assets/23a4f237-1629-4310-b65a-ba70b6f430ce" />


## 🛠️ Metodología de Desarrollo

La lógica central y el análisis de los algoritmos numéricos fueron implementados por los autores. Se utilizaron asistentes de IA generativa como herramienta de apoyo para:

* La optimización y refactorización del código de las clases `Solver`.
* La creación de las interfaces interactivas (scripts de Celda 2) para las demostraciones.
* Guia para crear el archivo colab para usar github de la forma esperada sin instalarlo.
* Guia para comprender de mejor forma los métodos numéricos; a modo de método educativo.
* Se excede de lo anteriormente dicho el método Newton Raphson.
