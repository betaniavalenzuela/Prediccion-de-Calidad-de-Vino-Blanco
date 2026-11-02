# **Predicción de la calidad del vino blanco a partir de sus propiedades fisicoquímicas**

## **1\. Descripción del conjunto de datos**

Para este proyecto se utilizó el conjunto de datos *Wine Quality – White Wine*, que contiene información sobre distintas propiedades fisicoquímicas de muestras de vino blanco y su correspondiente calificación de calidad.

Luego del proceso de limpieza y preparación, el conjunto de datos quedó conformado por **3961 registros y 12 columnas**. De estas columnas, 11 corresponden a variables predictoras y una representa la variable objetivo (quality), que se busca predecir mediante un modelo de aprendizaje automático.

Las variables que componen el conjunto de datos se describen a continuación:

| Variable | Tipo de dato | Significado |
| :---- | :---- | :---- |
| fixed acidity | Numérico (decimal) | Acidez fija del vino. |
| volatile acidity | Numérico (decimal) | Acidez volátil del vino. |
| citric acid | Numérico (decimal) | Cantidad de ácido cítrico. |
| residual sugar | Numérico (decimal) | Cantidad de azúcar residual. |
| chlorides | Numérico (decimal) | Concentración de cloruros. |
| free sulfur dioxide | Numérico (decimal) | Cantidad de dióxido de azufre libre. |
| total sulfur dioxide | Numérico (decimal) | Cantidad total de dióxido de azufre. |
| density | Numérico (decimal) | Densidad del vino. |
| pH | Numérico (decimal) | Medida relacionada con la acidez del vino. |
| sulphates | Numérico (decimal) | Concentración de sulfatos. |
| alcohol | Numérico (decimal) | Contenido de alcohol. |
| quality | Entero | Calificación de calidad del vino. |

## **2\. Origen de los datos**

El conjunto de datos fue publicado en 2009 y se encuentra disponible en UCI Machine Learning Repository, un repositorio público que reúne varios conjuntos de datos para ser utilizados.

Los datos del dataset estan asociados al trabajo de Paulo Cortez, titulado *Modeling wine preferences by data mining from physicochemical properties*. Las muestras corresponden a vinos verdes portugueses (*Vinho Verde*), elaborados en el norte de Portugal.

Los datos incluyen mediciones fisicoquímicas y una evaluación de calidad realizada mediante análisis sensorial. Esta información nos va a permitir estudiar si existe alguna relación entre las características del vino y la calificación obtenida.

## **3\. Carga y exploración inicial de los datos**

En primer lugar se realizó una exploración inicial para conocer la estructura del conjunto de datos, la cantidad de registros y columnas, los tipos de datos y la existencia de valores faltantes o registros duplicados.

Durante esta revisión se identificaron dos situaciones que requerían atención. Por un lado, la columna alcohol, que representa una variable numérica, había sido interpretada como texto debido a la presencia de algunos valores con un formato incorrecto. Por otro lado, se encontraron registros duplicados.

Estas observaciones hicieron necesario realizar algunas correcciones antes de continuar con el análisis.

## **4\. Limpieza y transformación de los datos**

La preparación de los datos tuvo como objetivo corregir inconsistencias y asegurar que la información pudiera utilizarse correctamente en las etapas posteriores.

En primer lugar, se revisó la columna alcohol, ya que algunos valores presentaban un formato incorrecto y no podían convertirse directamente a números. Se identificaron 34 registros con este problema. Para corregirlos, se consultó el archivo original del conjunto de datos y se recuperaron los valores correspondientes. De esta manera, la columna pudo convertirse al tipo numérico decimal.

También se detectaron **937 registros duplicados**. Se decidió eliminarlos para trabajar con combinaciones únicas de valores y evitar que las mismas observaciones tuvieran una influencia repetida durante el aprendizaje del modelo. Esta decisión corresponde a un criterio de preparación adoptado para el proyecto.

Posteriormente, mediante el análisis estadístico descriptivo, se observaron valores inusuales en la variable density. Al revisar los registros, se identificaron 51 valores que presentaban inconsistencias respecto de los datos originales. Estos fueron reemplazados por los valores correspondientes del archivo original.

Una vez realizadas las correcciones, se volvió a comprobar la estructura de los datos. El conjunto quedó conformado por **3961 registros y 12 columnas**, sin valores faltantes ni registros duplicados.

## **5\. Análisis exploratorio de datos (EDA)**

Una vez finalizada la limpieza, se realizó un análisis exploratorio para comprender mejor el comportamiento de las variables y observar posibles relaciones con la calidad del vino.

Se utilizaron medidas estadísticas descriptivas, histogramas y gráficos de correlación. Esto permitió identificar la distribución de los datos, reconocer posibles valores extremos y observar qué variables presentaban mayor relación con la variable objetivo.

En la distribución de quality se observó una concentración importante de calificaciones 5 y 6, que representan aproximadamente el 75 % de los registros. En cambio, las calificaciones más altas y más bajas aparecen con menor frecuencia. Esta distribución es importante porque indica que el conjunto de datos no presenta la misma cantidad de observaciones para todas las categorías de calidad.

También se analizaron los valores extremos mediante el método del rango intercuartílico (IQR). Si bien se detectaron posibles valores atípicos en algunas variables, se decidió conservarlos, ya que su presencia no implica necesariamente que sean errores de medición. Eliminarlos sin una justificación podría provocar la pérdida de información útil.

Por último, el análisis de correlación permitió observar que alcohol presenta la relación positiva más importante con quality, mientras que density muestra una relación negativa destacada. Esto indica que, dentro de los datos analizados, las muestras con mayor contenido de alcohol tienden a presentar calificaciones más altas, mientras que una mayor densidad tiende a relacionarse con calificaciones más bajas. Sin embargo, estas relaciones no implican causalidad ni permiten determinar por sí solas la calidad del vino.

## **6\. Preparación para el modelado**

Una vez finalizadas las etapas de carga, limpieza y análisis exploratorio, se prepararon los datos para su utilización en los modelos de aprendizaje automático.

Se separaron las variables predictoras (X), correspondientes a las 11 propiedades fisicoquímicas, de la variable objetivo (y), que contiene las calificaciones de calidad.

Posteriormente, se dividió el conjunto de datos en dos partes: un 80 % destinado al entrenamiento y un 20 % reservado para la prueba. Esta separación permite disponer de datos para entrenar los modelos y de otros registros para evaluar su desempeño con observaciones que no participaron del entrenamiento.

En esta etapa se obtuvieron 3168 registros para entrenamiento y 793 para prueba.

## **7\. Consideraciones finales**

El proceso de preparación permitió obtener un conjunto de datos limpio y estructurado, adecuado para continuar con el desarrollo del proyecto. La revisión de los tipos de datos, la corrección de inconsistencias, la eliminación de duplicados y el análisis exploratorio fueron pasos necesarios para comprender la información y tomar decisiones antes de construir los modelos.

A partir de esta preparación, el siguiente paso del trabajo será desarrollar y comparar modelos de aprendizaje automático que permitan predecir la calidad del vino blanco a partir de sus propiedades fisicoquímicas.

## **Bibliografía**

Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). *Modeling wine preferences by data mining from physicochemical properties*. Decision Support Systems, 47(4), 547–553.

UCI Machine Learning Repository. *Wine Quality Data Set*. [https\://archive.ics.uci.edu/dataset/186/wine+quality](https://archive.ics.uci.edu/dataset/186/wine+quality)

