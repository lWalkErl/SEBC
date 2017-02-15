Explain any adjustments
```
A. I have adjust a Worker vcores from 20 to 32 (calculate from i have 2 sockets * 8 Cores and percore has 2 Threads)
B. I have adjust a Worker memory from 128 to 256 because i have a lot of files to transform and i want to many container to handle
C. I have adjust Reserved OS Memory from 10% of all memory (25.6GB) to 32GB
```

What criteria affects workload factor? What does a value of 1, 2, or 4 signify?
```
I have a workload from ETL inject large data from text file to hdfs, sqoop injest data form RDBMS 
and spark streaming injest data form web application. So the value of workload factor is 3.
```
