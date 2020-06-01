title: Spark from scratch
slug: apachesparkfromscratch
category: spark
date: 2020-04-19
modified: 2020-05-31



Is it not easy to find example projects that implement a Big Data pipeline and can take advantage of Spark, so let's build one from scratch!

First, let's review some basics about Spark and Spark applications.

Spark is a distributed computing framework which provides an interface for programming clusters with data parallelism (i.e. distributing the data across multiple nodes for processing) and fault tolerance built-in. In Spark (and generally distributed computing) each node has it's own memory and CPU. Thanks to its architecture, Spark can perform processing tasks on very large data sets, and can distribute these tasks across multiple computers.

A Spark application runs as an independed process on a cluster and consists of one *driver process* in charge of the control flow of the work be done, and a set of *executors* arranged across the cluster nodes which do the actual work (i.e run the individual *tasks* in a *Spark job*) and store (i.e cache) any data specified by the user. 

<img src="https://spark.apache.org/docs/latest/img/cluster-overview.png" width="550">

Deploying and allocating resources to these processes is the responsibility of the *cluster manager* (YARN, Mesos or Spark Standalone). For more details, heres the [documentation](https://spark.apache.org/docs/latest/cluster-overview.html).

A tipical Spark application execution flow is as follows:
    1. The application start and instantiates a `Sparkcontext` which becomes the applciation driver.
    2. The driver program asks for resources to the cluster manager for launching executors.
    3. Cluster manager launches executors.
    4. The driver process runs through the user application, sending tasks to executors.
    5. Executors run the tasks and save the results. IF any worker crashes, its tasks are sent to a different executor. This is Spark fault tolerance mechanism.
    6. Once `SparkContext` is stopped or the main method exits (or crashes), all executors are terminated and cluster resources are released.

With this overview we can now get started with the project.

### Use case

> We are a Data Engineer at a small startup. The company is currently getting lots of Apache/application logs being copied to Amazon S3. Our team is assigned the task to process all of the high volume logs, and to expose this data so that the Data Science team can consume it using SQL or python.

### Problem statement

Below is waht we aim to achieve with the project.

Explore Big Data concepts:
- Build a Data Lake to store structured and unstructured data
- Use optimisation techniques such as partioned data/tables
- Use Parquet columnar data format

Define and schedule our ETL process:
- Create daily jobs to process raw incoming data in Apache log format, clean and extract relevant features data
- Create hourly and daily jobs to aggregate raw tables. These will be exposed so that analysts can run queries.

We'll be using AWS as a cloud base infrastructure throughout the project.


### Project approach

Our solution will use AWS as cloud base infrastructure, amnage our pipelines with Airflow and use Zeppelin as data consumption layer.

Here is a schema of the components:
<img src="https://i.imgur.com/WRoKIlS.png" width="550">


**Amazon S3 as a Data Lake**
We'll be using Amazon S3 as a data lake to store and retrieve our data. This wil make the data easily accessible at any time and from anywhere with an internet connection.

Amazon S3 benefits:
- Easy to use
- Stores both structured and unstructured data
- Cost effective
- No need to move data onto naother system to run analytics on it


**Airflow as job scheduler**

to be continued..

### The data

The first thign will need is data.
We are going to generate fake logs using the Fake Log Generator library.

Install by running:
```bash
git clone https://github.com/kiritbasu/Fake-Apache-Log-Generator.git
cd  Fake-Apache-Log-Generator
```

Create a virtual environment and install dependencies:
```bash
conda create --name py35 python=3.5
conda activate fakelogs
pip install -r requirements.txt 
```

Print some sample data to the terminal:
```bash
python apache-fake-log-gen.py -n 20
```

Create a zip file of the logs and specify RWSPARK as prefix for the filename:
```bash
python apache-fake-log-gen.py -n 20 -o GZ 
```

We now have our logs saved ```RWSPARK_access_log_20200531-125656.log.gz``` and ready to be uploaded to our S3 bucket.


#### Copy data to S3

TBC