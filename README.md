HidProxy

HidProxy — это инструмент для управления прокси-серверами с поддержкой автоматической настройки и мониторинга.

Оглавление

1. [Описание проекта](#описание-проекта)
2. [Установка](#установка)
3. [Использование](#использование)
4. [Логи установки](#логи-установки)
5. [Траблшутинг](#траблшутинг)
6. [Полезные ссылки](#полезные-ссылки)

Описание проекта

Проект HidProxy предоставляет удобный интерфейс для управления прокси-серверами. Он включает следующие функции:

- Автоматическая настройка прокси через Docker.
- Поддержка протоколов HTTP, HTTPS и других.
- Управление пользователями и портами через командную строку.
- Логирование и мониторинг работы сервера.

Установка

### Требования

- ОС: Linux (Debian/Ubuntu).
- Docker и Docker Compose должны быть установлены.

### Шаги установки

1. Клонируйте репозиторий:
   bash
   git clone https://github.com/Alex42prk/HidProxy.git
   cd HidProxy
   
   
   <button onclick="copyToClipboard('https://github.com/Alex42prk/HidProxy.git')">Копировать</button>

3. Соберите Docker-образ:
   bash
   docker build -t hidproxy .
   
   
 <button onclick="copyToClipboard('docker build -t hidproxy .')">Копировать</button>

3. Запустите контейнер:
   bash
   docker run -d --name hidproxy-container -p 80:80 -p 443:443 -p 54321:54321 hidproxy
   

   <button onclick="copyToClipboard('docker run -d --name hidproxy-container -p 80:80 -p 443:443 -p 54321:54321 hidproxy')">Копировать</button>

Использование

Настройка учетных данных

После установки вы можете настроить учетные данные для доступа к панели управления:

bash
x-ui setting -username admin -password "ВашПароль123" -port 54321


<button onclick="copyToClipboard('x-ui setting -username admin -password \"ВашПароль123\" -port 54321')">Копировать</button>

Команды управления

- Проверить статус сервера:
  bash
  docker ps
  

  <button onclick="copyToClipboard('docker ps')">Копировать</button>

- Остановить контейнер:
  bash
  docker stop hidproxy-container
  

  <button onclick="copyToClipboard('docker stop hidproxy-container')">Копировать</button>

- Запустить контейнер снова:
  bash
  docker start hidproxy-container
  

  <button onclick="copyToClipboard('docker start hidproxy-container')">Копировать</button>

Логи установки

Пример логов установки:

bash
Step 3/7 : RUN wget -O x-ui-linux-amd64.tar.gz https://github.com/vaxilu/x-ui/releases/download/0.3.2/x-ui-linux-amd64.tar.gz

Successfully built 9fde1a09c7ff
Successfully tagged x-ui-proxy:latest


<button onclick="copyToClipboard('https://github.com/vaxilu/x-ui/releases/download/0.3.2/x-ui-linux-amd64.tar.gz')">Копировать</button>

Полезные ссылки

- [GitHub Repository](https://github.com/Alex42prk/HidProxy)
  <button onclick="copyToClipboard('https://github.com/Alex42prk/HidProxy')">Копировать</button>

- [X-UI Documentation](https://github.com/vaxilu/x-ui)
  <button onclick="copyToClipboard('https://github.com/vaxilu/x-ui')">Копировать</button>


html
<script>
function copyToClipboard(text) {
  navigator.clipboard.writeText(text).then(() => {
    alert("Скопировано: " + text);
  }).catch(err => {
    console.error("Ошибка копирования: ", err);
  });
}
</script>





