Create a precious directory in HDFS
```
[hdfs@ip-172-31-9-193 ~]$ hadoop fs -mkdir /precious
```

Copy the ZIP course file into it
```
[hdfs@ip-172-31-9-193 ~]$ hadoop fs -put /tmp/SEBC.zip /precious/
[hdfs@ip-172-31-9-193 ~]$ hadoop fs -ls /precious/
Found 1 items
-rw-r--r--   3 hdfs supergroup     414615 2017-02-14 16:44 /precious/SEBC.zip
```

Enable snapshots for precious
```
[hdfs@ip-172-31-9-193 ~]$ hdfs dfsadmin -allowSnapshot  /precious
Allowing snaphot on /precious succeeded
```

Create a snapshot called sebc-hdfs-test
```
[hdfs@ip-172-31-9-193 ~]$ hadoop fs -createSnapshot /precious sebc-hdfs-test
Created snapshot /precious/.snapshot/sebc-hdfs-test
```

Delete the directory
```
[hdfs@ip-172-31-9-193 ~]$ hadoop fs -rm -r -skipTrash /precious
rm: The directory /precious cannot be deleted since /precious is snapshottable and already has snapshots
```

Delete the ZIP file
```
[hdfs@ip-172-31-9-193 ~]$ hadoop fs -rm /precious/SEBC.zip
```

Restore the deleted file
```
[hdfs@ip-172-31-9-193 ~]$ hadoop fs -ls -R /precious/.snapshot
drwxr-xr-x   - hdfs supergroup          0 2017-02-14 16:53 /precious/.snapshot/sebc-hdfs-test
-rw-r--r--   3 hdfs supergroup     414615 2017-02-14 16:44 /precious/.snapshot/sebc-hdfs-test/SEBC.zip
[hdfs@ip-172-31-9-193 ~]$ hadoop fs -cp /precious/.snapshot/sebc-hdfs-test/SEBC.zip /precious
[hdfs@ip-172-31-9-193 ~]$ hadoop fs -ls /precious
Found 1 items
-rw-r--r--   3 hdfs supergroup     414615 2017-02-14 17:02 /precious/SEBC.zip
```
