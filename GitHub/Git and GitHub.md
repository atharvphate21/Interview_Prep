### What is Git?
> Git is a distributed version control system used to track changes in source code. It allows multiple developers to work on the same project simultaneously without overwriting each other’s changes. Since it’s distributed, every developer has a full copy of the repository along with its history.

### What is Version Control?
> Version control is a system that tracks changes made to files over time. It helps us maintain history, collaborate with multiple developers, and revert to previous versions if something breaks. Git is an example of a distributed version control system.

### Difference between Git and GitHub?
> Git is a version control tool that we install locally to manage source code history. GitHub is a cloud platform that hosts Git repositories and provides collaboration features like pull requests, access control, and CI/CD integration.

### What is a Repository?
> A repository is a storage location where our project files and their entire version history are maintained. It contains source code, commits, branches, and configuration details. It can be either local on our system or remote on platforms like GitHub.

### What is a Working Directory?
> The working directory is the current project folder on my system where I create, edit, or delete files. These changes are not tracked by Git until I add them to the staging area.

### What is the Staging Area?
> The staging area is an intermediate area between the working directory and the repository. It allows me to selectively choose which changes I want to include in the next commit. So instead of committing everything, I can stage only specific files or changes.

### What is a Commit?
> A commit is a snapshot of the staged changes at a specific point in time. It saves the changes permanently in the repository along with metadata like author name, timestamp, and commit message.

### What is a Branch?
> A branch is a separate line of development. It allows me to work on new features or bug fixes without affecting the main branch. Once the work is completed and tested, I can merge it back into the main branch.

### What is HEAD in Git?
> HEAD is a pointer that refers to the current branch or the latest commit I am working on. Normally, it points to the latest commit of the current branch. If it’s in a detached state, it points directly to a specific commit instead of a branch.

### Difference between Local Repo and Remote Repo?
> A local repository is stored on my system and used for development work. A remote repository is hosted on platforms like GitHub and is used for collaboration. We push changes to the remote repository to share with the team and pull updates from it.


# 🔹 Repository & Setup

### How do you initialize a Git repository?
> To initialize a Git repository, I use the command `git init`. It creates a hidden `.git` folder inside the project directory, which starts tracking changes for that project.

### Difference between `git init` and `git clone`?
> `git init` is used to create a new repository from scratch in an existing project folder.
> `git clone` is used to copy an existing remote repository to my local system, including its history and branches.

### How do you configure username and email in Git?
> I configure it using:
> `git config --global user.name "My Name"`
> `git config --global user.email "myemail@example.com"`
> The `--global` flag sets it for all repositories on my system.

### What is `.gitignore` file?
> `.gitignore` is a file where we specify files or folders that Git should ignore.
> It is commonly used to exclude log files, build artifacts, environment files, and secrets from being tracked.

### How do you check Git configuration?
> I use `git config --list` to see all configurations.
> If I want to check a specific value, I use `git config user.name`.

# 🔹 Staging & Commit

### Difference between `git add .` and `git add -A`?
> `git add .` stages new and modified files in the current directory.
> `git add -A` stages all changes including deleted files across the entire repository.

### What is `git status`?
> `git status` shows the current state of the working directory and staging area.
> It tells me which files are modified, staged, or untracked.

### What is `git diff`?
> `git diff` shows the difference between the working directory and the staging area.
> It helps me see what changes I’ve made before committing.

### What is `git commit -m`?
> `git commit -m "message"` creates a commit with a message directly from the command line.
> It saves the staged changes permanently in the repository.

### What is `git commit --amend`?
> `git commit --amend` allows me to modify the last commit.
> I can change the commit message or add forgotten changes without creating a new commit.

### How do you undo the last commit?
> If I want to undo but keep changes, I use:
> `git reset --soft HEAD~1`
> If I want to completely remove it, I use:
> `git reset --hard HEAD~1`
> For shared branches, I prefer `git revert`.

### Difference between `git reset` and `git revert`?
> `git reset` moves the branch pointer backward and can rewrite history.
> `git revert` creates a new commit that reverses previous changes.
> In shared branches, revert is safer.

# 🔹 Branching

### How do you create a branch?
> I use `git branch branch-name` to create a branch.
> Or `git checkout -b branch-name` to create and switch in one step.

### How do you switch branches?
> I use `git switch branch-name` or `git checkout branch-name`.

### Difference between `git checkout` and `git switch`?
> `git checkout` is older and can switch branches or restore files.
> `git switch` is newer and specifically used for switching branches, making it clearer and safer.

### What is `git branch -d` vs `-D`?
> `-d` deletes a branch only if it is fully merged.
> `-D` force deletes the branch even if it’s not merged.

### What is an upstream branch?
> An upstream branch is the remote branch that my local branch tracks.
> It allows me to use simple commands like `git pull` and `git push` without specifying the remote branch.

### How do you rename a branch?
> I use `git branch -m old-name new-name` to rename a branch locally.

# 🔹 Merging & Rebasing

### What is merge?
> Merge combines changes from one branch into another and creates a new merge commit.

### What is rebase?
> Rebase moves the entire feature branch on top of another branch, rewriting history to create a linear structure.

### Difference between merge and rebase?
> Merge preserves history and creates a merge commit.
> Rebase rewrites history and creates a cleaner, linear commit structure.

### What is fast-forward merge?
> Fast-forward merge happens when there are no new commits in the target branch, so Git simply moves the branch pointer forward without creating a merge commit.

### What is merge conflict?
> A merge conflict occurs when two branches modify the same lines of code, and Git cannot decide which change to keep automatically.

### How do you resolve merge conflict?
> I open the conflicted file, remove the conflict markers, choose the correct changes, then stage the file and commit the resolution.

### What is interactive rebase?
> Interactive rebase, using `git rebase -i`, allows me to edit, squash, reorder, or remove commits before merging.

### When should you avoid rebase?
> I avoid rebasing public or shared branches because it rewrites history and can cause conflicts for other team members.

# 🔹 Stashing

### What is git stash?
> `git stash` temporarily saves uncommitted changes so I can switch branches without committing them.

### Difference between `stash pop` and `stash apply`?
> `stash pop` applies the stash and removes it from the stash list.
> `stash apply` applies it but keeps it in the stash list.

### How to stash specific files?
> I use `git stash push filename` to stash only specific files.

### How to list stashes?
> I use `git stash list` to see all saved stashes.
