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
