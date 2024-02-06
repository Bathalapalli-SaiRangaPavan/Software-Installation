## Installing Chocolatey on Windows

Chocolatey is a package manager for Windows that simplifies the process of installing, upgrading, and managing software. Follow these steps to install Chocolatey on your Windows machine:

1. **Open PowerShell as Administrator**: Right-click on the Start menu and select "Windows PowerShell (Admin)".

2. **Enable Execution of PowerShell Scripts**: Run the following command in the PowerShell window:
   ```powershell
   Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

3. **Run Chocolatey Installation Command**: Copy and paste the following command into the PowerShell window and press Enter.
   ```powershell
   Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
4. **Verify Installation**: After installation completes, you can verify if Chocolatey is installed properly by running:
   ```powershell
   choco

## Update Chocolatey:
It's a good practice to update Chocolatey to the latest version after installation. You can do this by running
```powershell
choco upgrade chocolatey

