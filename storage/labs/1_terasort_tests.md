Create a 10 GB file using teragen with set the number of mappers to four and block size is 32 MB
```
[walker@ip-172-31-9-193 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -D mapred.map.tasks=4 -D dfs.block.size=33554432 107374183 /user/walker/teragen
17/02/14 15:55:34 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-9-193.ap-southeast-1.compute.internal/172.31.9.193:8032
17/02/14 15:55:35 INFO terasort.TeraSort: Generating 107374183 using 4
17/02/14 15:55:35 INFO mapreduce.JobSubmitter: number of splits:4
17/02/14 15:55:35 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/02/14 15:55:35 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/02/14 15:55:35 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1487039277252_0005
17/02/14 15:55:35 INFO impl.YarnClientImpl: Submitted application application_1487039277252_0005
17/02/14 15:55:35 INFO mapreduce.Job: The url to track the job: http://ip-172-31-9-193.ap-southeast-1.compute.internal:8088/proxy/application_1487039277252_0005/
17/02/14 15:55:35 INFO mapreduce.Job: Running job: job_1487039277252_0005
17/02/14 15:55:41 INFO mapreduce.Job: Job job_1487039277252_0005 running in uber mode : false
17/02/14 15:55:41 INFO mapreduce.Job:  map 0% reduce 0%
17/02/14 15:55:52 INFO mapreduce.Job:  map 6% reduce 0%
17/02/14 15:55:55 INFO mapreduce.Job:  map 9% reduce 0%
17/02/14 15:55:58 INFO mapreduce.Job:  map 12% reduce 0%
17/02/14 15:56:01 INFO mapreduce.Job:  map 16% reduce 0%
17/02/14 15:56:04 INFO mapreduce.Job:  map 19% reduce 0%
17/02/14 15:56:07 INFO mapreduce.Job:  map 22% reduce 0%
17/02/14 15:56:10 INFO mapreduce.Job:  map 26% reduce 0%
17/02/14 15:56:13 INFO mapreduce.Job:  map 29% reduce 0%
17/02/14 15:56:16 INFO mapreduce.Job:  map 32% reduce 0%
17/02/14 15:56:19 INFO mapreduce.Job:  map 36% reduce 0%
17/02/14 15:56:22 INFO mapreduce.Job:  map 39% reduce 0%
17/02/14 15:56:25 INFO mapreduce.Job:  map 42% reduce 0%
17/02/14 15:56:28 INFO mapreduce.Job:  map 46% reduce 0%
17/02/14 15:56:31 INFO mapreduce.Job:  map 49% reduce 0%
17/02/14 15:56:32 INFO mapreduce.Job:  map 50% reduce 0%
17/02/14 15:56:42 INFO mapreduce.Job:  map 56% reduce 0%
17/02/14 15:56:45 INFO mapreduce.Job:  map 59% reduce 0%
17/02/14 15:56:48 INFO mapreduce.Job:  map 62% reduce 0%
17/02/14 15:56:51 INFO mapreduce.Job:  map 65% reduce 0%
17/02/14 15:56:54 INFO mapreduce.Job:  map 69% reduce 0%
17/02/14 15:56:57 INFO mapreduce.Job:  map 72% reduce 0%
17/02/14 15:57:00 INFO mapreduce.Job:  map 75% reduce 0%
17/02/14 15:57:03 INFO mapreduce.Job:  map 78% reduce 0%
17/02/14 15:57:06 INFO mapreduce.Job:  map 82% reduce 0%
17/02/14 15:57:09 INFO mapreduce.Job:  map 85% reduce 0%
17/02/14 15:57:12 INFO mapreduce.Job:  map 88% reduce 0%
17/02/14 15:57:15 INFO mapreduce.Job:  map 91% reduce 0%
17/02/14 15:57:18 INFO mapreduce.Job:  map 94% reduce 0%
17/02/14 15:57:21 INFO mapreduce.Job:  map 97% reduce 0%
17/02/14 15:57:23 INFO mapreduce.Job:  map 100% reduce 0%
17/02/14 15:57:23 INFO mapreduce.Job: Job job_1487039277252_0005 completed successfully
17/02/14 15:57:23 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=488652
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=344
                HDFS: Number of bytes written=10737418300
                HDFS: Number of read operations=16
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=8
        Job Counters 
                Launched map tasks=4
                Other local map tasks=4
                Total time spent by all maps in occupied slots (ms)=198591
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=198591
                Total vcore-seconds taken by all map tasks=198591
                Total megabyte-seconds taken by all map tasks=203357184
        Map-Reduce Framework
                Map input records=107374183
                Map output records=107374183
                Input split bytes=344
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1377
                CPU time spent (ms)=134190
                Physical memory (bytes) snapshot=1005264896
                Virtual memory (bytes) snapshot=6259675136
                Total committed heap usage (bytes)=658505728
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=230593860607047066
        File Input Format Counters 
                Bytes Read=0
        File Output Format Counters 
                Bytes Written=10737418300
## Check block size
[walker@ip-172-31-9-193 ~]$ hdfs fsck /user/walker/teragen/part-m-00003 -files -blocks
Connecting to namenode via http://ip-172-31-9-193.ap-southeast-1.compute.internal:50070
FSCK started by walker (auth:SIMPLE) from /172.31.9.193 for path /user/walker/teragen/part-m-00003 at Tue Feb 14 03:00:54 EST 2017
/user/walker/teragen/part-m-00003 2684354500 bytes, 80 block(s):  OK
0. BP-476058346-172.31.9.193-1487007755214:blk_1073743674_2850 len=33554432 Live_repl=3
1. BP-476058346-172.31.9.193-1487007755214:blk_1073743676_2852 len=33554432 Live_repl=3
2. BP-476058346-172.31.9.193-1487007755214:blk_1073743678_2854 len=33554432 Live_repl=3
3. BP-476058346-172.31.9.193-1487007755214:blk_1073743680_2856 len=33554432 Live_repl=3
4. BP-476058346-172.31.9.193-1487007755214:blk_1073743682_2858 len=33554432 Live_repl=3
5. BP-476058346-172.31.9.193-1487007755214:blk_1073743684_2860 len=33554432 Live_repl=3
6. BP-476058346-172.31.9.193-1487007755214:blk_1073743686_2862 len=33554432 Live_repl=3
7. BP-476058346-172.31.9.193-1487007755214:blk_1073743688_2864 len=33554432 Live_repl=3
8. BP-476058346-172.31.9.193-1487007755214:blk_1073743690_2866 len=33554432 Live_repl=3
9. BP-476058346-172.31.9.193-1487007755214:blk_1073743692_2868 len=33554432 Live_repl=3
10. BP-476058346-172.31.9.193-1487007755214:blk_1073743694_2870 len=33554432 Live_repl=3
11. BP-476058346-172.31.9.193-1487007755214:blk_1073743696_2872 len=33554432 Live_repl=3
12. BP-476058346-172.31.9.193-1487007755214:blk_1073743698_2874 len=33554432 Live_repl=3
13. BP-476058346-172.31.9.193-1487007755214:blk_1073743700_2876 len=33554432 Live_repl=3
14. BP-476058346-172.31.9.193-1487007755214:blk_1073743702_2878 len=33554432 Live_repl=3
15. BP-476058346-172.31.9.193-1487007755214:blk_1073743705_2881 len=33554432 Live_repl=3
16. BP-476058346-172.31.9.193-1487007755214:blk_1073743707_2883 len=33554432 Live_repl=3
17. BP-476058346-172.31.9.193-1487007755214:blk_1073743709_2885 len=33554432 Live_repl=3
18. BP-476058346-172.31.9.193-1487007755214:blk_1073743711_2887 len=33554432 Live_repl=3
19. BP-476058346-172.31.9.193-1487007755214:blk_1073743713_2889 len=33554432 Live_repl=3
20. BP-476058346-172.31.9.193-1487007755214:blk_1073743715_2891 len=33554432 Live_repl=3
21. BP-476058346-172.31.9.193-1487007755214:blk_1073743717_2893 len=33554432 Live_repl=3
22. BP-476058346-172.31.9.193-1487007755214:blk_1073743719_2895 len=33554432 Live_repl=3
23. BP-476058346-172.31.9.193-1487007755214:blk_1073743720_2896 len=33554432 Live_repl=3
24. BP-476058346-172.31.9.193-1487007755214:blk_1073743722_2898 len=33554432 Live_repl=3
25. BP-476058346-172.31.9.193-1487007755214:blk_1073743724_2900 len=33554432 Live_repl=3
26. BP-476058346-172.31.9.193-1487007755214:blk_1073743726_2902 len=33554432 Live_repl=3
27. BP-476058346-172.31.9.193-1487007755214:blk_1073743728_2904 len=33554432 Live_repl=3
28. BP-476058346-172.31.9.193-1487007755214:blk_1073743730_2906 len=33554432 Live_repl=3
29. BP-476058346-172.31.9.193-1487007755214:blk_1073743732_2908 len=33554432 Live_repl=3
30. BP-476058346-172.31.9.193-1487007755214:blk_1073743734_2910 len=33554432 Live_repl=3
31. BP-476058346-172.31.9.193-1487007755214:blk_1073743736_2912 len=33554432 Live_repl=3
32. BP-476058346-172.31.9.193-1487007755214:blk_1073743738_2914 len=33554432 Live_repl=3
33. BP-476058346-172.31.9.193-1487007755214:blk_1073743740_2916 len=33554432 Live_repl=3
34. BP-476058346-172.31.9.193-1487007755214:blk_1073743742_2918 len=33554432 Live_repl=3
35. BP-476058346-172.31.9.193-1487007755214:blk_1073743744_2920 len=33554432 Live_repl=3
36. BP-476058346-172.31.9.193-1487007755214:blk_1073743746_2922 len=33554432 Live_repl=3
37. BP-476058346-172.31.9.193-1487007755214:blk_1073743748_2924 len=33554432 Live_repl=3
38. BP-476058346-172.31.9.193-1487007755214:blk_1073743750_2926 len=33554432 Live_repl=3
39. BP-476058346-172.31.9.193-1487007755214:blk_1073743752_2928 len=33554432 Live_repl=3
40. BP-476058346-172.31.9.193-1487007755214:blk_1073743754_2930 len=33554432 Live_repl=3
41. BP-476058346-172.31.9.193-1487007755214:blk_1073743756_2932 len=33554432 Live_repl=3
42. BP-476058346-172.31.9.193-1487007755214:blk_1073743758_2934 len=33554432 Live_repl=3
43. BP-476058346-172.31.9.193-1487007755214:blk_1073743760_2936 len=33554432 Live_repl=3
44. BP-476058346-172.31.9.193-1487007755214:blk_1073743762_2938 len=33554432 Live_repl=3
45. BP-476058346-172.31.9.193-1487007755214:blk_1073743764_2940 len=33554432 Live_repl=3
46. BP-476058346-172.31.9.193-1487007755214:blk_1073743767_2943 len=33554432 Live_repl=3
47. BP-476058346-172.31.9.193-1487007755214:blk_1073743769_2945 len=33554432 Live_repl=3
48. BP-476058346-172.31.9.193-1487007755214:blk_1073743771_2947 len=33554432 Live_repl=3
49. BP-476058346-172.31.9.193-1487007755214:blk_1073743773_2949 len=33554432 Live_repl=3
50. BP-476058346-172.31.9.193-1487007755214:blk_1073743775_2951 len=33554432 Live_repl=3
51. BP-476058346-172.31.9.193-1487007755214:blk_1073743777_2953 len=33554432 Live_repl=3
52. BP-476058346-172.31.9.193-1487007755214:blk_1073743779_2955 len=33554432 Live_repl=3
53. BP-476058346-172.31.9.193-1487007755214:blk_1073743781_2957 len=33554432 Live_repl=3
54. BP-476058346-172.31.9.193-1487007755214:blk_1073743783_2959 len=33554432 Live_repl=3
55. BP-476058346-172.31.9.193-1487007755214:blk_1073743785_2961 len=33554432 Live_repl=3
56. BP-476058346-172.31.9.193-1487007755214:blk_1073743787_2963 len=33554432 Live_repl=3
57. BP-476058346-172.31.9.193-1487007755214:blk_1073743789_2965 len=33554432 Live_repl=3
58. BP-476058346-172.31.9.193-1487007755214:blk_1073743791_2967 len=33554432 Live_repl=3
59. BP-476058346-172.31.9.193-1487007755214:blk_1073743793_2969 len=33554432 Live_repl=3
60. BP-476058346-172.31.9.193-1487007755214:blk_1073743795_2971 len=33554432 Live_repl=3
61. BP-476058346-172.31.9.193-1487007755214:blk_1073743797_2973 len=33554432 Live_repl=3
62. BP-476058346-172.31.9.193-1487007755214:blk_1073743799_2975 len=33554432 Live_repl=3
63. BP-476058346-172.31.9.193-1487007755214:blk_1073743801_2977 len=33554432 Live_repl=3
64. BP-476058346-172.31.9.193-1487007755214:blk_1073743803_2979 len=33554432 Live_repl=3
65. BP-476058346-172.31.9.193-1487007755214:blk_1073743805_2981 len=33554432 Live_repl=3
66. BP-476058346-172.31.9.193-1487007755214:blk_1073743807_2983 len=33554432 Live_repl=3
67. BP-476058346-172.31.9.193-1487007755214:blk_1073743809_2985 len=33554432 Live_repl=3
68. BP-476058346-172.31.9.193-1487007755214:blk_1073743811_2987 len=33554432 Live_repl=3
69. BP-476058346-172.31.9.193-1487007755214:blk_1073743813_2989 len=33554432 Live_repl=3
70. BP-476058346-172.31.9.193-1487007755214:blk_1073743815_2991 len=33554432 Live_repl=3
71. BP-476058346-172.31.9.193-1487007755214:blk_1073743817_2993 len=33554432 Live_repl=3
72. BP-476058346-172.31.9.193-1487007755214:blk_1073743819_2995 len=33554432 Live_repl=3
73. BP-476058346-172.31.9.193-1487007755214:blk_1073743821_2997 len=33554432 Live_repl=3
74. BP-476058346-172.31.9.193-1487007755214:blk_1073743823_2999 len=33554432 Live_repl=3
75. BP-476058346-172.31.9.193-1487007755214:blk_1073743825_3001 len=33554432 Live_repl=3
76. BP-476058346-172.31.9.193-1487007755214:blk_1073743827_3003 len=33554432 Live_repl=3
77. BP-476058346-172.31.9.193-1487007755214:blk_1073743829_3005 len=33554432 Live_repl=3
78. BP-476058346-172.31.9.193-1487007755214:blk_1073743831_3007 len=33554432 Live_repl=3
79. BP-476058346-172.31.9.193-1487007755214:blk_1073743833_3009 len=33554372 Live_repl=3

Status: HEALTHY
 Total size:    2684354500 B
 Total dirs:    0
 Total files:   1
 Total symlinks:                0
 Total blocks (validated):      80 (avg. block size 33554431 B)
 Minimally replicated blocks:   80 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Tue Feb 14 03:00:54 EST 2017 in 4 milliseconds


The filesystem under path '/user/walker/teragen/part-m-00003' is HEALTHY

```

Time result of teragen
```
real    1m51.754s
user    0m4.667s
sys     0m0.271s
```

Run the terasort command
```
[walker@ip-172-31-9-193 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort /user/walker/teragen /user/walker/terasort
17/02/14 16:09:01 INFO terasort.TeraSort: starting
17/02/14 16:09:02 INFO input.FileInputFormat: Total input paths to process : 4
Spent 233ms computing base-splits.
Spent 6ms computing TeraScheduler splits.
Computing input splits took 240ms
Sampling 10 splits of 320
Making 3 from 100000 sampled records
Computing parititions took 903ms
Spent 1146ms computing partitions.
17/02/14 16:09:03 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-9-193.ap-southeast-1.compute.internal/172.31.9.193:8032
17/02/14 16:09:04 INFO mapreduce.JobSubmitter: number of splits:320
17/02/14 16:09:04 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1487039277252_0006
17/02/14 16:09:04 INFO impl.YarnClientImpl: Submitted application application_1487039277252_0006
17/02/14 16:09:04 INFO mapreduce.Job: The url to track the job: http://ip-172-31-9-193.ap-southeast-1.compute.internal:8088/proxy/application_1487039277252_0006/
17/02/14 16:09:04 INFO mapreduce.Job: Running job: job_1487039277252_0006
17/02/14 16:09:10 INFO mapreduce.Job: Job job_1487039277252_0006 running in uber mode : false
17/02/14 16:09:10 INFO mapreduce.Job:  map 0% reduce 0%
17/02/14 16:09:17 INFO mapreduce.Job:  map 1% reduce 0%
17/02/14 16:09:27 INFO mapreduce.Job:  map 2% reduce 0%
17/02/14 16:09:35 INFO mapreduce.Job:  map 3% reduce 0%
17/02/14 16:09:46 INFO mapreduce.Job:  map 4% reduce 0%
17/02/14 16:09:58 INFO mapreduce.Job:  map 5% reduce 0%
17/02/14 16:10:05 INFO mapreduce.Job:  map 6% reduce 0%
17/02/14 16:10:15 INFO mapreduce.Job:  map 7% reduce 0%
17/02/14 16:10:22 INFO mapreduce.Job:  map 8% reduce 0%
17/02/14 16:10:35 INFO mapreduce.Job:  map 9% reduce 0%
17/02/14 16:10:45 INFO mapreduce.Job:  map 10% reduce 0%
17/02/14 16:10:52 INFO mapreduce.Job:  map 11% reduce 0%
17/02/14 16:11:03 INFO mapreduce.Job:  map 12% reduce 0%
17/02/14 16:11:10 INFO mapreduce.Job:  map 13% reduce 0%
17/02/14 16:11:22 INFO mapreduce.Job:  map 14% reduce 0%
17/02/14 16:11:33 INFO mapreduce.Job:  map 15% reduce 0%
17/02/14 16:11:40 INFO mapreduce.Job:  map 16% reduce 0%
17/02/14 16:11:50 INFO mapreduce.Job:  map 17% reduce 0%
17/02/14 16:12:03 INFO mapreduce.Job:  map 18% reduce 0%
17/02/14 16:12:11 INFO mapreduce.Job:  map 19% reduce 0%
17/02/14 16:12:21 INFO mapreduce.Job:  map 20% reduce 0%
17/02/14 16:12:29 INFO mapreduce.Job:  map 21% reduce 0%
17/02/14 16:12:38 INFO mapreduce.Job:  map 22% reduce 0%
17/02/14 16:12:50 INFO mapreduce.Job:  map 23% reduce 0%
17/02/14 16:12:59 INFO mapreduce.Job:  map 24% reduce 0%
17/02/14 16:13:08 INFO mapreduce.Job:  map 25% reduce 0%
17/02/14 16:13:17 INFO mapreduce.Job:  map 26% reduce 0%
17/02/14 16:13:26 INFO mapreduce.Job:  map 27% reduce 0%
17/02/14 16:13:35 INFO mapreduce.Job:  map 28% reduce 0%
17/02/14 16:13:47 INFO mapreduce.Job:  map 29% reduce 0%
17/02/14 16:13:55 INFO mapreduce.Job:  map 30% reduce 0%
17/02/14 16:14:05 INFO mapreduce.Job:  map 31% reduce 0%
17/02/14 16:14:13 INFO mapreduce.Job:  map 32% reduce 0%
17/02/14 16:14:24 INFO mapreduce.Job:  map 33% reduce 0%
17/02/14 16:14:35 INFO mapreduce.Job:  map 34% reduce 0%
17/02/14 16:14:42 INFO mapreduce.Job:  map 35% reduce 0%
17/02/14 16:14:53 INFO mapreduce.Job:  map 36% reduce 0%
17/02/14 16:15:00 INFO mapreduce.Job:  map 37% reduce 0%
17/02/14 16:15:11 INFO mapreduce.Job:  map 38% reduce 0%
17/02/14 16:15:24 INFO mapreduce.Job:  map 39% reduce 0%
17/02/14 16:15:31 INFO mapreduce.Job:  map 40% reduce 0%
17/02/14 16:15:42 INFO mapreduce.Job:  map 41% reduce 0%
17/02/14 16:15:48 INFO mapreduce.Job:  map 42% reduce 0%
17/02/14 16:16:00 INFO mapreduce.Job:  map 43% reduce 0%
17/02/14 16:16:12 INFO mapreduce.Job:  map 44% reduce 0%
17/02/14 16:16:18 INFO mapreduce.Job:  map 45% reduce 0%
17/02/14 16:16:29 INFO mapreduce.Job:  map 46% reduce 0%
17/02/14 16:16:36 INFO mapreduce.Job:  map 47% reduce 0%
17/02/14 16:16:48 INFO mapreduce.Job:  map 48% reduce 0%
17/02/14 16:16:59 INFO mapreduce.Job:  map 49% reduce 0%
17/02/14 16:17:06 INFO mapreduce.Job:  map 50% reduce 0%
17/02/14 16:17:17 INFO mapreduce.Job:  map 51% reduce 0%
17/02/14 16:17:24 INFO mapreduce.Job:  map 52% reduce 0%
17/02/14 16:17:36 INFO mapreduce.Job:  map 53% reduce 0%
17/02/14 16:17:46 INFO mapreduce.Job:  map 54% reduce 0%
17/02/14 16:17:54 INFO mapreduce.Job:  map 55% reduce 0%
17/02/14 16:18:04 INFO mapreduce.Job:  map 56% reduce 0%
17/02/14 16:18:12 INFO mapreduce.Job:  map 57% reduce 0%
17/02/14 16:18:23 INFO mapreduce.Job:  map 58% reduce 0%
17/02/14 16:18:34 INFO mapreduce.Job:  map 59% reduce 0%
17/02/14 16:18:42 INFO mapreduce.Job:  map 60% reduce 0%
17/02/14 16:18:53 INFO mapreduce.Job:  map 61% reduce 0%
17/02/14 16:19:00 INFO mapreduce.Job:  map 62% reduce 0%
17/02/14 16:19:11 INFO mapreduce.Job:  map 63% reduce 0%
17/02/14 16:19:23 INFO mapreduce.Job:  map 64% reduce 0%
17/02/14 16:19:30 INFO mapreduce.Job:  map 65% reduce 0%
17/02/14 16:19:41 INFO mapreduce.Job:  map 66% reduce 0%
17/02/14 16:19:48 INFO mapreduce.Job:  map 67% reduce 0%
17/02/14 16:19:59 INFO mapreduce.Job:  map 68% reduce 0%
17/02/14 16:20:11 INFO mapreduce.Job:  map 69% reduce 0%
17/02/14 16:20:18 INFO mapreduce.Job:  map 70% reduce 0%
17/02/14 16:20:28 INFO mapreduce.Job:  map 71% reduce 0%
17/02/14 16:20:36 INFO mapreduce.Job:  map 72% reduce 0%
17/02/14 16:20:46 INFO mapreduce.Job:  map 73% reduce 0%
17/02/14 16:20:58 INFO mapreduce.Job:  map 74% reduce 0%
17/02/14 16:21:06 INFO mapreduce.Job:  map 75% reduce 0%
17/02/14 16:21:16 INFO mapreduce.Job:  map 76% reduce 0%
17/02/14 16:21:24 INFO mapreduce.Job:  map 77% reduce 0%
17/02/14 16:21:36 INFO mapreduce.Job:  map 78% reduce 0%
17/02/14 16:21:44 INFO mapreduce.Job:  map 79% reduce 0%
17/02/14 16:21:54 INFO mapreduce.Job:  map 80% reduce 0%
17/02/14 16:22:02 INFO mapreduce.Job:  map 81% reduce 0%
17/02/14 16:22:10 INFO mapreduce.Job:  map 81% reduce 3%
17/02/14 16:22:13 INFO mapreduce.Job:  map 81% reduce 4%
17/02/14 16:22:16 INFO mapreduce.Job:  map 81% reduce 5%
17/02/14 16:22:19 INFO mapreduce.Job:  map 81% reduce 6%
17/02/14 16:22:20 INFO mapreduce.Job:  map 82% reduce 6%
17/02/14 16:22:22 INFO mapreduce.Job:  map 82% reduce 7%
17/02/14 16:22:26 INFO mapreduce.Job:  map 82% reduce 8%
17/02/14 16:22:29 INFO mapreduce.Job:  map 82% reduce 9%
17/02/14 16:22:45 INFO mapreduce.Job:  map 83% reduce 9%
17/02/14 16:23:02 INFO mapreduce.Job:  map 84% reduce 9%
17/02/14 16:23:19 INFO mapreduce.Job:  map 85% reduce 9%
17/02/14 16:23:37 INFO mapreduce.Job:  map 86% reduce 9%
17/02/14 16:23:38 INFO mapreduce.Job:  map 86% reduce 10%
17/02/14 16:23:55 INFO mapreduce.Job:  map 87% reduce 10%
17/02/14 16:24:13 INFO mapreduce.Job:  map 88% reduce 10%
17/02/14 16:24:36 INFO mapreduce.Job:  map 89% reduce 10%
17/02/14 16:24:53 INFO mapreduce.Job:  map 90% reduce 10%
17/02/14 16:25:11 INFO mapreduce.Job:  map 91% reduce 10%
17/02/14 16:25:29 INFO mapreduce.Job:  map 92% reduce 10%
17/02/14 16:25:46 INFO mapreduce.Job:  map 93% reduce 10%
17/02/14 16:26:10 INFO mapreduce.Job:  map 94% reduce 10%
17/02/14 16:26:27 INFO mapreduce.Job:  map 95% reduce 10%
17/02/14 16:26:30 INFO mapreduce.Job:  map 95% reduce 11%
17/02/14 16:26:45 INFO mapreduce.Job:  map 96% reduce 11%
17/02/14 16:27:04 INFO mapreduce.Job:  map 97% reduce 11%
17/02/14 16:27:20 INFO mapreduce.Job:  map 98% reduce 11%
17/02/14 16:27:42 INFO mapreduce.Job:  map 99% reduce 11%
17/02/14 16:28:00 INFO mapreduce.Job:  map 100% reduce 11%
17/02/14 16:28:09 INFO mapreduce.Job:  map 100% reduce 22%
17/02/14 16:28:12 INFO mapreduce.Job:  map 100% reduce 23%
17/02/14 16:28:15 INFO mapreduce.Job:  map 100% reduce 24%
17/02/14 16:28:17 INFO mapreduce.Job:  map 100% reduce 27%
17/02/14 16:28:18 INFO mapreduce.Job:  map 100% reduce 28%
17/02/14 16:28:20 INFO mapreduce.Job:  map 100% reduce 29%
17/02/14 16:28:21 INFO mapreduce.Job:  map 100% reduce 30%
17/02/14 16:28:23 INFO mapreduce.Job:  map 100% reduce 31%
17/02/14 16:28:24 INFO mapreduce.Job:  map 100% reduce 32%
17/02/14 16:28:26 INFO mapreduce.Job:  map 100% reduce 33%
17/02/14 16:28:27 INFO mapreduce.Job:  map 100% reduce 34%
17/02/14 16:28:29 INFO mapreduce.Job:  map 100% reduce 35%
17/02/14 16:28:30 INFO mapreduce.Job:  map 100% reduce 36%
17/02/14 16:28:32 INFO mapreduce.Job:  map 100% reduce 37%
17/02/14 16:28:33 INFO mapreduce.Job:  map 100% reduce 38%
17/02/14 16:28:35 INFO mapreduce.Job:  map 100% reduce 39%
17/02/14 16:28:36 INFO mapreduce.Job:  map 100% reduce 40%
17/02/14 16:28:38 INFO mapreduce.Job:  map 100% reduce 41%
17/02/14 16:28:39 INFO mapreduce.Job:  map 100% reduce 42%
17/02/14 16:28:42 INFO mapreduce.Job:  map 100% reduce 44%
17/02/14 16:28:47 INFO mapreduce.Job:  map 100% reduce 56%
17/02/14 16:28:53 INFO mapreduce.Job:  map 100% reduce 60%
17/02/14 16:28:56 INFO mapreduce.Job:  map 100% reduce 62%
17/02/14 16:28:59 INFO mapreduce.Job:  map 100% reduce 64%
17/02/14 16:29:02 INFO mapreduce.Job:  map 100% reduce 66%
17/02/14 16:29:05 INFO mapreduce.Job:  map 100% reduce 68%
17/02/14 16:29:08 INFO mapreduce.Job:  map 100% reduce 70%
17/02/14 16:29:11 INFO mapreduce.Job:  map 100% reduce 72%
17/02/14 16:29:14 INFO mapreduce.Job:  map 100% reduce 74%
17/02/14 16:29:17 INFO mapreduce.Job:  map 100% reduce 75%
17/02/14 16:29:20 INFO mapreduce.Job:  map 100% reduce 77%
17/02/14 16:29:23 INFO mapreduce.Job:  map 100% reduce 78%
17/02/14 16:29:26 INFO mapreduce.Job:  map 100% reduce 89%
17/02/14 16:29:29 INFO mapreduce.Job:  map 100% reduce 90%
17/02/14 16:29:32 INFO mapreduce.Job:  map 100% reduce 91%
17/02/14 16:29:35 INFO mapreduce.Job:  map 100% reduce 92%
17/02/14 16:29:38 INFO mapreduce.Job:  map 100% reduce 93%
17/02/14 16:29:41 INFO mapreduce.Job:  map 100% reduce 94%
17/02/14 16:29:44 INFO mapreduce.Job:  map 100% reduce 95%
17/02/14 16:29:47 INFO mapreduce.Job:  map 100% reduce 96%
17/02/14 16:29:50 INFO mapreduce.Job:  map 100% reduce 97%
17/02/14 16:29:53 INFO mapreduce.Job:  map 100% reduce 98%
17/02/14 16:29:56 INFO mapreduce.Job:  map 100% reduce 99%
17/02/14 16:29:58 INFO mapreduce.Job:  map 100% reduce 100%
17/02/14 16:29:59 INFO mapreduce.Job: Job job_1487039277252_0006 completed successfully
17/02/14 16:30:00 INFO mapreduce.Job: Counters: 50
        File System Counters
                FILE: Number of bytes read=4792378547
                FILE: Number of bytes written=9495045101
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=10737468540
                HDFS: Number of bytes written=10737418300
                HDFS: Number of read operations=969
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=6
        Job Counters 
                Launched map tasks=320
                Launched reduce tasks=3
                Data-local map tasks=318
                Rack-local map tasks=2
                Total time spent by all maps in occupied slots (ms)=1454901
                Total time spent by all reduces in occupied slots (ms)=548943
                Total time spent by all map tasks (ms)=1454901
                Total time spent by all reduce tasks (ms)=548943
                Total vcore-seconds taken by all map tasks=1454901
                Total vcore-seconds taken by all reduce tasks=548943
                Total megabyte-seconds taken by all map tasks=1489818624
                Total megabyte-seconds taken by all reduce tasks=562117632
        Map-Reduce Framework
                Map input records=107374183
                Map output records=107374183
                Map output bytes=10952166666
                Map output materialized bytes=4662738945
                Input split bytes=50240
                Combine input records=0
                Combine output records=0
                Reduce input groups=107374183
                Reduce shuffle bytes=4662738945
                Reduce input records=107374183
                Reduce output records=107374183
                Spilled Records=214748366
                Shuffled Maps =960
                Failed Shuffles=0
                Merged Map outputs=960
                GC time elapsed (ms)=18264
                CPU time spent (ms)=1016180
                Physical memory (bytes) snapshot=153452376064
                Virtual memory (bytes) snapshot=509551509504
                Total committed heap usage (bytes)=158388977664
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters 
                Bytes Read=10737418300
        File Output Format Counters 
                Bytes Written=10737418300
17/02/14 16:30:00 INFO terasort.TeraSort: done
```

Time result of terasort
```
real    20m59.554s
user    0m9.142s
sys     0m0.650s
```
