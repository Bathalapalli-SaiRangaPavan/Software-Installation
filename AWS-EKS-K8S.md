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

### Set Up eksctl

- Reference: eksctl - https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html#installing-eksctl

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
```
```
sudo mv /tmp/eksctl /usr/local/bin
```
```
eksctl version
```

### Create EKS Cluster using eksctl

It will take 15 minutes to 20 minutues. execute below command at together 

```
eksctl create cluster --name=eksdemo1 \
                      --region=us-east-1 \
                      --zones=us-east-1a,us-east-1b \
                      --without-nodegroup 
                      
```
					  
								  
Get List of clusters

```
eksctl get cluster
```
### Create & Associate IAM OIDC Provider for our EKS Cluster
If u want to use everything effectively following in order is the best execute below 
```
eksctl utils associate-iam-oidc-provider \
    --region us-east-1 \
    --cluster eksdemo1 \
    --approve
```


### Create EC2 Keypair

- Create a new EC2 Keypair with name as kube-demo #better u select pem 

This keypair we will use it when creating the EKS NodeGroup.
This will help us to login to the EKS Worker Nodes using Terminal.

### Create Node Group with additional Add-Ons in Public Subnets
Create Public Node Group   

what all we create 
```
eksctl create --help  
```
what all options available for node group we can see here 
```
eksctl create nodegroup --help 
```
It will take 3 to 5 minutes. It will create t3.medium nodes with minimum 2 and maximum 4 
```
eksctl create nodegroup --cluster=eksdemo1 \
                       --region=us-east-1 \
                       --name=eksdemo1-ng-public1 \
                       --node-type=t3.medium \
                       --nodes=2 \
                       --nodes-min=2 \
                       --nodes-max=4 \
                       --node-volume-size=20 \
                       --ssh-access \
                       --ssh-public-key=kube-demo \
                       --managed \
                       --asg-access \
                       --external-dns-access \
                       --full-ecr-access \
                       --appmesh-access \
                       --alb-ingress-access 
```

Sometimes it will fail and it will recreate again 
List of nodes available
```
kubectl get nodes -o wide
```
- Take the pubic ip of created t3.medium nodes and do ssh with kube-demo as a pem file

## Delete EKS Cluster

### Delete Node Groups
```
# List EKS Clusters
eksctl get clusters

# Capture Node Group name
eksctl get nodegroup --cluster=eksdemo1

# Delete Node Group
eksctl delete nodegroup --cluster=eksdemo1 --name=eksdemo1-ng-public1
```

## Delete Cluster
```
eksctl delete cluster eksdemo1
```
