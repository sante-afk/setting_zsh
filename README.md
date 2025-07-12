# Installing and configuring ZSH in (Fedora/Ubuntu/NixOS/macOS) 🫩

This guide will help you quickly set up a ZSH terminal with improved display of information and the ability to expand functionality using plugins.

## Preparing the system
Update system packages:
```bash
# For Ubuntu/Debian:
sudo apt update && sudo apt upgrade -y

# For Fedora:
sudo dnf update -y

# For NixOS, go to the configuration file:
cd /etc/nixos/
nano configuration.nix

# For macOS, install Homebrew:
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# MacPorts (for older versions of macOS)
https://www.macports.org/install.php
```

## Installing the necessary components
Install git, zsh and wget:
```bash
# For Ubuntu/Debian:
sudo apt install -y git zsh wget

# For Fedora:
sudo dnf install -y git zsh wget

# For NixOS, add a line and rebuild:
environment.systemPackages = with pkgs; [
zsh
];

# Rebuild
sudo nixos-rebuild switch

# For macOS
brew install git zsh wget

# MacPorts (for older versions of macOS)
sudo port install git zsh wget
```

## Setting up ZSH
1. Create a configuration file (if it was not created automatically):
```bash
touch ~/.zshrc
```
2. Set zsh as the default shell on our system:
```bash
chsh -s $(which zsh)
```
>For NixOS, to set zsh as the default shell,
>add a few lines to the configuration file and rebuild.
```bash
# Set the shell at the system level
programs.zsh.enable = true;

# Change the shell for all users
users.defaultUserShell = pkgs.zsh;

# Change the shell for a specific user
users.users.<user_name> = {
shell = pkgs.zsh;
useDefaultShell = true;
};

# Rebuild
sudo nixos-rebuild switch
```
3. Install the popular Oh My Zsh plugin
to manage and improve the zsh shell configuration:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Installing the Powerlevel10k theme
1. Create a temporary directory for downloading files:
```bash
cd ~/ && mkdir tmp && cd tmp
```
2. Clone the repository and enter it:
```bash
git clone https://github.com/sshyta/setting_zsh.git
cd setting_zsh
```
3. Give access rights to the file, making it executable:
```bash
chmod +x fonts_install.sh
```
4. Run it:
```bash
zsh ./fonts_install.sh
```
5. Install the powerlevel10k theme:
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

You need to edit the `~/.zshrc` file and replace the value of the `ZSH_THEME` key with:
```bash
`ZSH_THEME="powerlevel10k/powerlevel10k"`
```

Launch the editor:
`nano ~/.zshrc`

To save changes, press Ctrl + X, Ctrl + Y, then press Enter

Restart the terminal