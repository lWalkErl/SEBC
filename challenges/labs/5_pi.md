Run the Hadoop pi program as the user fullerton
```
[fullerton@ip-172-31-5-240 ~]$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar pi 10 100
Number of Maps  = 10
Samples per Map = 100
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Starting Job
17/02/17 15:50:10 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-5-240.ap-southeast-1.compute.internal/172.31.5.240:8032
17/02/17 15:50:10 INFO hdfs.DFSClient: Created token for fullerton: HDFS_DELEGATION_TOKEN owner=fullerton@WALKER.SG, renewer=yarn, realUser=, issueDate=1487317810862, maxDate=1487922610862, sequenceNumber=2, masterKeyId=2 on 172.31.5.240:8020
17/02/17 15:50:10 INFO security.TokenCache: Got dt for hdfs://ip-172-31-5-240.ap-southeast-1.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.5.240:8020, Ident: (token for fullerton: HDFS_DELEGATION_TOKEN owner=fullerton@WALKER.SG, renewer=yarn, realUser=, issueDate=1487317810862, maxDate=1487922610862, sequenceNumber=2, masterKeyId=2)
17/02/17 15:50:11 INFO input.FileInputFormat: Total input paths to process : 10
17/02/17 15:50:11 INFO mapreduce.JobSubmitter: number of splits:10
17/02/17 15:50:11 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1487317300275_0002
17/02/17 15:50:11 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.5.240:8020, Ident: (token for fullerton: HDFS_DELEGATION_TOKEN owner=fullerton@WALKER.SG, renewer=yarn, realUser=, issueDate=1487317810862, maxDate=1487922610862, sequenceNumber=2, masterKeyId=2)
17/02/17 15:50:12 INFO impl.YarnClientImpl: Submitted application application_1487317300275_0002
17/02/17 15:50:12 INFO mapreduce.Job: The url to track the job: http://ip-172-31-5-240.ap-southeast-1.compute.internal:8088/proxy/application_1487317300275_0002/
17/02/17 15:50:12 INFO mapreduce.Job: Running job: job_1487317300275_0002
```
