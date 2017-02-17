Command and output for hdfs dfs -ls /user
```
[hdfs@ip-172-31-5-240 ~]$ hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - hdfs   supergroup          0 2017-02-17 15:03 /user/fullerton
drwxrwxrwx   - mapred hadoop              0 2017-02-17 15:01 /user/history
drwxrwxr-t   - hive   hive                0 2017-02-17 15:01 /user/hive
drwxrwxr-x   - hue    hue                 0 2017-02-17 15:02 /user/hue
drwxrwxr-x   - oozie  oozie               0 2017-02-17 15:02 /user/oozie
drwxr-xr-x   - hdfs   supergroup          0 2017-02-17 15:03 /user/raffles
```

The output from the CM API call ../api/v14/hosts
```
[root@ip-172-31-15-79 .ssh]# curl -u admin:admin 'http://172.31.15.79:7180/api/v14/hosts'
{
  "items" : [ {
    "hostId" : "da7e4c79-f7a1-4b30-8e72-da32ba806609",
    "ipAddress" : "172.31.10.84",
    "hostname" : "ip-172-31-10-84.ap-southeast-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-15-79.ap-southeast-1.compute.internal:7180/cmf/hostRedirect/da7e4c79-f7a1-4b30-8e72-da32ba806609",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 2,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 7933206528
  }, {
    "hostId" : "0498fc68-9760-4ce8-9d5b-31475612c04b",
    "ipAddress" : "172.31.11.191",
    "hostname" : "ip-172-31-11-191.ap-southeast-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-15-79.ap-southeast-1.compute.internal:7180/cmf/hostRedirect/0498fc68-9760-4ce8-9d5b-31475612c04b",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 2,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 7933206528
  }, {
    "hostId" : "9c9def8c-e081-4ffb-99e7-4db2b26299ee",
    "ipAddress" : "172.31.15.79",
    "hostname" : "ip-172-31-15-79.ap-southeast-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-15-79.ap-southeast-1.compute.internal:7180/cmf/hostRedirect/9c9def8c-e081-4ffb-99e7-4db2b26299ee",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 2,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 7933206528
  }, {
    "hostId" : "97d5b8a4-14d2-41fb-b631-ba0a9b68c8c0",
    "ipAddress" : "172.31.5.177",
    "hostname" : "ip-172-31-5-177.ap-southeast-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-15-79.ap-southeast-1.compute.internal:7180/cmf/hostRedirect/97d5b8a4-14d2-41fb-b631-ba0a9b68c8c0",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 2,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 7933206528
  }, {
    "hostId" : "c8064bd3-36d0-4d77-9576-54e977b747b0",
    "ipAddress" : "172.31.5.240",
    "hostname" : "ip-172-31-5-240.ap-southeast-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-15-79.ap-southeast-1.compute.internal:7180/cmf/hostRedirect/c8064bd3-36d0-4d77-9576-54e977b747b0",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 2,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 7933206528
  } ]
}
```
