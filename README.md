# Spark-Intro
# Contenido.
[Introducción.](#Introducción.)
[Instalación.](#Instalación.)
# Introducción.
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

### Características de los RDD:

* Principal abstracción de datos: Es la unidad básica, existen desde su inicio hasta su versión 3.0.
* Distribución: Los RDD se dritribuyen y particionan a lo largo del clúster.
* Creación simple: Al no poseer estructura formalmente, adoptan las más intuitiva.
* Inmutabilidad: Posterior a su creación no se pueden modificar
* Ejecución perezosa: A menos que se realice una acción.

Los RDD soportan tranformaciones y acciones, a continuación se muestran algunas de ellas.

| Transformaciones | Acciones  |
|---               | ---       |
| orderBy()        | show()    |
| groupBy()        | take()    |
| filter()         | count()   |
| select()         | collect() |
| join()           | save()    |

Las transformaciones no se ejecutan hasta que se llama a una acción. Por ejemplo: ordenar el RDD (RDD.orderBy()) no se ejecutara hasta que se mande una acción en este caso RDD.orderBy().show().

### ¿Cuándo usar un RDD?

Cuando te interesa controlar el flujo de Spark.
Si eres usuario Python, convertir a RDD un conjunto permite mejor control de datos.
Estás conectándote a versiones antiguas de spark.

### Características de los DataFrame

* Formato: A diferencia de un RDD poseen columnas, lo cual les otorga tipos de datos.
* Optimización: Poseen una mejor implementación, lo cual los hace preferibles.
* Facilidad de creación: Se pueden crear desde una base de datos externa, archivo o RDD existente.

### ¿Cuándo usar DataFrames?

Si poseemos semánticas de datos complicadas.
Vamos a realizar tareas de alto nivel como filtros, mapeos, agregaciones, promedios o sumas.
Si vamos a usar sentencias SQL.

# Instalación.

En una máquina ubuntu recien instalada ejecutar los siguientes comandos.

Para agregar el repositorio que nos permita instalar la versión 8.\
sudo add-apt-repository ppa:openjdk-r/ppa \

Ejecutar los siguiente comandos para actualizar los repositorios.
sudo apt-get -y update \
sudo apt-get -y upgrade 
* Instalación de java 8. \
sudo apt-get -y install openjdk-8-jre 
* Instalación de python3.\
sudo apt-get -y install python3
* Instalación de scala\
sudo apt-get -y install scala 
* Instalación de pip3 para poder instalar módulos.
sudo apt-get -y install python3-pip
* Instalación del modulo que convierte de python a java.\
sudo pip3 install py4j 
* Descargamos spark con hadoop.\
wget  https://dlcdn.apache.org/spark/spark-3.2.1/spark-3.2.1-bin-hadoop3.2.tgz
* Descompimimos el archivo descargado.
tar -xvf  spark-3.2.1-bin-hadoop3.2.tgz
* Renombar la carpeta a spark\
mv spark-3.2.1-bin-hadoop3.2 spark\
rm spark-3.2.1-bin-hadoop3.2.tgz
* Descargamos el paquete de anaconda y lo descomprimimos\
wget https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh\
sh Anaconda3-2020.02-Linux-x86_64.sh -b
* Exportamos la ruta para poder usar el instalador de paquetes de anaconda\
export PATH=/home/almighty/anaconda3/bin:$PATH
* En el ambiente de anaconda instalamos py4j\
conda install py4j
* Se agregan variables de entorno.
nano .bashrc\
##Java path\
export JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64"\
export PATH=$JAVA_HOME/bin:$PATH\
##Spark\
export SPARK_HOME="/home/almighty/spark"\
export PATH=$SPARK_HOME:$PATH\
export PYTHONPATH=$SPARK_HOME/python:$PYTHONPATH\
export PYSPARK_PYTHON=python3\

* Guardamos el archivo
* Recargamos el archivo .bashrc\
source .bashrc

* Para ver los primeros 10 registos de un archivo\
head -n 10 data.csv

* Para ejecutar codigo de python con spark-submit\
../spark/bin/spark-submit ejemplo1.py states.csv

## Ejecución de Spark en Jupyter Notebook
* Se agregan variables de entorno.
nano .bashrc\
##Jupyter\
export PYSPARK_DRIVER_PYTHON="JUPYTER"\
export PYSPARK_DRIVER_PYTHON_opts="notebook"\
export PATH=/home/almighty/anaconda3/bin:$PATH\

* Guardamos el archivo
* Recargamos el archivo .bashrc\
source .bashrc
* Instalamos el core de jupyter\
sudo apt install jupyter-core
* Cargamos el notebook de jupyter estando en una ruta diferente al home, por ejemplo Documents\
jupyter notebook
