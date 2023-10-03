# Classifier Chain basado en Label Powerset para la clasificación Multi-Etiqueta 

Uno de los métodos más utilizados para abordar la clasificación multi-etiqueta es el
enfoque conocido como "Classifier Chain" o "cadena de clasificadores". Este metodo se
basa en encadenar múltiples clasificadores, donde la salida de un clasificador se utiliza
como entrada para el siguiente, permitiendo así manejar la asignación de múltiples
etiquetas a una instancia. Sin embargo, a pesar de su eficacia, el uso de cadenas de
clasificadores a menudo conlleva un alto coste computacional. 

En este trabajo, proponemos una modificación de este enfoque que incorpora el concepto de
"powersets" o conjuntos de potencia. En lugar de construir una cadena de
clasificadores utilizando una sola etiqueta en cada paso, consideramos eslabones más
complejos compuestos por los powersets de un número reducido de etiquetas. Esta
modificación no solo simplifica el número de clasificadores necesarios, sino que
también puede mejorar la eficiencia computacional en problemas con un gran número
de etiquetas. 

# Algoritmo implementado.

El proceso comienza con la aplicación del algoritmo de clustering Balanced K-Means a
las etiquetas del conjunto de datos de entrenamiento. Este algoritmo tiene como
objetivo dividir las etiquetas en grupos o clusters de manera equilibrada con el objetivo
de que las etiquetas se agrupen en función de sus características y relaciones,
buscando una mayor eficiencia en la clasificación. El número de clusters se determina
automáticamente, para formar N grupos de 3 miembros como máximo.

_Entrenamiento del modelo_

Una vez que se ha realizado el clustering, se procede a entrenar la cadena de
clasificadores. Cada cluster de etiquetas se considera un problema de clasificación
independiente, asi que para cada cluster se entrena un clasificador utilizando un
enfoque basado en Label Powerset. El modelo de Label Powerset se utiliza para
transformar el problema de clasificación multi-etiqueta en un problema de clasificación
multi-clase, donde cada combinación única de etiquetas se trata como una clase
separada. Para nuestro caso el clasificador elegido al que aplicarle Label Powerset ha
sido Random Forest.

Cada clasificador de la lista se entrena con el conjunto de datos de características
original, concatenándole a dicho conjunto las predicciones dadas por los clasificadores
anteriores, siguiendo así el concepto principal de Classifier Chain. Esto permite que el
siguiente clasificador en la cadena tenga en cuenta tanto las predicciones previas como
las características originales para mejorar la precisión de la clasificación.

_Fase de predicción_

Finalmente, cuando se desea hacer predicciones para un nuevo conjunto de datos, el
algoritmo utiliza la cadena completa de clasificadores para generar predicciones multietiqueta. Cada clasificador en la cadena aborda un subconjunto específico de
etiquetas, y las predicciones de todos los clasificadores se combinan para obtener la
etiqueta final para cada instancia de datos. 

