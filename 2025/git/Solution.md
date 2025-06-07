**Git & GitHub for DevOps Engineers: A Hands-On Guide**

As a DevOps engineer, mastering Git and GitHub workflows is essential for efficient collaboration, automation, and 
infrastructure management. Whether you're contributing to open-source projects or managing internal
infrastructure-as-code (IaC) repositories, version control is foundational. 
In this post, we’ll walk through key Git/GitHub tasks with practical examples focused on DevOps scenarios.

🔹 **Forked & Cloned a Repo – Because Open Source Starts Here!**
Forking allows you to create your own copy of someone else's repository under your GitHub account. 
This is common in open-source contributions.

Example:
Let’s say you want to contribute to a Terraform module:

Go to the GitHub repo you want to contribute to (e.g., github.com/terraform-aws-modules/vpc).

Click Fork to create a copy in your account.

Clone the fork to your local machine:

```
bash

git clone https://github.com/yourusername/vpc.git
cd vpc

```
Now you're ready to explore, experiment, and contribute without affecting the original repo.

🔹 **Initialized a Local Repo – Set Up Projects from Scratch**
Sometimes you're building something new, like a Jenkins pipeline or Kubernetes manifest. You can start fresh with git init.

Example:
```
bash
mkdir k8s-manifests
cd k8s-manifests
git init
touch deployment.yaml
git add deployment.yaml
git commit -m "Initial commit with deployment manifest"
```
This local Git repository is now tracking your files. Time to push it to GitHub!

🔹 **Pushed Securely – Configured Remote Access Using Personal Access Token (PAT)**

Since August 2021, GitHub requires using PATs instead of passwords for HTTPS authentication.

Steps:

Generate a PAT from GitHub Developer Settings.

Add your GitHub repo as a remote:
```
bash

git remote add origin https://github.com/yourusername/k8s-manifests.git
```
Push your code securely:
```
bash

git push -u origin main
```
When prompted for username, use your GitHub username. For the password, use the PAT.

🔹 **Branching & Merging**
In DevOps, working with branches is critical, especially when handling CI/CD pipelines or infrastructure changes.

```
bash

# Create a feature branch
git checkout -b feature/new-helm-chart

# Make changes and commit
git add helm-chart/
git commit -m "Added Helm chart for monitoring stack"

# Push the branch
git push origin feature/new-helm-chart
```
On GitHub:

Open a Pull Request from your feature branch to main.

Review, discuss, and merge changes.

Handling Conflicts:
```
bash

git checkout main
git pull
git checkout feature/new-helm-chart
git merge main
# Resolve conflicts if any
git add .
git commit -m "Resolved merge conflicts"
```
🔹**SSH Authentication – Secure and Password-Free GitHub Access**

For frequent users, SSH is a secure and seamless alternative to HTTPS.

Setup Steps:

Generate SSH key:
```
bash

ssh-keygen -t ed25519 -C "your_email@example.com"
```
Add the public key to GitHub:

Go to Settings > SSH and GPG keys > New SSH Key.

Test your connection:
```
bash

ssh -T git@github.com
```
Clone using SSH:
```
bash

git clone git@github.com:yourusername/infra-ansible.git
```
No more password prompts! Perfect for automation and scripting.

👩‍💻 Final Thoughts
Whether you're managing IaC, CI/CD pipelines, or observability stacks, using Git effectively is non-negotiable. 
Here’s a quick DevOps-focused recap:

✅ Fork → Contribute to community tools

✅ Init → Start your own IaC or pipeline repo

✅ PAT → Securely push code

✅ Branch → Experiment safely

✅ SSH → Automate & authenticate seamlessly

Version control is the backbone of modern DevOps. 
Master it, and you'll unlock automation, auditability, and speed at scale.

Here is a list of  essential Git commands every DevOps engineer should know — complete with syntax and descriptions. 
These are categorized by common use cases: setup, daily work, collaboration, and troubleshooting.

# 📘 Essential Git Commands for DevOps Engineers

Mastering Git is critical for DevOps workflows, whether you're handling infrastructure as code (IaC), CI/CD pipelines, or automation scripts. Below is a categorized list of key Git commands every DevOps engineer should know.

---

## 🛠️ 1. Setup & Configuration

| Command | Description |
|---------|-------------|
| `git config --global user.name "Your Name"` | Set global Git username. |
| `git config --global user.email "you@example.com"` | Set global Git email. |
| `git config --global core.editor "vim"` | Set default text editor. |
| `git config --list` | Show all Git config settings. |

---

## 📁 2. Repository Management

| Command | Description |
|---------|-------------|
| `git init` | Initialize a new local repository. |
| `git clone <repo-url>` | Clone an existing repository. |
| `git remote -v` | Show connected remote repositories. |
| `git remote add origin <url>` | Add a remote called `origin`. |

---

## 📝 3. Staging & Committing Changes

| Command | Description |
|---------|-------------|
| `git status` | Show the working directory status. |
| `git add <file>` | Stage a specific file. |
| `git add .` | Stage all changes in current directory. |
| `git commit -m "message"` | Commit changes with a message. |
| `git commit -am "message"` | Add and commit tracked files in one step. |

---

## 🌿 4. Branching & Merging

| Command | Description |
|---------|-------------|
| `git branch` | List local branches. |
| `git branch <branch>` | Create a new branch. |
| `git checkout <branch>` | Switch to a branch. |
| `git checkout -b <branch>` | Create and switch to a new branch. |
| `git merge <branch>` | Merge a branch into the current branch. |
| `git branch -d <branch>` | Delete a branch. |

---

## 🔁 5. Pushing & Pulling

| Command | Description |
|---------|-------------|
| `git push origin <branch>` | Push local branch to remote. |
| `git push -u origin <branch>` | Push and set tracking for future pushes. |
| `git pull` | Pull latest changes from remote. |
| `git fetch` | Fetch changes without merging. |
| `git pull --rebase` | Pull using rebase instead of merge. |

---

## 🔐 6. Authentication

### Using SSH:

```bash
ssh-keygen -t ed25519 -C "you@example.com"
ssh -T git@github.com
```

## 🧹 7. Cleaning & Undoing

| Command                         | Description                                      |
|---------------------------------|--------------------------------------------------|
| `git reset <file>`             | Unstage a file.                                  |
| `git checkout -- <file>`       | Discard local changes to a file.                 |
| `git clean -fd`                | Delete untracked files/directories.             |
| `git revert <commit>`          | Create a new commit that reverses a previous one.|
| `git reset --hard <commit>`    | Hard reset to a previous commit (destructive). ⚠️ |

---

## 🕵️ 8. History & Inspection

| Command                        | Description                             |
|--------------------------------|-----------------------------------------|
| `git log`                      | Show commit history.                    |
| `git log --oneline`            | Condensed log (one commit per line).    |
| `git diff`                     | Show changes not yet staged.            |
| `git diff --staged`            | Show staged changes.                    |
| `git show <commit>`            | Show a specific commit’s content.       |
| `git blame <file>`             | Show line-by-line authorship.           |

---

## 💥 9. Conflict Resolution

| Command               | Description                     |
|-----------------------|---------------------------------|
| `git merge <branch>` | Attempt to merge a branch.      |
| `git status`         | Identify conflicted files.      |
| *(Resolve manually)* |                                 |
| `git add <file>`     | Mark conflict resolved.         |
| `git commit`         | Commit the merge result.        |

---

## 🔗 10. Submodules (for IaC, modules, etc.)

| Command                                           | Description                            |
|--------------------------------------------------|----------------------------------------|
| `git submodule add <url> path/`                 | Add a Git submodule.                   |
| `git submodule update --init --recursive`       | Initialize and update submodules.      |
