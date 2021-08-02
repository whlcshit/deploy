# hugegraph按照说明

* 以安装HugeGraph-Server 0.11.2为例


## 下载

components | version | 百度网盘下载地址
---|---|---
HugeGraph-Server | 0.11.2 | 链接: https://pan.baidu.com/s/1FB-suEuYJzZEtLdDYRDzvw  密码: nrwo

## 安装步骤

* 环境

```
[root@iZ2ze1a67q38izs9eq9w39Z hugegraph-0.11.2]# lsb_release -a
LSB Version:	:core-4.1-amd64:core-4.1-noarch
Distributor ID:	CentOS
Description:	CentOS Linux release 7.5.1804 (Core)
Release:	7.5.1804
Codename:	Core
```
* 依赖

  * lsof
```
yum install lsof -y
```
* 安装目录
```
cd /root/wanghonglin/deploy/hugegraph
```

* 将下载的HugeGraph-Server 0.11.2 放到安装目录中
```
[root@iZ2ze1a67q38izs9eq9w39Z hugegraph]# ls -lrth
总用量 200M
-rw-r--r-- 1 root root 200M 8月   2 20:50 hugegraph-0.11.2.tar.gz
```

* 解压
```
tar -zxvf hugegraph-0.11.2.tar.gz

[root@iZ2ze1a67q38izs9eq9w39Z hugegraph]# ls -lrth
总用量 200M
drwxr-xr-x 7  501 games 4.0K 11月 25 2020 hugegraph-0.11.2
-rw-r--r-- 1 root root  200M 8月   2 20:50 hugegraph-0.11.2.tar.gz
```

* 新建logs目录
```
cd /root/wanghonglin/deploy/hugegraph/hugegraph-0.11.2

[root@iZ2ze1a67q38izs9eq9w39Z hugegraph-0.11.2]# mkdir logs
[root@iZ2ze1a67q38izs9eq9w39Z hugegraph-0.11.2]# ls -lrth
总用量 32K
drwxr-xr-x 2  501 games 4.0K 8月   2 20:53 scripts
drwxr-xr-x 2  501 games  12K 8月   2 20:53 lib
drwxr-xr-x 2  501 games 4.0K 8月   2 20:53 ext
drwxr-xr-x 2  501 games 4.0K 8月   2 20:55 conf
drwxr-xr-x 2  501 games 4.0K 8月   2 20:59 bin
drwxr-xr-x 2 root root  4.0K 8月   2 21:00 logs

```

* Memory启动
  * 修改/root/wanghonglin/deploy/hugegraph/hugegraph-0.11.2/conf/hugegraph.properties
```
backend=memory
serializer=text
```

  * 启动server
```
cd /root/wanghonglin/deploy/hugegraph/hugegraph-0.11.2

[root@iZ2ze1a67q38izs9eq9w39Z hugegraph-0.11.2]# bin/start-hugegraph.sh
Starting HugeGraphServer...
Connecting to HugeGraphServer (http://127.0.0.1:8080/graphs).........OK
Started [pid 387]

[root@iZ2ze1a67q38izs9eq9w39Z hugegraph-0.11.2]# netstat -lntp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8080          0.0.0.0:*               LISTEN      387/java
tcp        0      0 127.0.0.1:8182          0.0.0.0:*               LISTEN      387/java
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1566/sshd

hugegraph启动成功
```

