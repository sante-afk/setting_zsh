# Установка и настройка ZSH в (Fedora/Ubuntu/macOS)

Данное руководство поможет быстро настроить терминал ZSH с улучшенным отображением 
информации и возможностью расширения функционала с помощью плагинов.

## Подготовка системы
Обновите пакеты системы:
```bash
# Для Ubuntu/Debian:
sudo apt update && sudo apt upgrade -y

# Для Fedora:
sudo dnf update -y

# Для macOS устанавливаем Homebrew:
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# MacPorts (для старых версий macOS)
https://www.macports.org/install.php
```

## Установка необходимых компонентов
Установим git, zsh и wget:
```bash
# Для Ubuntu/Debian:
sudo apt install -y git zsh wget

# Для Fedora:
sudo dnf install -y git zsh wget

# Для macOS
brew install git zsh wget

# MacPorts (для старых версий macOS)
sudo port install git zsh wget
```

## Настройка ZSH
1. Создайте конфигурационный файл (если он не создался автоматически):
```bash
touch ~/.zshrc
```
2. Назначим zsh коммандной оболочкой по умолчанию в нашей системе:
```bash
chsh -s $(which zsh)
```
3. Устанавливаем популярный фреймворк с открытым исходнам кодом 
для управления и улудшения конфигурации оболочки zsh:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Установка темы Powerlevel10k
1. Создаем временную директорию для загрузки файлов:
```bash
cd ~/ && mkdir tmp && cd tmp
```
2. Клонируем репозиторий и заходим в него:
```bash
git clone https://github.com/sshyta/setting_zsh.git
cd setting_zsh
```
3. Даем права доступа к файлу, делая его исполняемым:
```bash
chmod +x fonts_install.sh
```
4. Запускаем его:
```bash
./fonts_install.sh
```
5. Устанавливаем тему powerlevel10k:
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Необходимо отредактировать файл `~/.zshrc` заменить значение ключа `ZSH_THEME` на :
```bash
`ZSH_THEME="powerlevel10k/powerlevel10k"`
```

Запуск редактора:
`nano ~/.zshrc`

Для созранения изменений нажимаем Ctrl + X, Ctrl + Y, затем нажимаем Enter

Перезапускаем терминал
