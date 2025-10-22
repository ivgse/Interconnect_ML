# Interconnect_ML

En este proyecto desarrollo un modelo para encontrar a los clientes que tienen más probabilidad de dejar de contratar servicios con la compañía, y así poder crear estrategias de retención o planes personalizados.

Para esta tarea de clasificación, lo primero que hice fue hacer un merge de los 4 datasets, para crear un solo conjunto de datos y trabajar sobre este. En este proceso, para las caracteristicas que son solo Sí/No, hizo un reemplazo por 1/0; Y en los archivos que tienen menos observaciones, se trabajaron los Nan que se generaron al fusionar los dfs, con un 0 para indicar que no contaban con esos servicios. También se realizó OHE para las caracteristicas con más de dos valores.

Al revisar el target('EndDate'), se nota que hay desequilibrio de clases, por lo que se hace un sobreescalamiento para los modelos donde es necesario.

Pasando al entrenamiento de los modelos, se definen las columnas categoricas ordinales y se procesan con OrdinalEncoder, y se definen las categoricas no ordinales y se procesan mediante OHE, también se utilizó un escalador para datos numericos, así se prepararan los datos para los diferentes modelos. Se hace un modelo lineal para referencia, Un bosque aleatorio, dos modelos de gradiente y una red neuronal. Se creo también una función personalizada para evaluar los modelos mediante Accuracy y AUC ROC.

De acuerdo a nuestra metrica objetivo(ROC AUC), el modelo con mejores resultados es Catboost, seguido del bosque aleatorio, y si tomamos en cuenta nuestra metrica secundaria (Accuracy), Catboost es superior a todos los demás. Se realizo Validación Cruzada en Light GBM y en bosque aleatorio, ambos tuvieron metricas bastante altas, pero al correrlos con el set de validación, sus metricas clave bajaron considerablemente.
