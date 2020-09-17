# Técnicas de Machine Learning
Repositorio que contiene ejercicios de algoritmos de machine learning y definiciones sobre las diferentes técnicas

# K Nearest Neighbours
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
