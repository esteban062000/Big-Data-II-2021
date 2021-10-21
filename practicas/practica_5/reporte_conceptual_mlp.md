# Crash Course on Multi-Layer Perceptron

## 1. Multi-layer Perceptrons

Un **perceptrón** es un *modelo de una sola neurona* que fue el precursor de redes neuronales más grandes.

La idea del campo no es crear modelos realistas del cerebro, sino desarrollar algoritmos robustos y estructuras de datos que se pueden utilizar para modelar problemas difíciles.

El poder de las redes neuronales viene de su habilidad para aprender la representación en los datos de entrenamiento y cómo relacionarlo a la variable de salida que se desea predecir. En este sentido, las redes neuronales aprenden *mapeo*. Matemáticamente, son capaces de aprender cualquier función de mapeo y se ha demostrado que son un algoritmo de aproximación universal.

La capacidad predictiva de las redes neuronales viene de su estructura jerárquica o multi-capa. La estructura de datos puede elegir (aprender a representar) *features* en escalas diferentes o resoluciones, para combinarlas en *features* de mayor dimensión. Por ejemplo, pasar de líneas a figuras.

## 2. Neurons, Weights and Activations

La piedra angular de las redes neuronales son las **neuronas artificiales**. Ellas son unidades computacionales simples que tienen señales de entrada ponderadas y producen una señal de salida mediante una **función de activación**.

![](https://machinelearningmastery.com/wp-content/uploads/2016/05/Neuron.png)

### Neuron Weights

Como en regresión lineal, cada neurona tiene un *bias* que puede ser pensado como un valor de entrada que siempre tiene el valor 1.0 y también debe ser ponderado. Por lo general, los pesos se inicializan a valores aleatorios pequeños, por ejemplo, en el rango de 0.0 a 0.3, aunque esquemas más complejos de inicialización pueden ser utilizados. Como en regresión lineal, pesos más grandes indican mayor complejidad y fragilidad. Es deseable mantener los pesos en la red pequeños y se pueden utilizar técnicas de regularización.

### Activation

Los valores de entrada ponderados se suman y se envían a la función de activación, a veces llamada *transfer function*.

Una función de activación  es un mapeo de la suma de los valores de entrada hacia la salida de la neurona. Se llama *función de activación* porque determina el límite en el cual la neurona es activada y la fuerza de la señal de salida.

Históricamente, *simple step activation functions* eran usadas, donde si la suma de la entrada estaba por encima de un límite, por ejemplo 0,5, entonces la neurona tendría un valor de salida de 1.0; en otro caso, su salida sería 0.

Tradicionalmente, funciones de activación no lineales son usadas. Esto le permite a la red combinar las entradas en maneras más complejas y, en cambio, proveer una mayor capacidad en las funciones que puede modelar. Ejemplos de estas funciones son la sigmoide y la tangente hiperbólico.

## 3. Networks of Neurons

Las neuronas son colocadas en redes de neuronas. Una fila de neuronas se llama **capa** y una red puede tener múltiples capas. La arquitectura de las neuronas en la red, a menudo, se conoce como **topología de la red**.

![](https://machinelearningmastery.com/wp-content/uploads/2016/05/Network.png)

### Input or Visible Layers

La capa más inferior que toma la entrada del *dataset* se llama **capa visible**, porque es la parte expuesta de la red. A menudo, se tiene una neurona de entrada por cada valor o columna en los datos. Estas *no* son neuronas como las descritas anteriormente, sino solamente pasan la entrada de datos a la siguiente capa.

### Hidden Layers

Las capas después de la entrada son llamadas **capas ocultas**, porque no están directamente expuestas a la entrada. La red neuronal más simple conssite en tener una sola neurona en la capa oculta que envía directamente el valor de salida. 

**Deep learning** sepuede referir a tener muchas capas ocultas en la red. Son *deep* porque habrían sido exageradamente lentas de entrenar históricamente, pero toman segundos o minutos gracias a técnicas y hardware moderno.

### Output Layer

Es la responsable de enviar un valor o vector de valores como salida de la red, que corresponden al formato requerido por el problema. 

La elección de la función de activación en la capa de salida está fuertemente condicionada por el tipo de problema que se está modelando:
  
- Un problema de regresión puede tener una sola neurona de salida, sin función de activación.
- Una clasificación binaria puede tener una función sigmoide en combinación con un límite para determinar las clases.
- Un problema de clasificación multi clase podría tener una neurona de salida por cada clase, en combinación con la función de activación *softmax*.

## 4. Training Networks

Una vez configurada, la red neuronal debe ser entrada sobre el *dataset*.

### Data Preparation

Los datos deben ser numéricos, por ejemplo, valores reales. Si se tienen datos categóricos, se pueden convertir a valores reales utilizando **one hot encoding**. Esto consiste en agregar una columna nueva para cada clase (si se tienen datos "masculino" y "femenino" serían 2 columnas nuevas, por ejemplo) y un 0 o 1 es añadido para cada fila dependiendo de valor de cada clase. Esta misma técnica se puede utilizar para la salida en problemas de clasificación multi clase.

Las redes neuronales requieren que la entrada se escale de una manera consistente. Se puede reescalar al rango 0 a 1, lo que se conoce como **normalización**. También, se puede **estandarizar** para que su media sea 0 y su desviación estándar sea 1.

### Stochastic Gradient Descent

El algoritmo clásico y actualmente preferido para entrenar redes neuronale  es llamado **stochastic gradient descent**. Una fila de los datos es expuesta como entrada a la vez. La red procesa la entrada hacia arriba, activando las neuronas hasta que produce un valor de salida. Esto se llama un *forward pass* en la red. Es el tipo de pase que se usa luego para realizar predicciones. 

La salida de la red es comparada con la salida esperada y se calcula el error. Este error es luego propagado hacia atrás en la red, una capa por vez, y los pesos son actualizados según su contribución al error. En esto consiste el **backpropagation algorithm**.

Este proceso se repite para todos los ejemplos en los datos de entrenamiento. Una ronda de actualizar la red para todo el *dataset* se llama un **epoch**. Una red puede ser entrenada por decenas, centenas o muchos miles de *epochs*.

### Weight Updates

Los pesos en la red se pueden actualizar con base en los errores calculados para cada ejemplo de entrenamiento, lo que es llamado **online learning**. Puede resultar en cambios rápidos y caóticos a la red.

Alternativamente, los errores se pueden guardar a lo largo de todos los ejemplos de entrenamiento y actualizar la red hasta el final. Esto se llama **batch learning** y, por lo general, es más estable. 

La cantidad de pesos que son actualizados se controla mediante un parámetro de configuración llamado **learning rate**. También se conoce como **step size** y controla los cambios a los pesos en la red para un error dado. A menudo, se usan valores pequeños como 0.1, 0.01 o menos.

La actualización de pesos se puede complementar con parámetros de configuración adicionales:

- **Momentum** es un término que incorpora las propiedades de la actualización de pesos anterior, lo que permite continuar el cambio en esa dirección en particular aunque haya un error calculado más pequeño.
- **Learning Rate Decay** es utilizado para disminuir el *learning rate* en cada *epoch*, lo que le permite a la red hacer cambios grandes al inicio y cambios más pequeños al final.

### Prediction

La topología de la red y el conjunto final de pesos es todo lo que se necesita guardar del modelo. Las predicciones se llevan a cabo al darle una entrada al modelo, que realiza un *forward pass* y obtiene un valor de salida.

# Comentarios sobre algo que haya aprendido

El tema de redes neuronales ya había sido tratado con cierta profunidad en el curso de Inteligencia Artificial, por lo que los conceptos no me fueron completamente nuevos. Sin embargo, encontré provechoso repasar (o aprender) los términos formales para cada parte de la red (los señalé en negrita o cursiva; por ejemplo, *forward pass* o *batch learning*), que permiten leer otra literatura sobre el tema y comprender de qué trata. También, los últimos dos parámetros que se mencionaron, *momentum* y *Learning Rate Decay*, fueron completamente nuevos para mí, lo que significa una nueva herramienta en el *toolbox* disponible para trabajar con aprendizaje automático.

# Dudas sobre el tema tratado

No tengo dudas sobre el tema tratado.