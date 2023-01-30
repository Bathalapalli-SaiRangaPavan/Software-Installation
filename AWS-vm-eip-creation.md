# Create Virtual Machine in AWS Cloud

Go to AWS Management Console -> Ec2 -> Launch Instance 
- Step 1: Choose an Amazon Machine Image (AMI) -> [Amazon Linux 2 AMI (HVM) - Kernel 5.10, SSD Volume Type ]
- Step 2: Choose an Instance Type -> [t2.micro]
- Step 3: Configure Instance Details -> Number Of Instances [1] (usually we deploy in custom vpc)
- Step 4: Add Storage  -> [do not change any]
- Step 5: Add Tags -> Name  Server
- Step 6: Configure Security Group (port 22 should be opened) #by default its opened in AWS 
- Step 7: Key Pair - Create a key pair (Name -> mypersonalkey, Select (.pem), click (Download)) # Note: Don't loose pem file
- Step 8: Review And Launch
### Connect to server using session manager in the AWS 
- login: ec2 - user
- sudo su -
###  Connect to server using mobaxterm
- Click (Mobaxterm)
- Click (Session)
- Click (SSH)
- Remote Host - Give IP(Public)
- Click (Advanced SSH settings 
- Select (use private key - Give(Pem file))
- Click (ok)
- login: ec2 - user

### Elastic IP
Elastic IP address is a static IPv4 address designed for dynamic cloud computing. An Elastic IP address is allocated to your AWS account, and is yours until you release it.
#### If you want to allocate Elastic IP for entire region its billable
- Step 1 - You can see under network and security (or) Search (Elastic Ip) in AWS management console
- Step 1.1 - click (Elastic Ip) 
- Step 2 - click on (allocate elastic ip address) 
- Step 3 - Let all be default, click (allocate). Now u have got an elastic ip 
- Step 4 - click on (actions -> associate ec2 instance -> select which ec2 instance u need to associate)
#### If you don't want to assign Elastic IP to the server
- Click (elastic ip) -> (actions -> deassociate elastic -> diassociate) -> (actions -> release elastic ip address) 


#### AWS Pricing Calculator 
Lets you explore AWS services, and create an estimate for the cost of your use cases on AWS.

- Step 1 - search (Aws Pricing calculator) in Browser/google (or) https://calculator.aws/#/
- Step 2 - click (Create estimate)
- Step 3 - To estimate the cost 
##### Example: Search (EC2) -> click (Configure) -> (region - N virginia) -> operating system  (linux) -> instance type (search instances by name (t2.micro) u can see on demand hourly cost -> utilixzation (24/7 for 30 days (100)) -> pricing strategy (ondemand ec2 instance) -> EBS (30) -> you can see total monthly cost.
Its like a pay as you go model. Storage is chargable even u stop server (cpu, memory not charged)
