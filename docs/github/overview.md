# GitHub Overview

GitHub is a web-based platform that provides hosting for Git repositories along with powerful collaboration features. It's where millions of developers store, share, and collaborate on code projects.

## What is GitHub?

GitHub is built on top of Git and provides:

- 🏠 **Repository Hosting**: Store your Git repositories in the cloud
- 👥 **Collaboration Tools**: Work with others on projects
- 🔄 **Pull Requests**: Propose and review changes
- 🐛 **Issue Tracking**: Manage bugs and feature requests
- 📊 **Project Management**: Plan and track work
- 🚀 **Actions**: Automate workflows and deployments
- 📑 **Pages**: Host static websites directly from repositories

## GitHub vs Git

| Git | GitHub |
|-----|---------|
| Version control system | Hosting platform for Git repositories |
| Local tool | Web-based service |
| Command-line interface | Web interface + CLI tools |
| Manages code history | Adds collaboration features |
| Open source | Owned by Microsoft |

!!! info "Key Concept"
    Git is the tool, GitHub is the platform. You can use Git without GitHub, but GitHub enhances Git with collaboration features.

## Key GitHub Features

### 1. Repositories 📁
- **Public Repositories**: Open source projects visible to everyone
- **Private Repositories**: Restricted access for personal or team projects
- **Fork**: Create your own copy of someone else's repository
- **Clone**: Download a repository to your local machine

### 2. Collaboration Features 👥
- **Pull Requests**: Propose changes and get code reviews
- **Issues**: Track bugs, feature requests, and discussions
- **Discussions**: Community conversations about projects
- **Wiki**: Documentation and knowledge sharing
- **Projects**: Kanban-style project management

### 3. Social Features 🌟
- **Following**: Stay updated with developers and organizations
- **Starring**: Bookmark interesting repositories
- **Watching**: Get notifications about repository activity
- **Profile**: Showcase your projects and contributions

### 4. Development Tools 🛠️
- **GitHub Actions**: CI/CD workflows and automation
- **GitHub Pages**: Host static websites
- **Codespaces**: Cloud development environments
- **Security**: Vulnerability scanning and secret detection

## Getting Started with GitHub

### 1. Create a GitHub Account
1. Visit [github.com](https://github.com)
2. Sign up with your email address
3. Choose a username (this will be part of your repository URLs)
4. Verify your email address

### 2. Set Up Your Profile
```markdown
# Add to your GitHub profile README
## Hi there 👋

I'm a developer passionate about:
- Web development
- Open source projects
- Learning new technologies

### Technologies I work with:
- JavaScript/TypeScript
- Python
- React
- Node.js

### Find me around the web:
- Portfolio: [yourwebsite.com](https://yourwebsite.com)
- LinkedIn: [your-profile](https://linkedin.com/in/your-profile)
- Twitter: [@yourusername](https://twitter.com/yourusername)
```

### 3. Configure Git for GitHub
```bash
# Set your GitHub username and email
git config --global user.name "Your GitHub Username"
git config --global user.email "your-github-email@example.com"

# Optional: Set up SSH keys for secure authentication
ssh-keygen -t ed25519 -C "your-github-email@example.com"
```

## Repository Basics

### Creating a Repository

#### Method 1: On GitHub Web Interface
1. Click the "+" icon in the top right
2. Select "New repository"
3. Choose repository name and settings
4. Click "Create repository"

#### Method 2: From Command Line (GitHub CLI)
```bash
# Install GitHub CLI first
gh repo create my-project --public --source=. --remote=origin --push
```

### Repository Structure
```
your-repository/
├── README.md              # Project description and instructions
├── .gitignore            # Files to ignore in version control
├── LICENSE               # Legal terms for using your code
├── src/                  # Source code directory
├── docs/                 # Documentation
├── tests/                # Test files
└── .github/              # GitHub-specific configurations
    ├── workflows/        # GitHub Actions workflows
    └── ISSUE_TEMPLATE/   # Issue templates
```

## Common GitHub Workflows

### 1. Basic Workflow
```bash
# Clone repository
git clone https://github.com/username/repository.git
cd repository

# Make changes
echo "New feature" > feature.txt

# Stage and commit
git add feature.txt
git commit -m "Add new feature"

# Push to GitHub
git push origin main
```

### 2. Fork and Pull Request Workflow
```bash
# 1. Fork repository on GitHub (web interface)

# 2. Clone your fork
git clone https://github.com/yourusername/original-repo.git
cd original-repo

# 3. Create feature branch
git checkout -b feature/new-feature

# 4. Make changes and commit
git add .
git commit -m "Add new feature"

# 5. Push to your fork
git push origin feature/new-feature

# 6. Create pull request on GitHub (web interface)
```

### 3. Collaboration Workflow
```bash
# Add collaborator's remote
git remote add collaborator https://github.com/collaborator/repo.git

# Fetch their changes
git fetch collaborator

# Merge their changes
git merge collaborator/main

# Push combined changes
git push origin main
```

## GitHub Authentication

### HTTPS Authentication
```bash
# Using personal access token
git clone https://github.com/username/repo.git
# Enter username and personal access token when prompted
```

### SSH Authentication (Recommended)
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your-email@example.com"

# Add SSH key to ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy public key to GitHub settings
cat ~/.ssh/id_ed25519.pub

# Clone using SSH
git clone git@github.com:username/repo.git
```

## GitHub CLI (gh)

The GitHub CLI provides command-line access to GitHub features:

### Installation
```bash
# macOS
brew install gh

# Ubuntu
sudo apt install gh

# Windows (using winget)
winget install GitHub.CLI
```

### Common Commands
```bash
# Authentication
gh auth login

# Repository operations
gh repo create my-project
gh repo clone username/repository
gh repo view

# Pull requests
gh pr create --title "New feature" --body "Description"
gh pr list
gh pr merge 123

# Issues
gh issue create --title "Bug report" --body "Description"
gh issue list
gh issue close 456
```

## GitHub Features Deep Dive

### Pull Requests 🔄
Pull requests are the heart of GitHub collaboration:

1. **Create**: Propose changes from a branch
2. **Review**: Team members examine the code
3. **Discuss**: Collaborate on improvements
4. **Merge**: Integrate approved changes

### Issues 🐛
Track work and bugs:
- **Bug Reports**: Document problems
- **Feature Requests**: Suggest improvements
- **Tasks**: Track work items
- **Labels**: Categorize and filter issues

### GitHub Actions 🚀
Automate workflows:
```yaml
# .github/workflows/test.yml
name: Tests
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: npm test
```

### GitHub Pages 📄
Host static websites:
1. Enable Pages in repository settings
2. Choose source (branch or docs folder)
3. Access at `https://username.github.io/repository`

## Best Practices

### Repository Management
- ✅ Use clear, descriptive repository names
- ✅ Write comprehensive README files
- ✅ Include appropriate licenses
- ✅ Use .gitignore files
- ✅ Tag releases with semantic versioning

### Collaboration
- ✅ Write clear commit messages
- ✅ Use pull requests for code reviews
- ✅ Respond to issues promptly
- ✅ Follow project contribution guidelines
- ✅ Be respectful in discussions

### Security
- ✅ Use SSH keys or personal access tokens
- ✅ Don't commit sensitive information
- ✅ Enable two-factor authentication
- ✅ Review dependency security alerts
- ✅ Use secret scanning

## GitHub Alternatives

While GitHub is popular, other platforms exist:

- **GitLab**: Self-hosted or cloud, strong CI/CD
- **Bitbucket**: Atlassian ecosystem integration
- **Azure DevOps**: Microsoft ecosystem
- **Codeberg**: Open source, privacy-focused
- **SourceForge**: Older platform, still active

## Pricing and Plans

GitHub offers different tiers:

### Free Plan
- ✅ Unlimited public repositories
- ✅ Unlimited private repositories
- ✅ 2,000 GitHub Actions minutes/month
- ✅ 500MB GitHub Packages storage

### Pro Plan ($4/month)
- ✅ Everything in Free
- ✅ 3,000 GitHub Actions minutes/month
- ✅ 2GB GitHub Packages storage
- ✅ Advanced insights

### Team and Enterprise
- Higher limits and additional features
- Advanced security and compliance
- Priority support

## Next Steps

Now that you understand GitHub's role and features, let's dive deeper into:

1. **[Getting Started with GitHub](getting-started.md)** - Set up your first repository
2. **[Working with Remote Repositories](remote-repos.md)** - Push, pull, and sync code

## Quick Reference

```bash
# Repository operations
git clone <url>                    # Clone repository
git remote -v                      # View remotes
git push origin main               # Push to GitHub
git pull origin main               # Pull from GitHub

# GitHub CLI
gh repo create                     # Create repository
gh pr create                       # Create pull request
gh issue create                    # Create issue
gh auth status                     # Check authentication
```

Ready to start using GitHub? Let's begin with [getting started](getting-started.md)!

---

!!! tip "GitHub Success Tips"
    - Start with public repositories to build your portfolio
    - Contribute to open source projects to gain experience
    - Use GitHub's social features to connect with other developers
    - Keep your profile and repositories well-organized
