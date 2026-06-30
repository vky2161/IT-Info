# 1. What is GitHub?

GitHub is a cloud platform used to:
- Store Git repositories
- Backup code/notes
- Sync files between devices
- Track changes (version control)

It works with Git.

---

# 2. Create GitHub Account

Step 1:
Open website:

https://github.com

Step 2:
Click → Sign up

Step 3:
Enter:
- Email address
- Password
- Username

Step 4:
Verify email

Step 5:
Login to account

---

# 3. Setup GitHub Profile (Optional but recommended)

Go to:
Settings → Profile

Fill:
- Name
- Bio (optional)
- Profile URL (optional)

Profile URL example:
https://github.com/yourusername

---

# 4. Install Git (Required for local system)

Download Git:

https://git-scm.com/downloads

Install with default settings.

Verify:

```
git --version
```

---

# 5. Configure Git (IMPORTANT - ONE TIME SETUP)

Run these commands:

git config --global user.name "Your Name"
git config --global user.email "your_email@gmail.com"

Check:

```
git config --list
```

---

# 6. Create GitHub Repository

Step 1:
Login to GitHub

Step 2:
Click → New repository

Step 3:
Fill:
- Repository name (example: IT-Docs)
- Description (optional)
- Public / Private

Step 4:
Click → Create repository

---

# 7. Copy Repository URL

Click green "Code" button

Copy:

https://github.com/username/repo.git

---

# 8. Connect Local Folder to GitHub

Go to your project folder:

cd D:\files\

Initialize Git:

git init

Add remote:

git remote add origin https://github.com/username/repo.git

---

# 9. Add Files to Git

Add all files:

```shell
git add .
```

Commit:

```
git commit -m "Initial commit"

```
---

# 10. Push to GitHub

First push:

```
git branch -M main
git push -u origin main
```

---

# 11. Authentication (IMPORTANT)

GitHub does NOT accept password anymore.

Use:
- Personal Access Token (PAT)

Create here:
https://github.com/settings/tokens

Use token as password during push.

---

# 12. Daily Workflow (After setup)

Use only these commands:

```
git add .
git commit -m "update notes"
git push
```

---

# 13. Important Concepts

Git:
- Local version control system

GitHub:
- Cloud storage for Git

Repository:
- Project folder on GitHub

Commit:
- Save snapshot of changes

Push:
- Upload to GitHub

Pull:
- Download from GitHub

---

# 14. Best Practice for Obsidian

Recommended:
- Track only .md files
- Ignore .obsidian folder

Create .gitignore:

.obsidian/