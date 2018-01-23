https://www.cloudera.com/documentation/enterprise/5-7-x/topics/spark_avro.html

Writing Compressed Data Files
To set the compression type used on write, configure the spark.sql.avro.compression.codec property:
sqlContext.setConf("spark.sql.avro.compression.codec","codec") 
The supported codec values are *uncompressed, snappy, and deflate*. Specify the level to use with deflate compression in spark.sql.avro.deflate.level. For an example, see Writing Deflate Compressed Records.
