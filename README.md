# Big-Data-Using-Hadoop-and-Spark

# Lab 1: Setting Up VirtualBox & Cloudera, Running Linux Commands

## Objective  
This lab focuses on setting up a virtual environment using **VirtualBox and Cloudera** and executing basic **Linux commands**.  

## Technologies Used  
- Oracle VirtualBox  
- Cloudera VM  
- Linux (Command Line Interface - CLI)  

## Steps & Commands  

### 1. Setting Up VirtualBox & Cloudera  
- Installed **Oracle VirtualBox** and imported the Cloudera virtual machine.  
- Verified Cloudera installation by checking system boot.  

### 2. Running Basic Linux Commands  
Some of the key commands practiced:  

| **Command** | **Description** |  
|------------|---------------|  
| `ls` | Lists files and directories |  
| `ls -la` | Lists all files (including hidden ones) with permissions |  
| `pwd` | Displays current directory path |  
| `mkdir <dir>` | Creates a new directory |  
| `cd <dir>` | Navigates into a directory |  
| `touch testing` | Creates an empty file named "testing" |  
| `cat testing` | Displays the contents of "testing" |  
| `vi testing1` | Edits a file using Vi editor |  
| `df -h` | Displays disk space usage |  
| `ps aux` | Lists all running processes |  
| `cp <file> <destination>` | Copies a file |  
| `mv <file> <destination>` | Moves a file |  
| `rm <file>` | Deletes a file |  
| `env` | Displays environment variables |  
| `top` | Shows system task manager |  
| `free -m` | Displays memory usage |  
| `uptime` | Shows system uptime |  

## Expected Output  
- Successful installation of **VirtualBox & Cloudera**.  
- Execution of basic **Linux commands** with correct output.  

## Resource 
- LAB1.pdf file https://github.com/Rafiqbal/Big-Data-Using-Hadoop-and-Spark/blob/main/LAB1.pdf

# Lab 2: WordCount Program in Hadoop using Cloudera

## Objective  
This lab focuses on **understanding Hadoop's MapReduce framework** by running a **WordCount** program on Cloudera. The goal is to learn how data is processed in a **distributed computing environment** using Hadoop.

## Technologies Used  
- **Hadoop (MapReduce)**
- **HDFS (Hadoop Distributed File System)**
- **Cloudera VM**
- **Linux Command Line (Terminal)**

## Steps & Commands  

### 1. Creating a Sample Text File  
- A text file was created locally with sample content.

```bash
echo "Hadoop is powerful. Hadoop is fast." > sample.txt
```
- verify the content using cat sample.txt

### 2. Creating a Sample Text File 
- Create a directory in HDFS to store the input file:

```bash
hdfs dfs -mkdir /wordcount_input
```
- Upload sample.txt into HDFS:
```bash
hdfs dfs -put sample.txt /wordcount_input/
```
- Verify that the file has been uploaded:
```bash
hdfs dfs -ls /wordcount_input
```
### 3. Running the WordCount MapReduce Job
- Execute the Hadoop WordCount program:

```bash
hadoop jar /usr/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar wordcount /wordcount_input /wordcount_output
```
- This command runs the MapReduce job, which
   - Splits the text file into chunks.
   - Maps words to their frequencies.
   - Reduces the output to show word counts.
 
### 4. Viewing the Output
- Check the list of output files generated:

```bash
hdfs dfs -ls /wordcount_output
```
- Display the WordCount result:
```bash
hdfs dfs -cat /wordcount_output/part-r-00000
```
### Expected Output
- Example output from the WordCount program:
```bash
Hadoop    2
is        2
powerful. 1
fast.     1
```
### Resources 
LAB2.pdf file = https://github.com/Rafiqbal/Big-Data-Using-Hadoop-and-Spark/blob/main/LAB2.pdf

# Lab 3: HBase Table Creation

## Objective  
This lab focuses on **creating and managing an HBase table** in a Hadoop environment. The goal is to learn how to:  
- **Create an HBase table**  
- **Insert, update, delete, and retrieve records**  
- **Work with column families and schema design in HBase**  

## Technologies Used  
- **HBase (NoSQL Database)**  
- **Hadoop Distributed File System (HDFS)**  
- **Cloudera VM**  
- **Linux Command Line (Terminal)**  

## Steps & Commands  

### 1. Starting HBase  
- Open a terminal and start the HBase shell:  

  ```bash
  hbase shell
  ```

- Check if HBase is running by listing active tables:
  ```bash
  list
  ```

### 2. Creating an HBase Table
- Create a table named "student_info" with column families: personal, name, age, and gender:
  ```bash
  create 'student_info', 'personal', 'name', 'age', 'gender'
  ```
- Verify the table creation:
  ```bash
  list
  ```
### 3. Inserting Data into the Table
- nsert student records into the student_info table:
  ```bash
  put 'student_info', '1', 'name:first', 'John'
  put 'student_info', '1', 'name:last', 'Doe'
  put 'student_info', '1', 'age', '22'
  put 'student_info', '1', 'gender', 'Male'
  ```
- Verify the table creation:
```bash
put 'student_info', '2', 'name:first', 'Alice'
put 'student_info', '2', 'name:last', 'Smith'
put 'student_info', '2', 'age', '25'
put 'student_info', '2', 'gender', 'Female'
```
### 4. Retrieving Data
- Display all records from the table: 
  ```bash
  scan 'student_info'
  ```
- Verify the table creation:
```bash
get 'student_info', '1'
```

### 5. Updating Records
- Update the age of the student
```bash
put 'student_info', '1', 'age', '23'

```

### 6. Deleting Data
- Delete a specific column (e.g., first name of student 1)
  ```bash
  delete 'student_info', '1', 'name:first'
  ```
- Delete an entire row:
```bash
deleteall 'student_info', '1'
```
### 7. Dropping the Table (Additional)
- Disable the table before deleting: 
  ```bash
  disable 'student_info'
  ```
- drop 'student_info'
```bash
drop 'student_info'
```
- Verify that the table has been deleted:
```bash
list
```

### Resources
- LAB3.pdf file - https://github.com/Rafiqbal/Big-Data-Using-Hadoop-and-
Spark/blob/main/LAB3.pdf

# Lab 4: Apache Spark & HDFS File System  

## Objective  
This lab focuses on **using Apache Spark with HDFS** to process large datasets efficiently. The goal is to learn how to:  
- **Upload data to HDFS**  
- **Run a Hadoop MapReduce job**  
- **Execute Spark commands and store output**  

## Technologies Used  
- **Apache Spark**  
- **Hadoop MapReduce**  
- **HDFS (Hadoop Distributed File System)**  
- **Cloudera VM**  
- **Linux Command Line (Terminal)**  

## Steps & Commands  

### 1. Uploading Data to HDFS  
- Create an HDFS directory named `Sparkdata`:  
  ```bash
  hdfs dfs -mkdir /Sparkdata
  ```
- Verify the directory creation:
```bash
hdfs dfs -ls /
```
- Upload hivedata.txt into the HDFS directory:
```bash
dfs dfs -put hivedata.txt /Sparkdata/
```
- Check the uploaded file in HDFS:
```bash
hdfs dfs -ls /Sparkdata
```
### 2. Running Hadoop MapReduce Job
- Execute a Hadoop MapReduce job and store output in my_spark_output1:
```bash
hadoop jar /usr/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar wordcount /Sparkdata/hivedata.txt /wordcount_output
```
- Verify the output directory:
``` bash
hdfs dfs -ls /wordcount_output
```
- View the MapReduce job result:
```bash
hdfs dfs -cat /wordcount_output/part-r-00000
```
### 3. Running Apache Spark
- Start the Spark shell:
```bash
spark-shell
```
- Load data into Spark and store the output in my_spark_output2:
```scala
val data = sc.textFile("hdfs:///Sparkdata/hivedata.txt")
val wordCounts = data.flatMap(line => line.split(" ")).map(word => (word, 1)).reduceByKey(_ + _)
wordCounts.saveAsTextFile("hdfs:///spark_output")
```
- Verify the Spark output directory:
```bash
hdfs dfs -ls /spark_output
```
- View the output of the Spark job:
```bash
hdfs dfs -cat /spark_output/part-00000
```
Resources 
- LAB4.pdf - 


