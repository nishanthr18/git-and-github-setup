# Git & GitHub Setup for Beginners (Windows)

A simple step-by-step guide to connect Git with GitHub using **SSH** (Recommended).

---

# Prerequisites

- Install Git: https://git-scm.com/downloads
- Create a GitHub account: https://github.com

---

# Step 1: Verify Git Installation

Open **PowerShell** or **Git Bash**.

```bash
git --version
```

Example:

```text
git version 2.50.1.windows.1
```

---

# Step 2: Configure Git

Tell Git who you are.

```bash
git config --global user.name "Your Name"
```

Example:

```bash
git config --global user.name "Nishanth Gowda"
```

Now set your email.

```bash
git config --global user.email "your_email@example.com"
```

Example:

```bash
git config --global user.email "nishanth@example.com"
```

Verify:

```bash
git config --global --list
```

Output:

```text
user.name=Nishanth Gowda
user.email=nishanth@example.com
```

---

# Step 3: Check if an SSH Key Already Exists

```bash
ls ~/.ssh
```

If you see:

```text
id_ed25519
id_ed25519.pub
```

Skip to **Step 5**.

Otherwise continue.

---

# Step 4: Generate a New SSH Key

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Example:

```bash
ssh-keygen -t ed25519 -C "nishanth@example.com"
```

You'll see:

```text
Enter file in which to save the key
```

Press **Enter**.

You'll then be asked for a passphrase.

You can:

- Press **Enter** for no passphrase.
- Or create one for extra security.

---

# Step 5: Start the SSH Agent

Check its status.

```powershell
Get-Service ssh-agent
```

If it is stopped:

```powershell
Start-Service ssh-agent
```

(Optional) Start it automatically whenever Windows starts.

```powershell
Set-Service -Name ssh-agent -StartupType Automatic
```

---

# Step 6: Add the SSH Key

```bash
ssh-add ~/.ssh/id_ed25519
```

You should see:

```text
Identity added
```

---

# Step 7: Copy the Public Key

Display your public key.

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the **entire output**.

It starts with:

```text
ssh-ed25519 AAAA...
```

---

# Step 8: Add the SSH Key to GitHub

1. Open GitHub.
2. Click your profile picture.
3. Click **Settings**.
4. Click **SSH and GPG Keys**.
5. Click **New SSH Key**.
6. Title:

```
My Laptop
```

7. Paste your copied key.
8. Click **Add SSH Key**.

---

# Step 9: Test the Connection

```bash
ssh -T git@github.com
```

The first time you'll see:

```text
Are you sure you want to continue connecting (yes/no)?
```

Type:

```text
yes
```

Success:

```text
Hi your_username! You've successfully authenticated, but GitHub does not provide shell access.
```

Congratulations! Git is now connected to GitHub using SSH.

---

# Step 10: Create a New Repository on GitHub

Create a repository from GitHub.

Example:

```
learn-git
```

Do **NOT** initialize it with:

- README
- .gitignore
- License

Create an empty repository.

---

# Step 11: Create a Local Project

```bash
mkdir learn-git
```

```bash
cd learn-git
```

Initialize Git.

```bash
git init
```

---

# Step 12: Create Your First File

```bash
echo "# Learn Git" > README.md
```

---

# Step 13: Stage the File

```bash
git add .
```

---

# Step 14: Commit

```bash
git commit -m "Initial commit"
```

---

# Step 15: Connect Local Repository to GitHub

Copy the SSH URL from GitHub.

Example:

```text
git@github.com:your_username/learn-git.git
```

Add it as the remote.

```bash
git remote add origin git@github.com:your_username/learn-git.git
```

Verify:

```bash
git remote -v
```

Output:

```text
origin  git@github.com:your_username/learn-git.git (fetch)
origin  git@github.com:your_username/learn-git.git (push)
```

---

# Step 16: Push to GitHub

Rename the default branch.

```bash
git branch -M main
```

Push.

```bash
git push -u origin main
```

Done!

Your code is now on GitHub.

---

# Everyday Workflow

Check changed files.

```bash
git status
```

Stage changes.

```bash
git add .
```

Commit.

```bash
git commit -m "Describe your changes"
```

Push.

```bash
git push
```

Pull the latest changes.

```bash
git pull
```

---

# Useful Commands

Current branch

```bash
git branch
```

All branches

```bash
git branch -a
```

Create a branch

```bash
git checkout -b feature/login
```

Switch branch

```bash
git checkout main
```

Merge branch

```bash
git merge feature/login
```

View commit history

```bash
git log --oneline
```

View remotes

```bash
git remote -v
```

Remove remote

```bash
git remote remove origin
```

Change remote URL

```bash
git remote set-url origin git@github.com:username/repository.git
```

---

# Common Problems

### Permission denied (publickey)

Check:

```bash
ssh -T git@github.com
```

If it fails:

- Ensure your SSH key is added to GitHub.
- Ensure the SSH agent is running.
- Ensure your repository uses the SSH URL.

---

### Repository not found

Verify your remote.

```bash
git remote -v
```

If it shows HTTPS, switch to SSH.

```bash
git remote set-url origin git@github.com:username/repository.git
```

---

### Check Git Configuration

```bash
git config --global --list
```

---

# Recommended Folder Structure

```
Projects/
│
├── project-one/
├── project-two/
├── learn-git/
└── portfolio/
```

---

# Quick Reference

```bash
git status
git add .
git commit -m "message"
git push
git pull
git branch
git checkout branch-name
git log --oneline
```

---

# You're Ready!

You now know how to:

- Install Git
- Configure Git
- Generate an SSH key
- Connect GitHub with SSH
- Create repositories
- Push code to GitHub
- Pull changes
- Work with branches
- Use the most common Git commands
