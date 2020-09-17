# Técnicas de Machine Learning
Repositorio que contiene ejercicios de algoritmos de machine learning y definiciones sobre las diferentes técnicas

# K Nearest Neighbors
Los K Vecinos Ceranos esta es una técnica supervisada, se toman datos clasificados representados en un vector de caracteristicas. Por ejemplo tenemos puntos de colores en un espacio, las dimensiones de ese espacio serían el número de caracteristicas y los colores serían las categorias. Se miden las distancias entre los nuevos datos y los datos de los K cercanos que ya hemos clasificado.

## Posibles usos
* Clasificaciones basadas en sus caracteristicas númericas
* Ejecución de una regresión de valores numericos basados en caracteristicas del dato
* Ej: Predecir si un esposo le gustaría un regalo de navidad basado en el precio,tamaño, puntaje en amazon, entre otros
* Ej: Recor crediticio, clasificación de riesgo bajo o alto, o en una escala revisando caracteristicas de ingresos, valor de activos, entre otros
* Ej: Clasificar riesgo epilepsia basado en analisis de señales electroencefalográficas

## Cómo funciona?
Se inicia con N puntos de datos preclasificados, por lo que hablamos de una técnica supervisada. Cada dato que tiene caracteristicas M es representado por un vector con M caracteristicas. Cada entrada representa una caracteristica.

Por ejemplo la primer entrada podría ser el número de palabras en un correo, la segunda el número de signos de exclamación, la tercera cantidad de errores ortográficos, entre otros. Y cada vector es clasificado como spam o no spam. El número de clases no necesita ser dos, pueden ser más.

Cuando tenemos un nuevo punto, simplemente vericamos los datos originales la cercanía a los nuevos datos, la que nos indicará como clasificarlo.

Debemos escoger un K, el cual indicará cuantos cercanos queremos que detecte para cada punto nuevo. Si tenemos K=2 tendremos comparación con los dos más cercanos. Si se incrementa K, podremos comparar contra más

## Escogiendo un K
Tomar en cuenta: K pequeño podrías obtener un bajo bias pero una alta varianza. Un K grande es a la inversa.

## Algoritmo
* Paso 0: Primero se escalan todas las caracteristicas a tamaños comparables. Todas las caracteristicas deben den de escalarse.
* Paso 1: Tomamos nuestro nuevo y hasta ahora sin clasificar punto de datos, medimos la distancia entre este y todos los demás puntos. Buscamos los puntos K con las menores distancias. De esos K puntos de la clasificación con la mayor cantidad de apariciones se determina la clasificación del nuevo punto.
* No existe un aprendizaje real al finalizar el KNN. Un algoritmo el cual su modelo is generalizado solo con datos nuevos que son agregados es denominado algoritmo peresoso.

## Algunos problemas al utilizar KNN
* No existe un proceso de aprendizaje
* La clasificación de informacióm es un poco lenta
* Se debe medir el nuevo punto contra todos los ya clasificados (lento)
* Datos sesgados se produce cuando hay más puntos de una clase de las demás

## Regresión
Aunque KNN es utilizado para clasificación, puede también ser facilmente utilizado como una regresión.

Ejemplos:

* Utilizando funciones gausianas para las distancias
* EncaEncajando en un hiperplano los K puntos de datos, lo anterior es una regresion linear local

## Video complementario
Un video interesante para complementar sobre como crear un KNN desde cero. [Video](https://www.youtube.com/watch?v=hzOCDgfsSSQ)

## Ejercicio de KNN para iris de flores
Vamos a entender un poco como trabaja KNN utilizando un ejemplo basado en scikit-learn, que es una libreria que ya contiene un set de datos con IRIS de algunas flores.

El siguiente ejemplo lo abres y lo copias a tu drive de tu cuenta personal.
[Ejemplo](https://colab.research.google.com/drive/10Lt0KakjCIirvRRu_4eAx1O3HjIRSXAz)


# K Means Clustering
Es una técnica no supervisada de aprendizaje. Contamos con muchos puntos individuales de datos, cada uno representado por vectores. Cada entrada en el vector representa una caracteristica. La diferencia es que esta información no esta etiquetada o clasificada con anterioridad.

## Posibles usos
* Agrupaciones de información no etiquetada pero con caracteristicas similares
* Clasificar compradores mediante su historial de compras
* Ubicación optima de parqueos en una ciudad
* Optimización de talla de cuello y largo de brazo de camisas
* Agrupación de imágenes sin que esten preclasificadas

## Cómo Funciona?
Tenemos un conjunto de datos de N individuales, cada uno tiene asociado M- vectores dimensionales representando M caracteristicas, por lo que x a la potencia de n para n= 1 a N. Cada entrada en el vector representa una cantidad númerica diferente.

Por ejemplo cada vector podría representar un único hogar, el primer elemento en cada vector trae ingresos, el segundo número de carros, asi sucesibamente con las M dimensiones, la M-esima podría ser número de laptops.

Un [video](https://youtu.be/5I3Ei69I40s) de como funciona el KCM.

## Algoritmo K Means
**Paso 0**: Escalar. Este es un paso típico para cada algoritmo sobre los datos que vamos a utilizar. Esto porque vamos a trabajar con medidas de distancias.

**Paso 1**: Seleccionar algunos centros. Se debe alimentar el algoritmo con centros para los K clusters. Podría ser seleccionando K de N vectores para iniciar, o solo generar K aleatorios vectores. Al menos debería tenerse el mismo tamaño de caracteristicas como de sets de datos escalados, ya sea en terminos de media y desviación estandar o de mínimos y máximos. Estos centros serán determinados de toda la población.

**Paso 2**: Encontrar distancias de cada dato a los centros. Para cada punto de datos dentro del vector se debe medir la distancia desde el centroide hasta el punto para todos los K clusters. El tipo de medición que utilicemos depende del tipo problema que tengamos. Comúnmente se utiliza la fórmula de distancias eucledianas.

Dependiendo del problema se puede variar esta medición a una fórmula más apta para los datos que se tienen. Acá puede revisar otras dos opciones para medir centros.
Pueden revisar este [enlace](https://www.i2tutorials.com/top-machine-learning-interview-questions-and-answers/what-is-the-difference-between-euclidean-manhattan-and-hamming-distances/) para conocer diferentes fórmulas para cálcular centroides.





