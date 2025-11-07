# Proyecto [La Masia]: Métodos Numéricos para Ecuaciones No Lineales

Este repositorio presenta una biblioteca en Python, programada bajo el paradigma de Orientación a Objetos, que implementa métodos numéricos clásicos para hallar raíces de ecuaciones no lineales. Incluye los métodos de Bisección, Falsa Posición, Punto Fijo, Newton-Raphson, Brent y Secante. Cada método se entrega con documentación y demostraciones interactivas en Google Colab

## 📦 Instalación

Todas las demostraciones están diseñadas para ejecutarse directamente en Google Colab, por lo que no se requiere instalación local
---

## 🚀 Demos de Métodos

A continuación se encuentran los notebooks de demostración para cada método solicitado.

### 1. Método [Bisección (Búsqueda Binaria)]

Un método de bracketing (cerrado) que garantiza la convergencia (lineal) al subdividir el intervalo a la mitad en cada iteración. Es el método más robusto, aunque su convergencia es lenta.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1jyZGsyxJj7t7cbOkTvav4qktUrACT1-_)

### 2. Método [False position]

Un método de bracketing mejorado. Utiliza una interpolación lineal (una "secante") entre los puntos (a, f(a)) y (b, f(b)) para encontrar la siguiente aproximación. Generalmente converge mucho más rápido que Bisección

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/10mJiyQZrLNuU_JKxrtw4Wb3dFnqEmGIM)

### 3. Método [Fixed Point]

El método abierto fundamental. Requiere reescribir la ecuación f(x)=0 a la forma x=g(x). La raíz se encuentra iterando $x_{i+1} = g(x_i)$. Su convergencia (lineal) no está garantizada y depende críticamente de que la derivada $|g'(x)| < 1$ cerca de la raíz.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1VI0fNV0jC1jmPQSR0vnUbS0mH90diiAN)

### 4. Método [Newton Raphson]

El método abierto más potente. Utiliza la función f(x) y su derivada f'(x) para proyectar una línea tangente en cada iteración. Es conocido por su convergencia cuadrática (extremadamente rápida), aunque requiere el cálculo analítico de la derivada.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://docs.google.com/document/d/1rx0a1jCwzZ9SSd6w2etBNFZFZ9qM705Kqd0ENovpvWc/edit?usp=sharing)

### 5. Método [Secant]

Una modificación del método de Newton que evita el cálculo analítico de la derivada. En su lugar, aproxima la tangente usando una línea secante entre los dos puntos anteriores ($x_i$ y $x_{i-1}$). Ofrece una convergencia superlineal, casi tan rápida como la de Newton.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/16apzRzK3VbRNOabfQDMtGsVqzefqmOQ2?usp=sharing)

### 6. Método [Brent]

El método "patrón oro" de los buscadores de raíces. Es un método híbrido que combina la robustez de los métodos cerrados (Bisección) con la velocidad de los métodos abiertos (Secante e Interpolación Cuadrática Inversa). Comienza como un método rápido (Secante), pero monitorea activamente la convergencia. Si detecta que la convergencia es muy lenta o insegura, interviene y realiza un paso de Bisección (más lento pero 100% seguro) para garantizar el progreso.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1qrd4gV9R3iodZU92pC9vGyr8AFufOkYn?usp=sharing)

## 🧐 Análisis comparativo

### Bisection v/s False position
f(x): x**3 - x - 2
a : 1
b : 2
Iter: Prestablecido
#### False position
<img width="975" height="780" alt="image" src="https://github.com/user-attachments/assets/799472bb-866b-49f4-9623-9d6b72b02777" />
#### Bisection
<img width="951" height="784" alt="image" src="https://github.com/user-attachments/assets/c7fa6298-0ccd-4cb3-aebb-d1b09e1936f7" />
