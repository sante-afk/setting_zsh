# Installing and Configuring ZSH on Linux (Fedora/Ubuntu)

This guide will help you quickly set up a ZSH terminal with improved information display and the ability to extend functionality using plugins.

## Preparing the system
Update system packages:
```bash
# Для Ubuntu/Debian:
sudo apt update && sudo apt upgrade -y

# Для Fedora:
sudo dnf update -y
```
#### Installing the required components
Install git and zsh:
```bash
# Для Ubuntu/Debian:
sudo apt install -y git zsh

# Для Fedora:
sudo dnf install -y git zsh
```

#### Configuring ZSH
1. Create a configuration file (if it is not created automatically):
```bash
touch ~/.zshrc
```
2. Let's set zsh as the default command shell on our system:
```bash
chsh -s $(which zsh)
```
3. Install a popular open source framework for managing and improving the zsh shell configuration:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
#### Installing the Powerlevel10k theme
1. Create a temporary directory for downloading files:
```bash
cd ~/ && mkdir tmp && cd tmp
```
2. Download the fonts from the same repository and install them:
```bash
git clone https://github.com/sshyta/setting_zsh.git
```
3. Install the powerlevel10k theme:
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

You need to edit the `~/.zshrc` file and replace the value of the `ZSH_THEME` key with:
`ZSH_THEME="powerlevel10k/powerlevel10k"`

Launching the editor:
`nano ~/.zshrc`

To save changes, press Ctrl + X, Ctrl + Y, then press Enter
Restart the terminal