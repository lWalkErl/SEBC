The kinit command you use to authenticate your test user
```
[walker@ip-172-31-8-231 ~]$ kinit cloudera-scm
Password for cloudera-scm@WALKER.COM: 
```

The output from a klist command listing your credentials and ticket lifetime
```
[walker@ip-172-31-8-231 ~]$ klist
Ticket cache: FILE:/tmp/krb5cc_1001
Default principal: cloudera-scm@WALKER.COM

Valid starting       Expires              Service principal
02/16/2017 13:00:31  02/17/2017 13:00:31  krbtgt/WALKER.COM@WALKER.COM
        renew until 02/23/2017 13:00:31
```
