Add the first line from your server log
```
[root@ip-172-31-15-79 ~]# head -1 /var/log/cloudera-scm-server/cloudera-scm-server.log
2017-02-17 14:37:52,042 INFO main:com.cloudera.server.cmf.Main: Starting SCM Server. JVM Args: [-Dlog4j.configuration=file:/etc/cloudera-scm-server/log4j.properties, -Dfile.encoding=UTF-8, -Dcmf.root.logger=INFO,LOGFILE, -Dcmf.log.dir=/var/log/cloudera-scm-server, -Dcmf.log.file=cloudera-scm-server.log, -Dcmf.jetty.threshhold=WARN, -Dcmf.schema.dir=/usr/share/cmf/schema, -Djava.awt.headless=true, -Djava.net.preferIPv4Stack=true, -Dpython.home=/usr/share/cmf/python, -XX:+UseConcMarkSweepGC, -XX:+UseParNewGC, -XX:+HeapDumpOnOutOfMemoryError, -Xmx2G, -XX:MaxPermSize=256m, -XX:+HeapDumpOnOutOfMemoryError, -XX:HeapDumpPath=/tmp, -XX:OnOutOfMemoryError=kill -9 %p], Args: [], Version: 5.10.0 (#85 built by jenkins on 20170120-1037 git: aa0b5cd5eceaefe2f971c13ab657020d96bb842a)
```

Add the log line that contains the phrase "Started Jetty server"
```
[root@ip-172-31-15-79 ~]# cat /var/log/cloudera-scm-server/cloudera-scm-server.log |grep "Started Jetty server"
2017-02-17 14:39:07,367 INFO WebServerImpl:com.cloudera.server.cmf.WebServerImpl: Started Jetty server.
```

File db.properties
```
# Auto-generated by scm_prepare_database.sh on Fri Feb 17 14:32:49 SGT 2017
#
# For information describing how to configure the Cloudera Manager Server
# to connect to databases, see the "Cloudera Manager Installation Guide."
#
com.cloudera.cmf.db.type=mysql
com.cloudera.cmf.db.host=ip-172-31-5-240.ap-southeast-1.compute.internal
com.cloudera.cmf.db.name=scm
com.cloudera.cmf.db.user=scm
com.cloudera.cmf.db.setupType=EXTERNAL
com.cloudera.cmf.db.password=scmdb
```
