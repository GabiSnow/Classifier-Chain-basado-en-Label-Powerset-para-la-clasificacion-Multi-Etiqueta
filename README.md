-Label powerset based classifier chains for multi-label classification.-


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


