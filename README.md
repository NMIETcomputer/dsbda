# dsbda
Practical 11 - WordCount using Hadoop MapReduce
*Objective*
To implement a simple WordCount application that counts the number of occurrences of each word in a given input set using the Hadoop MapReduce framework on local-standalone setup.
Prerequisites

Ubuntu OS
Java JDK installed
Hadoop installed and configured


Steps to Execute
Step 1: Start Hadoop
> start-dfs.sh
> jps

Verify that NameNode, DataNode and SecondaryNameNode are running.


Step 2: Create Input File
> mkdir -p ~/wordcount/input
> nano ~/wordcount/input/input.txt

Add some sample text, save with Ctrl+X → Y → Enter


Step 3: Upload File to HDFS
> hdfs dfs -mkdir -p /user/hadoop/wordcount/input
> hdfs dfs -put ~/wordcount/input/input.txt /user/hadoop/wordcount/input/
> hdfs dfs -ls /user/hadoop/wordcount/input/

Step 4: Create Java File
> mkdir -p ~/wordcount/java
> cd ~/wordcount/java
> nano WordCount.java

Paste the WordCount.java code and save.


Step 5: Compile and Create JAR
> javac -classpath $(hadoop classpath) -d . WordCount.java
> jar cf wordcount.jar WordCount*.class

Step 6: Run the Hadoop Job
> hadoop jar wordcount.jar WordCount /user/hadoop/wordcount/input /user/hadoop/wordcount/output

Step 7: View Output
> hdfs dfs -cat /user/hadoop/wordcount/output/part-r-00000

Expected Output
Hadoop      2
Hello       3
MapReduce   2
World       1
great       1
is          2
powerful    1
