# Installing Terragrunt on Windows

## Download Terragrunt

1. Visit the official Terragrunt GitHub releases page: [Terragrunt Releases](https://github.com/gruntwork-io/terragrunt/releases)
2. Find the latest release version.
3. Download the Windows version as a ZIP file (e.g., `terragrunt_windows_amd64.zip`).

## Extract the Terragrunt Executable

After downloading the ZIP file, extract its contents to a directory of your choice.

## Add Terragrunt to Your System PATH

To make Terragrunt easily accessible from the command prompt, follow these steps:

1. Right-click on the Windows Start button and select "System".
2. Click on "Advanced system settings" on the left.
3. In the "System Properties" window, click the "Environment Variables" button.
4. In the "System Variables" section, find and select the "Path" variable, then click "Edit".
5. Click "New" and add the path to the directory containing the Terragrunt executable (e.g., `C:\Path\To\Terragrunt`).
6. Click "OK" to save the changes.

## Verify the Installation

To verify that Terragrunt is correctly installed, open a new Command Prompt and run the following command:

```bash
terragrunt --version
