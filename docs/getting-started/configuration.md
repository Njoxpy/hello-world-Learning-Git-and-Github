# Configuring Git

After installing Git, you need to configure it with your personal information. This configuration is essential because Git tracks who made each change in a repository.

## Why Configuration Matters

Every time you make a commit (save changes) to a repository, Git records:
- **Your name** - to identify who made the change
- **Your email** - for contact and GitHub integration
- **Timestamp** - when the change was made

!!! warning "Important"
    Without proper configuration, you might encounter errors when trying to make commits, or your contributions might not be properly attributed to you.

## Essential Configuration

### 1. Set Your Name

Configure your name globally (for all repositories):

```bash
git config --global user.name "Your Full Name"
```

**Example:**
```bash
git config --global user.name "John Doe"
```

!!! tip "Name Guidelines"
    - Use your real name for professional projects
    - Be consistent across all your repositories
    - Use the same name you use on GitHub/GitLab

### 2. Set Your Email

Configure your email address:

```bash
git config --global user.email "your.email@example.com"
```

**Example:**
```bash
git config --global user.email "john.doe@example.com"
```

!!! info "GitHub Integration"
    Use the same email address that you use for your GitHub account to ensure your commits are properly linked to your GitHub profile.

### 3. Set Your Default Editor

Configure a default text editor for Git operations:

#### For VS Code:
```bash
git config --global core.editor "code --wait"
```

#### For Other Editors:
```bash
# Vim
git config --global core.editor "vim"

# Nano
git config --global core.editor "nano"

# Notepad (Windows)
git config --global core.editor "notepad"
```

!!! note "Editor Usage"
    Git will open your default editor when you need to write commit messages or resolve merge conflicts.

## Viewing Your Configuration

### View All Configuration
```bash
git config --list
```

### View Specific Settings
```bash
# View your name
git config user.name

# View your email
git config user.email

# View your editor
git config core.editor
```

### Edit Configuration File
Open the global configuration file in your default editor:

```bash
git config --global -e
```

This opens the `.gitconfig` file where you can make manual edits.

## Configuration Levels

Git has three levels of configuration:

### 1. System Level (`--system`)
- Applies to all users on the system
- Stored in `/etc/gitconfig` (Linux/macOS) or `C:\Program Files\Git\etc\gitconfig` (Windows)
- Requires admin privileges

### 2. Global Level (`--global`) ⭐
- Applies to all repositories for the current user
- Stored in `~/.gitconfig` or `~/.config/git/config`
- **Most commonly used**

### 3. Local Level (`--local`)
- Applies only to the current repository
- Stored in `.git/config` within the repository
- Overrides global and system settings

!!! tip "Priority Order"
    Local settings override global settings, which override system settings.

## Additional Useful Configuration

### Set Default Branch Name
```bash
git config --global init.defaultBranch main
```

### Configure Line Endings
```bash
# For Windows
git config --global core.autocrlf true

# For macOS/Linux
git config --global core.autocrlf input
```

### Enable Color Output
```bash
git config --global color.ui auto
```

### Set Up Aliases (Optional)
Create shortcuts for common commands:

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
```

Now you can use `git st` instead of `git status`, etc.

## Verify Your Configuration

Let's make sure everything is configured correctly:

```bash
# Check your name and email
git config --global --list | grep user

# Test creating a simple repository
mkdir test-repo
cd test-repo
git init
echo "Hello Git!" > README.md
git add README.md
git commit -m "Initial commit"
```

If the commit succeeds without errors, your configuration is working correctly!

## Getting Help

When you're stuck or need to learn more about Git commands:

### General Help
```bash
git help
```

### Command-Specific Help
```bash
git help <command>

# Examples:
git help config
git help commit
git help status
```

### Quick Help
```bash
git <command> -h

# Example:
git config -h
```

## Next Steps

Excellent! You now have Git properly configured. Let's move on to learning the [Git basics](../git-basics/overview.md) and create your first repository!

---

!!! success "Configuration Complete"
    You're now ready to start using Git! Your commits will be properly attributed to you, and you have all the essential settings configured.
