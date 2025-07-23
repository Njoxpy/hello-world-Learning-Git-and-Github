# Branching Basics

Branching is one of Git's most powerful features, allowing you to diverge from the main line of development and work on different features or experiments in isolation.

## What is a Branch?

A **branch** in Git is essentially a movable pointer to a specific commit. Think of it as a lightweight, independent line of development where you can make changes without affecting other branches.

```mermaid
gitgraph
    commit id: "Initial commit"
    commit id: "Add homepage"
    branch feature/user-auth
    checkout feature/user-auth
    commit id: "Add login form"
    commit id: "Add authentication"
    checkout main
    commit id: "Fix homepage bug"
    merge feature/user-auth
    commit id: "Merge user auth"
```

## Why Use Branches?

### Benefits of Branching 🌟

1. **Isolation**: Work on features without affecting main code
2. **Experimentation**: Try new ideas safely
3. **Collaboration**: Multiple developers work simultaneously
4. **Organization**: Separate different types of work
5. **History**: Maintain clean project history

### Common Use Cases

- **Feature Development**: New functionality
- **Bug Fixes**: Isolate and fix issues
- **Experiments**: Test new approaches
- **Releases**: Prepare and maintain releases
- **Hotfixes**: Quick production fixes

## Basic Branch Operations

### Viewing Branches

```bash
# List local branches
git branch

# List all branches (local and remote)
git branch -a

# List remote branches only
git branch -r

# Show current branch
git branch --show-current
```

### Creating Branches

```bash
# Create new branch (doesn't switch to it)
git branch feature/new-login

# Create and switch to new branch
git checkout -b feature/new-login

# Modern way (Git 2.23+)
git switch -c feature/new-login
```

### Switching Branches

```bash
# Switch to existing branch
git checkout main
git checkout feature/new-login

# Modern way (Git 2.23+)
git switch main
git switch feature/new-login

# Switch to previous branch
git switch -
```

### Deleting Branches

```bash
# Delete merged branch (safe)
git branch -d feature/completed-feature

# Force delete branch (even if not merged)
git branch -D feature/abandoned-feature

# Delete remote branch
git push origin --delete feature/old-feature
```

## Branch Naming Conventions

### Popular Patterns

```bash
# Feature branches
feature/user-authentication
feature/payment-integration
feat/shopping-cart

# Bug fix branches
bugfix/login-error
fix/header-alignment
hotfix/security-patch

# Release branches
release/v1.2.0
release/2024-q1

# Experimental branches
experiment/new-ui
spike/performance-test
```

### Best Practices for Naming

- ✅ Use descriptive names
- ✅ Include ticket/issue numbers when relevant
- ✅ Use consistent prefixes
- ✅ Avoid spaces (use hyphens or underscores)
- ✅ Keep names concise but clear

```bash
# Good examples
feature/user-profile-page
bugfix/issue-123-login-crash
hotfix/security-vulnerability-cve-2024-001

# Avoid
feature/stuff
fix/bug
new-branch
```

## Working with Branches

### Complete Branch Workflow

```bash
# 1. Start from main branch
git switch main
git pull origin main

# 2. Create feature branch
git switch -c feature/user-dashboard

# 3. Make changes and commit
echo "Dashboard content" > dashboard.html
git add dashboard.html
git commit -m "Add user dashboard page"

# 4. Push branch to remote
git push -u origin feature/user-dashboard

# 5. Continue development
echo "More dashboard features" >> dashboard.html
git add dashboard.html
git commit -m "Add dashboard widgets"
git push

# 6. When feature is complete, merge back to main
git switch main
git pull origin main
git merge feature/user-dashboard

# 7. Clean up
git branch -d feature/user-dashboard
git push origin --delete feature/user-dashboard
```

### Keeping Branches Updated

```bash
# Update your feature branch with latest main
git switch feature/my-feature
git merge main

# Or rebase (cleaner history)
git rebase main

# Push updated branch
git push --force-with-lease origin feature/my-feature
```

## Branch Types and Strategies

### Main Branches

#### main/master
- **Purpose**: Primary development branch
- **Characteristics**: Always deployable
- **Protection**: Often protected from direct pushes

#### develop
- **Purpose**: Integration branch for features
- **Characteristics**: Latest development changes
- **Usage**: Common in Git Flow workflow

### Supporting Branches

#### Feature Branches
```bash
# Branch from: develop or main
# Merge back to: develop or main
# Naming: feature/* or feat/*

git switch -c feature/user-notifications develop
# ... work on feature ...
git switch develop
git merge --no-ff feature/user-notifications
```

#### Release Branches
```bash
# Prepare new release
git switch -c release/1.2.0 develop
# ... final testing and bug fixes ...
git switch main
git merge --no-ff release/1.2.0
git tag v1.2.0
```

#### Hotfix Branches
```bash
# Quick production fix
git switch -c hotfix/critical-bug main
# ... fix the bug ...
git switch main
git merge --no-ff hotfix/critical-bug
git switch develop
git merge --no-ff hotfix/critical-bug
```

## Advanced Branch Operations

### Branch Comparison

```bash
# See differences between branches
git diff main..feature/new-feature

# Show commits in feature branch not in main
git log main..feature/new-feature --oneline

# Show commits in both branches
git log --oneline --graph main feature/new-feature
```

### Branch Information

```bash
# Show branch with last commit
git branch -v

# Show merged branches
git branch --merged

# Show unmerged branches
git branch --no-merged

# Show branches and their tracking info
git branch -vv
```

### Renaming Branches

```bash
# Rename current branch
git branch -m new-branch-name

# Rename another branch
git branch -m old-name new-name

# Update remote tracking
git push origin -u new-name
git push origin --delete old-name
```

## Branch Protection and Rules

### GitHub Branch Protection

On GitHub, you can protect branches with rules:

1. **Require pull requests**: No direct pushes
2. **Require status checks**: CI must pass
3. **Require reviews**: Code review required
4. **Restrict pushes**: Only certain users can push
5. **Require signed commits**: Security requirement

### Setting Up Protection (GitHub Web)

1. Go to repository Settings
2. Click "Branches" in sidebar
3. Click "Add rule" next to "Branch protection rules"
4. Configure protection settings

### Setting Up Protection (GitHub CLI)

```bash
# Protect main branch
gh api repos/:owner/:repo/branches/main/protection \
  --method PUT \
  --field required_status_checks='{"strict":true,"contexts":[]}' \
  --field enforce_admins=true \
  --field required_pull_request_reviews='{"required_approving_review_count":1}' \
  --field restrictions=null
```

## Troubleshooting Branches

### Common Issues and Solutions

#### Can't Switch Branches (Uncommitted Changes)

```bash
# Problem: You have uncommitted changes
git switch feature-branch
# error: Your local changes would be overwritten

# Solution 1: Commit changes
git add .
git commit -m "WIP: work in progress"

# Solution 2: Stash changes
git stash
git switch feature-branch
# Later: git stash pop

# Solution 3: Create branch from current state
git switch -c temp-branch
```

#### Branch Already Exists

```bash
# Problem: Branch name already exists
git switch -c feature/login
# fatal: A branch named 'feature/login' already exists

# Solution: Use different name or delete existing
git branch -d feature/login  # if safe to delete
git switch -c feature/login-v2  # or use different name
```

#### Lost Commits After Branch Deletion

```bash
# Find lost commits
git reflog

# Recover branch from commit hash
git switch -c recovered-branch <commit-hash>
```

## Branch Workflows Comparison

### GitHub Flow (Simple)
```mermaid
gitgraph
    commit id: "A"
    branch feature
    checkout feature
    commit id: "B"
    commit id: "C"
    checkout main
    merge feature
    commit id: "D"
```

### Git Flow (Complex)
```mermaid
gitgraph
    commit id: "A"
    branch develop
    checkout develop
    commit id: "B"
    branch feature
    checkout feature
    commit id: "C"
    checkout develop
    merge feature
    checkout main
    merge develop
    commit id: "Release"
```

## Best Practices Summary

### Do's ✅
- Use descriptive branch names
- Keep branches focused and small
- Delete branches after merging
- Update branches regularly with main
- Use pull requests for code review
- Protect important branches

### Don'ts ❌
- Don't work directly on main/master
- Don't create long-lived feature branches
- Don't force push to shared branches
- Don't ignore merge conflicts
- Don't skip code reviews

## Quick Reference

```bash
# Branch basics
git branch                    # List branches
git switch -c new-branch     # Create and switch
git switch branch-name       # Switch branches
git branch -d branch-name    # Delete branch

# Branch information
git branch -v               # Show last commit
git branch --merged         # Show merged branches
git log --oneline --graph   # Visual branch history

# Remote branches
git push -u origin branch   # Push and set upstream
git branch -r              # List remote branches
git push origin --delete branch  # Delete remote branch
```

## Next Steps

Now that you understand branching basics, learn about [collaborative workflows](workflows.md) and how teams use branches to work together effectively.

---

!!! success "Branching Mastery"
    You now understand how to create, manage, and work with branches effectively. This foundation will serve you well in both solo and collaborative development!
