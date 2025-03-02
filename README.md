HidProxy — это приложение для управления прокси-серверами с поддержкой доменных зон `.com` и `.io`. Оно автоматически проверяет рабочие и быстрые прокси из списка в интернете, а также предоставляет удобный интерфейс для управления настройками через системный трей.

Установка

Локальная установка

1. Клонируйте репозиторий:
   bash
   git clone https://github.com/Alex42prk/HidProxy.git
   cd HidProxy
   
   <button onclick="copyToClipboard('https://github.com/Alex42prk/HidProxy.git')">Копировать</button>

2. Установите зависимости:
   bash
   pip install -r requirements.txt
   
Использование

Для запуска приложения выполните команду:

bash
python src/main.py

<button onclick="copyToClipboard('python src/main.py')">Копировать</button>

Развертывание на удаленном сервере

1. Убедитесь, что на сервере установлен Docker.
2. Скопируйте образ на сервер:
   bash
   docker save hidproxy | gzip > hidproxy.tar.gz
   scp hidproxy.tar.gz user@your-server:/path/to/destination
   
   <button onclick="copyToClipboard('docker save hidproxy | gzip > hidproxy.tar.gz')">Копировать</button>

3. Загрузите образ на сервере:
   bash
   docker load < hidproxy.tar.gz
   
   <button onclick="copyToClipboard('docker load < hidproxy.tar.gz')">Копировать</button>

4. Запустите контейнер:
   bash
   docker run -d --name hidproxy-server -p 80:80 -p 443:443 -p 54321:54321 hidproxy
   
   <button onclick="copyToClipboard('docker run -d --name hidproxy-server -p 80:80 -p 443:443 -p 54321:54321 hidproxy')">Копировать</button>

Дополнительные ссылки

- [Free Proxy List](https://free-proxy-list.net/)
  <button onclick="copyToClipboard('https://free-proxy-list.net/')">Копировать</button>

- [Pystray Documentation](https://github.com/moses-palmer/pystray)
  <button onclick="copyToClipboard('https://github.com/moses-palmer/pystray')">Копировать</button>



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

