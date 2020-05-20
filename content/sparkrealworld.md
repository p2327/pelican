title: Spark from scratch
slug: apachesparkfromscratch
category: spark
date: 2020-05-19
modified: 2020-05-19



Is it not easy to find example projects that implement a Big Data pipeline and can take advantage of Spark, so let's build one from scratch!

First, let's review some basics about Spark and Spark applications.

Spark is a distributed computing framework which provides an interface for programming clusters with data parallelism (i.e. distributing the data across multiple nodes for processing) and fault tolerance built-in. In Spark (and generally distributed computing) each node has it's own memory and CPU. Thanks to its architecture, Spark can perform processing tasks on very large data sets, and can distribute these tasks across multiple computers.

A Spark application runs as an independed process on a cluster and consists of one *driver process* in charge of the control flow of the work be done, and a set of *executors* arranged across the cluster nodes which do the actual work (i.e run the individual *tasks* in a *Spark job*) and store (i.e cache) any data specified by the user. 

<img src="https://spark.apache.org/docs/latest/img/cluster-overview.png" width="500">

Deploying and allocating resources to these processes is the responsibility of the *cluster manager* (YARN, Mesos or Spark Standalone). For more details, heres the [documentation](https://spark.apache.org/docs/latest/cluster-overview.html).

A tipical Spark application execution flow is as follows:
1. The application start and instantiates a `Sparkcontext¬ which becomes the applciation driver.
2. The driver program asks for resources to the cluster manager for launching executors.
3. Cluster manager launches executors.
4. The driver process runs through the user application, sending tasks to executors.
5. Executors run the tasks and save the results. IF any worker crashes, its tasks are sent to a different executor. This is Spark fault tolerance mechanism.
6. Once `SparkContext` is stopped or the main method exits (or crashes), all executors are terminated and cluster resources are released.

With this overview we can now get started with the project.

### Use case

> We are a Data Engineer at a small startup. The company is currently getting lots of Apache/application logs being copied to Amazon S3. Our team is assigned the task to process all of the high volume logs, and to expose this data so that the Data Science team can consume it using SQL or python.

### Problem statement

To be continued...