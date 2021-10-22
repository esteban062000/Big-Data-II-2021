# How to Choose an Activation Function for Deep Learning

Las **funciones de activación** son una parte crítica del diseño de una red neuronal. En las capas ocultas, determinan qué tan bien aprenderá el modelo sobre los datos de entrenamiento. En la capa de salida, determinan el tipo de predicción que puede hacer la red.

## 1. Activation Functions

Una **función de activación** en una red neuronal define cómo la suma ponderada de la entrada se transforma a una salida en alguna capa de la red. 

Algunas veces, la función de activación se conoce como **transfer function**. Si el rango de salida de la función de activación es limitado, entonces puede ser llamada **squashing function**. Muchas funciones de activación son no lineales y se conocen como la **nonlinearity** en la capa o en el diseño de la red. Se pueden utilizar distintas funciones de activación en distintas partes del modelo. Sin embargo, las redes están diseñadas para usar la misma función de activación para todos los nodos en una misma capa.

Típicamente, todas las capas ocultas utilizan la misma función de activación. La capa de salida, por lo general, utiliza una función de activación distinta y depende del tipo de predicción que se desea realizar con el modelo. 
## 2. Activation for Hidden Layers

Una capa oculta es una capa que recibe entrada de otra capa (que puede ser otra capa oculta o la capa de entrada) y provee una salida que va hacia otra capa (también oculta o de salida). Una red neuronal puede tenero cero o más capas ocultas. Típicamente, utilizan funciones de activación no lineales, lo que les permite aprender funciones más complejas.

### ReLU Hidden Layer Activation Function

La **rectified linear activation function** es tal vez la más común para las capas ocultas. Es simple de implementar y efectiva al lidiar con las limitaciones de otras funciones de activación. Específicamente, es menos susceptible a **vanishing gradients** que previenen a los modelos profundos de ser entrenados, aunque puede sufrir de otros problemas como unidades saturadas o "muertas".

La función ReLU se calcula de esta manera:

> max(0.0, x)

Se puede tener una intuición de la forma de esta función con el siguiente ejemplo:

```python
# example plot for the relu activation function
from matplotlib import pyplot

# rectified linear function
def rectified(x):
	return max(0.0, x)

# define input data
inputs = [x for x in range(-10, 10)]
# calculate outputs
outputs = [rectified(x) for x in inputs]
# plot inputs vs outputs
pyplot.plot(inputs, outputs)
pyplot.show()
```
![](https://machinelearningmastery.com/wp-content/uploads/2020/12/Plot-of-Inputs-vs-Outputs-for-the-ReLU-Activation-Function..png)

### Sigmoid Hidden Layer Activation Function

También se conoce como la **logistic function**. Es la misma función que se utiliza en la regresión logística. Toma cualquier valor real como entrada y devuelve una salida en el rango 0 a 1. Mientras más grande sea la entrada, más cercana a 1 será la salida.

Se calcula de la siguiente manera:

>\frac{1.0}{1.0+e^(-x))

Se puede tener una intuición de su forma con el siguiente ejemplo:

```python
# example plot for the sigmoid activation function
from math import exp
from matplotlib import pyplot

# sigmoid activation function
def sigmoid(x):
	return 1.0 / (1.0 + exp(-x))

# define input data
inputs = [x for x in range(-10, 10)]
# calculate outputs
outputs = [sigmoid(x) for x in inputs]
# plot inputs vs outputs
pyplot.plot(inputs, outputs)
pyplot.show()
```
![](https://machinelearningmastery.com/wp-content/uploads/2020/12/Plot-of-Inputs-vs-Outputs-for-the-Sigmoid-Activation-Function..png)

### Tanh Hidden Layer Activation Function

La **hyperbolic tangent activation function** también es conocida como la función **tanh**. Es muy similar a la función sigmoide e, incluso, tiene la misma forma de "S". La función toma cualquier valor real como entrada y devuelve una salida en el rango de -1 a 1. Mientras más grande sea la entrada, más cercana estará a 1.

Se calcula de la siguiente manera:

> \frac{e^x - e^(-x)}{e^x + e^(-x)}

Se puede tener una intuición de su forma con el siguiente ejemplo:

```python
# example plot for the tanh activation function
from math import exp
from matplotlib import pyplot

# tanh activation function
def tanh(x):
	return (exp(x) - exp(-x)) / (exp(x) + exp(-x))

# define input data
inputs = [x for x in range(-10, 10)]
# calculate outputs
outputs = [tanh(x) for x in inputs]
# plot inputs vs outputs
pyplot.plot(inputs, outputs)
pyplot.show()
```
![](https://machinelearningmastery.com/wp-content/uploads/2020/12/Plot-of-Inputs-vs-Outputs-for-the-Tanh-Activation-Function..png)

### How to Choose a Hidden Layer Activation Function 

Una red neuronal, por lo general, tendrá la misma función de activación en todas sus capas ocultas. La función de activación es típicamente elegida basada en el tipo de arquitectura de la red neuronal. Por ejemplo, arquitecturas como MLP y CNN utilizan ReLU.

La siguiente imagen puede servir de guía para determinar cuál función elegir.

![](https://machinelearningmastery.com/wp-content/uploads/2020/12/How-to-Choose-an-Hidden-Layer-Activation-Function.png)

## 3. Activation for Output Layers

La capa de salida en una red neuronal es la que produce directamente una predicción como salida del modelo. Todas las redes *feed-forward* tienen una capa de salida. 

### Linear Output Activation Function

Es también llamada **identidad** o **no activación**. Esta función no aplica ningún cambio al valor y lo devuelve exactamente como es.

```python
# example plot for the linear activation function
from matplotlib import pyplot

# linear activation function
def linear(x):
	return x

# define input data
inputs = [x for x in range(-10, 10)]
# calculate outputs
outputs = [linear(x) for x in inputs]
# plot inputs vs outputs
pyplot.plot(inputs, outputs)
pyplot.show()
```
![](https://machinelearningmastery.com/wp-content/uploads/2020/12/Plot-of-Inputs-vs-Outputs-for-the-Linear-Activation-Function.png)

Por lo general, los datos son normalizados o estandarizados antes de ser utilizados para entrenar el modelo.

### Sigmoid Output Activation Function

Idéntica a como se explicó anteriormente.

### Softmax Output Activation Function

La **softmax function** recibe un vector de valores reales y devuelve un vector, del mismo tamaño, con valores que suman 1.0, que puede ser interpretado como las probabilidades de pertenecer a cada clase. Está relacionada a la función **argmax**, que devuelve un 0 para todas las opciones y un 1 para la clase elegida. 

La función *softmax* se calcula de la siguiente manera:

> e^x / sum(e^x)

La función *softmax* no se puede graficar, pero se puede observar un ejemplo de ella en Python:

```python
from numpy import exp

# softmax activation function
def softmax(x):
	return exp(x) / exp(x).sum()

# define input data
inputs = [1.0, 3.0, 2.0]
# calculate outputs
outputs = softmax(inputs)
# report the probabilities
print(outputs)
# report the sum of the probabilities
print(outputs.sum())
```

### How to Choose an Output Activation Function

La función de activación en la capa de salida debe ser elegida con base en la predicción que se desea realizar. La siguiente imagen puede servir de guía para tomar una decisión:

![](https://machinelearningmastery.com/wp-content/uploads/2020/12/How-to-Choose-an-Output-Layer-Activation-Function.png)

# Comentarios sobre algo que haya aprendido

Esta lectura permitió conocer más a fondo las funciones de activación que, hasta el momento, yo desconocía. Únicamente había trabajado con ReLU, sin conocer cómo se calculaba o en qué casos es mejor utilizarla. Creo que las imágenes a modo de mapa concecptual, para guiar sobre cuál función de activación elegir, son particularmente útiles para tomar decisiones cuando se esté trabajando con redes neuronales. Esta lectura ofrece información muy práctica y lista para aplicar, combinada con los fundamentos suficientes para entender qué está pasando por debajo (por ejemplo, las fórmulas que se utilizan para cada función de activación). En lo personal, era el conocimiento que sentía que me faltaba sobre las funciones de activación en redes neuronales, por lo que fue de mucho provecho para mí.
# Dudas sobre el tema tratado

No tengo dudas sobre el tema tratado.