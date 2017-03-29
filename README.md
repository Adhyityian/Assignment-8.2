# Assignment-8.2

1.Explain the core changes made in Hadoop 2.x

-Resource Utilization is taken care by ResourceManager and NodeManager, whereas job monitoring is taken care by ApplicationMaster whereas in hadoop 1.x the jobTracker keeps track of resource utilization and job monitoring.
-Hadoop 2.x can scale up to 10000 nodes and 100000 tasks whereas Hadoop 1.x can handle a maximum of 4000 nodes and 40000 tasks.
-Resources are dynamic and finegrained.Thus better cluster utilization in Hadoop 2.x
-Hadoop 2.x Supports processing models other than Map Reduce whereas Hadoop 1.x supports only Mapreduce model.
-Hadoop 2.x Works on concepts of containers.containers can run generic tasks whereas Hadoop 1.x Works on concepts of slots – slots can run either a Map task or a Reduce task only.
-Hadoop 1.x doesn't support Microsoft windows whereas Hadoop 2.x supports Microsoft Windows.
-Hadoop 1.x has Single-Point-of-Failure (SPOF) – because of single Namenode- and in case of Namenode failure, needs manual intervention to overcome. whereas Hadoop 2.x has a feature to overcome SPOF with a standby Namenode and in case of Namenode failure, it is configured for automatic recovery.
-Hadoop 2.x has Multiple Namenode servers which manages multiple namespaces whereas Hadoop 1.x has only a single Namenode to manage the entire namespace.



2.Explain the difference between MapReduce 1 and MapReduce 2 / Yarn:
MAPREDUCE 1:

MapReduce is a Distributed Data Processing or Batch Processing Programming Model. Like HDFS, MapReduce component also uses Commodity Hardware to process “High Volume of Variety of Data at High Velocity Rate” in a reliable and fault-tolerant manner.

MapReduce component is again divided into two sub-components:

1)Job Tracker:
-Job Tracker is used to assign MapReduce Tasks to Task Trackers in the Cluster of Nodes. Sometimes, it reassigns same tasks to other Task Trackers as previous Task Trackers are failed or shutdown scenarios.
-Job Tracker maintains all the Task Trackers status like Up/running, Failed, Recovered etc.

2)Task Tracker:
-Task Tracker executes the Tasks which are assigned by Job Tracker and sends the status of those tasks to Job Tracker.

Working:
-Clients (one or more) submit their work to Hadoop System.
-When Hadoop System receives a Client Request, first it is received by a Master Node.
-Once all Task Trackers finished their job, Job Tracker takes those results and combines them into final result.

Hadoop can scale up to 4,000 nodes. When it exceeds that limit, it raises unpredictable behavior such as cascading failures and serious deterioration of overall cluster. 

MAPREDUCE 2/YARN:
MapReduce 2 component is again divided into two sub-components:

Job Tracker:
In MapReduce 2.0, the JobTracker is divided into three services:

ResourceManager, a persistent YARN service that receives and runs applications on the cluster.  A MapReduce job is an application.
JobHistoryServer, to provide information about completed jobs
Application Master, to manage each MapReduce job and is terminated when the job completes.

Task Tracker:
Also, the TaskTracker has been replaced with the NodeManager, a YARN service that manages resources and deployment on a node. NodeManager is responsible for launching containers that could either be a map or reduce task.

This new architecture breaks JobTracker model by allowing a new ResourceManager to manage resource usage across applications, with ApplicationMasters taking the responsibility of managing the execution of jobs. This change removes a bottleneck and let Hadoop clusters scale up to larger configurations than 4000 nodes. 
