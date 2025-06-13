# Installing and configuring ZSH on Linux (Fedora/Ubuntu)

This guide will help you quickly set up a ZSH terminal with improved information display and the ability to extend functionality using plugins.

## Preparing the system
Update system packages:
```bash
# For Ubuntu/Debian:
sudo apt update && sudo apt upgrade -y

# For Fedora:
sudo dnf update -y
```
## Installing the required components
Install git, zsh and wget:
```bash
# For Ubuntu/Debian:
sudo apt install -y git zsh wget

# For Fedora:
sudo dnf install -y git zsh wget
```

## Configuring ZSH
1. Create a configuration file (if it was not created automatically):
```bash
touch ~/.zshrc
```
2. Set zsh as the default command shell on our system:
```bash
chsh -s $(which zsh)
```
3. Install a popular open-source framework source code
for managing and improving zsh shell configuration:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
## Installing Powerlevel10k theme
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
./fonts_install.sh
```
5. Install the powerlevel10k theme:
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

You need to edit the `~/.zshrc` file and replace the value of the `ZSH_THEME` key with:
```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Launch the editor:
`nano ~/.zshrc`

To save changes, press Ctrl + X, Ctrl + Y, then press Enter
Restart the terminal
