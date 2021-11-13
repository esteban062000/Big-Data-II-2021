## Resumen de los temas estudiados

En estas semanas, se trabajó con algoritmos de aprendizaje no supervisado, en particular, relacionados a segmentación (*clustering*). De forma general, estos algoritmos buscan dividir un conjunto de datos en grupos que permitan capturar cierta estructura natural sobre ellos. Esto puede ser significativo o útil dependiendo del estudio a realizar. Cuando se trabaja con segmentación, se necesita: una métrica de similitud, codificar atributos categóricos, transformar atributos numéricos y definir cuántos *clusters* estamos buscando.

Los algoritmos, según su tipo, se pueden clasificar en: **particionamiento** (K-means, k-modes, k-medoids); **jerárquicos** (BIRCH, Chameleon); **Densidad** (DBSCAN, OPTICS, DENCLUE); **Grid** (STING, CLIQUE). Dos algoritmos bastante estudiados en las clases se comparan a continuación:

| K-Means     | DBSCAN |
| ----------- | ----------- |
| No determinístico      | Determinístico       |
| Agrupa todos los puntos en algún *cluster*   | Puede identificar puntos que no pertenecen a ningún *cluster*        |
| 1 parámetro (*k*)      |2 parámetros (*min_samples*, *eps*)      |
| Los *outliers* lo afectan      | Puede manejar mejor el ruido       |
| Más rápido      | Más lento        |

Para cualquier algoritmo, se recomienda utilizar técnicas de preprocesamiento y limpieza de datos, por ejemplo, normalizar o estandarizar.

Para la evaluación de una solución, se tienen dos formas principales: extrínsecas e intrínsecas. Las primeras, se utilizan cuando se tiene una *ground truth*; sin embargo, si ya se conoce desde antes la agrupación idónea, es un problema de clasificiación (o sea, no supervisado). Las formas intrínsecas, por su parte, buscan indicar qué tan bien separados están los *clusters* y se utilizan cuando no se tiene una *ground truth*.

También, se inició con el estudio de los *Self-Organising Maps (SOM)*, un método de segmentación basado en redes neuronales que, a menudo, utiliza reducción de dimensionalidad. Pertenece a los algoritmos del tipo *Grid-based Clustering* y, como K-means, busca encontrar un conjunto de centroides; sin embargo, cada centroide está asociado a una neurona. En SOM, se impone un orden topológico sobre los centroides; de esta forma, cada centroide tiene influencia sobre los otros en un vecindario. En general, SOM se puede utilizar para conocer la estructura de los datos, pero puede no haber correspondencia entre un *cluster* SOM y un *cluster* verdadero.

## Comentarios sobre algo aprendido

En los últimos meses, el curso ha estado muy ligado al aprendizaje automático. En lo personal, creo que ya tengo suficiente bagaje en el aprendizaje supervisado (gracias a cursos anteriores y lo visto en este curso), pero sentía que conocía muy poco sobre aprendizaje no supervisado. De esta forma, el abordaje de este tema en las últimas semanas ha sido de mucho provecho para mí, pues me ha permitido conocer más sobre esta área en la que no me sentía tan seguro.

Particularmente, había estudiado K-means bastante en un curso anterior, además de una breve introducción a los SOM en Inteligencia Artificial. Por ende, no conocía sobre todos los otros algoritmos que se mencionaron (BIRCH, DBSCAN, STING, CLIQUE), etc. Ahora, con este conocimiento, me siento mejor preparado para abordar problemas de aprendizaje automático en general.

También, me gustó la oportunidad que se ha dado en clase para dedicar tiempo a la práctica. Si bien la teoría permite conocer sobre estos temas, creo que es en la práctica donde se terminan de comprender bien los conceptos.

## Dudas sobre la materia estudiada

1. ¿El método CLIQUE tiene alguna relación con un clique en Teoría de Grafos? Busqué sobre el algoritmo y no me parece que mencionen explícitamente que se relacione con ese concepto, por lo que me parece curioso que le hayan asignado ese nombre.

## Posible uso que usted le dará a esta materia como profesional

Al conocer sobre otros algoritmos como DBSCAN, tengo una perspectiva más grande para decidir cuál herramienta se ajusta mejor al problema a estudiar. Por ejemplo, antes del curso, solo tenía k-means a disposición; ahora, conozco sobre los diferentes tipos de algoritmos que hay (particionamiento, jerárquicos, etc), por lo que hay un abanico de posibilidades para elegir. Un problema específico al que los podría aplicar, por ejemplo, sería tomar un conjunto de datos sobre estrellas y cuerpos celestes, aplicar algún algoritmo de *clustering* y determinar si las agrupaciones que realiza corresponden con alguna clasificación utilizada en el mundo real. Esto sería particularmente útil para comparar los *clusters* generados por SOM y DBSCAN con los *clusters* que se tienen en la vida real.

## Mencione cualquier material que utilizó como referencia para el aprendizaje.
En estas dos semanas, no he utilizado material extra en el aprendizaje.