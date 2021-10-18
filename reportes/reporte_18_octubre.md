## Resumen de los temas estudiados

Durante estas semanas, primeramente, se estudiaron los temas de las regresiones lineales y logísticas. Ambas habían sido introducidas en cursos anteriores (como Diseño de Experimentos), por lo que funcionó para repasar el tema. Sin embargo, la sección de *regularización* fue completamente nueva, pues no se habían mostrado técnicas como Lasso o Ridge anteriormente. Esta técnica permite ajustar el modelo para favorecer aquellas soluciones más simples, con heurísticas que se pueden aplicar para decidir la técnica apropiada (por ejemplo, Ridge cuando se sospecha colinealidad).

Seguidamente, se cubrió el tema de redes neuronales, que había sido introducido en el curso de Inteligencia Artificial y, en menor medida, Diseño de Experimentos. Se hizo hincapié en cómo son una extensión de los modelos lineales, para trabajar sobre funciones (y problemas) más complejos, que no necesariamente son lineales. Luego de explicar su forma más básica (el perceptrón), se mencionaron distintas funciones de activación, como Relu, sigmoidal o tangente hiperbólica. También, se brindaron recursos para aprender sobre el tema, como las librerías de Python scikit-learn y Keras. 

Hacia las últimas clases, se realizó una introducción al algoritmo de Máquina de Soporte Vectorial, que busca un hiperplano que permita clasificar los puntos en los grupos deseados. Se profundizó en el tema lo suficiente como para mostrar por qué el algoritmo funciona mejor sobre conjuntos de datos balanceados, y cómo realizar el *kernel trick* para trabajar sobre datasets poco balanceados. Finalmente, se revisaron huerísticas que permiten decidir cuál función de activación elegir en las redes neuronales. A grandes rasgos, estas dos semanas trataron sobre métodos para resolver problemas de clasificación.

## Comentarios sobre algo aprendido

En lo personal, las regresiones fueron un repaso breve sobre la materia de Diseño de Experimentos, con el añadido de la sección de regularización. Sobre las redes neuronales, me gustó que se trataran más en profundidad las funciones de activación, pues hasta el momento, únicamente había utilizado Relu sin entender por qué. También, en clase se discutieron distintos métodos de optimización (Gradiente del Descenso, Newton, Conjugate, etc), de los cuales únicamente conocía Gradiente del Descenso; creo que el curso, en general, ha permitido expandir el bagaje de técnicas disponibles para tratar problemas de aprendizaje automático.

El material que más me gustó fue el relacionado al algoritmo de Máquina de Soporte Vectorial, pues había sido mencionado anteriormente en 3 cursos distintos, pero nunca se había tratado en clase. En particular, me llamó la atención la aplicabilidad de la materia vista en Álgebra Lineal (para definir hiperplanos según sea necesario), que combina muy bien con lo aprendido en Cálculo sobre derivadas parciales que permiten explicar Gradiente del Descenso. En general, creo que el curso ha sido una oportunidad para interrelacionar conocimientos adquiridos en cursos anteriores, tanto de matemática como de la carrera en sí. 

## Dudas sobre la materia estudiada
Hasta el momento, no tengo dudas sobre la materia cubierta. 

## Posible uso que usted le dará a esta materia como profesional

Esta materia me ha permitido expandir mi conocimiento sobre las herramientas y técnicas disponibles para resolver problemas de clasificación. Aunque, en este momento, no tengo un problema de clasificación sobre el cual esté trabajando activamente, podré utilizar este conocimiento para discutir con otros colegas que sí están trabajando en ello y poder extraer ideas interesantes. Por ejemplo, un conocido del TEC ganó el año pasado el concurso mundial PlantCLEF, donde se debía implementar un algoritmo para clasificar plantas a partir de imágenes. Con el bagaje adquirido en este curso, yo podría preguntarle cómo trabajó sobre el problema, qué técnicas utilizó, cómo modificó el algoritmo de Máquina de Soporte Vectorial (o si lo consideró) durante la competencia; no necesariamente yo pueda entender todo lo que hizo, pero sí tengo las bases para poder aprender de una persona que esté trabajando en problemas de clasificación.

## Mencione cualquier material que utilizó como referencia para el aprendizaje.
En estas semanas, no he utilizado material extra en el aprendizaje.