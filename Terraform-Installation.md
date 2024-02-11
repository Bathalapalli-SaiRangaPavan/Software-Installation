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


# Installing Terraform on Windows

This guide provides step-by-step instructions for installing Terraform on a Windows system.

---

## Installation Steps

### 1. Download Terraform Binary

- Go to the [Terraform Downloads](https://www.terraform.io/downloads.html) page on the official Terraform website.
- Download the Terraform binary for Windows.

### 2. Extract Terraform Binary

- Once downloaded, extract the contents of the zip file to a directory of your choice on your Windows system.

### 3. Add Terraform to PATH

- Open "System (Control Panel)" > "Advanced system settings" > "Environment Variables...".
- Under "System variables", select the `Path` variable and click "Edit...".
- Add the full path to the directory where Terraform binary (`terraform.exe`) is located.
- Click "OK" on all windows to apply the changes.

### 4. Verify Installation

- Open a new command prompt window.
- Type `terraform --version` and press Enter to verify that Terraform is installed correctly.

---

## Additional Resources

- For more detailed installation instructions and troubleshooting, refer to the official [Terraform Installation Documentation](https://learn.hashicorp.com/tutorials/terraform/install-cli).

Check Version

```
terraform --version
```

