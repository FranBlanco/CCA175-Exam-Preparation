# Exec Source

## flume-test1.conf
```Shell
# [cloudera@quickstart ~]$ vi /etc/flume-ng/conf/flume-test1.conf

agent1.sources = exec1
agent1.channels = memory1
agent1.sinks = hdfs1

agent1.sources.exec1.type = exec
agent1.sources.exec1.command = ping google.com

agent1.channels.memory1.type = memory

agent1.sinks.hdfs1.type = hdfs
agent1.sinks.hdfs1.hdfs.path = /user/cloudera/flume/flume-exec-to-hdfs

agent1.sources.exec1.channels = memory1
agent1.sinks.hdfs1.channel = memory1
```

## flume-ng

```Shell

[cloudera@quickstart ~]$ flume-ng agent --conf conf --conf-file flume-test1.conf --name agent1 -Dflume.root.logger=FATAL,console

```

## Data loaded in HDFS
```Shell
[cloudera@quickstart ~]$ hdfs dfs -ls /user/cloudera/flume/flume-exec-to-hdfs
Found 4 items
-rw-r--r--   1 cloudera cloudera       1161 2017-10-29 06:44 /user/cloudera/flume/flume-exec-to-hdfs/FlumeData.1509284677745
-rw-r--r--   1 cloudera cloudera       1205 2017-10-29 06:44 /user/cloudera/flume/flume-exec-to-hdfs/FlumeData.1509284677746
-rw-r--r--   1 cloudera cloudera       1225 2017-10-29 06:45 /user/cloudera/flume/flume-exec-to-hdfs/FlumeData.1509284677747
-rw-r--r--   1 cloudera cloudera       1000 2017-10-29 06:45 /user/cloudera/flume/flume-exec-to-hdfs/FlumeData.1509284677748
```
