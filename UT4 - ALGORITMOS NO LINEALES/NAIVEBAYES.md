<h1>Naive bayes</h1>
<div class="container mt-5">
<p>Los algoritmos de minería de datos utilizados para tareas de clasificación son muy diversos. El objetivo de estos algoritmos es el mismo: la predicción de una variable objetivo. Sin embargo, el método de predicción se basa en una serie de técnicas multidisciplinares. El algoritmo ingenuo de Bayes tiene sus raíces en la estadística y la teoría de la probabilidad.

<p>Tenemos muchos factores diferentes que afectan al resultado, por lo que a medida que obtenemos más pruebas sobre los factores que afectan al resultado, podemos hacer mejores conjeturas sobre el resultado utilizando la teoría de la probabilidad. El algoritmo bayesiano ingenuo básicamente aprovecha la relación probabilística entre los factores (atributos) y la etiqueta de clase (resultado). El algoritmo hace una suposición fuerte y a veces ingenua de independencia entre los atributos, de ahí su nombre. La suposición de independencia entre atributos puede no ser siempre cierta.

<p>En algunos casos, podemos suponer que los ingresos anuales y la puntuación crediticia son independientes entre sí. Sin embargo, en muchos casos simplemente no lo sabemos. Si uno de los factores de la tasa de morosidad es el valor de la vivienda, entonces tenemos un escenario en el que tanto el factor de los ingresos anuales como el del valor de la vivienda están correlacionados y, por tanto, no son independientes. Los propietarios con ingresos elevados tienden a comprar casas más caras. El supuesto de independencia no se cumple siempre, pero la simplicidad y robustez del algoritmo compensan la limitación introducida por el supuesto de independencia.</p>
<h2>Cómo funciona:</h2>
<p>Supongamos que X es la evidencia (o conjunto de factores o atributos) e Y es el resultado (o clase objetivo o etiqueta). Aquí X es un conjunto, no atributos individuales, por lo tanto X = {X1, X2, X3,..., Xn}, donde Xi es un atributo individual, como la calificación crediticia. La probabilidad del resultado P(Y) se denomina probabilidad a priori y puede calcularse a partir del conjunto de datos. La probabilidad a priori muestra la probabilidad de un resultado en un conjunto de datos determinado. Por ejemplo, en el caso de las hipotecas, P(Y) es la tasa de impago de una hipoteca de vivienda, que es del 2%. P(Y|X) se denomina probabilidad condicional, que proporciona la probabilidad de un resultado dada la evidencia cuando conocemos el valor de X. De nuevo, utilizando el ejemplo de la hipoteca, P(Y|X) es la tasa media de impago dado que se conoce el historial crediticio de un individuo.</p> <p>Si el historial crediticio de un individuo es conocido, P(Y|X) es la tasa media de impago.

<p>Si el historial crediticio es excelente, entonces es probable que la probabilidad de impago sea inferior al 2%. P(Y|X) también se denomina probabilidad posterior. Calcular la probabilidad posterior es el objetivo del análisis predictivo mediante el teorema de Bayes. Es la probabilidad de un resultado a medida que aprendemos los valores de los atributos de entrada.</p> 

<p>$$
P(Y|X) = \frac{P(Y)*P(X|Y)}{P(X)}
$$</p>

<p>P(X|Y) es otra probabilidad condicional, llamada probabilidad condicional de clase. P(X|Y) es la probabilidad de que un atributo asuma un valor particular dada la etiqueta de clase. Al igual que P(Y), P(X|Y) también se puede calcular a partir del conjunto de datos. Si conocemos el conjunto de entrenamiento de impagos de préstamos, podemos calcular la probabilidad de una calificación crediticia "excelente" dado que el impago es un "sí". Como se indica en el teorema de Bayes, la probabilidad condicional de clase es crucial para calcular la probabilidad posterior. P(X) es básicamente la probabilidad de la evidencia. En el ejemplo de la hipoteca, es simplemente la proporción de individuos con una determinada calificación crediticia.</p> <p>

<p>Para clasificar un nuevo registro, podemos calcular P(Y|X) para cada clase de Y y ver qué probabilidad "gana". La etiqueta de clase Y con el valor más alto de P(Y|X) gana para un determinado valor de atributo X. Dado que P(X) es la misma para cada valor de clase del resultado, no tenemos que calcularla y asumirla como una constante. De forma más general, en un conjunto de ejemplo con n atributos X = {X1, X2, X3 ... Xn}</p> <p>

<p>$$
P(Y|X) = \frac {P(Y)* \prod_{i=1}^n P(X_i| Y)}{P(x)} 
$$</p>

<p>Si sabemos calcular la probabilidad condicional de clase P(X|Y) o la prod , entonces es fácil calcular la probabilidad posterior P(Y|X). Como P (X) es constante para cada valor de Y, basta con calcular el numerador de la ecuación para cada valor de clase.</p> <p>

<h3>Un ejemplo de golf:</h3>
<p>Ver video: https://www.youtube.com/embed/IlVINQDk4o8</p>

<h3>Limitaciones:</h3>
<p>El modelado bayesiano es bastante robusto en el manejo de valores perdidos. Si el conjunto de ejemplos de prueba no contiene un valor, supongamos que la temperatura no se calcula en el conjunto de ejemplos, el modelo bayesiano simplemente omite la probabilidad condicional de clase correspondiente para los resultados. Los valores que faltan en el conjunto de prueba serían difíciles de manejar en los árboles de decisión y los algoritmos de regresión, sobre todo cuando el atributo que falta se utiliza más arriba en el nodo del árbol de decisión o tiene más peso en la regresión. Aunque el algoritmo Bayes ingenuo es bastante robusto frente a los atributos que faltan, tiene algunas limitaciones. Here are couple of the most significant limitations and methods of mitigation.</p>

<ul>
    <li>Incomplete Training Set</li>
    <li>Continuous Attributes</li>
    <li>Attribute Independence</li>
</ul>

<p>One of the fundamental assumptions in the naïve Bayesian model is attribute independence. Bayes’ theorem is guaranteed only for independent attributes. In many real-life cases, this is quite a stringent condition to deal with. This is why the technique is called “naïve” Bayesian, because it assumes attributes independence. Before applying the naïve Bayesian algorithm, it makes sense to remove strongly correlated attributes. In the case of all numeric attributes, this can be achieved by computing a weighted correlation matrix. An advanced application of Bayes’ theorem, called a Bayesian belief network, is designed to handle data sets with attribute dependencies.</p>

<h3>Conclusion:</h3>
<p>The Bayesian algorithm provides a probabilistic framework for a classification problem. It has a simple and sound foundation for modeling the data and is quite robust to outliers and missing values. This algorithm is deployed widely in text mining and document classification where the application has a large set of attributes and attribute values to compute.</p>

<p>La singularidad de la técnica es que aprovecha la nueva información a medida que llega y trata de hacer la mejor predicción teniendo en cuenta las nuevas pruebas. En este sentido, es bastante similar a cómo funciona nuestra mente.</p>