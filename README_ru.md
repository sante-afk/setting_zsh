# Установка и настройка ZSH в Linux (Fedora/Ubuntu)

Данное руководство поможет быстро настроить терминал ZSH с улучшенным отображением информации и возможностью расширения функционала с помощью плагинов.

## Подготовка системы
Обновите пакеты системы:
```bash
# Для Ubuntu/Debian:
sudo apt update && sudo apt upgrade -y

# Для Fedora:
sudo dnf update -y
```
#### Установка необходимых компонентов
Установим git и zsh:
```bash
# Для Ubuntu/Debian:
sudo apt install -y git zsh

# Для Fedora:
sudo dnf install -y git zsh
```

#### Настройка ZSH
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
#### Установка темы Powerlevel10k
1. Создаем временную директорию для загрузки файлов:
```bash
cd ~/ && mkdir tmp && cd tmp
```
2. Скачиваем шрифты с этого же репозитория и устанавливаем их:
```bash
git clone https://github.com/sshyta/setting_zsh.git
```
3. Устанавливаем тему powerlevel10k:
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Необходимо отредактировать файл `~/.zshrc` заменить значение ключа `ZSH_THEME` на :
`ZSH_THEME="powerlevel10k/powerlevel10k"`

Запуск редактора:
`nano ~/.zshrc`

Для созранения изменений нажимаем Ctrl + X, Ctrl + Y, затем нажимаем Enter

Перезапускаем терминал
