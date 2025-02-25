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
LAB2.pdf file = 
