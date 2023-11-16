# 2.- Spark DataFrame Basics


1. [Introduction to Spark DataFrames](#schema1)
2. [Spark DataFrames Basics](#schema2)

<hr>

<a name="schema1"></a>

## 1. Introduction to Spark DataFrames

![df](./img/df_1.png)

![df](./img/df_2.png)

![df](./img/df_3.png)

![df](./img/df_4.png)

![df](./img/df_5.png)



<hr>

<a name="schema2"></a>

## 2. Spark DataFrames Basics
- Crear la sesion
```
from pyspark.sql import SparkSession
spark = SparkSession.builder.appName('Basics').getOrCreate()
spark
```
![df](./img/df_6.png)

- Mostrar el DataFrame
```
df = spark.read.json('./data/people.json')
df.show()
```
![df](./img/df_7.png)

- Imprimir el esquema del dataframe
``` 
df.printSchema()
```    
![df](./img/df_8.png)


- Mostrar las columnas del DataFrame
```
df.columns
```
![df](./img/df_9.png)

- Mostrar el resumen estadístico

```
df.describe().show()
``` 
```   

+-------+------------------+-------+
|summary|               age|   name|
+-------+------------------+-------+
|  count|                 2|      3|
|   mean|              24.5|   null|
| stddev|7.7781745930520225|   null|
|    min|                19|   Andy|
|    max|                30|Michael|
+-------+------------------+-------+

```

- Crear nuestro propio esqueme y cambiar los tipos de datos

```
from pyspark.sql.types import StructField, StringType, IntegerType,StructType
data_schema = [StructField('age',IntegerType(),True),
              StructField('name',StringType(),True)]
              
final_struc = StructType(fields = data_schema)
df.printSchema()
```
```
root
 |-- age: integer (nullable = true)
 |-- name: string (nullable = true)
```
