```
[hdfs@ip-172-31-9-193 ~]$ hadoop distcp hdfs://ip-172-31-15-226.ap-southeast-1.compute.internal:8020/lawankorn/SEBC/source hdfs://ip-172-31-9-193.ap-southeast-1.compute.internal/lawankore/SEBC/target
17/02/14 14:02:53 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://ip-172-31-15-226.ap-southeast-1.compute.internal:8020/lawankorn/SEBC/source], targetPath=hdfs://ip-172-31-9-193.ap-southeast-1.compute.internal/lawankore/SEBC/target, targetPathExists=false, filtersFile='null'}
17/02/14 14:02:53 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-9-193.ap-southeast-1.compute.internal/172.31.9.193:8032
17/02/14 14:02:53 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 3; dirCnt = 1
17/02/14 14:02:53 INFO tools.SimpleCopyListing: Build file listing completed.
17/02/14 14:02:53 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
17/02/14 14:02:53 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
17/02/14 14:02:53 INFO tools.DistCp: Number of paths in the copy list: 3
17/02/14 14:02:53 INFO tools.DistCp: Number of paths in the copy list: 3
17/02/14 14:02:53 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-9-193.ap-southeast-1.compute.internal/172.31.9.193:8032
17/02/14 14:02:54 INFO mapreduce.JobSubmitter: number of splits:2
17/02/14 14:02:54 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1487039277252_0003
17/02/14 14:02:54 INFO impl.YarnClientImpl: Submitted application application_1487039277252_0003
17/02/14 14:02:54 INFO mapreduce.Job: The url to track the job: http://ip-172-31-9-193.ap-southeast-1.compute.internal:8088/proxy/application_1487039277252_0003/
17/02/14 14:02:54 INFO tools.DistCp: DistCp job-id: job_1487039277252_0003
17/02/14 14:02:54 INFO mapreduce.Job: Running job: job_1487039277252_0003
17/02/14 14:03:00 INFO mapreduce.Job: Job job_1487039277252_0003 running in uber mode : false
17/02/14 14:03:00 INFO mapreduce.Job:  map 0% reduce 0%
17/02/14 14:03:05 INFO mapreduce.Job:  map 50% reduce 0%
17/02/14 14:03:10 INFO mapreduce.Job:  map 100% reduce 0%
17/02/14 14:03:11 INFO mapreduce.Job: Job job_1487039277252_0003 completed successfully
17/02/14 14:03:11 INFO mapreduce.Job: Counters: 33
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=250124
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=524289196
                HDFS: Number of bytes written=524288000
                HDFS: Number of read operations=37
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=9
        Job Counters 
                Launched map tasks=2
                Other local map tasks=2
                Total time spent by all maps in occupied slots (ms)=12351
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=12351
                Total vcore-seconds taken by all map tasks=12351
                Total megabyte-seconds taken by all map tasks=12647424
        Map-Reduce Framework
                Map input records=3
                Map output records=0
                Input split bytes=230
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=129
                CPU time spent (ms)=6120
                Physical memory (bytes) snapshot=563732480
                Virtual memory (bytes) snapshot=3145670656
                Total committed heap usage (bytes)=510132224
        File Input Format Counters 
                Bytes Read=966
        File Output Format Counters 
                Bytes Written=0
        org.apache.hadoop.tools.mapred.CopyMapper$Counter
                BYTESCOPIED=524288000
                BYTESEXPECTED=524288000
                COPY=3

[hdfs@ip-172-31-9-193 ~]$ hdfs fsck /Walker/SEBC/source -files -blocks
Connecting to namenode via http://ip-172-31-9-193.ap-southeast-1.compute.internal:50070
FSCK started by hdfs (auth:SIMPLE) from /172.31.9.193 for path /Walker/SEBC/source at Tue Feb 14 00:58:58 EST 2017
/Walker/SEBC/source <dir>
/Walker/SEBC/source/_SUCCESS 0 bytes, 0 block(s):  OK

/Walker/SEBC/source/part-m-00000 262144000 bytes, 2 block(s):  OK
0. BP-476058346-172.31.9.193-1487007755214:blk_1073743212_2388 len=134217728 Live_repl=3
1. BP-476058346-172.31.9.193-1487007755214:blk_1073743214_2390 len=127926272 Live_repl=3

/Walker/SEBC/source/part-m-00001 262144000 bytes, 2 block(s):  OK
0. BP-476058346-172.31.9.193-1487007755214:blk_1073743211_2387 len=134217728 Live_repl=3
1. BP-476058346-172.31.9.193-1487007755214:blk_1073743213_2389 len=127926272 Live_repl=3

Status: HEALTHY
 Total size:    524288000 B
 Total dirs:    1
 Total files:   3
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 131072000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Tue Feb 14 00:58:58 EST 2017 in 2 milliseconds


The filesystem under path '/Walker/SEBC/source' is HEALTHY

[hdfs@ip-172-31-9-193 ~]$ hdfs fsck /lawankore/SEBC/target -files -blocks
Connecting to namenode via http://ip-172-31-9-193.ap-southeast-1.compute.internal:50070
FSCK started by hdfs (auth:SIMPLE) from /172.31.9.193 for path /lawankore/SEBC/target at Tue Feb 14 01:04:27 EST 2017
/lawankore/SEBC/target <dir>
/lawankore/SEBC/target/_SUCCESS 0 bytes, 0 block(s):  OK

/lawankore/SEBC/target/part-m-00000 524288000 bytes, 4 block(s):  OK
0. BP-476058346-172.31.9.193-1487007755214:blk_1073743287_2463 len=134217728 Live_repl=3
1. BP-476058346-172.31.9.193-1487007755214:blk_1073743289_2465 len=134217728 Live_repl=3
2. BP-476058346-172.31.9.193-1487007755214:blk_1073743290_2466 len=134217728 Live_repl=3
3. BP-476058346-172.31.9.193-1487007755214:blk_1073743291_2467 len=121634816 Live_repl=3

Status: HEALTHY
 Total size:    524288000 B
 Total dirs:    1
 Total files:   2
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 131072000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Tue Feb 14 01:04:27 EST 2017 in 1 milliseconds


The filesystem under path '/lawankore/SEBC/target' is HEALTHY
```
