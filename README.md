
HidProxy / X-UI Installation Logs

## 1. Ошибки при установке через Docker Compose
**Контейнер Hiddify не запускается:**
bash
Error: Key not found: warp_mode
ERROR:systemctl:the ExecStartPre control process exited with error code

Решение:
bash
# Исправление конфигурации
mkdir -p /root/hiddify-config/hiddify-panel
echo "WARP_MODE=off" >> /root/hiddify-config/config.env
docker compose up -d

2. Логи установки X-UI
Ошибка монтирования файлов:
bash
Step 3/6 : RUN wget -O x-ui-linux-amd64.tar.gz https://github.com/vaxilu/x-ui/releases/download/0.3.2/x-ui-linux-amd64.tar.gz
tar: Child returned status 1


Исправление:
bash
Используйте проверенное зеркало
RUN wget -O x-ui-linux-amd64.tar.gz https://ghproxy.com/https://github.com/vaxilu/x-ui/releases/download/0.3.2/x-ui-linux-amd64.tar.gz


3. Пример Dockerfile
Файл `Dockerfile` для сборки X-UI:
ockerfile

FROM debian:12-slim
RUN apt-get update && apt-get install -y curl wget ca-certificates
RUN wget -O x-ui-linux-amd64.tar.gz https://ghproxy.com/https://github.com/vaxilu/x-ui/releases/download/0.3.2/x-ui-linux-amd64.tar.gz && \
    tar -zxvf x-ui-linux-amd64.tar.gz -C /usr/local/ && \
    rm x-ui-linux-amd64.tar.gz
RUN cp /usr/local/x-ui/x-ui /usr/bin/x-ui && \
    chmod +x /usr/bin/x-ui
RUN x-ui setting -username admin -password "SecurePass123" -port 54321
EXPOSE 80 443 54321
CMD ["/usr/bin/x-ui", "start"]



4. Траблшутинг
Частые ошибки:
- `Connection refused` — проверьте открытые порты в фаерволе:
  bash
  ufw allow 54321/tcp
  ufw reload
  
- `invalid token` — обновите GitHub-токен в настройках.


## 5. Полезные ссылки
- [Скрипт установки Hiddify](https://github.com/hiddify/Hiddify-Manager)
- [Документация X-UI](https://github.com/vaxilu/x-ui)


3. Форматирование логов
- Вставьте логи в блоки кода с указанием языка (например, `bash` для терминальных команд).
- Для длинных логов используйте сокращения (например, `...` вместо повторяющихся строк).

4. Сохранение
Нажмите "Commit changes" внизу страницы, чтобы сохранить `README.md`.

---

### 5. Дополнительно
- Если логи слишком большие, сохраните их в отдельные файлы (например, `logs/install.log`) и добавьте ссылки:
  markdown
  Полные логи доступны в [файле install.log](logs/install.log).
  

