## Resumen de los temas estudiados

En estas semanas, se trabajó principalmente sobre dos temas: **Series de Tiempo** y **Análisis de Flujo de Datos**. El primero de ellos, es muy relevante cuando se tienen *datsets* cuyos atributos objetivos son **dependientes del tiempo**, es decir, interesa analizar la dependencia entre la variable de salida y los aspectos temporales que intervienen en los datos. En particular, se pueden identificar patrones en las observaciones del pasado y, con base en ellos, realizar predicciones sobre el futuro. Aunque los tiempos discretos son más comunes, las Series de Tiempo pueden tratar también con variables continuas.

Las Series poseen varios componentes principales. El **trend** describe si la serie incrementa, decrementa o se mantiene estable; la **seasonality** se refiere a olas de frecuencia regular (es decir, fluctuaciones) que aparecen en la serie y se repiten cada cierto tiempo; por último, el **random noise** es un tipo de fluctuación que, a diferencia de la *seasonality*, no se puede explicar y es irregular. Estos tres componentes se pueden mezclar o, por el contrario, descomponer para analizar la estructura de datos de la serie. Las Series de Tiempo son **stationary**, es decir, las propiedades estadísticas de la serie (media, varianza, autocorrelación) **no** cambian en el tiempo.
No obstante, si la serie tiene tendencia y temporalidad, entonces **no** es estacionaria.

Para transformar una serie no estacionaria en una estacionaria, por ende, interesa eliminar componentes; en particular, la tendencia. Para esto, se cuenta con técnicas como **moving average** o la **técnica de diferenciación**. Si la serie tiene un período regular (por ejemplo, se repite en semanas / meses / días), se puede eliminar también la temporalidad.

Las Series de Tiempo permiten realizar predicciones, para lo cual se tienen distintos modelos:

- **Exponential Smoothing**.
  - *Simple Exponential Smoothing*: se calcula de manera recursiva, con un parámetro alpha entre 0 y 1, el cual determina el peso otorgado a las observaciones pasadas y a las más recientes (la suma de ambas debe dar 1).
  - *Exponential Smoothing with trend adjustment*: agrega un parámetro al modelo anterior, denominado beta, que permite asignarle mayor importancia a las tendencias cercanas que se logren identificar.
  - *Exponential Smoothing with trend and seasonality adjustment*: agrega un parámetro más, denominado gamma, que permite asignarle mayor importancia a la *seasonality* más reciente.
  - *Simple Adaptive Exponential Smoothing*: adapta los parámetros (alpha, beta y gamma) de forma dinámica respecto al tiempo.
  - *Exponential Smoothing with damped trend*: utiliza un parámetro nuevo, phi, para actualizar el componente de temporalidad según la proyección la tendencia actual.
- **Auto-regresivos**
  - Identifican relaciones entre las observaciones de una serie de tiempo, las cuales están separadas por intervalos fijos llamados *time lag*.
  - Requieren que la serie sea estacionaria.
  - Son más flexibles y más generales que los basados en Exponential Smoothing. En la práctica, ambas clases tienen un rendimiento similar.
  - En series de tiempo con componentes dinámicos (como fenómenos económicos), los modelos de Exponential Smoothing alcanzan mejores resultados.
  - *Moving average:* busca una regresión lineal entre la serie de tiempo original y la serie compuesta por los residuales en los *q* períodos anteriores.
  - *Autoregressive Moving average (ARMA)*: combina términos auto-regresivos con *moving average* para intentar conseguir un mejor modelo.
  - *Autoregressive Integrated Moving average*: se utiliza cuando la serie es **no** estacionaria, dado que no se puede usar ARMA directamente.
  - *Seasonal Autoregressive Integrated Moving average*: se utiliza cuando la serie tiene también *seasonality*.
  

Seguidamente, se estudió el tema de **Análisis de Flujo de Datos**. Este análisis es de gran utilidad cuando no se tiene mucho tiempo para analizar los datos, es decir, se deben tomar decisiones prontas dado que los datos cambian constantemente. Para esto, se debe pasar del *batch processing* al **stream processing**, el cual es un paradigma de procesamiento de datos diseñado para trabajar con *data sets infinitos*. Las diferencias entre ambos paradigmas se datallan en la siguiente tabla:

|                  | Batch                                 | Streaming                         |
| ---------------- | ------------------------------------- | ---------                         |
| Frecuencia       | Jobs poco frecuentes                  | Jobs permanentemente en ejecución |
| Desempeño        | Alta latencia (mins, horas)           | Baja latencia (secs, milisecs)    |
| Fuentes de datos | DBs, APIs, archivos                   | Colas, streaming, transacciones   |
| Tipo de análisis | Complejo                              | Simple                            |
| Procesamiento    | Ocurre después de almacenar los datos | Antes de almacenar los datos      |

La naturaleza de los datos tiene que ver con dos aspectos:

- **Cardinalidad**: tamaño finito o infinito.
- **Constitución**: tablas (*SQL, NoSQL, Archivos*) o *streams* (datos en movimiento). 

Los **tipos de procesamiento** se pueden clasificar en dos grandes clases:

- *Bounded data*
  - Esquema más conocido; los datos pasan por un motor de procesamiento como MapReduce.
  - Cuando se tienen problemas de muestreo (no se pueden almacenar todos los datos que llegan), no son muy efectivos.
- *Unbounded data*
  - Los datos de streaming suelen **no** estar en orden, por lo que es difícil analizarlos dentro de un contexto. Se tienen algunos enfoques para analizar estos datos:
  - *Time agnostic*: el tiempo es irrelevante para el análisis; fácil de implementar mediante *chunks* de los datos.
  - *Approximation*: transforman los datos y los convierten en algo similar que conserva ciertas similitudes.
  - *Windowing*: utiliza el algoritmo de *sliding window* para conservar ciertas características de la temporalidad.
  - *Windowing by processing time*: se apilan los datos entrantes en un *buffer* hasta conseguir un bloque de tiempo determinado.
  - *Windowing by event*: es el método más utilizado; los bloques determinan el tiempo del evento y no el tiempo de procesamiento.
  - *Tumbling Window*: se dispara cuando la ventana está llena, ya sea *count-based* o *temporal-based*.

Cuando el *stream* de datos es muy grande, puede ser necesario un **filtro** para eliminar tuplas u observaciones que no cumplen con un criterio de aceptación. Uno de ellos es el **Filtro de Bloom**, el cual es una estructura de datos probabilística que permite determinar membresía o no en un conjunto, mediante funciones hash. En él, pueden ocurrir falsos positivos, pero no falsos negativos.

## Comentarios sobre algo aprendido

Ambos temas los desconocía, por lo que estas dos semanas fueron las de mayor provecho para mí en el curso. Con respecto a las Series de Tiempo, durante las tareas iniciales del curso, tenía dudas sobre cómo utilizar *datasets* que incluyeran datos temporales: no sabía si debía tratarlos como un atributo más o darle un tratamiento especial. Con este tema, se me aclaró mucho el panorama sobre cómo trabajar en estas situaciones, al conocer que existe una gran cantidad de modelos que se ajustan al problema. En particular, me llamaron mucho la atención los modelos de Exponential Smoothing, pues su idea base (utilizar un parámetro para determinar cuánto peso se le asigna a las observaciones pasadas y a las más recientes) ya la había visto en el curso de Redes, pero aplicada al envío de paquetes en una red.

Con respecto al tema de Análisis de Datos, me gustó ver una estructura de datos probabilísticas, pues hasta el momento no habían sido consideradas en la carrera. En el mundial de la ICPC al que asistí, en Moscú, nos dieron una charla sobre investigación moderna en algoritmos y, en ella, se habló sobre los algoritmos de *streaming*. En particular, se mencionó que no se pueden guardar todos los datos y es necesario utilizar aleatorización, por lo que las estructuras y algoritmos deterministas no aplican en esta área. Me gustó mucho ver cómo un tema tan moderno pudo ser cubierto en clase, algo que difícilmente se ha logrado en cursos anteriores.

## Dudas sobre la materia estudiada

No tengo dudas sobre la materia estudiada.

## Posible uso que usted le dará a esta materia como profesional

En mi caso personal, desconocía las estructuras de datos probabilísticas, por lo que aprender sobre el Filtro de Bloom me dio un punto de partida para investigar sobre ellas y sus aplicaciones. También, con las Series de Tiempo, tengo una herramienta para procesar conjuntos de datos fuertemente ligados al aspecto temporal, algo que no podía hacer hasta el momento. Utilizando un problema similar al que propuse anteriormente (analizar si la serie "Gambito de Dama" influyó en que se jugaran más partidas con esa apertura en Lichess.org), con las series de tiempo podría analizar si existen tendencias en las aperturas que se juegan según la época del año. Por ejemplo, si el Campeonato Mundial de Ajedrez (un evento bienal) influye en los jugadores más novatos en utilizar aperturas más sólidas (Peón Rey o Peón Dama) o si, por ejemplo, las épocas cercanas a Navidad y fin de año influyen en utilizar aperturas menos comunes. 

## Mencione cualquier material que utilizó como referencia para el aprendizaje.
En estas dos semanas, no he utilizado material extra en el aprendizaje.