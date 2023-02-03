# Word Count MapReduce Example on Google Dataproc

## Prerequisites
- A Google Cloud Platform account
- The Dataproc, Cloud Storage, and Compute Engine APIs enabled

## Step 1: Create a new Dataproc cluster
1. Go to the [Google Cloud Console](https://console.cloud.google.com/)
2. Select your project and click on the hamburger menu on the top left corner.
3. Select Dataproc and click on "Create Cluster".
4. Choose a name for your cluster, select the number of worker nodes (at least 2), and select a region for your cluster.
5. Click on "Create" to create the cluster.

## Step 2: Download input file from Github
1. SSH into the master node of your cluster
2. Download the input file from Github using wget: `wget https://raw.githubusercontent.com/tofighi/BigData/main/datasets/mapreduce/input.txt`
3. Put the input file in the / directory of HDFS: `hadoop fs -put input.txt /`

<pre>
<Contents of input.txt>
Hadoop is a big data framework
Hadoop can store vast data
Hadoop processes big data
Hadoop can analyze vast data 
Hadoop is easy
</pre>

## Step 3: Run the MapReduce job
1. Run the following command to execute the MapReduce job: `hadoop jar /usr/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar wordcount /input.txt /output`


## Step 4: View the results
1. Run the following command to copy the output files from the Hadoop file system to your local machine: `hadoop fs -get /output .`
2. The output files will be in the output directory on your local machine, and you can view the results by opening the part-r-00000 file in a text editor.

> On the successful completion of a job, the MapReduce runtime creates a _SUCCESS file in the output directory. This may be useful for applications that need to see if a result set is complete just by inspecting HDFS. (MAPREDUCE-947)

The output files are by default named part-x-yyyyy where:

* x is either 'm' or 'r', depending on whether the job was a map only job, or reduce
* yyyyy is the mapper or reducer task number (zero based)
So a job which has 32 reducers will have files named part-r-00000 to part-r-00031, one for each reducer task.

<pre>
View the contents of out directory: <b>hadoop fs -ls /out</b>
/out/_SUCCESS
/out/part-r-00000
/out/part-r-00001
/out/part-r-00002
</pre>

## Step 4: Merge and view the final results
1. Run the following command to merge the results (make sure you have enough space if the file is big): `hadoop fs -getmerge /output ~/result.txt`
2. The merged results is available in content of the `~/result.txt`. You can take a look at it by running `cat ~/result.txt`

<pre>
<b>result.txt</b>
data	  4
easy	  1
framework 1
store	  1
vast	  2
analyze	  1
big	  2
can	  2
Hadoop	  5
a	  1
is	  2
processes 1
</pre>


## How MapReduce works on a cluster with 1 master and 2 workers
- The input file is split into chunks and distributed among the worker nodes.
- Each worker node runs the map function on its chunk of the input, and generates a set of intermediate key-value pairs.
- The worker nodes then send their intermediate key-value pairs to the master node.
- The master node combines the intermediate key-value pairs from the worker nodes and runs the reduce function on them to produce the final output.
