## 1. Используйте healthcheck-и
Атрибут [healthckeck](https://docs.docker.com/reference/compose-file/services/#healthcheck) позволяет определить команду, которая поможет docker compose следить за состоянием вашего сервиса. Docker и  Compose не могут рестартовать или управлять состоянием чего-либо, если не знаю о неисправности. 
```
healthcheck:
  test: ["CMD", "curl", "-f", "http://localhost:3000"]
  interval: 30s
  timeout: 5s
  retries: 3
```

## 2. Создание отдельного пользователя
Создайте в Dockerfile пользователя, не являющегося пользователем root, и переключитесь на него:
```
RUN useradd -m appuser
USER appuser
```