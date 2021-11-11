# Пример конфигурации devcontainer для python


## Файл конфигурации

_./devcontainer/devcontainer.json_

- context - путь, относительно чего будет запущен docker-compose.yml
- service - имя целевого сервиса из docker-compose
- workspaceFolder - директория, которая откроется при запуске контейнера (в docker-compose должен быть соответствующий volume, например, *workspaceFolder="project"* тогда в volume *.:project:cached*)
- settings - настройки vscode
- extensions - все необходимые расширения, которые будут установленны в контейнер
- forwardPorts - порты, которые необходимо открыть, например, для запуска сервера разработки
- overrideCommand - если true, то игнорирует command в docker-compose и Dockerfile
- dockerComposeFile - массив compose файлов, из которых будет собран один docker-compose файл (выполняется так: docker-compose -f dev.yml -f docker-compose.yml  config ). Таким образом, можно переопределять конфигурацию.
- runServices - запуск других контейнеров.
- postCreateCommand - позволяет что-то сделать, когда container запущен. Например, установить zsh как тут [zsh-in-docker](https://github.com/deluan/zsh-in-docker). Лучше все команды, даже если она одна, вынести в sh файл и указать путь до него.


## Language Server

- Pylance работает очень медленно (потребовалось даже указать, где искать библиотеки python.autoComplete.extraPaths)
- Jedi, Microsoft медленно.

## Запуск

- [Настроить](https://go.microsoft.com/fwlink/?linkid=830387) launch.json в папке .vscode
- Прокинуть порты в forwardPorts
