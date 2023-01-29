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
