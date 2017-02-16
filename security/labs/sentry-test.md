Use beeline to confirm your principal sees no tables
```
Beeline version 1.1.0-cdh5.8.2 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM
Enter username for jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM: walker
Enter password for jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.2)
Driver: Hive JDBC (version 1.1.0-cdh5.8.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-9-193.ap-southeast-> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20170216170606_87a639ca-fef7-4303-b27c-036058d42d2e): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170216170606_87a639ca-fef7-4303-b27c-036058d42d2e); Time taken: 0.07 seconds
INFO  : Executing command(queryId=hive_20170216170606_87a639ca-fef7-4303-b27c-036058d42d2e): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170216170606_87a639ca-fef7-4303-b27c-036058d42d2e); Time taken: 0.136 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
```

kinit as george, login to beeline, and use SHOW TABLES;
```
[george@ip-172-31-8-231 ~]$ beeline
Beeline version 1.1.0-cdh5.8.2 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM
Enter username for jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM: george
Enter password for jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.2)
Driver: Hive JDBC (version 1.1.0-cdh5.8.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-9-193.ap-southeast-> show tables;
INFO  : Compiling command(queryId=hive_20170216172626_9fac1d8c-056a-4b24-9578-e62210a29347): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170216172626_9fac1d8c-056a-4b24-9578-e62210a29347); Time taken: 0.065 seconds
INFO  : Executing command(queryId=hive_20170216172626_9fac1d8c-056a-4b24-9578-e62210a29347): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170216172626_9fac1d8c-056a-4b24-9578-e62210a29347); Time taken: 0.128 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.289 seconds)
```

Repeat the process as ferdinand
```
[ferdinand@ip-172-31-8-231 ~]$ kinit
Password for ferdinand@WALKER.COM: 
[ferdinand@ip-172-31-8-231 ~]$ beeline 
Beeline version 1.1.0-cdh5.8.2 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM
Enter username for jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM: ferdinand
Enter password for jdbc:hive2://ip-172-31-9-193.ap-southeast-1.compute.internal:10000/default;principal=hive/ip-172-31-9-193.ap-southeast-1.compute.internal@WALKER.COM: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.2)
Driver: Hive JDBC (version 1.1.0-cdh5.8.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-9-193.ap-southeast-> show tables;
INFO  : Compiling command(queryId=hive_20170216172828_ef4e81c0-563a-4947-aba7-a4927cae9188): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170216172828_ef4e81c0-563a-4947-aba7-a4927cae9188); Time taken: 0.062 seconds
INFO  : Executing command(queryId=hive_20170216172828_ef4e81c0-563a-4947-aba7-a4927cae9188): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170216172828_ef4e81c0-563a-4947-aba7-a4927cae9188); Time taken: 0.129 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.289 seconds)
0: jdbc:hive2://ip-172-31-9-193.ap-southeast-> 
```
