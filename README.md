# Analytics Service

## Описание

Микросервис аналитики в веб-приложении **CorporationX**. Отвечает за сбор и хранение данных об активности пользователей и проектов: запросы на менторство, просмотры и комментарии постов, лайки, посещаемость профилей пользователей и проектов, завершённые цели, подписки, покупки премиум-подписок, рекомендации и донаты на проекты. Реализован по event-driven принципу — сервис слушает соответствующие события из других сервисов через Redis Pub/Sub и сохраняет их в БД для последующего анализа. Также предоставляет [REST-эндпоинт](https://github.com/Erik18999/analytics_service/blob/werewolf-master-stream8/src/main/java/faang/school/analytics/controller/AnalyticsEventController.java) `/analytics` для получения аналитики по любой сущности за заданный промежуток времени.

## CI

Настроен GitHub Actions пайплайн для проверки Pull Request'ов в ветку `werewolf-master-stream8`: сборка проекта, прогон тестов, проверка стиля кода (Checkstyle), автоматический комментарий в PR при падении сборки.

- [`.github/workflows/ci.yml`](.github/workflows/ci.yml)

## Стек

- Java 17
- Spring Boot 3
- Spring Data JPA
- PostgreSQL
- Redis (Pub/Sub)
- Liquibase
- Feign Client
- MapStruct
- Checkstyle
- JUnit 5

## Запуск

### Предварительные требования
- Docker и Docker Compose
- JDK 17

### Шаги

1. Поднять инфраструктуру (Postgres, Redis, MinIO, Kafka):
```bash
git clone https://github.com/Erik18999/infra.git
cd infra
./run.sh
```
2. Склонировать и запустить сам сервис (порт 8086):
```bash
git clone https://github.com/Erik18999/analytics_service.git
cd analytics_service
```
Открыть проект в IntelliJ IDEA и запустить [`AnalyticsServiceApp`](src/main/java/faang/school/analytics/AnalyticsServiceApp.java).
