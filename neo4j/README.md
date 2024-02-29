# Neo4j

```shell
sudo curl -O http://dist.neo4j.org/neo4j-community-3.5.5-unix.tar.gz
tar -axvf neo4j-community-4.4.6-unix.tar.gz

cd /home/ubuntu/data/neo4j-community-4.4.6/bin/
sudo vim ../conf/neo4j.conf

sudo ./neo4j start
sudo ./neo4j console
sudo ./neo4j status

# 导入数据
./neo4j-admin  load --from=/home/data/graph-dbms-neo4j.dump --database=yourdb
```
