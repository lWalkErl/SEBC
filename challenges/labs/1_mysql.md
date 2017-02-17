The hostname of your MySQL node
```
[root@ip-172-31-5-240 run]# hostname
ip-172-31-5-240.ap-southeast-1.compute.internal
```

The command and output for mysql --version
```
[root@ip-172-31-5-240 run]# mysql --version
mysql  Ver 15.1 Distrib 5.5.54-MariaDB, for Linux (x86_64) using readline 5.1
```

The command and output for listing MySQL databases
```

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)
```
