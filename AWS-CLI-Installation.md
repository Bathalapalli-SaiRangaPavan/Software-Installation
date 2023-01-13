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


## Configure AWS Credentials in command line
```
aws configure
```
```
AWS Access Key ID [None]: AKIASUF7DEFKSIAWM <give your access key>
```
```
AWS Secret Access Key [None]: WL9G9Tl8lGm7w9t7B3NEDny1+w3N/K5F3HW/ <give your secret access key> 
```
```
Default region name [None]: us-east-1 <give ur region>
```
```
Default output format [None]: json
```



## Verify the AWS Credentials Profile

```
cat $HOME/.aws/credentials 
```

- go to IAM -> User -> security credentials  

### u can see accesscode at the end last 3 same as in the .aws/credentials 
