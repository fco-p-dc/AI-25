# Semana 02

## Aprendizaje supervisado

El aprendizaje supervisado en machine learning se da cuando entrenamos a la maquina con datos que estan correctamente clasificados o etiquetados. Despues se le da un nuevo set de datos para analizar y producir una prediccion.

Existe el error en muestra, los datos correctamente clasificados para entrenar, y el error fuera de muestra, que son los datos nuevos.

Se dice que $f ≈ h*$ si y solo si $E_i(h*) ≈ 0$ y $Eo(h*) ≈ E_i(h*)$, solo si se aplica esto se dice que hay aprendizaje.

## Desigualdad de Hoeffding 
$$
\displaystyle\ Pr[\epsilon \le|E_O(h*)-E_i(h*)|] \le 2exp(-2\epsilon^2)
$$
Donde M es el numero de datos y $\epsilon$ la diferencia del error dentro y fuera de muestra.

La desigualdad nos dice que la probabilidad de que el error en datos nuevos sea mucho mayor que el error que comete en los datos que ya vio. Si tenemos muchos datos la probabilidad de que el modelo sea malo en generalizacion es mas pequeña.

## Cardinalidad

La cardinalidad se refiere al numero de valores unicos que puede tomar la variable.
 
## Funcion de Crecimiento

Denota cuantas funciones diferentes podemos implementar con un conjunto de hipotesis $H$ sobre un conjunto de $M$ datos.

$$
\displaystyle\ Pr[\epsilon \le|E_O(h*)-E_i(h*)|] \le 2m_H(M)exp(-2\epsilon^2M)
$$

## Vapnik-Chervonenkis dimension

La Dimension VC de un conjunto de hipotesis $H$ es la cantidad maxima de datos que $H$ puede fragmentar completamente. 

Se representa tal dVC(H), esta es el valor mas grande de M para el cual $m_H(M)=2^M$ para cualquier conjunto $\{x^{(1)},..., x^{(M)}\} \in X$ y cualquier asignacion $f(x)\in \{-1,1\}$

Si $d_{VC}(H)$ finito, entonces
$$
\displaystyle\ Pr[\epsilon \le|E_O(h*)-E_i(h*)|] \le 4m_H(2M)exp(-1/8\epsilon^2M)
$$

Simplificado a:
$$
\displaystyle\ Pr[\epsilon \le|E_O(h*)-E_i(h*)|] \le \delta
$$
Donde $\delta ≈ M^{d_{VC}}e^{-M}$ 

### Regla de oro para la generalizacion
$$
\displaystyle\ 10d_{VC}(H) \le M
$$


## Arboles de Decision

Son diagramas generados a partir de datos, muestran las diferentes opciones y sus posibles resultados, enfatizando como los diferentes factores se relacionan. De manera jerarquica tienen los siguientes componentes:
* Raiz: Es el primer nodo que representa los datos.
* Ramas: Son las aristas que conectan a los nodos.
* Nodos internos: Son los nodos intermedio que conectan y estan basados en las decisiones del input.
* Nodos hoja: Son los nodos terminales y nos dan la prediccion.

## Entropia

La entropia condicional $H(Y|X)$ de una variable aleatoria $Y$ condicionada por una variable aleatoria $X$, nos da:

$$
\displaystyle\ H(Y|X)=\sum_{j=1}^vP(X=x_j)\sum_{i=1}^kP(Y=y_i|X=x_j)log_2P(Y=y_i|X=x_j)
$$

## Ganancia de Informacion

Es hacer la entropia menor despues de dividir, quedando:

$$
\displaystyle\ IG(X)=H(Y)-H(Y|X)
$$

Usandola de manera que al empezar un arbol de decision dividamos tomando el siguiente mejor atributo, como:
$$
\displaystyle\ argmaxIG(X_i)=argmaxH(Y)-H(Y|X_i)
$$

