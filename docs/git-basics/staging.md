# Staging Changes

The staging area is one of Git's most powerful features. It allows you to carefully select which changes to include in your next commit, giving you precise control over your project's history.

## Understanding the Staging Area

Think of the staging area as a **preparation area** for your next commit:

- 🎭 **Working Directory**: Where you make changes
- 📋 **Staging Area**: Where you prepare changes for commit
- 📚 **Repository**: Where committed changes are stored permanently

```mermaid
graph LR
    A[Working Directory<br/>Modified Files] -->|git add| B[Staging Area<br/>Ready to Commit]
    B -->|git commit| C[Repository<br/>Permanent History]
```

## The `git add` Command

The `git add` command moves changes from your working directory to the staging area.

### Basic Syntax
```bash
git add <file-or-pattern>
```

### Adding Single Files
```bash
# Add a specific file
git add README.md

# Add a file in a subdirectory
git add css/styles.css
```

### Adding Multiple Files
```bash
# Add multiple specific files
git add index.html css/styles.css js/script.js

# Add all files with specific extension
git add *.html

# Add all CSS files
git add css/*.css
```

### Adding All Changes
```bash
# Add all changes in current directory and subdirectories
git add .

# Add all changes in the entire repository
git add -A

# Add all tracked files (doesn't include new files)
git add -u
```

!!! warning "Be Careful with `git add .`"
    Using `git add .` stages ALL changes, including files you might not want to commit (like temporary files, logs, or sensitive data). Always review what you're staging!

## Checking What's Staged

Use `git status` to see what's in your staging area:

```bash
git status
```

Example output:
```
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   README.md
        modified:   index.html

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
        modified:   css/styles.css

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        config.txt
```

### Status Indicators
- **Green text** 🟢: Files staged for commit
- **Red text** 🔴: Modified files not yet staged
- **Untracked files**: New files Git doesn't know about

## Interactive Staging

For more precise control, use interactive staging:

```bash
# Interactive staging mode
git add -i

# Interactive patch mode (stage parts of files)
git add -p
```

### Patch Mode (`git add -p`)
This allows you to stage only specific parts of a file:

```bash
git add -p filename.txt
```

Git will show you each change and ask:
- `y` - stage this hunk
- `n` - don't stage this hunk
- `s` - split this hunk into smaller parts
- `q` - quit

## Practical Example

Let's work through a complete example:

### 1. Create and Modify Files
```bash
# Start with our initialized repository
cd learning-git

# Create multiple files
echo "# Learning Git" > README.md
echo "<h1>Hello World</h1>" > index.html
echo "body { margin: 0; }" > styles.css

# Check status
git status
```

### 2. Stage Files Selectively
```bash
# Stage only the README
git add README.md

# Check what's staged
git status

# Stage the HTML file
git add index.html

# Check status again
git status
```

### 3. Review Staged Changes
```bash
# See what's staged for commit
git diff --staged

# Or use the cached flag (same thing)
git diff --cached
```

## Unstaging Files

Sometimes you'll stage files by mistake. Here's how to unstage them:

```bash
# Unstage a specific file
git restore --staged filename.txt

# Unstage all staged files
git restore --staged .

# Alternative (older method)
git reset HEAD filename.txt
```

## Common Staging Patterns

### Stage by File Type
```bash
# All HTML files
git add *.html

# All files in src directory
git add src/

# All JavaScript files anywhere
git add **/*.js
```

### Exclude Certain Files
Create a `.gitignore` file to exclude files automatically:

```bash
# Create .gitignore file
cat > .gitignore << EOF
# Dependencies
node_modules/

# Build outputs
dist/
build/

# Environment files
.env
.env.local

# Editor files
.vscode/
*.swp
*.swo

# OS files
.DS_Store
Thumbs.db
EOF

# Stage the .gitignore file
git add .gitignore
```

## Staging Workflow Tips

### 1. Review Before Staging
```bash
# See what changed
git diff

# See status
git status
```

### 2. Stage Related Changes Together
Group related changes in the same commit:
```bash
# Good: related changes together
git add index.html css/styles.css
git commit -m "Update homepage layout and styles"
```

### 3. Use Descriptive Commits
Stage changes that belong to a single logical change:
```bash
# Good: one feature per commit
git add user-profile.html
git commit -m "Add user profile page"

git add login-form.js
git commit -m "Implement login form validation"
```

## Staging Best Practices

!!! tip "Best Practices"
    1. **Review before staging**: Always use `git status` and `git diff`
    2. **Stage related changes**: Group changes that belong together
    3. **Avoid staging everything**: Be selective with `git add .`
    4. **Use .gitignore**: Exclude files you never want to commit
    5. **Stage frequently**: Don't let too many changes accumulate

## Common Mistakes and Solutions

### Mistake 1: Staged Wrong File
```bash
# Problem: Accidentally staged config.txt
git add config.txt

# Solution: Unstage it
git restore --staged config.txt
```

### Mistake 2: Staged All Files Including Unwanted Ones
```bash
# Problem: Used git add . and staged too much
git add .

# Solution: Reset staging area
git restore --staged .

# Then stage selectively
git add README.md index.html
```

### Mistake 3: Forgot to Stage Modified File
```bash
# Problem: Made changes but forgot to stage
# Solution: Stage the updated file
git add modified-file.txt
```

## Quick Reference

```bash
# Staging commands
git add filename.txt     # Stage specific file
git add .               # Stage all changes
git add *.html          # Stage all HTML files
git add -A              # Stage all changes (including deletions)
git add -u              # Stage only tracked files

# Checking staged changes
git status              # See what's staged
git diff --staged       # See staged changes details

# Unstaging
git restore --staged file.txt  # Unstage specific file
git restore --staged .         # Unstage all files

# Interactive staging
git add -i              # Interactive mode
git add -p              # Patch mode
```

## Next Steps

Now that you understand how to stage changes, let's learn about [committing those changes](committing.md) to save them permanently in your repository!

---

!!! success "Staging Mastered!"
    You now understand how to selectively prepare changes for commit. This is a crucial skill that will help you create clean, organized project history.
