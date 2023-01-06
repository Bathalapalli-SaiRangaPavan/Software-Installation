## Prerequisite - Java 8

```
sudo su - 
```
```
sudo apt update
```
```
sudo apt install openjdk-8-jdk openjdk-8-jre
```
set path 

```
cat >> /etc/environment <<EOL
JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
JRE_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre
EOL
```
Check Java Version
```
java -version
```

## Nexus Installation 

```
wget https://download.sonatype.com/nexus/3/latest-unix.tar.gz
```
```
tar -xvf latest-unix.tar.gz
```
Give nexus-<current> 
```
cd nexus-3.44.0-01 
```
```
cd bin
```

Start the nexus artifactory
```
./nexus start
```
check the status of nexus artifactory
```
./nexus status 
```
Go to Browser access nexus 
```
nexus machine ip:8081 
```
