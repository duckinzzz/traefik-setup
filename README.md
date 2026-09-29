# traefik-setup

Traefik v3 как общий reverse-proxy плюс страница «техработы» вместо ошибок
502/503/504.

Роутинг по лейблам контейнеров: `exposedByDefault: false` и ограничение
одной сетью `proxy`, то есть наружу попадает только помеченное явно.
Сертификаты берутся готовыми из `/etc/letsencrypt`, вход `web` редиректит
на https. На неизвестном поддомене отдаётся та же заглушка вместо ошибки TLS.

## Запуск

```bash
docker network create proxy
docker compose up -d
```

Домены в `dynamic.yml` заменены на `EXAMPLE.ru`.
