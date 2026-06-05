# Módulo 4: Deep Learning - Actividad 1: Math Warm-Up

Este repositorio contiene la **Actividad 1 (Math Warm-Up)** correspondiente al **Módulo 4: Deep Learning** del programa académico impartido en el **Centro de Investigación y Estudios Avanzados del IPN (Cinvestav), Unidad Guadalajara**.

## 📋 Información del Proyecto
* **Institución:** Centro de Investigación y Estudios Avanzados del IPN (Cinvestav) - Unidad Guadalajara.
* **Curso:** MÓDULO 4: Deep Learning.
* **Profesor:** German Alonso Pinedo Díaz.
* **Alumno:** César Geovanni Machuca Pereida.

---

## 🎯 Objetivos del Repositorio
El propósito de este cuaderno es realizar un repaso y alineación matemática fundamental (*sanity check*) antes de profundizar en arquitecturas complejas de redes neuronales profundas. Se exploran las diferencias clave entre transformaciones lineales y afines, el rol crítico de las funciones de activación no lineales y la interpretación geométrica/operacional de las derivadas y gradientes en la optimización de funciones de pérdida.

---

## 🧠 Conceptos Teóricos Abordados

### 1. Funciones Lineales y Afines
En una dimensión, una función lineal clásica en Deep Learning se expresa formalmente como:
$$y = \beta + \omega x$$
Donde $\beta$ representa el intercepto (u ordenación al origen) y $\omega$ denota la pendiente. En dimensiones superiores ($D$), la ecuación se extiende a un hiperplano:
$$y = \beta + \sum_{i=1}^{D}\omega_i x_i$$

#### La Sonda de Linealidad (*Linearity Probe*)
Una función estrictamente lineal $g(\cdot)$ debe cumplir con dos propiedades fundamentales:
1. **Aditividad:** $g(x_1 + x_2) = g(x_1) + g(x_2)$
2. **Homogeneidad (Escalamiento):** $g(\alpha x) = \alpha g(x)$

*Análisis del cuaderno:* Se demuestra analíticamente que la función usada en Deep Learning $f(x) = \beta + \omega x$ **no es puramente lineal sino afín**, ya que la inclusión del sesgo (*bias* $\beta$) rompe la aditividad debido a que $f(x_1) + f(x_2) = 2\beta + \omega(x_1+x_2)$, mientras que $f(x_1+x_2) = \beta + \omega(x_1+x_2)$. Ambas expresiones solo coinciden si $\beta = 0$.

### 2. Funciones No Lineales
El cuaderno explica la necesidad matemática de las funciones de activación no lineales (como *ReLU, Sigmoid, Tanh*). Debido a que la composición de múltiples transformaciones lineales/afines consecutivas colapsa en una única transformación lineal equivalente ("*una línea de líneas es todavía solo una línea*"), se requiere introducir curvaturas en el espacio para modelar patrones complejos que no son linealmente separables.

Como contraste histórico, se revisa la formulación del clasificador de margen rígido (Primal) de las Máquinas de Vectores de Soporte (**SVM**), cuya función de decisión es lineal:
$$\min_{w,b}\ \frac{1}{2}\|w\|^2 \quad \text{s.t.}\quad y_i(w^\top x_i + b)\ge 1,\ \forall i$$

### 3. Derivadas y Optimización
Se analiza la derivada como el indicador de sensibilidad de salida ante perturbaciones infinitesimales en la entrada ("*¿si empujo un poco a $x$, cuánto cambia $y$?*"). En Deep Learning, los gradientes actúan como brújulas para la optimización de los parámetros:
* Si la derivada indica que incrementar un parámetro aumenta la pérdida, el optimizador se mueve en dirección opuesta.
* Si indica que el incremento disminuye la pérdida, el optimizador avanza en esa dirección.

---

## 💻 Implementación y Visualización Gráfica

El proyecto incluye funciones robustas programadas con `numpy` y `matplotlib` para inspeccionar visualmente estos comportamientos matemáticos sin modificar la configuración base establecida:

* **`plot_xy(x, y, ...)`**: Grafica funciones continuas en una dimensión (1D) sobre una malla con rejilla (*grid*) clara.
* **`plot_multiple(x, ys, labels, ...)`**: Permite superponer múltiples curvas usando un mapa de colores (`jet`), marcadores diferenciados y un indicador destacado (círculo rojo) en el origen $(0,0)$.
* **`contour2d(x1_mesh, x2_mesh, z, ...)`**: Renderiza mapas de contorno llenos (`contourf`) con 40 niveles de resolución y barras de color (*colorbar*) para evaluar superficies tridimensionales y gradientes en 2D.

---

## 🚀 Requisitos e Instalación

Para ejecutar este cuaderno de forma local o en entornos en la nube (como Google Colab o Jupyter), asegúrate de contar con Python 3.x y las siguientes dependencias:

```bash
pip install numpy matplotlib
