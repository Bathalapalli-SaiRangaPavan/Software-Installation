# EKS CLUSTER SETUP 

#### Create a server in AWS management console
- Search (EC2) -> Click (Launch Instnace)
- Choose an Amazon Macine Image (Amazon Linux 2 AMI)
- Choose An Instance Type (t2.micro)
- Configure Instance Details
- Add Storage
- Add tags (name eksctl_bootstrap)
- Configure Security Group
- Create a Key Pair 
- Launch the server 
- Login to the server using Mobaxterm (Remote Host -> Give IP(Public), Use Private Key (Pem file) -> Clisck (Ok)
- Connect to server using mobaxterm/putty/session manager
- Login as: ec2-user
- switch to root user
```
sudo su 
```
Check AWS Version 
```
aws --version 
```
By default u can able to see aws cli as we r using amazon linux if u want to do for RedHat follow the below 

### Install and configure AWS CLI

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip 
sudo ./aws/install
```

### Generate Access key & Secret key 
- Go to Services -> IAM -> Users -> Add-user (if needed u can use existing) "Your-Admin-User" -> select the user -> Security Credentials -> Create Access Key

Execute this below each commands in clii 
```
aws configure
```
```
AWS Access Key ID [None]: <give accessid> 
AWS Secret Access Key [None]: <give secret key>
Default region name [None]: us-east-1 <give region> 
Default output format [None]: json
```
If u can able to see vpc's then perfect if not it should get administrator access in IAM (AdministratorAccess)
```
aws ec2 describe-vpcs
```
If u can able to see vpc's then perfect if not it should get administrator access in IAM (AdministratorAccess)

### Set Up kubectl

- Reference: kubectl - https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html
```
curl -o kubectl https://s3.us-west-2.amazonaws.com/amazon-eks/1.22.6/2022-03-09/bin/linux/amd64/kubectl
```
Execution Permissions 
```
chmod +x ./kubectl
```
Move kubectl to Usr local bin 
```
mv ./kubectl /usr/local/bin
```
Check Version 
```
kubectl version --short --client
```
### Create an IAM Role and attache it to EC2 instance 

- AWS Console -> Search (IAM) -> Select (Roles) -> Click (Create role) -> we are attaching to ec2 so select (EC2) Click (Next:Permissions)
- Filter Policies (IAM Full Access) Select (IAM Full Access), 
- Filter Policies (Cloud Formation) Select (Cloud Formation Full Access) 
- Filter Policies (VPC) Select (VPC Full Access) 
- Filter Policies (EC2) Select (EC2 Full Access) 
- Filter Policies (Administration) Select (Administrator Access) 
- Click (Next : Tags) -> Click (Next : Review)
- Role Name (bootstrap_role) -> Click (Create Role)



### Now Attach It To Ec2 Instance

- AWS Console -> Search (EC2)  -> Select EC2 - Instance (eksctl_bootstrap) -> Select (Actions) -> Click (Security) -> Click (Modify IAM Role) 
- Select (bootstrap_role) -> Click (Save)

```
aws ec2 describe-vpcs 
```


