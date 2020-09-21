# Técnicas de Machine Learning
Repositorio que contiene ejercicios de algoritmos de machine learning y definiciones sobre las diferentes técnicas.

# K Nearest Neighbors
Los K Vecinos Ceranos esta es una técnica supervisada, se toman datos clasificados representados en un vector de características. Por ejemplo tenemos puntos de colores en un espacio, las dimensiones de ese espacio serían el número de características y los colores serían las categorias. Se miden las distancias entre los nuevos datos y los datos de los K cercanos que ya hemos clasificado.

## Posibles usos
* Clasificaciones basadas en sus características númericas.
* Ejecución de una regresión de valores númericos basados en caracteristicas del dato.
* Ej: Predecir si un esposo le gustaría un regalo de navidad basado en el precio, tamaño, puntaje en Amazon, entre otros.
* Ej: Recor crediticio, clasificación de riesgo bajo o alto, o en una escala revisando características de ingresos, valor de activos, entre otros.
* Ej: Clasificar riesgo de epilepsia basado en análisis de señales electroencefalográficas.

## ¿Cómo funciona?
Se inicia con N puntos de datos pre-clasificados, por lo que hablamos de una técnica supervisada. Cada dato que tiene características M que es representado por un vector con M características. Cada entrada representa una característica.

Por ejemplo, la primer entrada podría ser el número de palabras en un correo, la segunda el número de signos de exclamación, la tercera cantidad de errores ortográficos, entre otros. Y cada vector es clasificado como spam o no spam. El número de clases no necesita ser dos, pueden ser más.

Cuando tenemos un nuevo punto, simplemente vericamos en los datos originales la cercanía a los nuevos datos, la que nos indicará como clasificarlo.

Debemos escoger un K, el cual indicará cuantos puntos cercanos queremos que detecte para cada punto nuevo. Si tenemos K=2 tendremos comparación con los dos más cercanos. Si se incrementa K, podremos comparar contra más.

## Escogiendo un K
Tomar en cuenta: con un K pequeño podrías obtener un bajo bias pero una alta varianza. Un K grande es a la inversa.

## Algoritmo
* Paso 0: Primero se escalan todas las características a tamaños comparables. Todas las características deben de escalarse.
* Paso 1: Tomamos nuestro nuevo punto, hasta ahora sin clasificar puntos de datos y medimos la distancia entre este y todos los demás puntos. Buscamos los puntos K con las menores distancias. De esos K puntos de la clasificación con la mayor cantidad de apariciones se determina la clasificación del nuevo punto.
* No existe un aprendizaje real al finalizar el KNN. Un algoritmo el cual su modelo es generalizado solo con datos nuevos que son agregados es denominado algoritmo perezoso.

## Algunos problemas al utilizar KNN
* No existe un proceso de aprendizaje.
* La clasificación de información es un poco lenta.
* Se debe medir el nuevo punto contra todos los ya clasificados (lento).
* Datos sesgados se produce cuando hay más puntos de una clase que de las demás.
.
## Regresión
Aunque KNN es utilizado para clasificación, puede también ser facilmente utilizado como una regresión.

Ejemplos:

* Utilizando funciones gausianas para las distancias.
* Encajando en un hiperplano los K puntos de datos, lo anterior es una regresion linear local.

## Video complementario
Este es un video interesante para complementar sobre como crear un KNN desde cero. [Video](https://www.youtube.com/watch?v=hzOCDgfsSSQ)

## Ejercicio de KNN para iris de flores
Vamos a entender un poco como trabaja KNN utilizando un ejemplo basado en scikit-learn, que es una librería que ya contiene un set de datos con IRIS de algunas flores.

El siguiente ejemplo lo abres y lo copias a tu cuenta personal de Google Drive.
[Ejemplo](https://colab.research.google.com/drive/10Lt0KakjCIirvRRu_4eAx1O3HjIRSXAz)


# K Means Clustering
Es una técnica no supervisada de aprendizaje. Contamos con muchos puntos individuales de datos, cada uno representado por vectores. Cada entrada en el vector representa una característica. La diferencia es que esta información no esta etiquetada o clasificada con anterioridad.

## Posibles usos
* Agrupaciones de información no etiquetada pero con características similares.
* Clasificar compradores mediante su historial de compras.
* Ubicación óptima de parqueos en una ciudad.
* Optimización de talla de cuello y largo de brazo de camisas.
* Agrupación de imágenes sin que esten pre-clasificadas.

## ¿Cómo Funciona?
Tenemos un conjunto de datos de N individuales, cada uno tiene asociado M- vectores dimensionales representando M características, por lo que x a la potencia de n para n= 1 a N. Cada entrada en el vector representa una cantidad númerica diferente.

Por ejemplo, cada vector podría representar un único hogar, el primer elemento en cada vector trae ingresos, el segundo número de carros, así sucesivamente con las M dimensiones, la M-esima podría ser número de laptops.

Un [video](https://youtu.be/5I3Ei69I40s) de como funciona el KCM.

## Algoritmo K Means
**Paso 0**: Escalar. Este es un paso típico para cada algoritmo sobre los datos que vamos a utilizar. Esto porque vamos a trabajar con medidas de distancias.

**Paso 1**: Seleccionar algunos centros. Se debe alimentar el algoritmo con centros para los K clusters. Podría ser seleccionando K de N vectores para iniciar, o solo generar K vectores aleatorios . Al menos debería tenerse el mismo tamaño de características como de sets de datos escalados; ya sea, en términos de media y desviación estandar o de mínimos y máximos. Estos centros serán determinados de toda la población.

**Paso 2**: Encontrar distancias de cada dato a los centros. Para cada punto de datos dentro del vector se debe medir la distancia desde el centroide hasta el punto para todos los K clusters. El tipo de medición que utilicemos depende del tipo problema que tengamos. Comúnmente se utiliza la fórmula de distancias eucledianas.

Dependiendo del problema se puede variar esta medición a una fórmula más apta para los datos que se tienen. Acá puede revisar otras dos opciones para medir centros.
Pueden revisar este [enlace](https://www.i2tutorials.com/top-machine-learning-interview-questions-and-answers/what-is-the-difference-between-euclidean-manhattan-and-hamming-distances/) para conocer diferentes fórmulas para cálcular centroides.

El paso 2 continua hasta que se miden las distancias de todos los datos hasta que se crean los dos clusters, basados en los centroides que se determinaron inicialmente.

**El paso 3**: Encontrar los K centroides. Ahora nos toca tomar los datos en los clusters y determinar un nuevo centroide. Uno para cada cluster que se creó con los nuevos centroides se puede volver al paso dos y volver a estimar las distancias de los puntos a cada centroide. Esto puede cambiar los tamaños de los clusters y mover datos de un cluster a otro. Esto porque los centroides han cambiado. Esto se repite hasta que el algoritmo converje.

## Función de Error
Sumando todos las distancias cuadráticas al cluster cercano obtenemos un medida del total de distancias o una medida de error. El error se puede interpretar como la función de error del número de cluster K que tengamos. En el caso extremo de que sea K = N tendríamos un cluster por cada punto de datos y eso provocaria un error de 0.

![El Codo](/imagenes/errorfuntion.png)

Como se puede apreciar en la función va decreciendo conforme aumentan los K clusters. El descenso se controla al llegar K=3, puesto que 4, 5, 6 tienen un decenso más paulatino. Por lo que, podemos escoger 3 como el número idóneo para los clusters. No siempre será fácil.

## Ejemplo
Vamos a volver al ejemplo de los Iris pero ahora con este mismo algoritmo, recuerda hacer una copia en tu Drive del [ejemplo](https://colab.research.google.com/drive/1sJDA4nfNVEbMZNv2HY-DiA8lndtV1Hl2?usp=sharing)

Ejemplo [trivial](https://colab.research.google.com/drive/1vnGaLTHTuVpy0wstnnl0I4Gelqrybogm?usp=sharing)

Quieres profundizar más en este tema, revisa en este [enlace](https://developers.google.com/machine-learning/clustering). Se profundiza en el tipo de centroides y agrupaciones que se pueden hacer, como preparar los datos y como ejecutar un algoritmo más robusto.

# Naïve Bayes Classifier o Clasificador Bayeseano
Este algoritmo lo podemos denominar como de aprendizaje supervisado. Se tiene ejemplos de información que representa las diferentes clases que tenemos. Utilizando el teorema de Bayes nosotros calculamos la probabilidad de nuevos datos en cada clase.

## Posibles Usos
* Clasificación de datos usualmente texto y análisis de sentimientos.
* NLP para ayudar a una computadora a entender al humano.
* Detección de correos spam.
* Clasificar que parte de que una noticia es buena o mala.
* Predecir en que dirección unos tweets en twitter van a influenciar una elección o referendo.
* Determinar si tweets tristes son de un bot RUSO.

## Cómo funciona?
PSeudo código:
* Convertir el conjunto de datos a tabla de frecuencias.
* Crear una tabla de probabilidad calculando las correspondientes a diversos eventos.
* Utilizando Naïve Bayes se calcula la probabilidad posterior de cada clase.
* La clase con la probabilidad posterior más alta es el resultado de la predicción.

## Puntos fuertes del algoritmo
* Fácil y rápida forma de predecir clases para problemas binarios y multiclase.
* En casos donde se presume independecia de las variables, es una mejor opción a otros modelos de clasificación incluso con pocos datos de entrenamiento.

## Puntos débiles del algoritmo
* Son conocidos por ser pobres estimadores, no se deben tomar muy en serio las probabilidades que se obtienen.
* La presunción de independencia Naïve muy probablemente no refleje como son los datos en el mundo real.
* Cuando se encuentra una característica no observada en los datos de entrenamiento, esta tendrá una probabilidad de cero, volviendola inútil para hacer predicciones.

## Ejemplo
Para este caso vamos a clasificar texto, ya que en estos casos buscamos palabras clave, el Bayes se presta para este problema.
[Cuaderno](https://colab.research.google.com/drive/1UaIlB8hCbyVrtPvXc58_3VEG4xrNYRsN?usp=sharing)

**Reto basado en tu ejemplo, intenta crear un reconocedor de spam o correo basura novato**

## Clasificación de Imágenes
[Cuaderno](https://developers.google.com/machine-learning/practica/image-classification)


# Material complementario recomendado
[Guia de aprendizaje curso de google developer para Aprendizaje Automático](https://developers.google.com/machine-learning/crash-course)



