Slowest
```
Testing loop started on Wed Feb 15 15:23:34 SGT 2017

List parameters of teragen
Mapper containers = 30
Container memory = 2024
mapper JVM heap = 1619

real    2m3.910s
user    0m4.989s
sys     0m0.265s

List parameters of terasort
Reducer containers = 10
Container memory = 2024
mapper JVM heap = 1619
reducer JVM heap = 1619

real    5m47.409s
user    0m7.029s
sys     0m0.373s
Deleted /results/tg-10GB-30-10-2024
Deleted /results/ts-10GB-30-10-2024
Testing loop ended on Wed Feb 15 15:31:30 SGT 2017
```

Fastest
```
Testing loop started on Wed Feb 15 13:43:28 SGT 2017

List parameters of teragen
Mapper containers = 4
Container memory = 1024
mapper JVM heap = 819

real    1m9.572s
user    0m4.764s
sys     0m0.258s

List parameters of terasort
Reducer containers = 2
Container memory = 1024
mapper JVM heap = 819
reducer JVM heap = 409

real    4m8.035s
user    0m6.606s
sys     0m0.355s
Deleted /results/tg-10GB-4-2-1024
Deleted /results/ts-10GB-4-2-1024
Testing loop ended on Wed Feb 15 13:48:50 SGT 2017
```
