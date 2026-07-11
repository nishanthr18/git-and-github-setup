# Git & GitHub Setup Guide (Windows & macOS)

A beginner-friendly guide to install Git, configure it, connect it to GitHub using SSH, and push your first repository.

---

# Table of Contents

1. Install Git
2. Configure Git
3. Generate SSH Key
4. Start SSH Agent
5. Add SSH Key
6. Add SSH Key to GitHub
7. Test SSH Connection
8. Create Your First Repository
9. Push Your First Project
10. Daily Git Workflow
11. Common Commands
12. Troubleshooting

---

# 1. Install Git

## Windows

Download Git:

https://git-scm.com/download/win

Install using the default settings.

Verify installation:

```bash
git --version
```

---

## macOS

### Option 1 (Recommended)

Install using Homebrew.

```bash
brew install git
```

### Option 2

Install Xcode Command Line Tools.

```bash
xcode-select --install
```

Verify installation.

```bash
git --version
```

---

# 2. Configure Git

Configure your name.

```bash
git config --global user.name "Your Name"
```

Configure your email.

```bash
git config --global user.email "your_email@example.com"
```

Verify.

```bash
git config --global --list
```

Example:

```text
user.name=Nishanth Gowda
user.email=nishanth@example.com
```

---

# 3. Check for an Existing SSH Key

Both Windows and macOS:

```bash
ls ~/.ssh
```

If you see:

```text
id_ed25519
id_ed25519.pub
```

You already have an SSH key.

Otherwise continue.

---

# 4. Generate a New SSH Key

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Example:

```bash
ssh-keygen -t ed25519 -C "nishanth@example.com"
```

Press **Enter** to accept the default location.

Optionally enter a passphrase.

---

# 5. Start the SSH Agent

## Windows (PowerShell)

Check the service.

```powershell
Get-Service ssh-agent
```

If stopped:

```powershell
Start-Service ssh-agent
```

(Optional) Start automatically.

```powershell
Set-Service -Name ssh-agent -StartupType Automatic
```

---

## macOS

Start the agent.

```bash
eval "$(ssh-agent -s)"
```

---

# 6. Add the SSH Key

Windows:

```bash
ssh-add ~/.ssh/id_ed25519
```

macOS:

```bash
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

Older macOS versions:

```bash
ssh-add -K ~/.ssh/id_ed25519
```

---

# 7. Copy the Public Key

Windows (PowerShell)

```powershell
Get-Content ~/.ssh/id_ed25519.pub
```

OR

```bash
cat ~/.ssh/id_ed25519.pub
```

---

macOS

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the entire key.

---

# 8. Add the SSH Key to GitHub

1. Open GitHub.
2. Click your profile.
3. Settings.
4. SSH and GPG Keys.
5. New SSH Key.
6. Title:

```
My Laptop
```

7. Paste the key.
8. Click **Add SSH Key**.

---

# 9. Test the SSH Connection

```bash
ssh -T git@github.com
```

First time:

```text
Are you sure you want to continue connecting (yes/no)?
```

Type:

```text
yes
```

Expected output:

```text
Hi your_username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

# 10. Create a GitHub Repository

Create a repository on GitHub.

Example:

```
learn-git
```

Do **not** initialize it with:

- README
- License
- .gitignore

---

# 11. Create a Local Project

```bash
mkdir learn-git
```

```bash
cd learn-git
```

```bash
git init
```

Create a README.

```bash
echo "# Learn Git" > README.md
```

---

# 12. Stage Files

```bash
git add .
```

---

# 13. Commit

```bash
git commit -m "Initial commit"
```

---

# 14. Connect to GitHub

Copy the SSH URL.

Example:

```text
git@github.com:your_username/learn-git.git
```

Add the remote.

```bash
git remote add origin git@github.com:your_username/learn-git.git
```

Verify.

```bash
git remote -v
```

---

# 15. Push

Rename the default branch.

```bash
git branch -M main
```

Push.

```bash
git push -u origin main
```

Done!

---

# Daily Workflow

Check status.

```bash
git status
```

Stage.

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

Pull latest changes.

```bash
git pull
```

---

# Useful Commands

Current branch.

```bash
git branch
```

Create a branch.

```bash
git checkout -b feature/login
```

Switch branches.

```bash
git checkout main
```

Merge.

```bash
git merge feature/login
```

History.

```bash
git log --oneline
```

View remote.

```bash
git remote -v
```

Remove remote.

```bash
git remote remove origin
```

Change remote URL.

```bash
git remote set-url origin git@github.com:username/repository.git
```

---

# Troubleshooting

## Permission denied (publickey)

Run:

```bash
ssh -T git@github.com
```

If it fails:

- Ensure the SSH key is added to GitHub.
- Ensure the SSH agent is running.
- Ensure the repository uses an SSH remote.

---

## Repository not found

Check:

```bash
git remote -v
```

If it shows HTTPS:

```bash
git remote set-url origin git@github.com:username/repository.git
```

---

## Check Git Configuration

```bash
git config --global --list
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
git merge branch-name
git log --oneline
git remote -v
```

---

# You're Ready!

You now know how to:

- ✅ Install Git
- ✅ Configure Git
- ✅ Generate an SSH key
- ✅ Connect GitHub using SSH
- ✅ Create repositories
- ✅ Push and pull code
- ✅ Work with branches
- ✅ Troubleshoot common Git issues
