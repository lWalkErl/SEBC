List the command and output of ls /etc/yum.repos.d
```
[root@ip-172-31-15-79 yum.repos.d]# ls /etc/yum.repos.d
cloudera-manager.repo  mysql-community.repo  redhat.repo  redhat-rhui-client-config.repo  redhat-rhui.repo  rhui-load-balancers.conf
```

Use the scm_prepare_database.sh script to write your db.properties file
```
[root@ip-172-31-15-79 ~]# /usr/share/cmf/schema/scm_prepare_database.sh mysql -h ip-172-31-5-240.ap-southeast-1.compute.internal scm scm scmdb
JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.7.0_67-cloudera/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!
```
