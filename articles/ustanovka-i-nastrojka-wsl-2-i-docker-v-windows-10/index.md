# Установка и настройка WSL 2 и Docker в Windows 10

## Терминал Windows

В целом, устанавливать его не нужно, но так будет удобнее при начальных этапах настройки. Терминал Windows можно
установить из [Microsoft Store](https://aka.ms/terminal). Прочитать подробнее
можно [здесь](https://docs.microsoft.com/ru-ru/windows/terminal/get-started)

## Установка WSL

### Установка WSL 1

Запустите терминал правами администратора и откройте оболочку `PowerShell`

![Пустой терминал](images/pustoj-terminal.png)

Выполните следующую команду

```shell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

![активация функций wsl](images/aktivaciya-funkcij-wsl.png)

### Обновление до WSL 2

Выполните следующую команду

```shell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Установка версии по умолчанию

```shell
wsl --set-default-version 2
```

![обновление до wsl 2](images/obnovlenie-do-wsl-2.png)

Установка версии для конкретного дистрибутива

```shell
 wsl --set-version Ubuntu-20.04 1
```

### Установка дистрибутива

Откройте [Microsoft Store](https://aka.ms/wslstore) и выберите предпочтительный дистрибутив Linux. Напишите в
поиске `Ubuntu` и выберите один из вариантов:

![Магазин приложений](images/store.png)

Запустите установленный дистрибутив, введите логин и пароль

![ubuntu](images/ubuntu.png)

После этого можно продолжить работать в нем или в терминале Windows

## Настройка окружения WSL

### Установка Node.js

Выполните следующие команды

```shell
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt install build-essential
```

Проверка установки

```shell
node -v
```

![версия ноды](images/versiya-nody.png)

## Docker

### Установка

Скачайте и установите докер с [официального сайта](https://www.docker.com/products/docker-desktop)
![установка докера](images/ustanovka-dokera.png)

Запустите `Docker Desktop` и перейдите в настройки. Убедитесь, что включен флажок `Use the WSL 2 based engine`

![wsl2 engine](images/wsl2-engine.png)

Если все верно сделано на этапе установке дистрибутива ubuntu, то он появится в списке на
вкладке `Resources > WSL Integration`. Активируйте его и сохраните настройки

![Integration](images/integration.png)
Лучше всего после этого перезагрузить компьютер и дождаться полного включения докера

### Проверка

Для проверки доступности, откройте дистрибутив ubuntu и выполните команды

```shell
docker --version 
```

![docker-version](images/docker-version.png)
Выполните следующую команду для запуска тестового контейнера

```shell
docker run hello-world
```

![docker-test.png](images/docker-test.png)
В случае успеха, вы увидите такое сообщение:

![hello-world](images/hello-world.png)



## Финал 
На этом настройка закончена, приятного кодинга =)
