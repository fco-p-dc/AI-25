# Semana 03

## Binarizar

Arbol binario, partir un atributo X en el valor t
* Una rama X < t
* Otra rama X >= t

Partiendo entre diferentes clases en el atributo X.

## Arboles de decision

Es un algoritmo de aprendizaje supervisado no parametrico. Se pueden utilizar tanto datos numericos como categoricos. Sirven como un bloque para tecnicas mas avanzadas.

## Problemas con Arboles de Decision

Son aproximadores universales, con cualquier contenido de informacion que se le da se podra discretizar. Por ello tienden a sobreajustar con los datos que se tienen, lo que no permite que aprenda. Para generalizar se necesita tener una funcion que no sea tan buena.

## Hacer problemas simples que generalicen bien

### Aprendizaje de ensemble
Es el concepto general de combinar las predicciones de multiples modelos de aprendizaje automatico para obtener una prediccion final mas robusta y precisa. 

### Bagging

Es un metodo de ensemble que sirve para mejorar la estabilidad y precision de los modelos. Intenta reducir la varianza y previniendo el sobreajuste. Funciona de la siguiente manera:
* Bootstrap: Se crean multiples conjuntos de datos de entrenamiento nuevos muestreando aleatoriamente con reemplazo del conjunto de datos original.
* Entrenamiento independiente: Entrena un modelo base en cada uno de estos conjuntos de datos muestreados.
* Agregacion: Para hacer una prediccion, combina las predicciones de todos los modelos entrenados. En clasificacion se hace votacion, para regresion se hace un promedio.

### Boosting

La tecnica de ensemble de boosting sirve para crear un clasificador fuerte de la mano de clasificadores debiles. Reduciendo el sesgo y la varianza, logrando un alto rendimiento. Ejemplos de estos son el AdaBoost, GradientBoost. Funciona de la siguiente manera:
* Inicializa asignando pesos iguales a todos los datos.
* Entrena un modelo debil en los datos.
* Identifica e incremente los pesos de datos mal clasificados.
* Se combinan los modelos.
* Se repite el proceso hasta que el modelo mejora o estabiliza.

### Bosques Aleatorios

Otro metodo de ensemble es el algoritmo Random Forest que utiliza arboles de decision como modelos base. Estos se forman siguiendo:
* Bootstrap: Se crean multiples conjuntos de datos de entrenamiento con muestreo con reemplazo del conjunto original.
* Seleccion aleatorio de caracteristicas: Al construir cada arbol, se selecciona un subconjunto aleatorio de caracteristicas. La mejor division se elige solo dentro de este subconjunto.
* Entrenamiento: Se entrena un arbol de decision en cada conjunto de datos de entrenamiento muestreado y utilizando el paso anterior.
* Agregacion: Se agrega el resultado de todos los arboles como en Bagging.