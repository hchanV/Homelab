# Git Common Commands


```bash
git status
Shows what changed.

git add <file-or-folder>
Stages a file or folder for the next commit.

git commit -m "message describing the change"
Creates a local checkpoint on your computer.

git push
Uploads commits to GitHub.

git stash
Temporarily saves your current changes and cleans your working folder.

Use this when you want to ask:
Can Git set my unfinished work aside for a bit?

git add *.md
Stages Markdown files in the current folder.

git add docs/
Stages everything inside the docs folder.

git add docs/**/*.md
Stages Markdown files inside docs and its subfolders.

git diff
Shows changes in your working files compared to the last commit.

Use this before staging if you want to review what you changed.

git diff --staged
Shows changes that are staged and ready to commit.

Use this before committing if you want to double-check what will be saved.

git show <commit-hash>
Shows details and file changes from a specific commit.

Commit all changes
git status
git add .
git commit -m "Describe what changed"
git push

Stage absolutely everything in the repo
git add -A
git commit -m "Describe what changed"
git push

Rename a file or folder
mv old-name new-name

Delete a file
rm filename.md

Delete a folder

rmdir folder-name
