# Push `SkyCast` to GitHub

This file contains step-by-step PowerShell commands to push the `SkyCast` project to your GitHub repository:

Repository URL (example):
https://github.com/adarshprajapa123/Java-Experiment-nimbus-submission.git

## 1) Quick checklist
- Confirm you have Git installed and configured (name/email).
- Decide whether to use HTTPS (recommended with Git Credential Manager or PAT) or SSH.
- If the remote repository already contains commits, you'll need to reconcile histories (pull, merge, or force push).

## 2) Initialize, commit, add remote, and push (PowerShell)
Open PowerShell, then run these commands from the project root (replace the path if different):

```powershell
cd 'c:\Users\adars\Desktop\Mini-Project-Java-main\SkyCast'
# Initialize repo if not already a git repository
git init
# Make first commit
git add .
git commit -m "Initial commit"
# Make main branch (optional but common)
git branch -M main
# Add remote (HTTPS)
git remote add origin https://github.com/adarshprajapa123/Java-Experiment-nimbus-submission.git
# Push to GitHub
git push -u origin main
```

If the push fails due to authentication, use one of the methods below.

## 3) Push using HTTPS + Personal Access Token (PAT)
- Create a Personal Access Token (classic or fine-grained) on GitHub with `repo` scope.
- Use Git Credential Manager (recommended) which will prompt for your credentials when pushing.

If you need to push once using a token in the URL (less secure, avoid saving token in history):

```powershell
# Not recommended for long-term use — this leaves token in shell history
git push https://<TOKEN>@github.com/adarshprajapa123/Java-Experiment-nimbus-submission.git main
```

Better: let Git Credential Manager prompt for username and token when running `git push`.

## 4) Push using SSH (preferred for repeated access)
- Generate an SSH key (if you don't have one):

```powershell
ssh-keygen -t ed25519 -C "your_email@example.com"
# or use rsa if ed25519 is not supported
```

- Copy the public key (`~/.ssh/id_ed25519.pub`) and add it to GitHub > Settings > SSH and GPG keys.
- Change remote to SSH and push:

```powershell
git remote remove origin
git remote add origin git@github.com:adarshprajapa123/Java-Experiment-nimbus-submission.git
git push -u origin main
```

## 5) If the remote already has content
If `git remote add origin ...` fails because a remote already exists, update the remote URL:

```powershell
git remote set-url origin https://github.com/adarshprajapa123/Java-Experiment-nimbus-submission.git
# or use SSH URL similarly
```

If histories diverge and you intentionally want to overwrite the remote (use with caution):

```powershell
# Force push (this will replace remote history with your local history)
git push -u origin main --force
```

## 6) Troubleshooting
- Authentication errors: prefer using SSH or Git Credential Manager + PAT.
- Permission errors: ensure your GitHub user (adarshprajapa123) has write access to the repo.
- Large files: GitHub rejects very large files; consider using Git LFS or removing large artifacts before pushing.

---
If you want, I can:
- Walk through these steps with you interactively.
- Attempt to run the push here if you provide temporary credentials (not recommended). Instead I can guide you to set up SSH or PAT on your machine.
