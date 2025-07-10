# Git & GitHub Cheatsheet

## Essential Terminal Commands
```bash
pwd                    # Print working directory
ls                     # List directory contents
cd directory-name      # Change directory
```

## Git Setup & Configuration
```bash
git --version                        # Check Git version
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --list                    # View configuration
```

## Repository Initialization
```bash
git init                            # Initialize current directory
git init directory-name             # Create new repo with directory
git clone URL                       # Clone remote repository
git clone URL new-name              # Clone and rename
```

## Basic Workflow
```bash
git status                          # Check repository status
git add filename                    # Stage specific file
git add .                          # Stage all changes
git commit -m "commit message"     # Commit with message
git commit -am "message"           # Stage and commit tracked files
```

## Viewing History & Changes
```bash
git log                            # View commit history
git log --oneline                  # Compact log format
git log -n 5                       # Show last 5 commits
git log --since="2 weeks ago"      # Filter by date
git log --until="2024-01-01"       # Filter until date
git log filename                   # History for specific file
git show commit-hash               # Show specific commit
```

## Comparing Changes
```bash
git diff                           # Working directory vs last commit
git diff --staged                  # Staged changes vs last commit
git diff filename                  # Specific file changes
git diff commit1 commit2           # Compare two commits
git diff HEAD~1 HEAD               # Compare with previous commit
git diff branch1 branch2           # Compare branches
```

## Branch Management
```bash
git branch                         # List all branches
git branch branch-name             # Create new branch
git switch branch-name             # Switch to branch
git switch -c new-branch          # Create and switch
git checkout branch-name           # Alternative switch command
git branch -m old-name new-name    # Rename branch
git branch -d branch-name          # Delete merged branch
git branch -D branch-name          # Force delete branch
```

## Merging & Rebasing
```bash
git merge branch-name              # Merge branch into current
git merge --no-ff branch-name      # Force merge commit
git merge --squash branch-name     # Squash merge
git rebase main                    # Rebase current branch onto main
git rebase -i HEAD~3               # Interactive rebase last 3 commits
```

## Remote Operations
```bash
git remote                         # List remotes
git remote -v                      # List remotes with URLs
git remote add name URL            # Add remote
git remote remove name             # Remove remote
git fetch origin                   # Fetch from remote
git pull origin branch-name        # Fetch and merge
git push origin branch-name        # Push to remote
git push -u origin branch-name     # Push and set upstream
```

## Undoing Changes
```bash
git restore filename               # Discard working directory changes
git restore --staged filename      # Unstage file
git checkout HEAD~1 -- filename    # Restore file from previous commit
git revert commit-hash             # Revert commit (creates new commit)
git revert --no-edit HEAD          # Revert without editor
git reset --soft HEAD~1            # Undo last commit, keep changes staged
git reset --mixed HEAD~1           # Undo last commit, unstage changes
git reset --hard HEAD~1            # Undo last commit, discard changes
```

## Stashing
```bash
git stash                          # Stash current changes
git stash push -m "message"        # Stash with message
git stash list                     # List stashes
git stash apply                    # Apply latest stash
git stash apply stash@{n}          # Apply specific stash
git stash drop                     # Delete latest stash
git stash pop                      # Apply and delete latest stash
```

## Advanced Git Commands
```bash
git cherry-pick commit-hash        # Apply commit to current branch
git bisect start                   # Start bisect debugging
git bisect bad                     # Mark current as bad
git bisect good commit-hash        # Mark commit as good
git bisect reset                   # Exit bisect mode
git reflog                         # View reference log
git worktree add path branch       # Create worktree
git worktree list                  # List worktrees
git worktree remove path           # Remove worktree
```

## Git LFS (Large File Storage)
```bash
git lfs install                    # Initialize LFS
git lfs track "*.csv"             # Track file types
git lfs track "*.zip"             # Track zip files
git lfs pull                      # Download LFS content
git lfs ls-files                  # List tracked files
```

## Submodules
```bash
git submodule add URL path         # Add submodule
git submodule status               # List submodules
git submodule update --init        # Initialize submodules
git submodule update --remote      # Update submodules
git submodule deinit name          # Remove submodule
```

## GitHub CLI Commands
```bash
gh auth login                      # Authenticate with GitHub
gh repo create repo-name           # Create repository
gh repo clone owner/repo           # Clone repository
gh issue create                    # Create issue
gh issue list                      # List issues
gh pr create                       # Create pull request
gh pr list                         # List pull requests
gh pr merge                        # Merge pull request
```

## Git Aliases (Add to .gitconfig)
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
git config --global alias.lg "log --oneline --decorate --graph --all"
```

## Markdown Formatting (README.md)
```markdown
# Heading 1
## Heading 2
### Heading 3

**Bold text**
*Italic text*
`Code`
```code block```

[Link text](URL)
![Image alt text](image-url)

- Bullet point
1. Numbered list

| Column 1 | Column 2 |
|----------|----------|
| Data 1   | Data 2   |
```

## Common Git Patterns
```bash
# Feature branch workflow
git switch main
git pull origin main
git switch -c feature-branch
# ... make changes ...
git add .
git commit -m "Add feature"
git push origin feature-branch
# ... create PR on GitHub ...
git switch main
git pull origin main
git branch -d feature-branch

# Hotfix workflow
git switch main
git switch -c hotfix-branch
# ... fix issue ...
git add .
git commit -m "Fix critical bug"
git push origin hotfix-branch
# ... merge immediately ...

# Sync fork with upstream
git remote add upstream URL
git fetch upstream
git switch main
git merge upstream/main
git push origin main
```

## Gitignore Examples
```gitignore
# OS generated files
.DS_Store
Thumbs.db

# IDE files
.vscode/
.idea/
*.swp
*.swo

# Language specific
node_modules/
__pycache__/
*.pyc
*.pyo
.env
.venv/
venv/

# Build artifacts
dist/
build/
*.egg-info/

# Logs
*.log
logs/

# Database
*.db
*.sqlite3

# Sensitive data
.env
config.json
secrets.txt
```

## Troubleshooting Commands
```bash
git status                         # Check current state
git log --oneline -10             # Recent commits
git remote -v                     # Check remotes
git branch -a                     # All branches
git fetch --all                   # Fetch all remotes
git clean -fd                     # Remove untracked files/dirs
git fsck                          # Check repository integrity
git gc                            # Garbage collection
```

## Emergency Recovery
```bash
# Recover deleted branch
git reflog
git checkout -b recovered-branch commit-hash

# Recover lost commits
git reflog
git cherry-pick commit-hash

# Undo last commit but keep changes
git reset --soft HEAD~1

# Remove file from Git but keep locally
git rm --cached filename
```

## Performance & Maintenance
```bash
git gc --aggressive               # Aggressive garbage collection
git prune                        # Remove unreachable objects
git fsck --full                  # Full file system check
git count-objects -vH            # Repository size info
git log --all --graph --oneline  # Visualize branch structure
```

---

*Quick Reference: Always check `git status` before major operations*