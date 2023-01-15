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
1. SSH into the master node of your cluster: `gcloud compute ssh <cluster-name>-m`.
2. Download the input file from Github using wget: `wget https://raw.githubusercontent.com/tofighi/BigData/main/datasets/mapreduce/input.txt`
3. Put the input file in the / directory of HDFS: `hadoop fs -put input.txt /`

## Step 3: Run the MapReduce job
1. Create a new directory in the Hadoop file system to store the output of the MapReduce job: `hadoop fs -mkdir -p output`
2. Run the following command to execute the MapReduce job: `hadoop jar /usr/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar wordcount /input.txt output`


## Step 4: View the results
1. Run the following command to copy the output files from the Hadoop file system to your local machine: `hadoop fs -copyToLocal output output`
2. The output files will be in the output directory on your local machine, and you can view the results by opening the part-r-00000 file in a text editor.

## How MapReduce works on a cluster with 1 master and 2 workers
- The input file is split into chunks and distributed among the worker nodes.
- Each worker node runs the map function on its chunk of the input, and generates a set of intermediate key-value pairs.
- The worker nodes then send their intermediate key-value pairs to the master node.
- The master node combines the intermediate key-value pairs from the worker nodes and runs the reduce function on them to produce the final output.
