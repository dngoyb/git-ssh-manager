# Git SSH Key Manager

A bash script for managing multiple SSH keys for different Git providers (GitHub, GitLab, and Bitbucket). This script simplifies the process of generating, testing, and managing SSH keys for different Git platforms and accounts.

## System Requirements

### Linux and macOS
- Git installed on your system
- Bash shell
- SSH client (`openssh-client`)

### Windows
- [Git for Windows](https://gitforwindows.org/) (includes Git Bash)
- Run the script from Git Bash, NOT from Command Prompt or PowerShell
- If you haven't installed Git for Windows:
  1. Download Git for Windows from https://gitforwindows.org/
  2. During installation:
     - Choose "Use Git and optional Unix tools from the Command Prompt"
     - Choose "Use OpenSSH" when prompted for SSH executable
     - Other options can be left at their defaults

## Installation

### Linux and macOS
1. Download the script:
```bash
curl -O https://raw.githubusercontent.com/dngoyb/git-ssh-manager/main/git-ssh-manager.sh
```

2. Make it executable:
```bash
chmod +x git-ssh-manager.sh
```

### Windows
1. Open Git Bash (NOT Command Prompt or PowerShell)
2. Download the script:
```bash
curl -O https://raw.githubusercontent.com/yourusername/git-ssh-manager/main/git-ssh-manager.sh
```

3. Make it executable:
```bash
chmod +x git-ssh-manager.sh
```

4. Note: If you get a permission error, try:
```bash
# Navigate to your home directory
cd ~
# Create a bin directory if it doesn't exist
mkdir -p bin
# Move the script there
mv git-ssh-manager.sh ~/bin/
# Add execute permission
chmod +x ~/bin/git-ssh-manager.sh
```

## Usage

### Linux and macOS
Run the script:
```bash
./git-ssh-manager.sh
```

### Windows (Git Bash)
Run the script:
```bash
# If in the same directory
./git-ssh-manager.sh

# If moved to ~/bin
~/bin/git-ssh-manager.sh
```

### Important Notes for Windows Users

1. **File Locations on Windows**
   - SSH keys: `C:\Users\YourUsername\.ssh\`
   - SSH config: `C:\Users\YourUsername\.ssh\config`
   - Git config: `C:\Users\YourUsername\.gitconfig`

2. **Common Windows Issues**
   - If you get "permission denied" errors:
     ```bash
     # In Git Bash
     eval "$(ssh-agent -s)"
     ssh-add ~/.ssh/your_key_name
     ```
   - If ssh-agent isn't running:
     ```bash
     # Add to your ~/.bashrc
     eval `ssh-agent -s`
     ```
   - If keys aren't persisting between sessions:
     1. Create/edit `~/.bashrc`:
        ```bash
        if [ -z "$SSH_AUTH_SOCK" ] ; then
            eval `ssh-agent -s`
            ssh-add
        fi
        ```

3. **Line Ending Issues**
   - If you get "bad line" errors in your SSH config:
     ```bash
     # Fix line endings
     sed -i 's/\r$//' ~/.ssh/config
     ```

[Rest of the README remains the same...]

## Troubleshooting

[Previous troubleshooting section plus:]

### Windows-Specific Issues

#### Permission Denied
```bash
# Make sure you're running Git Bash as administrator
# Right-click Git Bash -> Run as administrator
```

#### SSH Agent Issues
```bash
# Start SSH agent manually
eval `ssh-agent -s`
ssh-add ~/.ssh/your_key_name
```

#### Path Issues
```bash
# Check if .ssh directory exists
ls -la ~/.ssh

# Create .ssh directory if it doesn't exist
mkdir -p ~/.ssh
chmod 700 ~/.ssh
```

#### Line Ending Issues
```bash
# Configure Git to handle line endings
git config --global core.autocrlf input
```

[Rest of the README remains the same...]
