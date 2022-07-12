
(base) chchang@chchang-a01 flink-playgrounds % cd table-walkthrough
(base) chchang@chchang-a01 table-walkthrough % docker-compose up
(base) chchang@chchang-a01 table-walkthrough % docker-compose ps
NAME                                 COMMAND                  SERVICE             STATUS              PORTS
table-walkthrough-data-generator-1   "/docker-entrypoint.…"   data-generator      running
table-walkthrough-grafana-1          "/run.sh"                grafana             running             0.0.0.0:3000->3000/tcp
table-walkthrough-jobmanager-1       "/docker-entrypoint.…"   jobmanager          running             0.0.0.0:8082->8081/tcp
table-walkthrough-kafka-1            "start-kafka.sh"         kafka               running             0.0.0.0:9092->9092/tcp
table-walkthrough-mysql-1            "docker-entrypoint.s…"   mysql               running             33060/tcp
table-walkthrough-taskmanager-1      "/docker-entrypoint.…"   taskmanager         running             8081/tcp
table-walkthrough-zookeeper-1        "/bin/sh -c '/usr/sb…"   zookeeper           running             0.0.0.0:2181->2181/tcp
(base) chchang@chchang-a01 table-walkthrough %

(base) chchang@chchang-a01 table-walkthrough % docker-compose exec mysql mysql -Dsql-demo -usql-demo -pdemo-sql
mysql> use sql-demo;
Database changed
mysql> select count(*) from spend_report;
+----------+
| count(*) |
+----------+
|   314777 |
+----------+
1 row in set (0.05 sec)

mysql> select count(*) from spend_report;
+----------+
| count(*) |
+----------+
|   315570 |
+----------+
1 row in set (0.02 sec)

mysql>
mysql> exit;
Bye

(base) chchang@chchang-a01 table-walkthrough % docker-compose down
[+] Running 8/8
 ⠿ Container table-walkthrough-data-generator-1  Removed                            11.1s
 ⠿ Container table-walkthrough-taskmanager-1     Removed                             7.1s
 ⠿ Container table-walkthrough-grafana-1         Removed                             3.4s
 ⠿ Container table-walkthrough-jobmanager-1      Removed                             3.1s
 ⠿ Container table-walkthrough-mysql-1           Removed                             9.6s
 ⠿ Container table-walkthrough-kafka-1           Removed                             8.9s
 ⠿ Container table-walkthrough-zookeeper-1       Removed                            11.1s
 ⠿ Network table-walkthrough_default             Removed                             0.1s

