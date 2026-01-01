Below is the **Git Cheat Sheet converted cleanly into Markdown**, preserving structure and making it easy to use as a README or documentation page.

---

# 🧰 Git Cheat Sheet

Git is a free and open-source distributed version control system responsible for everything GitHub-related that happens locally on your computer. This cheat sheet covers the most commonly used Git commands.

---

## 📌 Stage & Snapshot

*Working with snapshots and the Git staging area*

### Check status

```bash
git status
```

Show modified files in the working directory and staged files for the next commit.

### Stage a file

```bash
git add [file]
```

Add a file as it looks now to your next commit.

### Unstage a file

```bash
git reset [file]
```

Unstage a file while retaining changes in the working directory.

### View unstaged changes

```bash
git diff
```

Show differences not yet staged.

### View staged changes

```bash
git diff --staged
```

Show differences staged but not committed.

### Commit changes

```bash
git commit -m "descriptive message"
```

Commit staged content as a new snapshot.

---

## ⚙️ Setup

*Configuring user information for all repositories*

```bash
git config --global user.name "firstname lastname"
```

Set the name used for commits.

```bash
git config --global user.email "valid-email"
```

Set the email associated with commits.

```bash
git config --global color.ui auto
```

Enable automatic command-line coloring.

---

## 🚀 Setup & Init

*Initializing and cloning repositories*

### Initialize a repository

```bash
git init
```

### Clone a repository

```bash
git clone [url]
```

Retrieve a full repository from a remote URL.

---

## 🌿 Branch & Merge

*Isolating and integrating work*

### List branches

```bash
git branch
```

### Create a branch

```bash
git branch [branch-name]
```

### Switch branches

```bash
git checkout [branch-name]
```

### Merge branches

```bash
git merge [branch]
```

### View commit history

```bash
git log
```

---

## 🔄 Share & Update

*Working with remote repositories*

### Add remote

```bash
git remote add [alias] [url]
```

### Fetch changes

```bash
git fetch [alias]
```

### Merge remote branch

```bash
git merge [alias]/[branch]
```

### Push changes

```bash
git push [alias] [branch]
```

### Pull changes

```bash
git pull
```

---

## 🗂️ Tracking Path Changes

*Versioning file deletes and moves*

### Remove file

```bash
git rm [file]
```

### Move or rename file

```bash
git mv [old-path] [new-path]
```

### View moved paths

```bash
git log --stat -M
```

---

## 📦 Temporary Commits (Stashing)

*Save work temporarily*

### Save changes

```bash
git stash
```

### List stashes

```bash
git stash list
```

### Restore latest stash

```bash
git stash pop
```

### Delete stash

```bash
git stash drop
```

---

## 🧹 Rewrite History

*Modifying commit history*

### Rebase branch

```bash
git rebase [branch]
```

### Hard reset

```bash
git reset --hard [commit]
```

⚠ Clears staging area and rewrites working tree.

---

## 🔍 Inspect & Compare

*Reviewing commits and changes*

### Commit history

```bash
git log
```

### Compare branches

```bash
git log branchB..branchA
```

### File history across renames

```bash
git log --follow [file]
```

### Diff between branches

```bash
git diff branchB...branchA
```

### Show commit/object

```bash
git show [SHA]
```

---

## 🚫 Ignoring Patterns

*Prevent unintentional file tracking*

### Global ignore file

```bash
git config --global core.excludesfile [file]
```

### Example `.gitignore`

```gitignore
logs/
*.notes
pattern*/
```

---

## 🖥️ Installation & GUIs

* **GitHub for Windows**
  [https://windows.github.com](https://windows.github.com)

* **GitHub for Mac**
  [https://mac.github.com](https://mac.github.com)

* **Git (All Platforms)**
  [https://git-scm.com](https://git-scm.com)

---

## 🎓 GitHub Education

GitHub is free for students and teachers.
More info: [https://education.github.com](https://education.github.com)
Contact: [education@github.com](mailto:education@github.com)

---

If you want, I can also:

* Add **command explanations & examples**
* Turn this into a **one-page printable PDF**
* Create a **GitHub-flavored README**
* Add **visual diagrams for Git flow**

Just say the word 👍
