<div align="center">

## TECNOLÓGICO NACIONAL DE MÉXICO

### INSTITUTO TECNOLÓGICO DE TIJUANA

SUBDIRECCIÓN ACADÉMICA
 
DEPARTAMENTO DE SISTEMAS Y COMPUTACIÓN
 
SEMESTRE SEPTIEMBRE 2020 – ENERO 2021

INGENIERÍA EN SISTEMAS COMPUTACIONALES

<img src="../images/logo.png" width="200" height="200">




### MASTER

JOSÉ CHRISTIAN ROMERO HERNÁNDEZ

### CLASS

BIG DATA 

### UNIT 2

#### "GRADIENT-BOOSTED TREE CLASSIFIER"


### TEAM

BERNARDINO MARTINEZ JERONIO 14212334

CERON URIBE ARTURO 17211506

GUTIERREZ LUNA YURIDIA NAYELI 16212353

HERNANDEZ GAMBINO KEVIN JOSAFAT 17211049

MARTINEZ FLORES PAMELA STEPHANY	16212034

MOSQUEDA ESPINOZA ADAMARI ANTONIA 16212363





**TIJUANA, BAJA CALIFORNIA, NOVEMBER 25, 2020.** 




</div>







# GRADIENT-BOOSTED TREE CLASSIFIER, GRADIENT BOOSTING O "CLASIFICADOR DE ÁRBOLES POTENCIADO POR GRADIENTES" 

### Concepto

Gradient boosting es una técnica de aprendizaje automático para problemas de regresión y clasificación que producen un modelo de predicción en forma de un conjunto de modelos de predicción débiles. Esta técnica construye un modelo de una manera escénica y generaliza el modelo permitiendo la optimización de una función de pérdida diferenciable arbitraria.

### ¿Cómo funciona?

Gradient boosting básicamente combina a los alumnos débiles en un solo alumno fuerte de una manera iterativa. A medida que se añade cada alumno débil, se ajusta un nuevo modelo para proporcionar una estimación más precisa de la variable de respuesta. Los nuevos alumnos débiles se correlacionan al máximo con el gradiente negativo de la función de pérdida, asociado con todo el conjunto. La idea de aumentar el gradiente es que se puede combinar un grupo de modelos de predicción relativamente débiles para construir un modelo de predicción más fuerte.

### Ejemplo 

Como hemos dicho, boosting es la creación de un clasificador fuerte a partir de muchos débiles. Por ejemplo si tenemos 2 árboles, la predicción sería la suma de las clasificaciones:

![](https://github.com/AdamariMosqueda/Gradient-boosted-tree-classifier/blob/master/images/example.png)

Matemáticamente se expresa de la siguiente forma:

**_Si tenemos 2 árboles, se suman las predicciones_**

Pero tambíen se puede expresar como la suma del último árbol a lo que ya teníamos sumado.

![](https://github.com/AdamariMosqueda/Gradient-boosted-tree-classifier/blob/master/images/math1.png)

Esta función **ŷ** es nuestra predicción y tenemos que optimizarla. Para ello creamos una función objetivo (basada en el error cuadrático por ejemplo) que tenemos que minimizar:

![](https://github.com/AdamariMosqueda/Gradient-boosted-tree-classifier/blob/master/images/math2.png)


### Aplicaciones 

"Neurobiótica se refiere al estudio del sistema nervioso en conjunto con la tecnología. De particular importancia en el campo de la neurobiótica es el cerebro y su interacción directa con los sistemas informáticos, así como los métodos de simulación externa del cerebro"

![](https://github.com/AdamariMosqueda/Gradient-boosted-tree-classifier/blob/master/images/neuro.png)

Gradient boosting es una herramienta práctica útil para las tareas de predicción, y proporciona consistentemente resultados de mayor precisión en comparación con los modelos convencionales de aprendizaje automático. Por ejemplo, el aumento del gradiente ayuda a crear modelos que pueden mapear las lecturas de los sensores EMG y EEG al seguimiento del movimiento humano y el reconocimiento de la actividad.

### Fuentes de consulta 
- https://towardsdatascience.com/machine-learning-part-18-boosting-algorithms-gradient-boosting-in-python-ef5ae6965be4 
- https://fhernanb.github.io/libro_mod_pred/gradboost.html 
- https://spainml.com/blog/como-funciona-gradient-boosting/ 
- https://deepai.org/machine-learning-glossary-and-terms/gradient-boosting 
- https://en.wikipedia.org/wiki/Gradient_boosting#:~:text=Gradient%20boosting%20is%20a%20machine,prediction%20models%2C%20typically%20decision%20trees.  
- https://blog.paperspace.com/gradient-boosting-for-classification/ 
- https://medium.com/gradient-boosting-working-limitations-time/gradient-boosting-working-and-applications-28e8d4ba866d 
- https://en.wikipedia.org/wiki/Neurobiotics 
- https://spainml.com/blog/como-funciona-gradient-boosting/  