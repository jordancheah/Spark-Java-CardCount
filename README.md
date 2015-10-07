# Spark-Java-CardCount

This Java program illustrates how to use Spark to process data in HDFS and write the results back to HDFS.

## Data File
The data file is a text file, with each line = <cardnum> <tab> <cardsuit>
```
6    Diamond
3   Diamond
4   Club
4   Heart
3   Club
5   Spade
1   Diamond
...
```

## How To Compile
```
mvn eclipse:eclipse
mvn package
```

## How To Run

Start the spark-master daemon by running:
```
$ sudo service spark-master start
```

Start the spark-worker daemon by running:
```
$ sudo service spark-worker start
```

Run the Spark job:
```
$ spark-submit --class solution.CardCount target/sparkhelloworld-1.0-SNAPSHOT.jar playing_cards_simple output_spark
```

## Output


```
$ hadoop fs -ls output_spark
Found 2 items
-rw-r--r--   1 vmuser supergroup          0 2015-08-04 17:32 output_spark/_SUCCESS
-rw-r--r--   1 vmuser supergroup         61 2015-08-04 17:32 output_spark/part-00000

$ hadoop fs -cat output_spark/part-00000
(Heart,666648)
(Diamond,664345)
(Spade,665475)
(Club,664773)
```
