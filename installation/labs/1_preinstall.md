Check vm.swappiness on all your nodes
```
[root@ip-172-31-8-231 ~]# cat /proc/sys/vm/swappiness
30
## Temporarily change it by issuing
[root@ip-172-31-8-231 ~]# sysctl vm.swappiness=1
vm.swappiness = 1
## And then set the value permanently
[root@ip-172-31-8-231 ~]# vi /etc/sysctl.conf
# sysctl settings are defined through files in
# /usr/lib/sysctl.d/, /run/sysctl.d/, and /etc/sysctl.d/.
#
# Vendors settings live in /usr/lib/sysctl.d/.
# To override a whole file, create a new file with the same in
# /etc/sysctl.d/ and put new settings there. To override
# only specific settings, add a file with a lexically later
# name in /etc/sysctl.d/ and put new settings there.
#
# For more information, see sysctl.conf(5) and sysctl.d(5).
vm.swappiness=1
## check the value again
[root@ip-172-31-8-231 ~]# cat /proc/sys/vm/swappiness
1
```

Show the mount attributes of all volumes
```
[root@ip-172-31-8-231 ~]# df -h 
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2      100G  985M  100G   1% /
devtmpfs        3.9G     0  3.9G   0% /dev
tmpfs           3.7G     0  3.7G   0% /dev/shm
tmpfs           3.7G   17M  3.7G   1% /run
tmpfs           3.7G     0  3.7G   0% /sys/fs/cgroup
tmpfs           757M     0  757M   0% /run/user/1000
tmpfs           757M     0  757M   0% /run/user/0
```

Show the reserve space of any non-root, ext-based volumes
fro this case i can't separate root and non-root because my system create 1 disk on each instance 
```
[root@ip-172-31-8-231 ~]# cat /etc/fstab

#
# /etc/fstab
# Created by anaconda on Thu Oct 20 12:47:25 2016
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=3ed41454-00c8-4803-bf61-2ee88aa54dbf /                       xfs     defaults        0 0
```

Disable transparent hugepages
```
[root@ip-172-31-8-231 /]# cat  /sys/kernel/mm/transparent_hugepage/enabled 
[always] madvise never
[root@ip-172-31-8-231 /]# cat /sys/kernel/mm/transparent_hugepage/defrag
[always] madvise never
## Temporarily disable transparent hugepages by issuing
[root@ip-172-31-8-231 /]# echo never > /sys/kernel/mm/transparent_hugepage/enabled
[root@ip-172-31-8-231 /]# echo never > /sys/kernel/mm/transparent_hugepage/defrag 
## Set the command to disable transparent hugepages when restart server
[root@ip-172-31-8-231 /]# vi /etc/rc.local
#!/bin/bash
# THIS FILE IS ADDED FOR COMPATIBILITY PURPOSES
#
# It is highly advisable to create own systemd services or udev rules
# to run scripts during boot instead of using this file.
#
# In contrast to previous versions due to parallel execution during boot
# this script will NOT be run after all other services.
#
# Please note that you must run 'chmod +x /etc/rc.d/rc.local' to ensure
# that this script will be executed during boot.

touch /var/lock/subsys/local
echo never > /sys/kernel/mm/transparent_hugepage/enabled
echo never > /sys/kernel/mm/transparent_hugepage/defrag
## Check the value of transparent hugepages again
[root@ip-172-31-8-231 /]# cat  /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]
[root@ip-172-31-8-231 /]# cat  /sys/kernel/mm/transparent_hugepage/defrag 
always madvise [never]
```

List your network interface configuration
```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
        inet 172.31.8.231  netmask 255.255.240.0  broadcast 172.31.15.255
        inet6 fe80::f5:4dff:fe4e:9f03  prefixlen 64  scopeid 0x20<link>
        ether 02:f5:4d:4e:9f:03  txqueuelen 1000  (Ethernet)
        RX packets 7979  bytes 729861 (712.7 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7089  bytes 1365531 (1.3 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 68  bytes 6420 (6.2 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 68  bytes 6420 (6.2 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

List forward and reverse host lookups using getent or nslookup
```
[root@ip-172-31-8-231 /]# getent hosts 172.31.8.231
172.31.8.231    ip-172-31-8-231.ap-southeast-1.compute.internal
```

Show the nscd service is running
```
[root@ip-172-31-8-231 /]# systemctl status nscd
Unit nscd.service could not be found.
## The service not found so i will install this service
[root@ip-172-31-8-231 /]# yum list nscd
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
rhui-REGION-client-config-server-7                                                                               | 2.9 kB  00:00:00     
rhui-REGION-rhel-server-releases                                                                                 | 3.5 kB  00:00:00     
rhui-REGION-rhel-server-rh-common                                                                                | 3.8 kB  00:00:00     
(1/7): rhui-REGION-client-config-server-7/x86_64/primary_db                                                      | 5.4 kB  00:00:00     
(2/7): rhui-REGION-rhel-server-rh-common/7Server/x86_64/group                                                    |  104 B  00:00:00     
(3/7): rhui-REGION-rhel-server-releases/7Server/x86_64/updateinfo                                                | 1.8 MB  00:00:00     
(4/7): rhui-REGION-rhel-server-releases/7Server/x86_64/group                                                     | 701 kB  00:00:00     
(5/7): rhui-REGION-rhel-server-rh-common/7Server/x86_64/primary_db                                               | 110 kB  00:00:00     
(6/7): rhui-REGION-rhel-server-rh-common/7Server/x86_64/updateinfo                                               |  29 kB  00:00:00     
(7/7): rhui-REGION-rhel-server-releases/7Server/x86_64/primary_db                                                |  33 MB  00:00:01     
Available Packages
nscd.x86_64                                      2.17-157.el7_3.1                                       rhui-REGION-rhel-server-releases
[root@ip-172-31-8-231 /]# yum install nscd
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
Resolving Dependencies
--> Running transaction check
---> Package nscd.x86_64 0:2.17-157.el7_3.1 will be installed
--> Processing Dependency: glibc = 2.17-157.el7_3.1 for package: nscd-2.17-157.el7_3.1.x86_64
--> Running transaction check
---> Package glibc.x86_64 0:2.17-157.el7 will be updated
--> Processing Dependency: glibc = 2.17-157.el7 for package: glibc-common-2.17-157.el7.x86_64
---> Package glibc.x86_64 0:2.17-157.el7_3.1 will be an update
--> Running transaction check
---> Package glibc-common.x86_64 0:2.17-157.el7 will be updated
---> Package glibc-common.x86_64 0:2.17-157.el7_3.1 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================================
 Package                    Arch                 Version                           Repository                                      Size
========================================================================================================================================
Installing:
 nscd                       x86_64               2.17-157.el7_3.1                  rhui-REGION-rhel-server-releases               267 k
Updating for dependencies:
 glibc                      x86_64               2.17-157.el7_3.1                  rhui-REGION-rhel-server-releases               3.6 M
 glibc-common               x86_64               2.17-157.el7_3.1                  rhui-REGION-rhel-server-releases                11 M

Transaction Summary
========================================================================================================================================
Install  1 Package
Upgrade             ( 2 Dependent packages)

Total download size: 15 M
Is this ok [y/d/N]: y
Downloading packages:
Delta RPMs disabled because /usr/bin/applydeltarpm not installed.
(1/3): nscd-2.17-157.el7_3.1.x86_64.rpm                                                                          | 267 kB  00:00:00     
(2/3): glibc-common-2.17-157.el7_3.1.x86_64.rpm                                                                  |  11 MB  00:00:00     
(3/3): glibc-2.17-157.el7_3.1.x86_64.rpm                                                                         | 3.6 MB  00:00:00     
----------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                    29 MB/s |  15 MB  00:00:00     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Updating   : glibc-common-2.17-157.el7_3.1.x86_64                                                                                 1/5 
  Updating   : glibc-2.17-157.el7_3.1.x86_64                                                                                        2/5 
warning: /etc/nsswitch.conf created as /etc/nsswitch.conf.rpmnew
  Installing : nscd-2.17-157.el7_3.1.x86_64                                                                                         3/5 
  Cleanup    : glibc-common-2.17-157.el7.x86_64                                                                                     4/5 
  Cleanup    : glibc-2.17-157.el7.x86_64                                                                                            5/5 
  Verifying  : glibc-2.17-157.el7_3.1.x86_64                                                                                        1/5 
  Verifying  : nscd-2.17-157.el7_3.1.x86_64                                                                                         2/5 
  Verifying  : glibc-common-2.17-157.el7_3.1.x86_64                                                                                 3/5 
  Verifying  : glibc-common-2.17-157.el7.x86_64                                                                                     4/5 
  Verifying  : glibc-2.17-157.el7.x86_64                                                                                            5/5 

Installed:
  nscd.x86_64 0:2.17-157.el7_3.1                                                                                                        

Dependency Updated:
  glibc.x86_64 0:2.17-157.el7_3.1                                 glibc-common.x86_64 0:2.17-157.el7_3.1                                

Complete!
## Start nscd service
[root@ip-172-31-8-231 /]# systemctl start nscd
[root@ip-172-31-8-231 /]# systemctl status nscd
โ— nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-02-13 03:53:03 EST; 3s ago
  Process: 3559 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 3560 (nscd)
   CGroup: /system.slice/nscd.service
           โ””โ”€3560 /usr/sbin/nscd

Feb 13 03:53:03 ip-172-31-8-231.ap-southeast-1.compute.internal nscd[3560]: 3560 monitoring file `/etc/hosts` (4)
Feb 13 03:53:03 ip-172-31-8-231.ap-southeast-1.compute.internal nscd[3560]: 3560 monitoring directory `/etc` (2)
Feb 13 03:53:03 ip-172-31-8-231.ap-southeast-1.compute.internal nscd[3560]: 3560 monitoring file `/etc/resolv.conf` (5)
Feb 13 03:53:03 ip-172-31-8-231.ap-southeast-1.compute.internal nscd[3560]: 3560 monitoring directory `/etc` (2)
Feb 13 03:53:03 ip-172-31-8-231.ap-southeast-1.compute.internal nscd[3560]: 3560 monitoring file `/etc/services` (6)
Feb 13 03:53:03 ip-172-31-8-231.ap-southeast-1.compute.internal nscd[3560]: 3560 monitoring directory `/etc` (2)
Feb 13 03:53:03 ip-172-31-8-231.ap-southeast-1.compute.internal nscd[3560]: 3560 disabled inotify-based monitoring for file `/etc/...ory
Feb 13 03:53:03 ip-172-31-8-231.ap-southeast-1.compute.internal nscd[3560]: 3560 stat failed for file `/etc/netgroup'; will try ag...ory
Feb 13 03:53:03 ip-172-31-8-231.ap-southeast-1.compute.internal nscd[3560]: 3560 Access Vector Cache (AVC) started
Feb 13 03:53:03 ip-172-31-8-231.ap-southeast-1.compute.internal systemd[1]: Started Name Service Cache Daemon.
Hint: Some lines were ellipsized, use -l to show in full.

## Enable auto start service
[root@ip-172-31-8-231 /]# systemctl enable nscd
Created symlink from /etc/systemd/system/multi-user.target.wants/nscd.service to /usr/lib/systemd/system/nscd.service.
Created symlink from /etc/systemd/system/sockets.target.wants/nscd.socket to /usr/lib/systemd/system/nscd.socket.
[root@ip-172-31-8-231 /]# systemctl list-unit-files |grep nscd
nscd.service                                enabled 
nscd.socket                                 enabled 
```

Show the ntpd service is running
```
[root@ip-172-31-8-231 /]# systemctl status ntpd
Unit ntpd.service could not be found.
## The service not found so i will install this service
[root@ip-172-31-8-231 /]# yum list ntp
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
Available Packages
ntp.x86_64                                      4.2.6p5-25.el7_3.1                                      rhui-REGION-rhel-server-releases
[root@ip-172-31-8-231 /]# yum install ntp
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
Resolving Dependencies
--> Running transaction check
---> Package ntp.x86_64 0:4.2.6p5-25.el7_3.1 will be installed
--> Processing Dependency: ntpdate = 4.2.6p5-25.el7_3.1 for package: ntp-4.2.6p5-25.el7_3.1.x86_64
--> Processing Dependency: libopts.so.25()(64bit) for package: ntp-4.2.6p5-25.el7_3.1.x86_64
--> Running transaction check
---> Package autogen-libopts.x86_64 0:5.18-5.el7 will be installed
---> Package ntpdate.x86_64 0:4.2.6p5-25.el7_3.1 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================================
 Package                      Arch                Version                           Repository                                     Size
========================================================================================================================================
Installing:
 ntp                          x86_64              4.2.6p5-25.el7_3.1                rhui-REGION-rhel-server-releases              547 k
Installing for dependencies:
 autogen-libopts              x86_64              5.18-5.el7                        rhui-REGION-rhel-server-releases               66 k
 ntpdate                      x86_64              4.2.6p5-25.el7_3.1                rhui-REGION-rhel-server-releases               85 k

Transaction Summary
========================================================================================================================================
Install  1 Package (+2 Dependent packages)

Total download size: 699 k
Installed size: 1.6 M
Is this ok [y/d/N]: y
Downloading packages:
(1/3): ntp-4.2.6p5-25.el7_3.1.x86_64.rpm                                                                         | 547 kB  00:00:00     
(2/3): autogen-libopts-5.18-5.el7.x86_64.rpm                                                                     |  66 kB  00:00:00     
(3/3): ntpdate-4.2.6p5-25.el7_3.1.x86_64.rpm                                                                     |  85 kB  00:00:00     
----------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                   1.3 MB/s | 699 kB  00:00:00     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : autogen-libopts-5.18-5.el7.x86_64                                                                                    1/3 
  Installing : ntpdate-4.2.6p5-25.el7_3.1.x86_64                                                                                    2/3 
  Installing : ntp-4.2.6p5-25.el7_3.1.x86_64                                                                                        3/3 
  Verifying  : ntpdate-4.2.6p5-25.el7_3.1.x86_64                                                                                    1/3 
  Verifying  : ntp-4.2.6p5-25.el7_3.1.x86_64                                                                                        2/3 
  Verifying  : autogen-libopts-5.18-5.el7.x86_64                                                                                    3/3 

Installed:
  ntp.x86_64 0:4.2.6p5-25.el7_3.1                                                                                                       

Dependency Installed:
  autogen-libopts.x86_64 0:5.18-5.el7                                ntpdate.x86_64 0:4.2.6p5-25.el7_3.1                               

Complete!
## Start ntpd service
[root@ip-172-31-8-231 /]# systemctl start ntpd
[root@ip-172-31-8-231 /]# systemctl status ntpd
โ— ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-02-13 03:57:50 EST; 5s ago
  Process: 3638 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 3639 (ntpd)
   CGroup: /system.slice/ntpd.service
           โ””โ”€3639 /usr/sbin/ntpd -u ntp:ntp -g

Feb 13 03:57:50 ip-172-31-8-231.ap-southeast-1.compute.internal ntpd[3639]: Listen and drop on 1 v6wildcard :: UDP 123
Feb 13 03:57:50 ip-172-31-8-231.ap-southeast-1.compute.internal ntpd[3639]: Listen normally on 2 lo 127.0.0.1 UDP 123
Feb 13 03:57:50 ip-172-31-8-231.ap-southeast-1.compute.internal ntpd[3639]: Listen normally on 3 eth0 172.31.8.231 UDP 123
Feb 13 03:57:50 ip-172-31-8-231.ap-southeast-1.compute.internal ntpd[3639]: Listen normally on 4 lo ::1 UDP 123
Feb 13 03:57:50 ip-172-31-8-231.ap-southeast-1.compute.internal ntpd[3639]: Listen normally on 5 eth0 fe80::f5:4dff:fe4e:9f03 UDP 123
Feb 13 03:57:50 ip-172-31-8-231.ap-southeast-1.compute.internal ntpd[3639]: Listening on routing socket on fd #22 for interface updates
Feb 13 03:57:50 ip-172-31-8-231.ap-southeast-1.compute.internal systemd[1]: Started Network Time Service.
Feb 13 03:57:51 ip-172-31-8-231.ap-southeast-1.compute.internal ntpd[3639]: 0.0.0.0 c016 06 restart
Feb 13 03:57:51 ip-172-31-8-231.ap-southeast-1.compute.internal ntpd[3639]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
Feb 13 03:57:51 ip-172-31-8-231.ap-southeast-1.compute.internal ntpd[3639]: 0.0.0.0 c011 01 freq_not_set
Hint: Some lines were ellipsized, use -l to show in full.

## Enable auto start service
systemctl enable ntpd
[root@ip-172-31-8-231 /]# systemctl enable ntpd
Created symlink from /etc/systemd/system/multi-user.target.wants/ntpd.service to /usr/lib/systemd/system/ntpd.service.
[root@ip-172-31-8-231 /]# systemctl list-unit-files |grep ntpd
ntpd.service                                enabled 
```

Disable selinux
```
[root@ip-172-31-8-231 ssh]# vi /etc/sysconfig/selinux

# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
SELINUX=disabled
# SELINUXTYPE= can take one of three two values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected.
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted
## Temporarily change it by issuing
[root@ip-172-31-8-231 ~]# setenforce 0
```

Setting ulimit
```
## Add nofile and nproc in file /etc/security/limits.conf
[root@ip-172-31-8-231 ~]# vi /etc/security/limits.conf
#<domain>      <type>  <item>         <value>
#

* - nofile 32768
* - nproc 65536

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#@student        -       maxlogins       4

# End of file
[root@ip-172-31-8-231 ~]# ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 31136
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 32768
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 65536
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```
