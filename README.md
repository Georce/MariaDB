# MariaDB
MariaDB is a drop-in replacement for MySQL.
MariaDB strives to be the logical choice for database professionals looking for a robust, scalable, and reliable SQL server. To accomplish this, the MariaDB Foundation work closely and cooperatively with the larger community of users and developers in the true spirit of Free and open source software, and release software in a manner that balances predictability with reliability.

![mariadb-logo](mariadb.png)

# Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Benefits](#benefits)
- [Quick Start](#quick-start)
- [Technology](#technology)


# Introduction
MariaDB Galera Cluster is a synchronous multi-master cluster for MariaDB. It is available on Linux only, and only supports the XtraDB/InnoDB storage engines (although there is experimental support for MyISAM - see the wsrep_replicate_myisam system variable).

# Features
- **Synchronous replication**
- **Active-active multi-master topology**
- **Read and write to any cluster node**
- **Automatic membership control, failed nodes drop from the cluster**
- **Automatic node joining**
- **True parallel replication, on row level**
- **Direct client connections, native MySQL look & feel**

# Benefits
*The above features yield several benefits for a DBMS clustering solution, including:*
- **No slave lag**
- **No lost transactions**
- **Both read and write scalability**
- **Smaller client latencies**

# Quick Start
You can launch services using the command line,

*MariaDB Galera cluster 10.0.16
Node1 Node2*

```bash
root@node1#mysql
MariaDB [(none)]>grant usage on *.* to cluster@"%" identified by "123456";
MariaDB [(none)]>grant all privileges on *.* to cluster@"%";
MariaDB [(none)]>flush privileges;
```

Configuration

```bash
cp /usr/share/mysql/wsrep.cnf /etc/my.cnf.d/
vi /etc/my.cnf.d/wsrep.cnf
```

```bash
wsrep_provider=/usr/lib64/galera/libgalera_smm.so
wsrep_cluster_address=”gcomm://”
wsrep_sst_auth=cluster:123456
```

# Technology
MariaDB Galera Cluster uses the Galera library for the replication implementation. To interface with Galera replication, we have enhanced MariaDB to support the replication API definition in the wsrep API project.

The implementation of the replication API in MariaDB happens in the open source MySQL-wsrep project.
