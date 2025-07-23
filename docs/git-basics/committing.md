# Committing Changes

Commits are the heart of Git - they represent snapshots of your project at specific points in time. A good understanding of commits is essential for effective version control.

## What is a Git Commit?

A commit is a **permanent snapshot** of your staged changes, stored in your repository's history. Each commit includes:

- 📸 **Snapshot**: The exact state of your files at that moment
- 👤 **Author**: Who made the changes (name and email)
- 📅 **Timestamp**: When the commit was created
- 💬 **Message**: Description of what changed and why
- 🔗 **Parent**: Reference to the previous commit(s)
- 🆔 **Hash**: Unique identifier (SHA-1)

## The `git commit` Command

### Basic Commit
```bash
git commit -m "Your commit message"
```

### Commit with Detailed Message
```bash
git commit
```
This opens your default editor for a multi-line commit message.

### Skip Staging for Tracked Files
```bash
git commit -a -m "Update existing files"
```
The `-a` flag automatically stages all modified tracked files.

## Writing Good Commit Messages

A good commit message follows this structure:

```
Short summary (50 characters or less)

More detailed explanation if needed. Wrap lines at 72 characters.
Explain what changed and why, not how.

- Bullet points are okay
- Use present tense: "Fix bug" not "Fixed bug"
- Reference issues: Fixes #123
```

### Examples of Good Commit Messages

**Short and clear:**
```bash
git commit -m "Fix login button alignment"
git commit -m "Add user authentication system"
git commit -m "Update README with installation instructions"
```

**Detailed commit message:**
```
Add user profile page

- Create profile.html template
- Add CSS styling for profile cards
- Implement user data fetching
- Add responsive design for mobile devices

This addresses the user request for profile management
functionality mentioned in issue #45.
```

### Message Conventions

Many projects follow conventional commit formats:

```
type(scope): description

Examples:
feat(auth): add password reset functionality
fix(ui): resolve button alignment issue
docs(readme): update installation instructions
style(css): improve header styling
refactor(api): simplify user data handling
test(auth): add login validation tests
```

## Commit Best Practices

### 1. Make Atomic Commits
Each commit should represent **one logical change**:

```bash
# Good: One feature per commit
git add user-form.html
git commit -m "Add user registration form"

git add validation.js
git commit -m "Add form validation"

# Bad: Multiple unrelated changes
git add user-form.html validation.js footer.html
git commit -m "Various updates"
```

### 2. Commit Frequently
Don't wait too long between commits:

```bash
# Good workflow
git add feature.js
git commit -m "Implement basic feature structure"

# Continue working...
git add feature.js
git commit -m "Add error handling to feature"

# Continue working...
git add feature.js tests.js
git commit -m "Add tests for feature"
```

### 3. Use Present Tense
Write commit messages as if they complete the sentence "This commit will...":

```bash
# Good
git commit -m "Fix login validation bug"
git commit -m "Add user profile page"
git commit -m "Update dependencies"

# Avoid
git commit -m "Fixed login validation bug"
git commit -m "Added user profile page"
git commit -m "Updated dependencies"
```

## Practical Examples

### Example 1: Complete Workflow
```bash
# Start with a clean repository
git status

# Create and modify files
echo "<h1>Welcome</h1>" > index.html
echo "body { margin: 0; }" > styles.css

# Stage the files
git add index.html styles.css

# Check what's staged
git status

# Commit with a good message
git commit -m "Add basic HTML structure and CSS reset"

# Verify the commit
git log --oneline
```

### Example 2: Multi-line Commit Message
```bash
# Stage your changes
git add .

# Open editor for detailed message
git commit

# In the editor, write:
# Add user authentication system
# 
# - Implement login and logout functionality
# - Add password hashing with bcrypt
# - Create session management
# - Add input validation for forms
# 
# This completes the authentication requirements
# from the project specification.
```

## Viewing Commit History

### Basic Log
```bash
git log
```

### Condensed View
```bash
git log --oneline
```

### Graphical View
```bash
git log --graph --oneline --decorate
```

### Filter by Author
```bash
git log --author="Your Name"
```

### Filter by Date
```bash
git log --since="2 weeks ago"
git log --until="2024-01-01"
```

## Amending Commits

### Fix the Last Commit Message
```bash
git commit --amend -m "Corrected commit message"
```

### Add Files to Last Commit
```bash
# Stage the forgotten files
git add forgotten-file.txt

# Amend the last commit
git commit --amend --no-edit
```

!!! warning "Amending Published Commits"
    Only amend commits that haven't been pushed to a shared repository. Amending published commits can cause problems for collaborators.

## Common Commit Scenarios

### Scenario 1: Bug Fix
```bash
# Find and fix the bug
vim app.js

# Stage the fix
git add app.js

# Commit with clear message
git commit -m "Fix null pointer exception in user service"
```

### Scenario 2: New Feature
```bash
# Implement the feature
git add new-feature.js new-feature.html new-feature.css

# Commit the complete feature
git commit -m "Add dark mode toggle functionality"
```

### Scenario 3: Documentation Update
```bash
# Update documentation
git add README.md docs/

# Commit documentation changes
git commit -m "docs: update API documentation and README"
```

## Troubleshooting Commits

### Forgot to Add a File
```bash
# After committing, realize you forgot a file
git add forgotten-file.txt
git commit --amend --no-edit
```

### Wrong Commit Message
```bash
# Immediately after committing
git commit --amend -m "Correct commit message"
```

### Committed to Wrong Branch
```bash
# Create new branch from current commit
git branch correct-branch

# Reset current branch to previous commit
git reset --hard HEAD~1

# Switch to correct branch
git checkout correct-branch
```

## Commit Hooks

You can automate checks before commits using Git hooks:

### Pre-commit Hook Example
Create `.git/hooks/pre-commit`:
```bash
#!/bin/sh
# Run tests before committing
npm test
if [ $? -ne 0 ]; then
    echo "Tests failed. Commit aborted."
    exit 1
fi
```

## Advanced Commit Features

### Interactive Commits
```bash
# Choose what to include in commit
git add -p
git commit -m "Selective changes"
```

### Signed Commits
```bash
# Sign commits with GPG
git commit -S -m "Add secure feature"
```

### Empty Commits
```bash
# Create commit without changes (useful for triggering CI)
git commit --allow-empty -m "Trigger deployment"
```

## Quick Reference

```bash
# Basic committing
git commit -m "message"           # Commit staged changes
git commit -a -m "message"        # Stage and commit tracked files
git commit --amend                # Modify last commit

# Viewing commits
git log                           # Full commit history
git log --oneline                 # Condensed history
git show                          # Show last commit details
git show <commit-hash>            # Show specific commit

# Commit information
git log --author="Name"           # Filter by author
git log --since="1 week ago"      # Filter by date
git log --grep="pattern"          # Search commit messages
```

## Next Steps

Great! You now understand how to create meaningful commits. Next, let's learn about [working with files](files.md) in Git, including renaming, moving, and deleting files.

---

!!! success "Commit Mastery"
    You now know how to create clear, meaningful commits that will help you and your team understand the project's evolution over time!
