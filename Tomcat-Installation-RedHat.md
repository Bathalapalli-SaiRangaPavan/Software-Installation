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

u can see Binary Distributions, right click (tar.gz) ->  click on (copy link address)

Im installing Tomcat9 version
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
You can see catalina.sh, startup.sh, shutdown.sh etc binary files

u should be in bin to start or stop the server ./shutdown.sh

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
Go to aws  open the port 8080 in the security group (custom TCP 8080 ANYWHERE)

```
Browse Tomcat:8080
```
-> Click on (manager app) -> u get an error 403 access denied
-> cd ~
-> ls
-> cd apache-tomcat-9.0.54
-> ls
-> cd webapps
-> ls ( u can see 5 default applications)
-> cd manager/
-> ls
-> cd META-INF/
-> vi context.xml
  -> (comment )
<! --
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
-->

-> go to browser and click on manager app (we are not getting error it is asking the username and password )
Go to conf directory
(cd ../../../conf/)
or
-> cd ~
-> cd apache-tomcat-9.0.54 
-> ls 
-> cd conf 
-> ls
-> vi tomcat-users.xml
 -> (u can see 
  <!--
    <role rolenmae="tomcat"
    | 
    |
    |
    |
  -->
u add below line after -->
-> <user username="devopslearning" password="passw0rd" roles="manager-gui,admin-gui" />
------------------------------------------------------------------------
to add one more user uadd like the above n number of users
-> <user username="devopspractise" password="passw0rd" roles="manager-gui,admin-gui" />
--------------------------------------------------------------------------------------
now go to browser and login using dusernbame: devopslearning, password: passw0rd
now u succesfully loged in

now click (host manager) -> u get an error 403 access denied
go to webapps u can see host manager
-> cd ../webapps/
-> ls
-> cd host-manager
-> ls
-> cd META-INF
-> ls
-> vi context.xml
 
  -> (comment )
<! --
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
-->

now go to browser click on (host manager) and login using dusernbame: devopslearning, password: passw0rd
to clear the cache (ctrl+shift+delete)
