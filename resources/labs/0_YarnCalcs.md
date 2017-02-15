Explain any adjustments
```
A. I have adjust Reserved OS Memory from 10% of all memory (12.8GB) to 24GB
B. I have adjust about memory of mapper adnd reducer below
   mapreduce.map.memory.mb from 1024 to 2048
   mapreduce.map.java.opts.max.heap from 800 to 1639
   mapreduce.reduce.memory.mb from 1024 to 4096
   mapreduce.reduce.java.opts.max.heap from 800 to 3277
   Reason: almost files in hdfs are compression files and parquet files, so i adjust a memory of map and reduce
C. I have adjust yarn.scheduler.minimum-allocation-mb from 1024 to 2048 because the configuration of mapreduce.map.memory.mb in Task Container Settings and Gateway Settings started at 2048
```

What criteria affects workload factor? What does a value of 1, 2, or 4 signify?
```
I have a workload from ETL inject large data from text file to hdfs, sqoop injest data form RDBMS 
and spark streaming injest data form web application. So the value of workload factor is 3.
```
