# Semana 05

## Regresion logistica

Es un algoritmo de clasificacion binaria. Se utiliza para predicir la probabilidad de que un elemento pertenezca a una de las dos clases posibles (ejemplo, 0 o 1). Utiliza:
* Funcion Lineal:

$$ z=w^Tx+b$$

* Funcion Sigmoide: es la funcion logistica que tiene forma de en S, comprime cualquier valor z en un rango entre 0 y 1. 

$$\sigma(z)=\frac{1}{1+e^{-z}}$$

* Prediccion: Se toma una decision con base al valor anterior. Si $\sigma(z)\ge umbral$ predecimos 1; si $\sigma(z)<umbral$ predecimos 0. Siendo el umbral un parametro segun el problema.
* Funcion de Perdida: Normalmente se utiliza la perdida de entropia o la perdida logaritmica. Con una etiqueta $y\in\{0,1\}$ y probabilidad predicha $p=\sigma(w^Tx+b)$, la perdida se define como:
   
$$L(y,p) = -[ylog(p)+(1-y)log(1-p)]$$

Donde si p es cercana a cero cuando y=1 entonces la perdida es grande. La idea es minimizar la perdida de entropia.

## Torres de Hanoi

Un problema de rompecabezas, consiste en tres varillas con un numero de discos de diferentes tamaños, que inicialmente estan apilados en la primer varilla en orden de tamaño decreciente, el disco mas grande hasta abajo, con el objetivo de mover toda la pila hasta la tercer varilla, respetando las reglas:
* Solo se mueve un disco a la vez
* Un disco solo se puede mover a una varilla vacia o encima de un disco mas grande.
* El disco mas grande nunca puede estar encima de otro disco.

## Modelo Busqueda

Es un metodo para encontrar una secuencia de acciones que conducen a un estado terminal deseado. Los componentes de un modelo de este estilo son:
* Estado inicial: El punto de partida.
* Acciones: Las acciones posibles que iniciaran transiciones de un estado a otro.
* Transiciones: Describe como una accion cambia el estado actual.
* Estado terminal deseado: El estado que se busca.
* Costo de la ruta: un valor numerico asociado a la secuencia.

### Tipos de busqueda

* Busqueda no informada: Busqueda en Anchura (BFS) o en Profundidad (DSF).
* Busqueda informada (heuristica): Busqueda A*.

## Arbol de busqueda, PACMAN
El arbol de busqueda utilizando como base el juego Pacman, con los siguientes componentes:
* Estado: La posicion de Pacman, de los fantamas, la ubicacion de la comida y el estado de los power ups.
* Acciones: Los movimientos posibles de Pacman (arriba, abajo, izquierda, derecha).
* Estado Objetivo: Pacman se las come todas.
* Costo: El tiempo o la distancia.
