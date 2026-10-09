# corpoario-notifications

Microsserviço de Notificações da plataforma de ateliê digital (Quarkus, Java 25, Maven).

Contém apenas a estrutura inicial: nenhuma entidade, endpoint, consumidor ou template foi implementado.

## Stack

REST/JSON, Hibernate ORM com Panache + PostgreSQL, Flyway, Hibernate Validator,
RabbitMQ (SmallRye Reactive Messaging), Quarkus Mailer (SMTP), OpenAPI, health checks e métricas Prometheus.

## Requisitos

- JDK 25
- Maven 3.9+
- PostgreSQL, RabbitMQ e um servidor SMTP (ex.: Mailpit/MailHog) acessíveis

## Executar

```shell
mvn quarkus:dev
```

Empacotar: `mvn package` e executar com `java -jar target/quarkus-app/quarkus-run.jar`.

Ao iniciar, o Flyway executa os scripts de `src/main/resources/db/migration` (ex.: `V1__descricao.sql`).

## Configuração (variáveis de ambiente)

| Variável | Padrão |
|---|---|
| `DB_URL` | `jdbc:postgresql://localhost:5432/notifications` |
| `DB_USERNAME` / `DB_PASSWORD` | `notifications` / `notifications` (somente desenvolvimento) |
| `RABBITMQ_HOST` / `RABBITMQ_PORT` | `localhost` / `5672` |
| `RABBITMQ_USERNAME` / `RABBITMQ_PASSWORD` | `guest` / `guest` (somente desenvolvimento) |
| `SMTP_HOST` / `SMTP_PORT` | `localhost` / `1025` |
| `SMTP_USERNAME` / `SMTP_PASSWORD` | vazio |
| `SMTP_FROM` | `no-reply@example.com` |
| `SMTP_START_TLS` | `OPTIONAL` (`DISABLED`, `OPTIONAL`, `REQUIRED`) |
| `SMTP_SSL` | `false` |

Nunca versione credenciais reais.

## Endpoints operacionais

- OpenAPI: `/q/openapi`
- Health: `/q/health`
- Métricas Prometheus: `/q/metrics`
