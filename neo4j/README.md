# Neo4j

Neo4j is a high-speed graph database with unbounded scale, security, and data integrity for mission-critical intelligent applications.

```shell
sudo curl -O http://dist.neo4j.org/neo4j-community-3.5.5-unix.tar.gz
tar -axvf neo4j-community-4.4.6-unix.tar.gz

cd /home/ubuntu/data/neo4j-community-4.4.6/bin/
sudo vim ../conf/neo4j.conf

sudo ./neo4j start
sudo ./neo4j console
sudo ./neo4j status

# import the data
./neo4j-admin  load --from=/home/data/graph-dbms-neo4j.dump --database=yourdb
```
