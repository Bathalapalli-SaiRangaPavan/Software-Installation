## Install Java 11
```
sudo su -
```
```
sudo apt update
```
```
sudo apt install openjdk-11-jre
```
```
java -version
```

## Install Jenkins 

To download the particular version - https://updates.jenkins-ci.org/download/war/
- Iam installing 2.303.3

```
wget https://updates.jenkins-ci.org/download/war/2.303.3/jenkins.war
```

Run in backgroud 

```
nohup java -jar jenkins.war & 
```

By default it runs on 8080 
# To access 
```
jenkins server ip:8080
```
Once u access jenkins it will ask to give password. Login to Jenkins server and execute below command

```
cat /root/.jenkins/secrets/initialAdminPassword
```
paste password in the jenkins gui 

```
Select (install suggested plugins)
```
Give random 
```
Create First Admin User
username: admin
password: password
confirm password: password 
Full name: Pavan
Email-address: admin@admin.com  
```
Give Default 
```
Click (save & continue) 
Click (save & finish)
Click (start using jenkins) 
```

Now start using Jenkins 
