# Git & GitHub workflow guide

A complete reference covering every stage: starting a new project, cloning an existing one, the everyday update cycle, and occasional housekeeping.

## A) Starting a brand-new project (never pushed before)

**1. Go to your folder**
```bash
cd /path/to/your/folder
```

**2. Initialize git (if not already a repo)**
```bash
git status
git init
```

**3. Stage and commit**
```bash
git add .
git commit -m "initial commit"
```

**4. Create an empty repo on GitHub**
- Go to github.com → **+** → **New repository**
- Give it a name
- **Do not** add a README, .gitignore, or license
- Click **Create repository**

> Why empty? If you add a README, GitHub creates its own separate commit history. When you later push your local commits, the two histories won't have a common starting point, and the push gets rejected (or needs a merge with possible conflicts). Starting empty means your local history slides in cleanly.

**5. Connect it**
```bash
git remote add origin https://github.com/username/repo-name.git
git branch -M main
```
Why `branch -M main`: older Git versions default a new repo's branch to `master`, while GitHub now defaults new repos to `main`. If your local branch name doesn't match GitHub's, the push can fail or create a mismatched branch. This command force-renames your current branch to `main`. If `git status` already shows "On branch main," this step is a no-op — safe to run either way.

**6. Push**
```bash
git push -u origin main
```
If prompted for a password, use a **Personal Access Token** instead — create one at GitHub → Settings → Developer settings → Personal access tokens (with `repo` scope).

## B) Working with a repo that already exists on GitHub

**Clone it to your machine**
```bash
cd /path/to/where/you/want/it
git clone https://github.com/username/repo-name.git
cd repo-name
```
This creates a folder with all files and the full commit history already inside. `origin` is set up automatically.

## C) The everyday update cycle

Run this every time you add or change files — in either A or B repos:
```bash
git status
git add .
git commit -m "describe what changed"
git push
```
Note: after the first push, you don't need `-u origin main` again — plain `git push` works.

## D) Occasional housekeeping

**Rename a repo:**
- GitHub → repo → **Settings** → **General** → **Repository name** → **Rename**
- Then update your local remote:
```bash
git remote set-url origin https://github.com/username/new-repo-name.git
```

**Check your remote is correct:**
```bash
git remote -v
```
You should see the URL listed for both `fetch` and `push`.

---

## 🚀 How this repo was uploaded (VS Code → GitHub)

This section documents the exact workflow used to publish this folder, for reference and reuse on future cohorts.

### Step 1 — Open the folder in VS Code

- Launch VS Code
- **File → Open Folder**
- Select the `R-by-Nahid-Cohort-4` folder

### Step 2 — Open the Source Control panel

- Click the **Source Control** icon in the left sidebar
- Or use the shortcut: `Ctrl+Shift+G`

### Step 3 — Initialize the repository

- Click **Initialize Repository**
- This converts the folder into a Git repository

### Step 4 — Stage all files

- All files appear under **Changes**
- Hover over "Changes" → click the **+** icon to stage everything at once (works the same whether there are 5 files or 500)

### Step 5 — Commit

- Type a short message in the input box, e.g. `initial upload`
- Click **✓ Commit** (or `Ctrl+Enter`)

### Step 6 — Publish to GitHub

- Click **Publish Branch**
- Choose:
  - GitHub account (sign in if it's your first time)
  - Repository name (defaults to the folder name)
  - **Public** or **Private**
- VS Code creates the GitHub repo, connects it, and pushes everything — no manual commands required

✅ **Done.** All files are now live on GitHub.

---

## 🔁 Updating this repo later

Whenever new files are added or existing ones are edited:

| Step | Action |
|------|--------|
| 1 | Open Source Control panel (`Ctrl+Shift+G`) |
| 2 | Stage changed files (click **+**) |
| 3 | Write a commit message → click **✓ Commit** |
| 4 | Click **Sync Changes** (↑ icon) to push to GitHub |

> 💡 **Tip:** If working from more than one computer, always **Pull** (↓ icon) before making new changes, to avoid push conflicts.

---

## 🧠 Underlying concept

```
Edit file        →  Working directory   (changes exist only on your computer)
   ↓ stage (+)
Staging area      (marks "ready to save")
   ↓ commit
Local repository   (permanent snapshot, still local only)
   ↓ push / sync
GitHub             (now visible online)
```

VS Code's buttons are just a visual layer over the same Git commands (`git add`, `git commit`, `git push`) — nothing about the underlying process changes.

---

## 📚 Course content

| File type | Description |
|-----------|--------------|
| `Class-XX.R` | Weekly class scripts |
| `*.csv` | Practice datasets |
| `*.png` | Visualizations referenced in class |
| `quarto.qmd` / `quarto.html` | Rendered course notes |

---

## 🙋 Maintained by

**Nahid** — Omics Learning Center
Cancer biology & bioinformatics education, in English and Bangla.

**Quick map:**
- **A** → folder that's never touched GitHub
- **B** → joining or continuing work on a repo that already exists
- **C** → the loop you'll run constantly, regardless of A or B
- **D** → as-needed
