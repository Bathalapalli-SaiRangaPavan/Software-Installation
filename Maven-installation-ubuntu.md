## Prerequisites
Make sure install Java on your system

```
java -version
```

If not install java - https://tecadmin.net/install-oracle-java-11-ubuntu-18-04-bionic/
## Maven installation 
 
 
 ```
  cd /usr/local
  ```
  ```
  wget https://dlcdn.apache.org/maven/maven-3/3.8.7/binaries/apache-maven-3.8.7-bin.tar.gz
  ```
  ```
  sudo tar xvf apache-maven-3.8.7-bin.tar.gz
  ```
  ```
  ln -s apache-maven-3.8.7 apache-maven
  ```
  ```
  sudo vi /etc/profile.d/apache-maven.sh
  ```
 Insert below lines to /etc/profile.d/apache-maven.sh
  ```       
  export JAVA_HOME=/usr/lib/jvm/java-11-oracle
  export M2_HOME=/usr/local/apache-maven
  export MAVEN_HOME=/usr/local/apache-maven
  export PATH=${M2_HOME}/bin:${PATH}
  ```
 ```
  source /etc/profile.d/apache-maven.sh
  ```
 Verify version
 ```
  mvn -version 
 ``` 
 Reference
 - https://tecadmin.net/install-apache-maven-on-ubuntu/ 
 - https://maven.apache.org/download.cgi
 
 Other Way to install Maven
 
 ```
 sudo apt install maven
 ```
