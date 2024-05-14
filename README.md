# No-Estructurados

Autores:
- Lawrence Javier Minguillán Van Kapel
- Alberto Sánchez Bonastre
  
Los datos de entrenamiento son:
- data.xlsx

El Main donde se encuentra el desarrollo del proyecto es:
- ADNE_Final_Texto.ipynb

Los modelos finales son:
- RNN encontrado con el nombre: model_rnn_40 .keras
- Word embeddings, se puede descargar el archivo usado en el link: https://huggingface.co/stanfordnlp/glove/resolve/main/glove.42B.300d.zip
- Transfer learning, se puede descargar el archivo usado en el link: https://drive.google.com/file/d/1uxqtDa0EVjqnBD67csC9AVScs3i9g92z/view?usp=sharing





# README

Este documento de README tiene como objetivo proporcionar una descripción clara y concisa de la evolución de las pruebas realizadas en el código. A continuación, se describe cómo se han pasado de un RNN a embeddings y luego a un modelo de transferencia.


## Evolución de las pruebas

El desarrollo y las pruebas del código han pasado por varias etapas, explorando diferentes enfoques y técnicas para mejorar la calidad de las recomendaciones generadas. A continuación, se resumen las etapas clave:



### Prueba con RNN (Redes Neuronales Recurrentes):
En la primera etapa, el código incluía un modelo basado en RNN para generar recomendaciones. Este enfoque se basaba en el uso de secuencias de datos y el aprendizaje de patrones temporales en el comportamiento del usuario. Sin embargo, esta prueba inicial mostró limitaciones en términos de escalabilidad y rendimiento con conjuntos de datos grandes.


Ejemplo de código para entrenar un modelo de RNN:

``` python
from keras.models import Sequential
from keras.layers import LSTM, Dense

model = Sequential()
model.add(LSTM(100, input_shape=(X.shape[1], X.shape[2])))
model.add(Dense(y.shape[1], activation='softmax'))
model.compile(loss='categorical_crossentropy', optimizer='adam')
model.fit(X_train, y_train, epochs=10, batch_size=32)
```

### Prueba con embeddings:
En la segunda etapa, se realizaron pruebas utilizando embeddings para representar los datos de entrada. Los embeddings son representaciones densas y de baja dimensionalidad que capturan características y relaciones semánticas entre los elementos. Esta prueba mostró una mejora en la escalabilidad y eficiencia en comparación con el enfoque anterior basado en RNN.


Ejemplo de código para entrenar un modelo utilizando embeddings:

``` python
from keras.models import Sequential
from keras.layers import Embedding, Flatten

model = Sequential()
model.add(Embedding(input_dim=num_items, output_dim=64, input_length=sequence_length))
model.add(Flatten())
model.add(Dense(num_items, activation='softmax'))
model.compile(loss='sparse_categorical_crossentropy', optimizer='adam')
model.fit(X_train, y_train, epochs=10, batch_size=32)
```


### Prueba con transfer learning:
En la etapa más reciente, se han realizado pruebas utilizando modelos de transferencia. La transferencia de aprendizaje implica reutilizar conocimientos y características aprendidos de un modelo previamente entrenado en un conjunto de datos diferente y aplicarlos a un nuevo conjunto de datos. Esta prueba demostró una mayor precisión y capacidad para capturar características relevantes en los datos.


Ejemplo de código para utilizar un modelo de transferencia:

``` python
from keras.applications import VGG16
from keras.models import Model
from keras.layers import GlobalAveragePooling2D, Dense

base_model = VGG16(weights='imagenet', include_top=False, input_shape=(224, 224, 3))
x = base_model.output
x = GlobalAveragePooling2D()(x)
x = Dense(1024, activation='relu')(x)
predictions = Dense(num_classes, activation='softmax')(x)
model = Model(inputs=base_model.input, outputs=predictions)
model.compile(optimizer='adam', loss='categorical_crossentropy')
model.fit(X_train, y_train, epochs=10, batch_size=32)
```


## Requisitos y dependencias

El código se implementa en un lenguaje de programación específico y puede requerir ciertas bibliotecas o dependencias. Asegúrese de cumplir con los siguientes requisitos antes de ejecutar el código:



### Lenguaje de programación: 
- Python

### Bibliotecas y dependencias:

- keras

- numpy

- scipy




## Instrucciones de uso

A continuación se proporcionan instrucciones sobre cómo utilizar el código para generar recomendaciones personalizadas:




### Configuración del entorno:



Instale Python y las bibliotecas necesarias.

Clone el repositorio del código en su máquina local.




### Preparación de los datos:



Asegúrese de tener los datos de entrada en el formato adecuado.

Realice algún preprocesamiento de los datos según sea necesario.




### Selección del modelo:



Determine qué enfoque de modelo desea utilizar: RNN, embeddings o transferencia de aprendizaje.




### Ejecución del código:



Abra el archivo principal del código en su editor de texto o entorno de desarrollo preferido.

Configure los parámetros y opciones según sea necesario.

Ejecute el código y espere a que se generen las recomendaciones.




### Interpretación de los resultados:



Analice las recomendaciones generadas y evalúe su calidad y relevancia.

Realice ajustes en los parámetros o en el modelo según sea necesario.




### Limitaciones y mejoras futuras

Es importante tener en cuenta las limitaciones del código y considerar posibles mejoras futuras:



El código actual puede requerir una mayor optimización para conjuntos de datos extremadamente grandes.

Las recomendaciones pueden verse afectadas por la calidad y la cantidad de los datos de entrada.

Se pueden realizar mejoras adicionales en los modelos utilizados para aumentar la precisión y la relevancia de las recomendaciones.
