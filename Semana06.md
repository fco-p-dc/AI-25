# Semana 06

## Juegos con Adversarios


Se formalizan con lo siguiente:
* Estados: La configuracion del juego en un momento dado, empezando con $s_0$
* Jugadores/Agentes: Al menos 2, normalmente toman turnos. $P=\{1,...,n\}$
* Acciones: Movimientos legales de cada agente en un estado
* Transiciones: Define lo que pasa en el juego de un estado a otro despues de una accion $SxA->S'$
* Terminales: Un estado que finaliza el juego
* Utilidad: Asigna un valor numerico a los estados terminales para cada jugador, indicando victoria, empate o derrota.

Ejemplos: Damas chinas, ajedrez, tic-tac-toe

### Juegos de Suma Cero

Los agentes o jugadores, tienen utilidades opuestas, la ganancia de uno es la perdida del otro, de ahi el nombre, donde la suma de las utilidades de todos los jugadores es cero. Si se tienen dos jugadores, lo que se buscaria es maximizar a uno, minimizar al oponente. 

### Arboles

Los arboles son la representacion grafica de todas las posibles secuencias de movimientos en el juego, comenzando en $s_0$ como nodo raiz y terminan en nodos hoja que son los estados terminales que dictaminan la utilidad para cada jugador.

### Minimax

Algoritmo de busqueda recursiva, que busca determinar el mejor movimiento para un jugador, asumiendo que el oponente jugara de manera optima. Se intentara maximizar el movimiento del jugador y minimizar la utilidad del oponente, lo que nos da:

$$ V(s)= maxV(s') ~ para~el~jugador $$

Se inicializa $$v=-\infty$$

Se hace una iteracion para cada estado sucesor:

$$v=max(v,valor-minimo(sucesor))$$

y se regresa v. De otro modo,

$$ V(s')= minV(s') ~ para~el~oponente $$

Se inicializa $$v=+\infty$$

Se hace una iteracion para cada estado sucesor:

$$v=max(v,valor-maximo(sucesor))$$

y se regresa v.

Se pueden seguir los siguientes pasos:
* Construccion del arbol de juego: Se explora el arbol de juego hasta una cierta profundidad o hasta alcanzar los estados terminales.
* Evaluacion de los nodos hoja: Se asignan los valores de utilidad a los nodos hoja
* Propagacion hacia arriba: El jugador que se maximiza se elige un movimiento de utilidad maximo entre los hijos del nodo. El jugador que se minimiza se elige el movimiento que conduce al estado con menor utilidad de los nodos hijos.
* Nodo raiz: El valor que toma el nodo raiz, representa el mejor resultado que se puede garantizar si ambos jugadores juegan de manera optima.
### Poda de Arboles

Problema con Minimax es que su eficiencia es muy mala para grandes estados. Teniendo que:
$$Tiempo: O(b^m)$$
$$Espacio: O(bm)$$

Por ejemplo para ajedrez se tendria, b=35 y m=100, lo que hace imposible de realizar. Para ello, se utiliza una tecnica de optimizacion que es la poda (pruning) para no tener que buscar todo el arbol generado en Minimax.

#### Alpha-Beta

El objetivo es reducir el numero de nodos que se exploraran del algoritmo, sin afectar la decision final. Funciona con dos valores $\alpha$ y $\beta$:
* Alpha($\alpha$): El valor de la mejor opcion que se ha encontrado para el jugador que maximiza en el camino actual.
* Beta($\beta$): El valor minimo que hemos encontrado para el jugador que minimiza en el camino actual.

Si se encuentra un nodo para el jugador que se minimiza que es menor o igual a $\alpha$ no se necesita explorar mas a los nodos hermanos, se puede podar. Del otro modo, si un nodo para el jugador maximiza encuentra un valor que es mayor o igual a $\beta$, no necesita explorar mas, ya que el jugador que minimiza no eligiria un camino que lleve a ese nodo, se puede podar la rama y dejar de explorar.
