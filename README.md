# macOS Bootstrap Script

This repository contains a bootstrap script designed to set up a freshly reinstalled macOS computer with your dotfiles configuration.

## ⚠️ Warning

This script is **destructive** and will overwrite your current dotfiles. It is intended for use on **new machines** only.

## Prerequisites

Before running the bootstrap script, you'll need:

1. **A GitHub Personal Access Token** with appropriate permissions to access the private `osx-dotfiles` repository
   - Create one at: https://github.com/settings/tokens
   - Make sure it has access to private repositories

2. **Your Git name and email** (for git configuration)

## Quick Start

### Step 1: Download the Bootstrap Script

If you have this repository cloned, you can skip to Step 2. Otherwise, download the `.bootstrap` file:

```bash
# Option 1: Clone this repository
git clone <this-repo-url>
cd private-dotfiles-bootstrap

# Option 2: Download just the bootstrap file using curl
curl -O https://raw.githubusercontent.com/<your-username>/private-dotfiles-bootstrap/main/.bootstrap
```

### Step 2: Make the Script Executable

```bash
chmod +x .bootstrap
```

### Step 3: Run the Bootstrap Script

```bash
./.bootstrap
```

Or if you're in a different directory:

```bash
/path/to/.bootstrap
```

## What the Script Does

The bootstrap script will:

1. **Install Xcode Command Line Tools** - Required for git and other development tools
2. **Configure Git** - Sets up your git name and email globally
3. **Clone Private Repository** - Clones the `osx-dotfiles` repository using your GitHub token
4. **Run Init Script** - Executes the `init.sh` script from the cloned dotfiles repository
5. **Optional Cleanup** - Optionally removes the cloned repository after setup

## Interactive Prompts

During execution, the script will ask you for:

1. **Confirmation** - Type `y` to continue (any other input will exit)
2. **Git Name** - Your full name for git commits
3. **Git Email** - Your email address for git commits
4. **GitHub Token** - Your personal access token (input is hidden for security)
5. **Cleanup Confirmation** - Type `y` to remove the cloned repository after setup, or `n` to keep it

## Example Usage

```bash
# Navigate to the directory containing .bootstrap
cd ~/Downloads/private-dotfiles-bootstrap

# Make it executable
chmod +x .bootstrap

# Run it
./.bootstrap

# Follow the prompts:
# - Confirm with 'y'
# - Enter your git name when prompted
# - Enter your git email when prompted
# - Enter your GitHub token when prompted
# - Choose whether to cleanup with 'y' or 'n'
```

## Troubleshooting

### Script won't run

If you get a "Permission denied" error:
```bash
chmod +x .bootstrap
```

### Xcode tools installation

The script will trigger the Xcode Command Line Tools installation. You may need to:
- Accept the license agreement in a popup window
- Wait for the installation to complete before the script continues

### GitHub token issues

If you encounter authentication errors:
- Verify your token has access to private repositories
- Make sure the token hasn't expired
- Check that you have access to the `TroTi13/osx-dotfiles` repository

## Notes

- The script uses `zsh` shell (standard on macOS)
- Your GitHub token is cleared from memory after use (not stored)
- The script will clone the dotfiles repository to `~/dotfiles`
- The `init.sh` script in the dotfiles repository handles the actual dotfiles setup

## Security

- Your GitHub token is entered securely (input is hidden)
- The token is unset from the environment after use
- The token is only used for cloning the private repository

