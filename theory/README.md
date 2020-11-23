# Gradient Boosted tree classifier 

## Components
Gradient Boosting has three main components:

1. Loss Function - The role of the loss function is to estimate how good the model is at making predictions with the given data. This could vary depending on the problem at hand. For example, if we're trying to predict the weight of a person depending on some input variables (a regression problem), then the loss function would be something that helps us find the difference between the predicted weights and the observed weights. On the other hand, if we're trying to categorize if a person will like a certain movie based on their personality, we'll require a 
loss function that helps us understand how accurate our model is at classifying people who did or didn't like certain movies.

2. Weak Learner - A weak learner is one that classifies our data but does so poorly, perhaps no better than random guessing. In other words, it has a high error rate. These are typically decision trees (also called decision stumps, because they are less complicated than typical decision trees).

1. Additive Model - This is the iterative and sequential approach of adding the trees (weak learners) one step at a time. After each iteration, we need to be closer to our final model. In other words, each iteration should reduce the value of our loss function.



## Gradient boosting vs Adaptive boosting

| Gradient boosting | Adaptive boosting | 
| --- | --- |
| This approach trains learners based upon minimising the loss function of a learner (i.e., training on the residuals of the model)  | This method focuses on training upon misclassified observations. Alters the distribution of the training dataset to increase weights on sample observations that are difficult to classify.| 
| Weak learners are decision trees constructed in a greedy manner with split points based on purity scores (i.e., Gini, minimise loss). Thus, larger trees can be used with around 4 to 8 levels. Learners should still remain weak and so they should be constrained (i.e., the maximum number of layers, nodes, splits, leaf nodes) | The weak learners incase of adaptive boosting are a very basic form of decision tree known as stumps. |
| All the learners have equal weights in the case of gradient boosting. The weight is usually set as the learning rate which is small in magnitude. | The final prediction is based on a majority vote of the weak learners’ predictions weighted by their individual accuracy. | 


# Gradient-boosted-tree-classifier

## 1.-Gradient boosting
El algoritmo de Boosting por etapas hacia adelante es también una estrategia muy codiciosa. En cada paso, el árbol que tenemos como solución es el que más reduce Θ̂𝑚 =
arg 𝑚𝑖𝑛Θ𝑚
∑ 𝐿(𝑦𝑖, 𝑓𝑚−1(𝑥𝑖) + 𝑇(𝑥𝑖, Θ𝑚))𝑁𝑖=1, dado el modelo actual 𝑓𝑚−1. De esta forma, las predicciones dadas por 𝑇(𝑥𝑖, Θ𝑚) son análogas a las componentes del gradiente con signonegativo 𝑔𝑖𝑚 = [𝜕𝐿(𝑦𝑖,𝑓(𝑥𝑖)𝜕𝑓(𝑥𝑖)]𝑓(𝑥𝑖)=𝑓𝑚−1(𝑥𝑖) . La principal diferencia entre ambas es que las
componentes procedentes de los árboles 𝑡𝑚 = (𝑇(𝑥1,Θ𝑚), 𝑇(𝑥2,Θ𝑚), … , 𝑇(𝑥𝑁,Θ𝑚)) no sonindependientes. Están obligadas a ser las predicciones de un árbol de decisión de nodo 𝐽𝑚-
terminal, mientras que el gradiente negativo es la dirección de máximo descenso sinrestricciones.

La solución a 𝛾̂𝑗𝑚 = arg 𝑚𝑖𝑛𝛾𝑗𝑚 ∑ 𝐿(𝑦𝑖, 𝑓𝑚−1(𝑥𝑖 𝑥) + 𝛾𝑗𝑚)𝑖∈𝑅𝑗𝑚 en el método de pasos haciaadelante es análoga a la de 𝜌𝑚 = arg 𝑚𝑖𝑛𝜌 𝐿(𝑓𝑚−1 − 𝜌𝑔𝑚) en el caso del método de máximo descenso, con la diferencia de que en el primero se realiza una búsqueda separada en línea paraaquellas componentes de 𝑡𝑚 que corresponden a cada región terminal {𝑇(𝑥𝑖, Θ𝑚)}0𝑥𝑖∈𝑅𝑗𝑚.
Si minimizar la función de pérdida en el conjunto de datos de entrenamiento 𝐿(𝑓) =∑ 𝐿(𝑦𝑖, 𝑓(𝑥𝑖))𝑁𝑖=1 fuese el único objetivo, el algoritmo de máximo descenso sería la mejoropción. El gradiente es fácil de calcular para cualquier función de perdida diferenciable, mientras que resolver Θ̂𝑚 = arg 𝑚𝑖𝑛Θ𝑚∑ 𝐿(𝑦𝑖 , 𝑓𝑚−1(𝑥𝑖) + 𝑇(𝑥𝑖, Θ𝑚))𝑁𝑖=1 es difícil debido al ya mencionado criterio de robustez. Desafortunadamente, el gradiente solo está definido para las observaciones del conjunto de entrenamiento, siendo el principal y último objetivo generalizar la expresión 𝑓𝑀(𝑥) a los datos del conjunto test.

Una posible solución a este dilema presentado es inducir un árbol 𝑇(𝑥, Θ𝑚) en la m-ésima iteración cuyas predicciones 𝑡𝑚 estén tan cerca como sea posible del gradiente negativo. Esto nos conduce a   ̃𝑚 = arg 𝑚𝑖𝑛Θ𝑚 ∑(−𝑔𝑖𝑚 − 𝑇(𝑥𝑖 , Θ))2

Explicándolo con mayor detalle, se trata de ajustar un árbol 𝑇 a los valores del gradiente con signo negativo mediante mínimos cuadrados. Como vimos anteriormente, existen algoritmos rápidos para inducir árboles de decisión mediante mínimos cuadrados. Aunque las regiones 𝑅̃ 𝑗𝑚que obtenemos mediante la solución a Θ̃𝑚 = arg 𝑚𝑖𝑛Θ𝑚
∑ (−𝑔𝑖𝑚 − 𝑇(𝑥𝑖 , Θ)) 𝑁 2 𝑖=1 no son idénticas a las obtenidas 𝑅𝑗𝑚 resolviendo Θ̂𝑚 = arg 𝑚𝑖𝑛Θ𝑚 ∑ 𝐿(𝑦𝑖 , 𝑓𝑚−1 (𝑥𝑖 ) + 𝑇(𝑥𝑖 , Θ𝑚)) 𝑁 𝑖=1 , sí podemos decir que son similares, ya que persiguen un mismo objetivo. En cualquier caso, el procedimiento de Boosting mediante pasos hacia adelante y la inducción de un árbol de decisión
de manera descendente son procedimientos de aproximación. Tras construir el árbol mediante la expresión Θ̃𝑚 = arg 𝑚𝑖𝑛Θ𝑚 ∑ (−𝑔𝑖𝑚 − 𝑇(𝑥𝑖 , Θ)) 𝑁 2 𝑖=1 , el valor que toman las observaciones que caen en una región viene dado por la expresión 
