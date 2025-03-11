# Setting Up SSH Key for GitHub on Windows

Follow these steps to generate and configure an SSH key for secure authentication with GitHub on Windows.

## **1. Open PowerShell as Administrator**

Press **Win + X** → Click **Windows Terminal (Admin)** or **PowerShell (Admin)**.

---

## **2. Generate SSH Key**

Run the following command to generate an SSH key using the `ed25519` algorithm:

```powershell
ssh-keygen -t ed25519 -C "<github-email-id>" -f C:\Users\%USERNAME%\.ssh\<github-username>
```

- When prompted for a **passphrase**, **press Enter** (leave it empty).
- Press **Enter** again to confirm.

---

## **3. Start SSH Agent and Add Key**

### **Step 1: Start SSH Agent**

Run:
```powershell
Start-Service ssh-agent
```

Set it to start automatically:
```powershell
Set-Service -Name ssh-agent -StartupType Automatic
```

### **Step 2: Add the SSH Key**
```powershell
ssh-add C:\Users\%USERNAME%\.ssh\<github-username>
```

### **Step 3: Verify Key Addition**
```powershell
ssh-add -l
```

---

## **4. Add SSH Key to GitHub**

### **Step 1: Retrieve the Public Key**
```powershell
Get-Content C:\Users\%USERNAME%\.ssh\<github-username>.pub
```

### **Step 2: Copy the Output and Add It to GitHub**
- Go to **GitHub → Settings → SSH and GPG keys → New SSH Key**
- **Paste the copied key** and save it.

---

## **5. Configure SSH for GitHub**

### **Step 1: Create/Edit the SSH Config File**

Run:
```powershell
notepad C:\Users\%USERNAME%\.ssh\config
```

### **Step 2: Add the Following Content and Save the File**

```
Host <username>
    Hostname github.com
    User git
    IdentityFile C:\Users\%USERNAME%\.ssh\<github-username>
```

---

## **6. Test SSH Connection with GitHub**

Run the following command:
```powershell
ssh -T git@<github-username>
```

If everything is set up correctly, you should see a message confirming authentication:
```plaintext
Hi <your-github-username>! You've successfully authenticated, but GitHub does not provide shell access.
```

### 🎉 **Done! You can now securely interact with GitHub using SSH.**

