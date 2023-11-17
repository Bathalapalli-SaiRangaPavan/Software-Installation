# Setting Up SSH Keys for Bitbucket Authentication

## Generate SSH Key Pair

If you haven't already generated an SSH key pair on your Git Bash, follow these steps:

1. Open a terminal or command prompt on your Git Bash.
2. Run the following command: `ssh-keygen`
3. Choose a location to save the keys (default is usually fine).
4. Set a passphrase for added security (optional).

## Retrieve Your Public Key

To retrieve your public key, run the following command:

```bash
cat ~/.ssh/id_rsa.pub
```
## Adding SSH Key to Your Bitbucket Account

Follow these steps to add your SSH key to your Bitbucket account for passwordless authentication:

1. **Log in to Bitbucket:**
   - Open your web browser and navigate to [Bitbucket](https://bitbucket.org/).
   - Log in to your Bitbucket account.

2. **Access Bitbucket Settings:**
   - Click on your profile picture or avatar located in the lower-left corner of the Bitbucket interface.

3. **Navigate to SSH Keys:**
   - In the settings menu, scroll down and find the "Security" section.

4. **Click on "SSH keys":**
   - Under the "Security" section, locate and click on the "SSH keys" option.

5. **Add SSH Key:**
   - Once in the "SSH keys" section, click the "Add key" button.

6. **Label Your SSH Key:**
   - In the "Label" field, provide a name for your SSH key (e.g., "My Public Key").

7. **Paste Your Public Key:**
   - In the "Key" field, paste the public key you copied in Step 2 of the SSH key generation process.

8. **Save Your SSH Key:**
   - Click the "Add key" button to save your SSH key to your Bitbucket account.

Now, you have successfully added your SSH key to your Bitbucket account, enabling passwordless authentication for your Git operations.
