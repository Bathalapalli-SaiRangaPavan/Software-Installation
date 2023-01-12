## Browse: https://www.terraform.io/downloads


## Terraform Installation in ubuntu

```
sudo su - 
```
```
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
```
```
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```
```
sudo apt update && sudo apt install terraform
```
Check Version
```
terraform --version
```



## Terraform Installation in Amazon-Linux

```
sudo su - 
```
```
sudo yum install -y yum-utils
```
```
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
```
```
sudo yum -y install terraform
```
```
terraform --version
```


## Terraform Installation in RHEL

```
sudo su - 
```
```
sudo yum install -y yum-utils
```
```
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
```
```
sudo yum -y install terraform
```

Check Version

```
terraform --version
```

