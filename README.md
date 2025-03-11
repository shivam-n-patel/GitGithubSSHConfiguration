# Git SSH Configuration Setup

Easily configure SSH settings for managing multiple Git accounts on a single device. This setup is useful for handling personal and work GitHub accounts or different repositories seamlessly.

## 📂 Folder Structure

- **Windows/** → SSH setup instructions for Windows.
- **Mac-Linux/** → SSH setup instructions for macOS and Linux.

## 📌 Setup Instructions

1. **Windows Users:** Follow the steps in the `Windows` folder.
2. **Mac/Linux Users:** Follow the steps in the `Mac-Linux` folder.

Choose the appropriate guide based on your operating system and configure Git SSH effortlessly.

---

## 🚀 Using SSH with Git

### 🔹 Cloning a Repository Using SSH
```sh
git clone git@<github-username>:<github-username>/your-repository.git
```

### 🔹 Initializing a New Repository and Adding SSH Remote
```sh
git init
git add .
git commit -m "first commit"
```

```sh
// The above commit command might prompt you to do the following 2 commands (to be done only once)
// if not prompted skip these commands
git config user.email "github-email-id"
git config user.name "github-user-name"
```

```sh
git branch -M main
```

Add SSH remote:
```sh
git remote add origin git@<github-username>:<github-username>/your-repository.git
git push -u origin main
```
