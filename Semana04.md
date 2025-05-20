# Semana 04

## Clasificacion Lineal

Es un clasificador simple, donde se utiliza una linea recta en el plano para separar clases. La decision del limite esta definida por un conjunto de parametros que determinan la orientacion y posicion.

Con un clasificador binario general que:
$$
\displaystyle\ f_w(x) = sign(w.\phi(x))
$$

Donde $w$ son los pesos que determinan la orientacion
### Prediccion

La prediccion de la clase se basa entonces en el signo, por ejemplo para las clases 1 y -1:
* si $f(x)\ge 0$ predecimos la clase 1
* si $f(x)<0$ predecimos la clase -1

### Funcion de Perdida

La funcion de perdida mide que tan bien esta funcionando el clasificador, nos dice que tanto se castiga al modelo al cometer un error en la prediccion. Como objetivo tenemos que encontrar los valores de $w$ y $b$ que minimicen la perdida en el entrenamiento.

#### Hinge Loss

Se define como:

$$
\displaystyle\ Loss_{hinge}(x,y,w) = max(1-(w.\phi(x))y,0)
$$

Si la etiqueta verdadera es 1 y la puntuacion $f(x)$ es $\ge1$ la perdida es 0. Si la etiqueta es -1 y la puntuacion $f(x)\le -1$ la perdida es 0. En otro caso, donde la prediccion es incorrecta hay una perdida proporcional a la distancia hasta el margen de clasificacion.

## Regresion Lineal

Es una tecnica de estadistica usada para encontrar las relaciones entre caracteristicas y una etiqueta. El enfoque es predecir una variable continua, en lugar de buscar una linea que separe las clases, buscamos una linea que se ajuste a los datos.

### Funcion de Perdida

#### MSE

El error cuadratico medio (MSE en ingles) es una funcion de perdida muy comun para la regresion lineal. Dice, dado un conjunto de $m$ datos de entrenamiento $\{(x_i, y_i)\}^m_i$ donde $x_i$ es la variable predictora o caracteristicas e $y_i$ es el valor objetivo real, la prediccion es $\hat{y} = w^Tx_i+b$. Para darnos una ecuacion:
$$
\displaystyle\ MSE = \frac{1}{m}\sum_i^m (\hat{y_i}-y_i)^2
$$

Con ello, se calcula el promedio de los cuadrados de las diferencias entre los valores predichos y los reales. Dandole mas peso a los errores grandes.

### Optimizacion

Se utiliza la optimizacion para encontrar los mejores valores para los parametros del modelo, como el peso $w$ y el sesgo $b$, minimizando la funcion de perdida.

### Gradiente

Es un vector que apunta hacia la direccion del mayor incremento de la funcion. Se denota como 
$$
\displaystyle\ \triangledown J(w, b)
$$

Donde J es una funcion de perdida, sus componentes son las derivadas parciales de la funcion con respecto a cada parametro.

#### Descenso de Gradiente

Es un algoritmo iterativo de optimizacion, usando el gradiente, buscamos lo contrario para encontrar el minimo de la funcion de perdida. Se comienza con valores iniciales aleatorios para los parametros, se actualizan en la direccion opuesta del gradiente, moviendo paso a paso haca la region donde la perdida es menor.

$$
\displaystyle\ w_{t+1} = w_t - \eta \triangledown _wJ(w_t,b_t)
$$
$$
\displaystyle\ b_{t+1} = b_t - \eta \triangledown _bJ(w_t,b_t)
$$

Donde $\eta$ es la tasa de aprendizaje, que controla el tamaño del paso que damos en cada iteracion.
