# Análisis RFM utilizando métodos de Clustering

## Introducción

El presente análisis RFM se realizó para una tienda online de indumentaria masculina, que apunta a un segmento de 20 a 45 años y comercializa en todo el territorio argentino.

El análisis RFM permite identificar a los mejores clientes de acuerdo al comportamiento histórico transaccional. Clasifica a los clientes por su valor en función de tres variables:

* Recencia (Recency): días transcurridos desde la última compra.
* Frecuencia (Frecuency): número de compras por período de tiempo.
* Valor Monetario (Monetary Value): valor de las compras totales realizadas por el cliente en el periodo de análisis.

## Código y recursos utilizados
* Versión de Python: 3.6
* Librerías: pandas, numpy, sklearn, matplotlib, seaborn, scipy, plotly
* Dataset: propio

## Preparación de datos
Se unificaron dos datasets, el primero con datos transaccionales de MercadoPago de 2020 y 2021 de la tienda online y el segundo con datos de usuarios de la misma. Se realizó limpieza de valores nulos y selección de columnas para trabajar.
Se calcularon las variables recencia, frecuencia y valor monetario para modelar.
Se realizó limpieza de outliers, rescaleo y normalización de datos.

## Análisis Exploratorio (EDA)
Al analizar las tres variables del análisis RFM se obervó lo siguiente:

#### Recencia:
Una alta concentración de usuarios compró por última vez entre 200 y 390 días previos a la fecha del análisis, con una media de 228 días; y en menor medida, una concentración de usuarios que compró en los últimos 30 días previos a la fecha del análisis.

#### Frecuencia:
La mayoría de los usuarios del periodo compró una sola vez en la tienda, y en menor proporción un grupo de usuarios compró entre 2 y 3 veces.

#### Valor Monetario:
Existe una gran proporción de usuarios que en el periodo realizó transacciones por un valor promedio de $10.400.

## Modelado
Se optó por aplicar tres modelos de Clustering y comparar sus resultados.

#### K-means
Encuentra una partición de los datos en k grupos, tal que la distancia media dentro de los puntos de cada grupo sea mínima.

#### Hierarchical Clustering (Clustering Jerárquico)
Construye clusters anidados, de los que se puede extraer luego una cantidad dada de grupos.

## Conclusiones
El método de clustering que mejor delimitó los grupos dentro del dataset analizado fue el método Jerárquico (Agglomerative Clustering con el parámetro de linkage complete). Para en análisis final se desestimó el parámetro de linkage ward por tener similitud con K-means. 
Al comparar los clusters de K-means se observa en el gráfico tridimensional que algunos puntos en los grupos no tuvieron una clara delimitación entre sí, es decir, algunos puntos de un cluster determinado puede pertencer a otro. 
Se observa que K-means devuelve una delimitación de clusters poco lógica a la forma de los datos.

En términos comerciales, al analizar los clusters obtenidos por el método Jerárquico, encontramos que:

* En cuanto al monto gastado por los clusters, no existe gran diferencia entre ambos. Se ubican en el rango de 0-10.000 pesos (clusters 0 y 1).
* En cuanto a la frecuencia de compra, se encuentra una clara diferenciación entre los que compraron entre 1 y 3 veces (cluster 1) de los que compraron 1 o 2 veces (cluster 0).
* En cuanto a los días transcurridos desde la última compra (recencia), no se observan diferencias en dicha variable, en ambos clusters, los días transcurridos desde la última compra están entre los 100 y 300.
* En tanto el cluster más interesante del análisis RFM es el 1, puesto que compra los mismos montos y su última compra fue en la misma cantidad de días que el cluster 0, pero lo ha realizado con mayor frecuencia.

## Consideraciones finales sobre el análisis de clustering realizado
El dataset utilizado contiene datos de transacciones del último año, en tanto, se plantea como siguiente paso realizar un análisis de robustez de los clusters agregando más datos de transacciones. A pesar de haber aplicado 2 métodos que encontraron clusters delimitados, al analizar las características de los mismos, no se encontraron grandes diferencias (solo en la variable frecuencia) que puedan ser de gran interés comercial, por ende sería conveniente seguir completando el dataset con mayor cantidad de transacciones para volver a realizar el análisis. En otras palabras, el conjunto de datos muestra un gran cluster y no varios clusters individualizados susceptibles de interés comercial.

## Fuentes
* https://www.kaggle.com/hellbuoy/online-retail-k-means-hierarchical-clustering
* https://towardsdatascience.com/data-driven-growth-with-python-part-2-customer-segmentation-5c019d150444
* https://colab.research.google.com/drive/15w3BPG8rCJFOFIteH2oc-C73Nx-Yhiv2#scrollTo=nSOUDCtlnZK8
* https://www.kaggle.com/datark1/customers-clustering-k-means-dbscan-and-ap
