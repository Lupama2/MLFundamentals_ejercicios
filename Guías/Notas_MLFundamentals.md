Guía 2

2.1.4. Se puede poner el gráfico encima de la imagen de California? Estará a escala?
2.1.5. Se refiere a que intente crear nuevos atributos a partir de algunos existentes que me podrían ser útiles para el análisis exploratorio?

09/09/2022 - comentarios de la resolución del profesor

Standarización

Para los numéricos normalizamos con la media y dividimos por la desviación estándar. Sklearn tiene una función que lo hace automáticamente
Para los categóricos hacemos un OneHotEncoder (o uno ordenal)
Por último, juntamos los datos, ya sea con numpy o usamos dataframes.
En el proceso hay que tener cuidado de no haber desordenado los datos. En el caso de que se haya hecho, es necesario mantener una variable índices que me sirva para concatenar correctamente.

Modelos
En el notebook de la cátedra no se hace feature engineering para mejorar los modelos

Regresión lineal
Viendo los resultados, uno encuentra coeficientes con e17. Suele haber una tendencia a que coefs grandes implican que el modelo "está haciendo cualquier cosa". En tal caso se puede hacer regularización, pesando los parámetros en la función de Loss, o podría directamente tirar esos features.
Una vez hecho esto, uno puede plotear los datos de entrenamiento junto con la predicción, solo usando precios vs alguna variable. El gráfico que más sentido tiene hacer es con las variables correlacionadas. Es útil ver si hay overfitting.

Árbol de decisión para la regresión
Sin usar los datos estandarizados.
Las predicciones calzan exactamente arriba del dato real. Overfitting característico de los árboles.

Random Forest
Anda mejor que la regresión lineal, se parece mucho a los puntos pero no es capaz de predecir el ruido, indicando que no es overfitting. Esto es cualitativo porque se hizo gráficamente

Métricas en una regresión
Comparación de modelos. No hay problemas con las unidades de los errores porque no están estandarizados los resultados. En clases hubo una discusión sobre si había o no que desestandarizar los errores.


CV
Cross validation
Nos interesa que los scores sean más o menos parecidos porque si no en algún caso está overfitteando. Uno puede ver esto directamente con el desvío estándard. Si el desvío estándard es grande, sabemos que el modelo es muy sensible a hacer overfitting porque ((se ajusta muy bien a algunos datos y muy mal a otros))

Estaría bueno hacer la misma partición para todos los modelos. Esto se puede hacer con una seed

CV Trees
Tengo un montón de error porque en cada tree ((estoy haciendo overfitting))

CV Random Forest
Tiene un mejor rendimiento

Una vez hecho esto, uno podría hacer feature engineering para mejorar el modelo.

FINE TUNING
Buscamos hiperparámetros para mejorar aún más el rendimiento. Bajo este concepto, uno hace gridsearch probando con distintos parámetros. Generalmente tarda mucho tiempo en hacerse porque para cada conjunto de hiperparámetros tiene que hacer crossvalidation y toma mucho tiempo, a pesar de que no se gana demasiado. Para hacer esto está bueno saber muy bien qué significa cada hiperparámetro.
En el gridsearch en Python se puede poner los hiperparámetros como diccionario. Si no sabemos cómo variar los hiperparámetros, podemos usar random search CV.

En Random Forest está bueno usar la métrica de "Feature importance", es decir, la pureza que resulta de un split en el que está involucrado un feature en particular. Hay que tener cuidado para tomar decisiones de feature engineering sobre esto. 




