# Data Engineer Programming Test

Suponga que se presenta la necesidad de ingestar archivos planos de distintos aplicativos origen, realizarles pequeñas transformaciones (mayoritariamente de formato) y guardarlo en formato Apache Parquet.

Dada esta necesidad se pide generar una solución que contemple las siguientes características:

1.- Debe tener la flexibilidad suficiente para procesar archivos de texto ancho fijo y delimitados.

2.- Como input debe recibir los siguientes parámetros:

	a.- El path de origen del archivo a ser ingestado;
	b.- El path destino donde se escribirá ese archivo;
	c.- La metadata necesaria para procesar el archivo crudo (header y anchos de columnas);
	d.- La cantidad de archivos en los que se va a escribir la salida;
	e.- Permitir el agregado de columnas al data frame con valores predefinidos.
	
Se solicita que lo desarrollado sea capaz de ser ejecutado en cualquier computadora de forma local, de ser posible, con la menor cantidad de dependencias.

### Sets de prueba
Se proveen dos archivos para realizar *pruebas*.

nyse_2012.csv, delimitado por comas, con cabecera. El parquet de salida debe estar particionado por una columna extra, llamada partition_date y cuyo valor viene dado por parámetro.

nyse_2012_ts.txt, de ancho fijo, sin cabecera y con las siguientes longitudes de columnas:

|columna|tipo de dato|longitud|
| ------------- | ------------- | ------------- |
|stock|string|6|
|transaction_date|timestamp|24|
|open_price|float|7|
|close_price|float|7|
|max_price|float|7|
|min_price|float|7|
|variation|float|7|

El parquet de salida debe estar particionado por la columna stock.


Preguntas para charlar en la devolución:
1. Qué problemas se generaban por los Skewed Joins, hasta Spark 3.0.0?
2. Cuándo tiene sentido hacer un broadcast de un dataframe?
3. Para qué requerimiento implementarías una cola de mensajes en una solución orientada a datos?
4. Si decidiste no hacerlo con Spark, podrías implementar la misma solución en Spark? Qué partes del código crees que deberian cambiar de tu solución por código de Spark?
5. Cuál crees que es la mejor manera para recibir los parámetros?

### Criterios de evaluación
Tener en cuenta:
* Calidad del código desarrollado.
* Mantenibilidad.
* Claridad y facilidad de entendimiento.
* Performance y escalabilidad.
* Pragmatismo.

(Los criterios de evaluación son guías para brindar mayor claridad al candidato en términos de cómo su trabajo será calificado, esta evaluación se centrará en dichos conceptos pero no necesariamente se limitará a los mismos)
