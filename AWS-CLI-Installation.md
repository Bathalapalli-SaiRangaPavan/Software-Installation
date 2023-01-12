## Pre requisite - You should have an aws account created and ready 

### Generate Security Credentials using AWS Management Console
- Go to Services -> IAM -> Users -> Add-user (if needed u can use existing) "Your-Admin-User" -> select the user -> Security Credentials -> Create Access Key


- Browse - https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html


Configure AWS credentials using SSH Terminal on your local desktop

## Install AWS CLI V2

```
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
```
```
sudo installer -pkg AWSCLIV2.pkg -target /
```
```
aws --version
```
