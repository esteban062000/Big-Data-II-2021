## Resumen de los temas estudiados

Durante estas semanas, se terminó con el tema de introducción a los modelos, cubriendo su concepto, tipos y funcionalidad de cada uno. Al inicio, se realizó una comparación muy útil entre ellos (por ejemplo, jerárquico vs plano; determinista vs estocástico, etc), que facilitó comprender las diferencias y ventajas que tienen entre sí. También, se mencionaron modelos que están basados en procesos estadísticos, mientras que otros, como los de *machine learning*, tienen una base más computacional. Una parte importante de esta materia sirvió como repaso del curso Diseño de Experimentos, mientras que otra parte permitió extrapolar los conocimientos adquiros (por ejemplo, en un curso anterior vimos la Matriz de Correlación, que funciona de manera similar a la Matriz de Confusión, que vimos en el presente curso).

Seguidamente, se inició con el tema de aprendizaje automático, específicamente con árboles de decisión. Para introducir el tema, se mencionaron dos tipos de problemas típicos: clasificación y regresión, ambos explorados en cursos anteriores. Sin embargo, los árboles no habían sido tratados con profundidad anteriormente, por lo que permitió aumentar el conocimiento en esta área. Se mostraron en un orden lógico y natural: primero árboles de decisión, luego bosques aleatorios y, para finalizar, algoritmos relacionados al *ensemble* como *gradient boosting*, que funcionan de manera muy similar a una red neuronal. Este tema me gustó bastante y creo que es de mucha utilidad para los problemas que se ajusten bien a este modelo.

Finalmente, se cubrió el tema de *cross validaton*. Se definió qué es y los tipos de validación que se utilizan, así como las ventajas de cada uno. De particular utilidad fue la explicación sobre el *stratified k-fold cross validation*, sumamente mencionado en los tutoriales desarrollados hasta ahora. Considero que, mediante la información gráfica, fue más sencillo comprender cómo funciona y por qué es mejor que una validación no estratificada. Finalmente, se mencinaron otras técnicas de validación como LOOCV y *nested cross validation*, que se unieron al bagaje de herramientas disponibles al tratar con problemas de aprendizaje automático.

## Comentarios sobre algo aprendido

La introducción a los modelos fue particularmente útil para mí, al poder comparar los tipos de cada uno con sus ventajas y desventajas. No conocía los modelos planos ni jerárquicos, por ejemplo, por lo que pude aprovechar bastante esta parte del curso. También, me gustó aprender sobre árboles de decisión, pues había escuchado el término anteriormente pero no sabía qué era. Me pareció bastante útil la forma en que se cubrió el tema, pasando de lo más sencillo (árboles) a lo más elaborado (bosques con gradiente del descenso). Esta herramienta es nueva para mí, por lo que me permitió expandir el conocimiento sobre el área y comprender cómo se interrelaciona con otros temas vistos anteriormente (por ejemplo, redes neuronales que también utilizan gradiente del descenso). 

Con respecto a las estrategias de entrenamiento y validación, me pareció sumamente útil el abordaje de *stratified k-fold cross validation*. Los modelos son tan buenos como lo son sus resultados (y su aplicabilidad), por lo que comprender cómo entrenarlos y validarlos es fundamental. Hasta antes del curso, la única manera con la que contaba era una validación cruzada con *k-folds* sin estratificar, mucho menos robusta que las aprendidas en el curso. Con este conocimiento, se pueden alcanzar mejores resultados al validar de una mejor manera los modelos que se desarrollen.

## Dudas sobre la materia estudiada
Hasta el momento, no tengo dudas sobre la materia cubierta. 

## Posible uso que usted le dará a esta materia como profesional

Considero que le daré mayor uso a la sección de validación de modelos. En particular, desconocía cómo funcionaba el *stratified k-fold cross validation*, por lo que ahora podré implementarlo en los futuros modelos a desarrollar. Por ejemplo, continuando con el caso de predecir cuántas partidas jugadas en Lichess.com utilizaron el Gambito de Dama después de que se estrenara la serie homónima, se podría construir un modelo para predecir cuál partida empezará con esta apertura. Hasta antes del curso, la validación que yo habría hecho sería un *k-fold* de agrupaciones por ELO; por ejemplo, entrenar primero en partidas de principiantes, luego intermedios y por último avanzados. Ahora, con el conocimiento adquirido de la estratificación, sé que una validación más robusta involucraría mezclar muestras de estas categorías y no agruparlas por separado. Una posible consecuencia de este nuevo conocimiento podría ser, por ejemplo, tener un mejor modelo productivo al final del proyecto.

## Mencione cualquier material que utilizó como referencia para el aprendizaje.
En estas semanas, no he utilizado material extra en el aprendizaje.