### Prerequsite: Java

```
sudo su - 
```
Install 3rd party tools in opt directory 

```
cd /opt
```
```
yum install wget -y
```
### Install Java
```
wget -c --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jdk-8u131-linux-x64.rpm 
```
```
yum install jdk-8u131-linux-x64.rpm -y
```
```
java -version
```
```
yum install java-1.8* -y
```

### Install Tomcat 

Browse: https://tomcat.apache.org/download-90.cgi

- u can see Binary Distributions, right click (tar.gz) ->  click on (copy link address)

I'm installing Tomcat 9 version
```
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.54/bin/apache-tomcat-9.0.54.tar.gz
```
```
tar -xvzf apache-tomcat-9.0.54.tar.gz 
```
untar

```
rm -rf apache-tomcat-9.0.54.tar.gz 
```
Go inside apache-tomcat-9.0.54

```
cd apache-tomcat-9.0.54
cd bin/
ls
```
- u can see catalina.sh, startup.sh, shutdown.sh etc binary files

- u should be in bin to start or stop the server ./shutdown.sh

```
./startup.sh 
```

```
ps -ef | grep tomcat
```
To see which port tomcat is running 
```
netstat -tunlap
```
- Go to aws  open the port 8080 in the security group (custom TCP 8080 ANYWHERE)
- Browse TomcatServerIp:8080
### Once you see Tomcat GUI


- Click on (manager app) 

- u get an error 403 access denied

Execute Below each Command in Tomcat Server

```
cd ~
ls
cd apache-tomcat-9.0.54
ls
cd webapps
ls 
cd manager/
ls
cd META-INF/
vi context.xml
```
comment below line 

```
<! --
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
-->
```
- go to browser and click on manager app you are not getting error it is asking the username and password

- Go to conf directory in Tomcat Server u can use below command 

```
cd ../../../conf/
```
or you can use below commands to go to conf directory 
- Execute each command. If you have executed above command no need to execute below commands. 

```
cd ~
cd apache-tomcat-9.0.54 
ls 
cd conf 
ls
```
Now u can see tomcat-users.xml u go inside and add username and password
```
vi tomcat-users.xml
```
u can see below 

```
  <!--
    <role rolenmae="tomcat"
    | 
    |
    |
    |
  -->
```
u add below line after 
- Note: Give your username, Password
```
<user username="admin" password="passw0rd" roles="manager-gui,admin-gui" />   
```

to add one more user add like the above 
```
<user username="pavan" password="passw0rd" roles="manager-gui,admin-gui" />
```

- now go to browser and login using username: admin, password: passw0rd
- now succesfully logged into manager-gui

- now click (host manager) 
- u get an error 403 access denied
go to webapps u can see host manager
Execute below each command 
```
cd ../webapps/
ls
cd host-manager
ls
cd META-INF
ls
```

```
vi context.xml
```
comment 
```
<! --
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
-->
```

- Now go to browser click on (host manager) and login using username: admin, password: passw0rd
- To clear the cache (ctrl+shift+delete)
