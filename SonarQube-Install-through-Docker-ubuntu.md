  Note: We need a Docker in SonarQube machine. You can write script.

## Prerequisites: Install Docker in SonarQube Machine
```
sudo su - 
```
```
vi docker.sh 
```

```
sudo apt-get update -y
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-key fingerprint 0EBFCD88
sudo apt-get update -y
sudo apt-get install docker-ce docker-ce-cli containerd.io -y 
```

Execute below command 

```
sh docker.sh 
```
- It will take time to install Docker  

Check Docker version  
```
docker version 
```
## Install sonarqube as a docker container 
```
docker run -d -p 9000:9000 sonarqube:lts
```
### Access sonarqube DashBoard
```
sonarqube ip : 9000
```
- u can see sonarqube dashboard 

Give Below Credentials 

```
username: admin 
password: admin   
```

change password 

```
old password: admin 
new password: password  <Create new password>
confirm password: password <confirm new password>
```

- Note - u always run as a soonar user dont run as a root user. Once u login to server u switch to sonar user su - sonar

