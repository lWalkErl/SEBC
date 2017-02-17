List the Linux release you have chosen
```
[root@ip-172-31-15-79 ~]# cat /etc/redhat-release 
Red Hat Enterprise Linux Server release 7.3 (Maipo)
```

Show that the disk space on each node is at least 30 GB
```
/dev/xvda2      100G  1.3G   99G   2% /
[root@ip-172-31-15-79 ~]# ssh ip-172-31-15-79.ap-southeast-1.compute.internal "df -h |grep /dev/xvda2"
/dev/xvda2      100G  1.3G   99G   2% /
[root@ip-172-31-15-79 ~]# ssh ip-172-31-5-240.ap-southeast-1.compute.internal "df -h |grep /dev/xvda2"
/dev/xvda2      100G  1.3G   99G   2% /
[root@ip-172-31-15-79 ~]# ssh ip-172-31-11-191.ap-southeast-1.compute.internal "df -h |grep /dev/xvda2"
/dev/xvda2      100G  1.3G   99G   2% /
[root@ip-172-31-15-79 ~]# ssh ip-172-31-10-84.ap-southeast-1.compute.internal "df -h |grep /dev/xvda2"
/dev/xvda2      100G  1.3G   99G   2% /
[root@ip-172-31-15-79 ~]# ssh ip-172-31-5-177.ap-southeast-1.compute.internal "df -h |grep /dev/xvda2"
/dev/xvda2      100G  1.3G   99G   2% /
```

List the command and output for yum repolist enabled
```
[root@ip-172-31-15-79 ~]# yum repolist enabled
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                                    repo name                                                                 status
rhui-REGION-client-config-server-7/x86_64                  Red Hat Update Infrastructure 2.0 Client Configuration Server 7                6
rhui-REGION-rhel-server-releases/7Server/x86_64            Red Hat Enterprise Linux Server 7 (RPMs)                                  13,838
rhui-REGION-rhel-server-rh-common/7Server/x86_64           Red Hat Enterprise Linux Server 7 RH Common (RPMs)                           209
repolist: 14,053
```

List the /etc/passwd entries for raffles and fullerton in your setup file
```
[root@ip-172-31-15-79 ~]# cat /etc/passwd |grep raffles
raffles:x:2000:1002::/home/raffles:/bin/bash
[root@ip-172-31-15-79 ~]# cat /etc/passwd |grep fullerton
fullerton:x:3000:1001::/home/fullerton:/bin/bash
```

List the /etc/group entries for hotels and shops in your setup file
```
[root@ip-172-31-15-79 ~]# cat /etc/group |grep hotels
hotels:x:1001:
[root@ip-172-31-15-79 ~]# cat /etc/group |grep shops
shops:x:1002:
```
