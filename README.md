# Fiscalization Registrator

## Работа с приватным репозиторием

### Нужно выставить переменную окружения GOPRIVATE

```shell
export GOPRIVATE="gitlab.services.mts.ru/*"
```

### Создать (и поддерживать актуальность) в домашней директории файл .netrc с таким содержимым

```text
machine git.intmts.ru login твоймтсовскийлогин password твоймтсовскийпароль
```

### Для запуска нужно иметь переменную CONFIG_PATH с путём к конфигу

```shell
CONFIG_PATH=config/local.json 
```

### В директории docker
1. Переименовать .env.dist -> .env;
2. В энвы ```CI_JOB_TOKEN``` - установить значение  [Gitlab Access Token](https://git.intmts.ru/-/profile/personal_access_tokens);

---

## [Swagger](docs/openapi/swagger.json)

## Шорткаты для локалки

* Запустить линтер
    ```shell
    make lint
    ```
* Поднять проект в контейнере
    ```shell
    make up
    ```

* Поднять инфраструктуру в контейнере и сервис локально
    ```shell
    make up-dev
    go run cmd/main.go  
    ```

* Swagger документация
    ```shell
    make swagger-init:
    ```
* Накатить миграции
    ```shell
    make mu
    ```

* Help
    ```shell
    make help
    ```

* Статус миграций
    ```shell
    make ms
    ```

---

##  Генерация моков

* Установить mockery
    ```text
    https://github.com/vektra/mockery
    ```

* Для добавления новых пакетов генерации моков в [.mockery.yaml](.mockery.yaml) в раздел **packages** необходимо добавить новый пакет, [Док](https://vektra.github.io/mockery/v2.42/features/#packages-configuration).

* Запустить генерацию моков в корне проекта
    ```shell
    mockery
    ```
--- 




##  Генерация моков

* Установить mockery
```text
https://github.com/vektra/mockery
```

Для добавления новых пакетов генерации моков в [.mockery.yaml](.mockery.yaml) в раздел **packages** необходимо добавить новый пакет, [Док](https://vektra.github.io/mockery/v2.42/features/#packages-configuration).



* Запустить генерацию моков в корне проекта
```shell
mockery
```
--- 
## Конфигурация

| Options                       | Env Variables                         | Default values  | Description                                                       |
|-------------------------------|---------------------------------------|----------------|-------------------------------------------------------------------|
| frame_config.http_server.port  | FRAME_CONFIG_HTTP_SERVER_PORT         | 8080           | HTTP порт                                                         |
| logger.level                   | LOGGER_LEVEL                          | debug          | уровень логирования и вывод в stdout(info, error, warning, debug) |
| config_path                    | CONFIG_PATH                           | config/local.json | путь к конфигу                                                   |
| kafka.brokers                  | KAFKA_BROKERS                         | localhost       | хост подключения к кафке                                          |
| ATOL client host               | ATOL_CLIENT_HOST                      | string        | Хост для подключения к ATOL                                        |
| ATOL credentials login         | ATOL_CRD_LOGIN                        | string        | Логин для ATOL                                                     |
| ATOL credentials password      | ATOL_CRD_PASS                         | string        | Пароль для ATOL                                                    |
| Fiscalization host             | FISCALIZATION_HOST                    | string        | Хост для фискализации                                              |

## Зависимости
```text
gitlab.services.mts.ru/shop/microservices/lib/frame v1.8.0
github.com/go-chi/chi/v5 v5.0.12
github.com/go-playground/validator/v10 v10.22.1
github.com/ilyakaznacheev/cleanenv v1.5.0
github.com/json-iterator/go v1.1.12
github.com/pkg/errors v0.9.1
github.com/prometheus/client_golang v1.20.3
github.com/segmentio/kafka-go v0.4.47
github.com/stretchr/testify v1.9.0
github.com/swaggo/swag v1.16.3
github.com/valyala/fasthttp v1.55.0
go.opentelemetry.io/otel v1.30.0
go.opentelemetry.io/otel/exporters/otlp/otlptrace/otlptracehttp v1.28.0
go.opentelemetry.io/otel/exporters/prometheus v0.52.0
go.opentelemetry.io/otel/sdk v1.30.0
go.opentelemetry.io/otel/sdk/metric v1.30.0
go.uber.org/multierr v1.11.0
```
