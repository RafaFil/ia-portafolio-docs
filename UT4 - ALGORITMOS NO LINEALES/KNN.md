<h1>KNN</h1>
<div class="container">
<p>
    Todo el conjunto de datos de entrenamiento se "memoriza" y, cuando es necesario clasificar registros de ejemplo sin etiquetar, los atributos de entrada de los nuevos registros sin etiquetar se comparan con todo el conjunto de entrenamiento para encontrar la coincidencia más cercana. La etiqueta de clase del registro de entrenamiento más cercano es la etiqueta de clase prevista para el registro de prueba no visto. Se trata de un método no paramétrico, en el que no se generaliza ni se intenta encontrar la distribución del conjunto de datos (Altman, 1992). Una vez que los registros de entrenamiento están en la memoria, la clasificación del registro de prueba es muy sencilla. Hay que encontrar el registro de entrenamiento más cercano para cada registro de prueba.
</p>

<p>
    Esta clase de aprendices adopta un enfoque contundente, en el que no se realiza ningún "aprendizaje" a partir de datos de entrenamiento, sino que el conjunto de datos de entrenamiento se utiliza como tabla de consulta para ajustar las variables de entrada y encontrar el resultado. Estos enfoques se denominan aprendices perezosos.
</p>

<h2 class="mt-5">Cómo funciona:</h2>

<p>
    Cualquier registro de un conjunto de datos puede visualizarse como un punto en un espacio n-dimensional, donde n es el número de atributos. ¿Qué ocurre cuando el punto de datos se encuentra en el límite de dos atributos de clases diferentes? La clasificación puede ser complicada porque en la vecindad hay más de una clase en las proximidades. Necesitamos un algoritmo eficaz para resolver estos casos y medir la proximidad de los puntos de datos con más de dos dimensiones. Una técnica consiste en encontrar el punto de datos de entrenamiento más cercano a un punto de datos de prueba no visto en un espacio multidimensional, y utilizar el valor de la clase objetivo del punto de datos de entrenamiento más cercano como la clase objetivo predicha para el punto de datos de prueba. Esto es similar al funcionamiento del algoritmo k-NN.
</p>

<p>
    La k del algoritmo k-NN indica el número de registros de entrenamiento cercanos que deben tenerse en cuenta al realizar la predicción de un registro de prueba sin etiquetar. Cuando k = 1, el modelo intenta encontrar el primer registro más cercano y adopta la etiqueta de clase del primer registro de entrenamiento más cercano como valor de la clase objetivo predicha. Dado que la clase del registro objetivo se evalúa por votación, a k se le suele asignar un número impar para un problema de dos clases.
</p>

<h2 class="mt-5">Medida de proximidad:</h2>

<p>
    La eficacia del algoritmo k-NN depende de la determinación de la semejanza o desemejanza entre un registro de prueba y el registro de entrenamiento memorizado. Una medida de proximidad entre dos registros es la medida de proximidad de sus atributos.
</p>

<h4 class="mt-5">Distancia</h4>
<ul>
            <li>Euclídea</li>
            <li>Manhattan</li>
            <li>Chebyshev</li>
            <li>Minkowski: (Generalizacion de las distancias)</li>
</ul>
<p>
$$
d = \left( \sum_{i=1}^n |x_i - y_i|^p \right)^{\frac{1}{p}}
$$
</p>
<p>
    Cuando p = 1, la medida de distancia es la distancia Manhattan, cuando p = 2 la medida de distancia es la distancia Euclídea, y cuando p = ∞ la medida de distancia es la distancia Chebyshev.
</p>

<p>
    <strong>y′ = clase máxima(y1, y2, ⋯ ,yk)</strong>
</p>

<p><strong>Ponderaciones:</strong> Cuando k es más de uno, se puede argumentar que los vecinos más cercanos deberían tener más peso en el resultado de la clase objetivo predicha que los vecinos más lejanos. Esto se puede conseguir asignando pesos a todos los vecinos, con los pesos aumentando a medida que los vecinos se acercan al punto de datos.</p>
<p>
w_i=\frac{e^{-d(x_in_i)}}{\sum_{i=1}^k e^{-d(x_in_i)}}
</p>
<p><strong>y = clase máxima(w1 * y1, w2 * y2, ⋯ , wk * yk)</strong></p>


<aside class="alert alert-info">
<strong>💡Nota: Un problema de la aproximación por distancia es que depende de la escala y las unidades de los atributos. Para mitigar el problema causado por las diferentes medidas y unidades, todas las entradas de k-NN suelen normalizarse, donde los valores de los datos se reescalan para ajustarse a un rango determinado. La normalización de todos los atributos proporciona una comparación justa entre ellos.
</strong>
</aside>

<aside class="alert alert-info">
<strong>💡Nota: La medida de distancia funciona bien para atributos numéricos. Sin embargo, si el atributo es categórico (nominal), la distancia entre dos puntos es 0 o 1. Si los valores de los atributos son los mismos, la distancia es 0. Si los valores de los atributos son iguales, la distancia es 0 y si los valores de los atributos son diferentes, la distancia es 1. Si el atributo es ordinal con más de dos valores, los valores ordinales se pueden convertirse al tipo de datos entero con los valores 0, 1, 2, ..., n - 1 y el atributo convertido puede tratarse como un atributo numérico para el cálculo de la distancia.
</strong>
</aside>

<h4 class="mt-5">Similitud de Correlación</h4>

<p>
    La correlación entre dos puntos de datos X e Y es la medida de la relación lineal entre los atributos X e Y.
</p>

<h4 class="mt-5">Coeficiente de Correspondencia Simple</h4>

<p>
    El coeficiente de correspondencia simple (CMS) se utiliza cuando los conjuntos de datos tienen atributos binarios. Por ejemplo, X es (1,1,0,0,1,1,0) e Y es (1,0,0,1,1,0,0). Podemos medir la similitud entre estos dos puntos de datos basándonos en la aparición simultánea de 0 o 1 con respecto al total de apariciones.
</p>

<h2 class="mt-5">Conclusión:</h2>

<p>
    El modelo k-NN requiere normalización para evitar cualquier sesgo por cualquier atributo que tenga unidades grandes o pequeñas en la escala. El modelo es bastante robusto cuando falta algún valor de atributo en el registro de prueba. Si falta el valor en el registro de prueba, se ignora todo el atributo en el modelo, y aún así el modelo puede funcionar con una precisión razonable. En el ejemplo de aplicación, si la
no se conoce la longitud del sépalo de un registro de prueba, el modelo ignora la longitud del sépalo. Cuando falta el valor de un atributo, k-NN se convierte en un modelo tridimensional en lugar de las cuatro dimensiones habituales.
Como aprendiz perezoso, la relación entre la entrada y la salida no puede explicarse, ya que el modelo no es más que un conjunto memorizado de todos los registros de entrenamiento. No hay generalización ni abstracción de la relación.
</p>
</div>