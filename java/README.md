# Java

```shell
# install from source code
wget https://repo.huaweicloud.com/java/jdk/8u201-b09/jdk-8u201-linux-x64.tar.gz

tar -zxvf jdk-8u201-linux-x64.tar.gz

# set java environment variables
sudo vim /etc/profile
export JAVA_HOME=/home/ubuntu/java/jdk1.8.0_211
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH

# refresh the environment variables
source /etc/profile

# chcek the java version
java -version

# compile java code
javac HelloWorld.java
javac -encoding UTF-8 HelloWorld.java

# run java code
java HelloWorld

# run java package
javac -d . *.java
java adapter.MainApp
```

## Jar

```shell
# create jar package
jar cf app.jar -C . adapter

# create MANIFEST.MF file and write the content
# Manifest-Version: 1.0
# Main-Class: adapter.MainApp
jar cfm app.jar MANIFEST.MF -C . adapter

# check the content
jar tf adapter.jar

# decompress
jar -xvf adapter.jar

# run the jar
java -jar adapter.jar

# run the jar in background
nohup java -jar adapter.jar > log.txt 2>&1 &
```
