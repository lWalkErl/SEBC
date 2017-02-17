Run the terasort program as raffles using /user/raffles/tgen512m
```
[raffles@ip-172-31-5-240 ~]$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort /user/raffles/tgen512m /user/raffles/tsort512m
17/02/17 15:47:50 INFO terasort.TeraSort: starting
17/02/17 15:47:52 INFO hdfs.DFSClient: Created token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@WALKER.SG, renewer=yarn, realUser=, issueDate=1487317672480, maxDate=1487922472480, sequenceNumber=1, masterKeyId=2 on 172.31.5.240:8020
17/02/17 15:47:52 INFO security.TokenCache: Got dt for hdfs://ip-172-31-5-240.ap-southeast-1.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.5.240:8020, Ident: (token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@WALKER.SG, renewer=yarn, realUser=, issueDate=1487317672480, maxDate=1487922472480, sequenceNumber=1, masterKeyId=2)
17/02/17 15:47:52 INFO input.FileInputFormat: Total input paths to process : 6
Spent 289ms computing base-splits.
Spent 4ms computing TeraScheduler splits.
Computing input splits took 294ms
Sampling 10 splits of 156
Making 3 from 100000 sampled records
Computing parititions took 934ms
Spent 1230ms computing partitions.
17/02/17 15:47:53 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-5-240.ap-southeast-1.compute.internal/172.31.5.240:8032
17/02/17 15:47:54 INFO mapreduce.JobSubmitter: number of splits:156
17/02/17 15:47:54 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1487317300275_0001
17/02/17 15:47:54 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.5.240:8020, Ident: (token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@WALKER.SG, renewer=yarn, realUser=, issueDate=1487317672480, maxDate=1487922472480, sequenceNumber=1, masterKeyId=2)
17/02/17 15:47:55 INFO impl.YarnClientImpl: Submitted application application_1487317300275_0001
17/02/17 15:47:55 INFO mapreduce.Job: The url to track the job: http://ip-172-31-5-240.ap-southeast-1.compute.internal:8088/proxy/application_1487317300275_0001/
17/02/17 15:47:55 INFO mapreduce.Job: Running job: job_1487317300275_0001
17/02/17 15:48:05 INFO mapreduce.Job: Job job_1487317300275_0001 running in uber mode : false
17/02/17 15:48:05 INFO mapreduce.Job:  map 0% reduce 0%
17/02/17 15:48:15 INFO mapreduce.Job:  map 1% reduce 0%
17/02/17 15:48:20 INFO mapreduce.Job:  map 2% reduce 0%
17/02/17 15:48:22 INFO mapreduce.Job:  map 3% reduce 0%
17/02/17 15:48:27 INFO mapreduce.Job:  map 4% reduce 0%
17/02/17 15:48:33 INFO mapreduce.Job:  map 5% reduce 0%
17/02/17 15:48:38 INFO mapreduce.Job:  map 6% reduce 0%
17/02/17 15:48:44 INFO mapreduce.Job:  map 7% reduce 0%
17/02/17 15:48:45 INFO mapreduce.Job:  map 8% reduce 0%
17/02/17 15:48:51 INFO mapreduce.Job:  map 9% reduce 0%
17/02/17 15:48:56 INFO mapreduce.Job:  map 10% reduce 0%
17/02/17 15:49:02 INFO mapreduce.Job:  map 11% reduce 0%
17/02/17 15:49:03 INFO mapreduce.Job:  map 12% reduce 0%
17/02/17 15:49:09 INFO mapreduce.Job:  map 13% reduce 0%
17/02/17 15:49:15 INFO mapreduce.Job:  map 14% reduce 0%
17/02/17 15:49:21 INFO mapreduce.Job:  map 15% reduce 0%
17/02/17 15:49:27 INFO mapreduce.Job:  map 16% reduce 0%
17/02/17 15:49:28 INFO mapreduce.Job:  map 17% reduce 0%
17/02/17 15:49:34 INFO mapreduce.Job:  map 18% reduce 0%
17/02/17 15:49:39 INFO mapreduce.Job:  map 19% reduce 0%
17/02/17 15:49:45 INFO mapreduce.Job:  map 20% reduce 0%
17/02/17 15:49:46 INFO mapreduce.Job:  map 21% reduce 0%
17/02/17 15:49:52 INFO mapreduce.Job:  map 22% reduce 0%
17/02/17 15:49:58 INFO mapreduce.Job:  map 23% reduce 0%
17/02/17 15:50:03 INFO mapreduce.Job:  map 24% reduce 0%
17/02/17 15:50:09 INFO mapreduce.Job:  map 25% reduce 0%
17/02/17 15:50:10 INFO mapreduce.Job:  map 26% reduce 0%
17/02/17 15:50:16 INFO mapreduce.Job:  map 27% reduce 0%
17/02/17 15:50:21 INFO mapreduce.Job:  map 28% reduce 0%
17/02/17 15:50:27 INFO mapreduce.Job:  map 29% reduce 0%
17/02/17 15:50:33 INFO mapreduce.Job:  map 30% reduce 0%
17/02/17 15:50:34 INFO mapreduce.Job:  map 31% reduce 0%
17/02/17 15:50:40 INFO mapreduce.Job:  map 32% reduce 0%
17/02/17 15:50:45 INFO mapreduce.Job:  map 33% reduce 0%
17/02/17 15:50:51 INFO mapreduce.Job:  map 34% reduce 0%
17/02/17 15:50:52 INFO mapreduce.Job:  map 35% reduce 0%
17/02/17 15:50:58 INFO mapreduce.Job:  map 36% reduce 0%
17/02/17 15:51:03 INFO mapreduce.Job:  map 37% reduce 0%
17/02/17 15:51:09 INFO mapreduce.Job:  map 38% reduce 0%
17/02/17 15:51:15 INFO mapreduce.Job:  map 39% reduce 0%
17/02/17 15:51:16 INFO mapreduce.Job:  map 40% reduce 0%
17/02/17 15:51:22 INFO mapreduce.Job:  map 41% reduce 0%
17/02/17 15:51:27 INFO mapreduce.Job:  map 42% reduce 0%
17/02/17 15:51:33 INFO mapreduce.Job:  map 43% reduce 0%
17/02/17 15:51:34 INFO mapreduce.Job:  map 44% reduce 0%
17/02/17 15:51:40 INFO mapreduce.Job:  map 45% reduce 0%
17/02/17 15:51:45 INFO mapreduce.Job:  map 46% reduce 0%
17/02/17 15:51:51 INFO mapreduce.Job:  map 47% reduce 0%
17/02/17 15:51:57 INFO mapreduce.Job:  map 48% reduce 0%
17/02/17 15:51:58 INFO mapreduce.Job:  map 49% reduce 0%
17/02/17 15:52:04 INFO mapreduce.Job:  map 50% reduce 0%
17/02/17 15:52:09 INFO mapreduce.Job:  map 51% reduce 0%
17/02/17 15:52:15 INFO mapreduce.Job:  map 52% reduce 0%
17/02/17 15:52:16 INFO mapreduce.Job:  map 53% reduce 0%
17/02/17 15:52:23 INFO mapreduce.Job:  map 54% reduce 0%
17/02/17 15:52:29 INFO mapreduce.Job:  map 55% reduce 0%
17/02/17 15:52:34 INFO mapreduce.Job:  map 56% reduce 0%
17/02/17 15:52:40 INFO mapreduce.Job:  map 57% reduce 0%
17/02/17 15:52:41 INFO mapreduce.Job:  map 58% reduce 0%
17/02/17 15:52:47 INFO mapreduce.Job:  map 59% reduce 0%
17/02/17 15:52:52 INFO mapreduce.Job:  map 60% reduce 0%
17/02/17 15:52:58 INFO mapreduce.Job:  map 61% reduce 0%
17/02/17 15:52:59 INFO mapreduce.Job:  map 62% reduce 0%
17/02/17 15:53:05 INFO mapreduce.Job:  map 63% reduce 0%
17/02/17 15:53:11 INFO mapreduce.Job:  map 64% reduce 0%
17/02/17 15:53:16 INFO mapreduce.Job:  map 65% reduce 0%
17/02/17 15:53:22 INFO mapreduce.Job:  map 66% reduce 0%
17/02/17 15:53:23 INFO mapreduce.Job:  map 67% reduce 0%
17/02/17 15:53:29 INFO mapreduce.Job:  map 68% reduce 0%
17/02/17 15:53:34 INFO mapreduce.Job:  map 69% reduce 0%
17/02/17 15:53:40 INFO mapreduce.Job:  map 70% reduce 0%
17/02/17 15:53:41 INFO mapreduce.Job:  map 71% reduce 0%
17/02/17 15:53:47 INFO mapreduce.Job:  map 72% reduce 0%
17/02/17 15:53:53 INFO mapreduce.Job:  map 73% reduce 0%
17/02/17 15:53:59 INFO mapreduce.Job:  map 74% reduce 0%
17/02/17 15:54:05 INFO mapreduce.Job:  map 76% reduce 0%
17/02/17 15:54:11 INFO mapreduce.Job:  map 77% reduce 0%
17/02/17 15:54:17 INFO mapreduce.Job:  map 78% reduce 0%
17/02/17 15:54:23 INFO mapreduce.Job:  map 79% reduce 0%
17/02/17 15:54:29 INFO mapreduce.Job:  map 81% reduce 0%
17/02/17 15:54:35 INFO mapreduce.Job:  map 82% reduce 0%
17/02/17 15:54:41 INFO mapreduce.Job:  map 83% reduce 0%
17/02/17 15:54:51 INFO mapreduce.Job:  map 83% reduce 9%
17/02/17 15:54:53 INFO mapreduce.Job:  map 84% reduce 9%
17/02/17 15:54:59 INFO mapreduce.Job:  map 85% reduce 9%
17/02/17 15:55:11 INFO mapreduce.Job:  map 86% reduce 9%
17/02/17 15:55:15 INFO mapreduce.Job:  map 86% reduce 10%
17/02/17 15:55:17 INFO mapreduce.Job:  map 87% reduce 10%
17/02/17 15:55:29 INFO mapreduce.Job:  map 88% reduce 10%
17/02/17 15:55:40 INFO mapreduce.Job:  map 89% reduce 10%
17/02/17 15:55:47 INFO mapreduce.Job:  map 90% reduce 10%
17/02/17 15:56:00 INFO mapreduce.Job:  map 91% reduce 10%
17/02/17 15:56:06 INFO mapreduce.Job:  map 92% reduce 10%
17/02/17 15:56:17 INFO mapreduce.Job:  map 93% reduce 10%
17/02/17 15:56:23 INFO mapreduce.Job:  map 94% reduce 10%
17/02/17 15:56:35 INFO mapreduce.Job:  map 95% reduce 10%
17/02/17 15:56:39 INFO mapreduce.Job:  map 95% reduce 11%
17/02/17 15:56:41 INFO mapreduce.Job:  map 96% reduce 11%
17/02/17 15:56:51 INFO mapreduce.Job:  map 97% reduce 11%
17/02/17 15:57:01 INFO mapreduce.Job:  map 98% reduce 11%
17/02/17 15:57:06 INFO mapreduce.Job:  map 99% reduce 11%
17/02/17 15:57:17 INFO mapreduce.Job:  map 100% reduce 11%
17/02/17 15:57:21 INFO mapreduce.Job:  map 100% reduce 23%
17/02/17 15:57:27 INFO mapreduce.Job:  map 100% reduce 27%
17/02/17 15:57:33 INFO mapreduce.Job:  map 100% reduce 42%
17/02/17 15:57:36 INFO mapreduce.Job:  map 100% reduce 44%
17/02/17 15:57:39 INFO mapreduce.Job:  map 100% reduce 56%
17/02/17 15:57:45 INFO mapreduce.Job:  map 100% reduce 60%
17/02/17 15:57:51 INFO mapreduce.Job:  map 100% reduce 75%
17/02/17 15:57:54 INFO mapreduce.Job:  map 100% reduce 77%
17/02/17 15:57:57 INFO mapreduce.Job:  map 100% reduce 89%
17/02/17 15:58:03 INFO mapreduce.Job:  map 100% reduce 93%
17/02/17 15:58:09 INFO mapreduce.Job:  map 100% reduce 98%
17/02/17 15:58:12 INFO mapreduce.Job:  map 100% reduce 100%
17/02/17 15:58:12 INFO mapreduce.Job: Job job_1487317300275_0001 completed successfully
17/02/17 15:58:12 INFO mapreduce.Job: Counters: 50
        File System Counters
                FILE: Number of bytes read=2275600754
                FILE: Number of bytes written=4519298385
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=5120024804
                HDFS: Number of bytes written=5120000000
                HDFS: Number of read operations=477
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=6
        Job Counters 
                Launched map tasks=156
                Launched reduce tasks=3
                Data-local map tasks=154
                Rack-local map tasks=2
                Total time spent by all maps in occupied slots (ms)=743581
                Total time spent by all reduces in occupied slots (ms)=250926
                Total time spent by all map tasks (ms)=743581
                Total time spent by all reduce tasks (ms)=250926
                Total vcore-seconds taken by all map tasks=743581
                Total vcore-seconds taken by all reduce tasks=250926
                Total megabyte-seconds taken by all map tasks=761426944
                Total megabyte-seconds taken by all reduce tasks=256948224
        Map-Reduce Framework
                Map input records=51200000
                Map output records=51200000
                Map output bytes=5222400000
                Map output materialized bytes=2223499425
                Input split bytes=24804
                Combine input records=0
                Combine output records=0
                Reduce input groups=51200000
                Reduce shuffle bytes=2223499425
                Reduce input records=51200000
                Reduce output records=51200000
                Spilled Records=102400000
                Shuffled Maps =468
                Failed Shuffles=0
                Merged Map outputs=468
                GC time elapsed (ms)=9042
                CPU time spent (ms)=508110
                Physical memory (bytes) snapshot=76580569088
                Virtual memory (bytes) snapshot=250350514176
                Total committed heap usage (bytes)=78473854976
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters 
                Bytes Read=5120000000
        File Output Format Counters 
                Bytes Written=5120000000
17/02/17 15:58:12 INFO terasort.TeraSort: done
```
