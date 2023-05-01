# **Clasificador de Aves**

-----
### Este proyecto va a consistir en el análisis, exploración de datos y creación de un modelo de red neuronal convolucional para la predicción de la 525 diferentes razas de aves, Para ello he usas las librerías y herramientas correspondientes al Deep Learning.



-----

### Organización de carpetas: 

* scr/
    * data/: Contiene los archivos usados en el proyecto.
    
    * Images/: Contiene imágenes usadas en este archivo Markdown.

    * Model/: Contiene los modelos realizados en el proyecto.

    * notebooks/: son archivos jupyter notebook usados en todo el proceso.

------

### Fuente: [Kaggle](https://www.kaggle.com/datasets/gpiosenka/100-bird-species?select=birds.csv)

------

### En este proyecto de pueden apreciar conocimientos en:

* Python
* Deep Learning
* Keras
* TensorFlow
* ImagineProcessing
* Computer Vision
* Supervised Learning
* Classifier Models

------

## **Importación de los datos**

#### Importamos y leemos los datos que tenemos.

class id|	filepaths	|labels|	data set	|scientific name
----|-----|----|----|----
0.0	|train/ABBOTTS BABBLER/001.jpg|	ABBOTTS BABBLER	|train	|MALACOCINCLA ABBOTTI
0.0	|train/ABBOTTS BABBLER/007.jpg| ABBOTTS BABBLER	|train	|MALACOCINCLA ABBOTTI
0.0 |train/ABBOTTS BABBLER/008.jpg|	ABBOTTS BABBLER	|train	|MALACOCINCLA ABBOTTI
0.0 |train/ABBOTTS BABBLER/009.jpg|	ABBOTTS BABBLER	|train  |MALACOCINCLA ABBOTTI
0.0	|train/ABBOTTS BABBLER/002.jpg|	ABBOTTS BABBLER	|train	|MALACOCINCLA ABBOTTI
524.0|	valid/BLACK BREASTED PUFFBIRD/3.jpg|	BLACK BREASTED PUFFBIRD	|valid	|NOTHARCHUS PECTORALIS
524.0|	valid/BLACK BREASTED PUFFBIRD/4.jpg|    BLACK BREASTED PUFFBIRD	|valid	|NOTHARCHUS PECTORALIS
524.0|	valid/BLACK BREASTED PUFFBIRD/1.jpg|    BLACK BREASTED PUFFBIRD	|valid	|NOTHARCHUS PECTORALIS
524.0|	valid/BLACK BREASTED PUFFBIRD/2.jpg|	BLACK BREASTED PUFFBIRD|	valid	|NOTHARCHUS PECTORALIS
524.0|	valid/BLACK BREASTED PUFFBIRD/5.jpg|	BLACK BREASTED PUFFBIRD|	valid	|NOTHARCHUS PECTORALIS

columnas:
* class id: El ID numérico para identificar la clase.
* filepaths: Las rutas de cada archivo.
* labels: Las etiquetas en tipo texto de cada archivo.
* data set: El dataset al que pertenece(Train/Valid/Test).
* scientific name: El nombre científico de la especie de ave.

#### Visualizamos una muestra de nuestros datos

![IMAGEN](src/Images/Imagen1.PNG)

#### Dividimos los datos entre train y test

```py
train, test= train_test_split(data, test_size = 0.2, random_state=2)
train, val= train_test_split(train, test_size = 0.2, random_state=2)

```

#### Generamos nuevos datos artificiales a partir de los que ya tenemos:

![IMAGEN](src/Images/Imagen2.PNG)

#### Se modifica ligeramente la imagen original para generar varias imágenes artificiales, así nuetro modelo tendra más muestras para ser entrenado y apdrender mejor ya que la el mismo ave se ve de diferentes formas(Nuestro modelo aprenderá a identificar un ave miranto a la derecha o izquierda, de arriba a abajo o de abajo a arriba, si lo vemos desde abajo, del revés, etc.)

#### Ahora aplicamos este cambio a todas nuestras imágenes de todos nuestros datasets (train/valid/test).

## Creación del modelo

#### Red Convolucional
Tipo de capa|número de neuronas|Rango del Filtro|Función de activación|Número de filtros
-----|-----|----|---|------
Convolucional|49.152|3x3|Indefinido|64
Pooling||2x2||
Convolucional|Indefinido|3x3|Relu|128
Pooling||2x2||
## Elegimos la función sigmoide ya que queremos que nos devuelva un array de probabilidades.
#### Red Neuronal
Capa| Número de neuronas| Función de activación
------|-----|------
Flatten
1|128|Relu
2|1|Función sigmoide
#### Compilación
Optimizador| Función de coste| Métrica
---|---|---
Adam|Binary Crossentropy| Accuracy

## Evaluación del modelo
métrica| valor
----|----
Accuracy| 0.9980751872062683

#### Vemos que nuestro modelo tiene una precisión bastante alta, casi del 100%.

## Guardamos el modelo.
