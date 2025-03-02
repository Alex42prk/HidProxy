X-UI Proxy Manager

X-UI Proxy Manager — это инструмент для управления прокси-серверами с поддержкой автоматической настройки и мониторинга. Этот проект позволяет легко развернуть и настроить прокси-сервер на базе Docker.

Оглавление

1. [Описание проекта](#описание-проекта)
2. [Установка](#установка)
3. [Использование](#использование)
4. [Логи установки](#логи-установки)
5. [Траблшутинг](#траблшутинг)
6. [Лицензия](#лицензия)

Описание проекта

Проект X-UI Proxy Manager предоставляет удобный интерфейс для управления прокси-серверами. Он включает следующие функции:

- Автоматическая настройка прокси через Docker.
- Поддержка протоколов HTTP, HTTPS и других.
- Управление пользователями и портами через командную строку.
- Логирование и мониторинг работы сервера.

Установка

Требования

- ОС: Linux (Debian/Ubuntu).
- Docker и Docker Compose должны быть установлены.

Шаги установки

1. Клонируйте репозиторий:
   bash
   git clone https://github.com/Alex42prk/HidProxy.git
   cd HidProxy
   

2. Соберите Docker-образ:
   bash
   docker build -t x-ui-proxy .
   

3. Запустите контейнер:
   bash
   docker run -d --name x-ui-container -p 80:80 -p 443:443 -p 54321:54321 x-ui-proxy
   

Использование

Настройка учетных данных

После установки вы можете настроить учетные данные для доступа к панели управления:

bash
x-ui setting -username admin -password "ВашПароль123" -port 54321


Команды управления

- Проверить статус сервера:
  bash
  docker ps
  

- Остановить контейнер:
  bash
  docker stop x-ui-container
  

- Запустить контейнер снова:
  bash
  docker start x-ui-container
  

Логи установки

Пример логов установки:

bash
Step 3/7 : RUN wget -O x-ui-linux-amd64.tar.gz https://github.com/vaxilu/x-ui/releases/download/0.3.2/x-ui-linux-amd64.tar.gz

Length: 16509803 (16M) [application/octet-stream]
Saving to: 'x-ui-linux-amd64.tar.gz'

Successfully built acd0d7c3dc91
Successfully tagged x-ui-proxy:latest


Траблшутинг

Проблемы с установкой

Если возникают ошибки при установке, проверьте:

1. Наличие необходимых зависимостей:
   bash
   apt-get update && apt-get install -y curl wget ca-certificates
   

2. Корректность ссылок на ресурсы. Например, если GitHub недоступен, используйте зеркало:
   bash
   RUN wget -O x-ui-linux-amd64.tar.gz https://ghproxy.com/https://github.com/vaxilu/x-ui/releases/download/0.3.2/x-ui-linux-amd64.tar.gz
   

Проблемы с запуском

Если контейнер не запускается, проверьте логи:
bash
docker logs x-ui-container


Лицензия

Этот проект распространяется под лицензией [MIT](LICENSE).

Авторы

Alex42prk: [GitHub](https://github.com/Alex42prk)

