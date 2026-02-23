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

# 🔹 Git Internals (Devops)

### What are Git objects?
> Git stores data as objects in its database. There are four main types of Git objects:
> **Blob** – stores file content
> **Tree** – stores directory structure
> **Commit** – stores metadata like author, message, and pointer to tree
> **Tag** – stores tag information
>
> Every object is identified by a unique SHA hash.

### What is SHA in Git?
> SHA stands for Secure Hash Algorithm.
> Git uses SHA-1 to generate a unique 40-character hash for every commit and object.
> This ensures data integrity because even a small change in the file generates a completely different hash.

### What is Detached HEAD?
> Detached HEAD happens when I checkout a specific commit instead of a branch.
> In this state, HEAD points directly to a commit, not a branch.
> If I make new commits, they may be lost unless I create a new branch.

### What is Git reflog?
> Reflog records all changes made to HEAD, including commits that were reset or deleted.
> It is mainly used for recovery purposes, like restoring lost commits after a reset or force push.

### What is Git cherry-pick?
> Git cherry-pick allows me to apply a specific commit from one branch onto another branch.
> It is useful when I want to move a single bug fix without merging the entire branch.

### What is Git tag?
> A Git tag is used to mark a specific commit, usually for releases like v1.0 or v2.1.
> It helps in versioning and production deployments.

### Difference between Lightweight Tag and Annotated Tag?
> A lightweight tag is just a pointer to a commit.
> An annotated tag contains additional metadata like author name, date, and message.
> For production releases, we usually use annotated tags.

### What is Git bisect?
> Git bisect is used to find the commit that introduced a bug.
> It works using binary search by marking commits as good or bad until the problematic commit is identified.

### What is a Git submodule?
> A submodule allows me to include another Git repository inside my main repository as a dependency.
> It keeps the external project separate but linked at a specific commit.

### What is Git subtree?
> Git subtree also allows including another repository, but unlike submodule, it merges the external project directly into the main repository.
> It is easier to manage because it does not require separate initialization or cloning steps.

# 🔹 GitHub-Specific Answers

### What is GitHub?
> GitHub is a cloud-based platform that hosts Git repositories and provides collaboration features like pull requests, code reviews, access control, issue tracking, and CI/CD integration.
> It helps teams collaborate efficiently on software projects.

### What is a Pull Request?
> A Pull Request is a GitHub feature used to propose changes from one branch to another.
> It allows team members to review the code, discuss changes, run automated tests, and approve the changes before merging into the main branch.

### Difference between Pull Request and Merge Request?
> Functionally, they are the same.
> GitHub calls it a Pull Request, while GitLab calls it a Merge Request.
> Both are used for code review and merging changes into a target branch.

### What is a fork in GitHub?
> A fork is a copy of someone else’s repository into my own GitHub account.
> It allows me to make changes independently without affecting the original repository.
> Forking is commonly used in open-source contributions.

### What is GitHub Actions?
> GitHub Actions is GitHub’s built-in CI/CD tool.
> It allows us to automate workflows like build, test, security scanning, and deployment whenever events like push or pull request occur.

### What is a GitHub workflow file?
> A GitHub workflow file is a YAML file stored inside `.github/workflows/` directory.
> It defines automation steps, triggers, jobs, and actions to run in the CI/CD pipeline.

### What is a GitHub runner?
> A GitHub runner is a server that executes GitHub Actions workflows.
> It can be GitHub-hosted or self-hosted, depending on project requirements.

### What is a protected branch?
> A protected branch is a branch with restrictions applied to it.
> For example, it can require pull request reviews, prevent direct pushes, enforce status checks, and block force pushes.
> It is commonly used for main or production branches.

### What is a CODEOWNERS file?
> A CODEOWNERS file defines specific people or teams responsible for reviewing certain files or directories.
> When a pull request modifies those files, the defined owners are automatically requested for review.

### What is a GitHub webhook?
> A webhook is a mechanism that sends real-time HTTP notifications when certain events happen in a repository, like push or pull request creation.
> It is commonly used to trigger external CI/CD tools like Jenkins.

# 🔐 Authentication & Security

### Why is password authentication removed from GitHub?
> GitHub removed password authentication for security reasons.
> Passwords are vulnerable to brute-force attacks and leaks.
> Instead, GitHub now uses more secure methods like Personal Access Tokens and SSH keys, which provide better access control and expiration management.

### What is a Personal Access Token (PAT)?
> A Personal Access Token is a secure token used instead of a password for HTTPS authentication in GitHub.
> It allows granular permissions like read-only or full repository access and can be revoked anytime.
> It improves security compared to traditional passwords.

### Difference between HTTPS and SSH authentication?
> HTTPS authentication uses a username and Personal Access Token.
> SSH authentication uses a public-private key pair.
>
> SSH is generally more secure and convenient for developers because once configured, it doesn’t require entering credentials repeatedly.

### How do you generate an SSH key?
> I generate an SSH key using:
> `ssh-keygen -t ed25519 -C "myemail@example.com"`
> This creates a public and private key pair in the `.ssh` directory.

### How do you add an SSH key to GitHub?
> First, I copy the public key using:
> `cat ~/.ssh/id_ed25519.pub`
>
> Then I go to GitHub → Settings → SSH and GPG keys → New SSH Key, and paste the public key there.

### What is GPG signing in Git?
> GPG signing is used to cryptographically sign commits and tags.
> It verifies that the commit was actually made by the claimed author and has not been tampered with.
> It improves authenticity and security of commits.

### How do you restrict force push?
> We restrict force push by enabling branch protection rules in GitHub.
> In protected branches like main, we disable force push and require pull request approvals before merging.

👉 *“How do you secure production branches?”*
> We use protected branches with required pull request reviews, status checks from CI pipelines, no direct pushes, and no force pushes. We also use role-based access control and least privilege access.

# 🚀 DevOps Scenario-Based Git Answers

### Your teammate force-pushed and deleted commits. How do you recover?
> First, I would check `git reflog` locally to find the lost commit hash because reflog tracks all HEAD movements.
> Once I identify the correct commit, I create a new branch from that commit and push it back to remote.
>
> If it’s not available locally, I would check with other team members who may still have the commit in their local repositories.

### You accidentally committed secrets. What will you do?
> First, I would immediately rotate or revoke the exposed credentials.
> Then I would remove the secret from the code and rewrite Git history using tools like `git filter-repo` or BFG to permanently remove it.
> After that, I would force push the cleaned history and inform the team.
>
> To prevent this in the future, I would use `.gitignore` and secret scanning tools.

### How do you manage multiple environments (dev/stage/prod) using Git?
> We usually manage environments using separate branches or configuration files.
> For example:
>
> * `develop` branch for dev
> * `release` branch for staging
> * `main` branch for production
>
> We also use environment-specific configuration variables in CI/CD pipelines instead of hardcoding them in Git.

### How do you implement Git branching strategy in CI/CD?
> Each branch triggers a different pipeline workflow.
> For example:
>
> * Feature branch → run build & unit tests
> * Develop branch → deploy to dev environment
> * Main branch → deploy to production
>
> CI/CD pipelines are configured to trigger automatically on push or pull request events.

### What is GitFlow?
> GitFlow is a branching strategy that uses separate branches for feature development, releases, and hotfixes.
> It includes:
>
> * `main` for production
> * `develop` for integration
> * `feature/*`
> * `release/*`
> * `hotfix/*`
>
> It is useful for large teams and structured release cycles.

### What is trunk-based development?
> In trunk-based development, developers frequently merge small changes directly into the main branch.
> Branches are short-lived, and CI runs continuously.
> It supports faster delivery and works well with modern DevOps practices.

### How do you handle hotfix in production?
> I create a `hotfix` branch from the main production branch.
> After fixing and testing the issue, I merge it back into main and also into develop to keep branches synchronized.
> Then I tag the release and trigger deployment.

### How do you revert a faulty deployment?
> If we use version tagging, I would redeploy the previous stable tag.
> If needed, I would use `git revert` to create a new commit that undoes the faulty changes.
>
> In CI/CD, we usually redeploy the previous stable Docker image tagged with the commit SHA.

### How do you resolve long-running branch conflicts?
> I avoid long-running branches as much as possible.
> But if they exist, I regularly merge the main branch into the feature branch to reduce conflicts.
> During conflict resolution, I carefully review changes, test thoroughly, and ensure CI passes before merging.

### How do you ensure code quality before merge?
> We enforce pull request reviews, require at least one approval, and enable CI checks like unit tests, linting, and security scans.
> We also protect the main branch and prevent direct pushes.

👉 *“How do you ensure traceability in production?”*
> We use annotated Git tags and commit SHA for Docker image tagging. This ensures we can trace every deployment back to a specific commit.

# 🚀 Git in CI/CD (DevOps-Focused)

### ✅ 1. How does Git integrate with Jenkins?
> Jenkins integrates with Git using plugins like the Git Plugin.
> When code is pushed to a repository, Jenkins pulls the latest code from Git and triggers the pipeline.
>
> The pipeline then performs stages like build, test, scan, Docker build, and deployment.
>
> In most setups, this trigger happens through webhooks.

### ✅ 2. How does GitHub Actions trigger a pipeline?
> GitHub Actions is event-driven.
> When an event like push, pull request, or tag creation occurs, it triggers the workflow defined in a YAML file inside `.github/workflows/`.
>
> The workflow then runs jobs on a GitHub runner.

### ✅ 3. What is a webhook in CI/CD?
> A webhook is a mechanism that sends an HTTP POST request to a configured URL when a specific event occurs in Git, like a push or pull request.
>
> For example, when code is pushed to GitHub, a webhook notifies Jenkins to start the pipeline automatically.

### ✅ 4. What is shallow clone?
> A shallow clone is when we clone a repository with limited commit history using:
> `git clone --depth=1`
>
> It improves pipeline performance by downloading only the latest commit instead of the full history.

### ✅ 5. Why use specific commit SHA in deployments?
> Using a specific commit SHA ensures traceability and reproducibility.
> It guarantees that the exact same version of code can be deployed again if needed.
>
> It also helps in debugging and auditing deployments.

### ✅ 6. What is commit hash used for in Docker image tagging?
> The commit hash is often used as a Docker image tag to uniquely identify the build.
>
> For example:
> `myapp:3f2a1c7`
>
> This ensures every Docker image is directly linked to a specific Git commit.

### ✅ 7. How do you rollback to previous version using Git?
> If we use Git tags for releases, I checkout the previous stable tag and redeploy it.
>
> In CI/CD, we usually redeploy the previous Docker image built from the stable commit SHA.

### ✅ 8. What is tagging strategy in production?
> In production, we use semantic versioning like `v1.0.0`, `v1.1.0`, or `v2.0.1`.
>
> Each production release is marked with an annotated tag.
>
> CI/CD pipelines are configured to trigger deployment when a production tag is created.

👉 *“How do you ensure safe production deployment?”*
> We use protected branches, required pull request approvals, automated CI checks, version tagging, and deployment based on specific commit SHA to ensure safe and traceable production releases.

# 🚀 Advanced Git

### ✅ 1. Explain Git rebase vs cherry-pick with real example.
> Rebase is used to move an entire branch on top of another branch, rewriting commit history to make it linear.
>
> Cherry-pick is used to apply a specific commit from one branch onto another branch.
>
> For example, if I have a feature branch with 5 commits and I want to update it with the latest main branch changes, I use rebase.
>
> But if I only need one bug-fix commit from another branch, I use cherry-pick instead of merging the entire branch.

### ✅ 2. How does Git handle large files?
> Git is optimized for text files and tracks changes efficiently using compression and snapshots.
> However, it does not handle large binary files efficiently because it stores full snapshots instead of diffs for binaries.
>
> For large files, we use Git LFS.

### ✅ 3. What is Git LFS?
> Git LFS, or Large File Storage, is an extension that replaces large files with pointers inside Git.
> The actual large files are stored separately on a remote server.
>
> This helps keep the repository lightweight and improves clone performance.

### ✅ 4. How do you squash commits?
> I squash commits using interactive rebase:
> `git rebase -i HEAD~n`
>
> Then I mark multiple commits as "squash" to combine them into a single commit.
>
> This is useful before merging feature branches to keep clean commit history.

### ✅ 5. What happens internally when you run `git commit`?
> When I run `git commit`, Git:
>
> 1. Takes staged files
> 2. Creates blob objects for file contents
> 3. Creates a tree object representing directory structure
> 4. Creates a commit object with metadata and parent reference
> 5. Updates the branch pointer
>
> Each object is stored with a unique SHA hash.

### ✅ 6. What is a pack file?
> A pack file is a compressed file where Git stores multiple objects together to optimize storage and improve performance.
>
> Instead of storing each object separately, Git compresses them into pack files, especially during operations like `git gc`.

### ✅ 7. How do you optimize Git repository size?
> To optimize repo size:
>
> * Remove large unnecessary files
> * Use Git LFS for large binaries
> * Clean history using `git filter-repo` if needed
> * Run `git gc` to clean unused objects
>
> Regular maintenance keeps repository lightweight.

### ✅ 8. What is a bare repository?
> A bare repository does not contain a working directory.
> It only contains Git data and is typically used as a central remote repository for collaboration.

### ✅ 9. What is a Git hook?
> A Git hook is a script that runs automatically when certain Git events occur, like commit, push, or merge.
>
> Hooks are used to enforce rules such as code formatting, linting, or preventing commits with secrets.

### ✅ 10. Difference between pre-commit and post-commit hooks?
> A pre-commit hook runs before a commit is created. It can block the commit if validation fails.
>
> A post-commit hook runs after the commit is successfully created and cannot prevent it.

👉 *“Why avoid rebase on shared branches?”*
> Because rebase rewrites commit history, and rewriting shared history can cause conflicts and confusion for other developers.

### How to delete a remote branch?
> I delete a remote branch by pushing an empty reference to it.

```bash
git push origin --delete branch-name
```

(Alternative)

```bash
git push origin :branch-name
```

### How to undo last 2 commits but keep changes?
> I reset HEAD back by 2 commits while keeping my changes.

Keep changes staged:

```bash
git reset --soft HEAD~2
```

Keep changes unstaged (in working directory):

```bash
git reset --mixed HEAD~2
```

### How to remove a file from staging?
> I unstage the file without deleting it.

```bash
git restore --staged filename
```

(Older way)

```bash
git reset HEAD filename
```

### How to move commits from one branch to another?
> If I need specific commits, I use cherry-pick.

```bash
git checkout target-branch
git cherry-pick <commit1> <commit2>
```

> If I want to move the *latest* commits, I can also rebase the branch onto target, but cherry-pick is safer for selective commits.

### How to check who changed a specific line?
> I use blame to see author and commit for each line.

```bash
git blame filename
```

For specific lines:

```bash
git blame -L 20,40 filename
```

### How to find when a bug was introduced?
> I use `git bisect` to binary search the exact commit that introduced the bug.

```bash
git bisect start
git bisect bad
git bisect good <known-good-commit>
```

Then Git guides me commit by commit; after finding:

```bash
git bisect reset
```

### How to compare two branches?
> I compare branches using diff.

Files/changes between branches:

```bash
git diff branch1..branch2
```

Only commit list difference:

```bash
git log branch1..branch2 --oneline
```

### How to clone a specific branch?
> I clone only one branch to save time and space.

```bash
git clone -b branch-name --single-branch <repo-url>
```

### How to pull without a merge commit?
> I pull using rebase so it doesn’t create a merge commit.

```bash
git pull --rebase
```

(Or set it permanently)

```bash
git config --global pull.rebase true
```

### How to resolve a rebase conflict?
> During rebase, if conflicts happen, I resolve them file by file, stage them, then continue the rebase.

Steps:

```bash
git status
# fix conflicts in files
git add <fixed-files>
git rebase --continue
```

If I want to abort:

```bash
git rebase --abort
```

If I want to skip that commit:

```bash
git rebase --skip
```

### How do you manage code reviews?
> We use Pull Requests for every change. We require at least one or two approvals, keep PRs small, and use a checklist: functionality, readability, tests, security, and rollback impact. CI must pass before merge, and we use review comments + suggestions to improve quality.

### How do you enforce branch protection?
> We enable branch protection rules on `main` (and sometimes `release/*`). We require PR reviews, passing status checks, up-to-date branches, and we disable force push and deletion. For critical repos, we also enforce CODEOWNERS reviews.

### How do you prevent direct push to main branch?
> We protect the `main` branch and remove direct push permissions. Only PR merges are allowed, and merges require approvals plus CI checks. This ensures every production change is reviewed and tested.

### How do you manage a monorepo?
> In a monorepo, we enforce clear folder ownership, consistent structure, and CODEOWNERS per directory. CI is optimized to run only affected tests using path filters. We also standardize tooling, versioning approach, and enforce quality gates for shared modules.

### How do you handle multiple contributors?
> We follow a branching strategy like feature branches + PRs, use clear naming conventions, and enforce review + CI. We also keep good documentation, issue templates, and use labels/milestones. Regular syncs and small PRs reduce conflicts and speed up reviews.

### What is semantic versioning?
> Semantic versioning is a version format like `MAJOR.MINOR.PATCH`, for example `2.4.1`.
> **MAJOR** for breaking changes, **MINOR** for backward-compatible features, and **PATCH** for backward-compatible bug fixes.

### How do you tag a release?
> We tag the commit that represents the release, usually on `main`. We prefer annotated tags for production releases. Then CI/CD can deploy based on that tag.

(If they want command)

```bash
git tag -a v1.2.0 -m "Release v1.2.0"
git push origin v1.2.0
```

### How do you create release notes?
> We create release notes from merged PRs between two tags. We summarize features, fixes, breaking changes, and known issues. In GitHub, we often use “Generate release notes” and ensure it’s categorized using labels like feature/bugfix/breaking-change.

### How do you automate versioning?
> We automate versioning using commit conventions and CI pipelines. For example, Conventional Commits + semantic-release can automatically decide whether to bump major/minor/patch, create tags, generate changelogs, and publish releases.

### How do you manage open-source contributions?
> We use forks and pull requests. Contributors work on feature branches in their fork, then open a PR to the upstream repo. We enforce contribution guidelines, coding standards, CI checks, and maintainers review before merging. We also use issues for discussion and clear templates to reduce back-and-forth.

### Difference between `git fetch` and `git pull`?
> **Fetch** downloads updates from the remote into my local repo but doesn’t change my working branch.
> **Pull** downloads the updates and immediately merges or rebases them into my current branch.
> So, **pull = fetch + merge (or rebase)**.

### Difference between `git reset --soft`, `--mixed`, `--hard`?
> They all move HEAD back, but differ in what they keep:
* **`--soft`**: keeps changes **staged** (index unchanged).
  *Use when I want to redo commits but keep everything ready to commit.*
* **`--mixed`** (default): keeps changes **unstaged** (resets staging area).
  *Use when I want changes back in working directory.*
* **`--hard`**: discards changes from **staging and working directory**.
  *Use carefully—it can delete work.*

### Can we rebase a public branch?
> **Generally, no.**
> Rebasing a public/shared branch rewrites history, so teammates who already pulled it will face conflicts and confusion.
> If it’s absolutely required, we coordinate with the team and force-push carefully—but best practice is **avoid rebasing public branches**.

### What happens if two people push the same branch?
> If two people push different commits to the same branch, the second push usually gets rejected with a **non-fast-forward** error because the remote branch has new commits.
> The correct approach is: **pull/rebase latest changes, resolve conflicts if any, then push again**.
> If someone force-pushes, it can overwrite others’ work—so we prevent that using branch protection.

### Can Git track empty directories?
> **No.** Git tracks files, not empty folders.
> If we need to keep an empty directory in the repo, we typically add a placeholder file like `.gitkeep` (or a README) inside it.