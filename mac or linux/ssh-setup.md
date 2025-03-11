# Setting Up SSH Key for GitHub Authentication on Linux or Mac

Follow the steps below to generate and configure an SSH key for secure authentication with GitHub.

## 1. Generate SSH Key
Run the following command to generate an SSH key using the `ed25519` algorithm:

```sh
ssh-keygen -t ed25519 -C "<github-email-id>" -f ~/.ssh/<github-username>
```

- When prompted for a passphrase, **press Enter** (leaving it empty).
- Press **Enter** again to confirm.

## 2. Start SSH Agent and Add Key
Change to the SSH directory:

```sh
cd ~/.ssh
```

Start the SSH agent:

```sh
eval "$(ssh-agent -s)"
```

Add the newly created SSH key to the agent:

```sh
ssh-add ~/.ssh/<github-username>
```

Verify that the key has been added successfully:

```sh
ssh-add -l
```

## 3. Add SSH Key to GitHub
Retrieve the public key:

```sh
cat ~/.ssh/<github-username>.pub
```

Copy the output and add it to your GitHub account under:
- **GitHub → Settings → SSH and GPG keys → New SSH Key**
- Paste the copied key and save.

## 4. Configure SSH for GitHub
Open the SSH configuration file:

```sh
nano ~/.ssh/config
```

Add the following lines:

```sh
Host <github-username>
    Hostname github.com
    User git
    IdentityFile ~/.ssh/<github-username>
```

Save and exit (in nano, press **CTRL + X**, then **Y**, then **Enter**).

## 5. Test SSH Connection
Verify the SSH connection with GitHub:

```sh
ssh -T git@<github-username>
```

If everything is set up correctly, you should see a success message confirming authentication.

### 🎉 Done! You can now securely interact with GitHub using SSH.

