# Spark-Intro
## Contenido.
[Introducción.](##Introducción.)
## Introducción.
Apache Spark es un framework de trabajo para el desarrollo de grandes datos o big data y se preocupa de la velocidad y continuidad del procesamiento de datos.

* Apache Spark se enfoca en procesamiento de datos desde la memoria ram.
* Posee naturalmente un modulo para ML, streaming y grafos.
* No depende de un sistema de archivos.

Apache Spark soporta multiples lenguajes como son:

* Java
* Scala (Spark corre nativamente aquí)
* Python
* R

## Componentes de Spark.
RDD es uno de los pilares base de Apache Spark, los Resilient Distributed Datasets (RDD), se tratan de datasets tolerantes a fallos, capaces de operar en paralelo.

Características de los RDD:

* Principal abstracción de datos: Es la unidad básica, existen desde su inicio hasta su versión 3.0.
* Distribución: Los RDD se dritribuyen y particionan a lo largo del clúster.
* Creación simple: Al no poseer estructura formalmente, adoptan las más intuitiva.
* Inmutabilidad: Posterior a su creación no se pueden modificar
* Ejecución perezosa: A menos que se realice una acción.

Los RDD soportan tranformaciones y acciones a continuación se muestran algunas de ellas.

| Transformaciones | Acciones  |
|---               | ---       |
| orderBy()        | show()    |
| groupBy()        | take()    |
| filter()         | count()   |
| select()         | collect() |
| join()           | save()    |
