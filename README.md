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

## Interpretación de los resultados:

![image](https://github.com/LawrenceJavier/No-Estructurados/assets/74473715/8067313e-e6fe-4d72-80f8-48cddec8b955)


Los resultados obtenidos, son de esperar visto que en la red RNN ha sido entrenada con solo 5000 datos, los cuales tienen cierto sesgo. En este modelo hemos obtenido una precision total de 54%. 
Dando paso al words embedding desarrollado, con GloVe hemos obtenido una mejor precision del modelo de un 71%. El aumento en precisión del 54% al 71% al cambiar de una RNN a GloVe puede deberse a que los vectores GloVe capturan mejor las relaciones semánticas entre las palabras, lo que permite un mejor rendimiento en ciertas tareas de NLP donde estas relaciones son importantes.
Finalizando con el transfer Learning, el aumento en la precisión hasta un 78% al emplear BERT puede atribuirse a su capacidad para modelar relaciones semánticas y contextuales complejas en el lenguaje, aprovechando su pre-entrenamiento en corpus masivos. Al ajustar los parámetros de BERT a la tarea específica, el modelo se adapta mejor a los detalles del conjunto de datos objetivo, mejorando así su capacidad predictiva al capturar los matices del contexto y las relaciones entre las palabras con mayor precisión.


## Evolución de las pruebas

El desarrollo y las pruebas del código han pasado por varias etapas, explorando diferentes enfoques y técnicas para mejorar la calidad de las recomendaciones generadas. A continuación, se resumen las etapas clave:



### Prueba con RNN (Redes Neuronales Recurrentes):
En la primera etapa, el código incluía un modelo basado en RNN para generar recomendaciones. Este enfoque se basaba en el uso de secuencias de datos y el aprendizaje de patrones temporales en el comportamiento del usuario. Sin embargo, esta prueba inicial mostró limitaciones en términos de escalabilidad y rendimiento con conjuntos de datos grandes.


### Prueba con embeddings:
En la segunda etapa, se realizaron pruebas utilizando embeddings para representar los datos de entrada. Los embeddings son representaciones densas y de baja dimensionalidad que capturan características y relaciones semánticas entre los elementos. Esta prueba mostró una mejora en la escalabilidad y eficiencia en comparación con el enfoque anterior basado en RNN.


### Prueba con transfer learning:
En la etapa más reciente, se han realizado pruebas utilizando modelos de transferencia. La transferencia de aprendizaje implica reutilizar conocimientos y características aprendidos de un modelo previamente entrenado en un conjunto de datos diferente y aplicarlos a un nuevo conjunto de datos. Esta prueba demostró una mayor precisión y capacidad para capturar características relevantes en los datos.


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



Instale Python y las bibliotecas indicadas.

Clone el repositorio del código en su máquina local.




### Preparación de los datos:



Asegúrese de tener los datos de entrada en el formato adecuado y localizadas en las mismas posociones que se indican en el repositorio.

Realice algún preprocesamiento de los datos según sea necesario.



### Ejecución del código:



Abra el archivo principal, indicado en el inicio del repositorio, en su editor de texto o entorno de desarrollo preferido.

Configure los parámetros y opciones según sea necesario creando su respectivo entorno virtual.



### Limitaciones y mejoras futuras

Es importante tener en cuenta las limitaciones del código y considerar posibles mejoras futuras:

- Limitaciones
  - Sesgo de datos: los datos utilizados para entrenar la RNN pueden tener sesgos inherentes, lo que podría afectar su capacidad para generalizar correctamente.

  - Falta de información contextual: las RNN pueden tener dificultades para capturar y recordar información de contexto a largo plazo, lo que afecta su capacidad para comprender mejor el significado y el contexto detrás de las palabras en un texto.

  - Dependencia de la calidad de los datos: la precisión de la RNN depende de la calidad y representación de los datos utilizados para entrenar.
  - Vocabulario: Los embeddings solo representan palabras o tokens presentes en el conjunto de datos de entrenamiento. Palabras poco comunes o nuevas que no estén presentes en el conjunto de datos pueden no tener una representación adecuada en el embedding y afectar el rendimiento del modelo.
  - Transfer Learning con BERT requiere de una gran cantidad de datos de entrenamiento para aprovechar al máximo su capacidad de aprendizaje.
  - BERT es un modelo de lenguaje masivo con millones de parámetros, lo que lleva a un tiempo de entrenamiento considerablemente largo.
    
- Mejoras
    - Utilizar arquitecturas más avanzadas como LSTM o GRU, que abordan el problema del desvanecimiento/explotación del gradiente y pueden capturar mejor la información contextual a largo plazo.
  - Aumentar el tamaño y diversidad del conjunto de datos para minimizar el sesgo y mejorar la capacidad de generalización.
  - Seguir experimentando con diferentes hiperparámetros
  - En lugar de adaptar BERT directamente a dominios específicos, se pueden realizar ajustes adicionales en el modelo pre-entrenado mediante un proceso de fine-tuning específico para esos dominios.
  - Utilizar modelos más pequeños como DistilBERT, que han sido diseñados para tener una estructura más compacta y un tiempo de entrenamiento más rápido sin perder demasiado rendimiento.
