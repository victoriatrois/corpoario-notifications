# corpoario-notifications

Notifications microservice of the digital atelier platform (Quarkus, Java 25, Maven).

It contains only the initial structure: no entities, endpoints, consumers or e-mail templates have been implemented.

A Portuguese version of this document is available in [README.pt-br.md](README.pt-br.md).

## Stack

REST/JSON, Hibernate ORM with Panache + PostgreSQL, Flyway, Hibernate Validator,
RabbitMQ (SmallRye Reactive Messaging), Quarkus Mailer (SMTP), OpenAPI, health checks and Prometheus metrics.

## Requirements

- JDK 25
- Maven 3.9+
- PostgreSQL, RabbitMQ and an SMTP server (e.g. Mailpit/MailHog) reachable from the service

## Running

```shell
mvn quarkus:dev
```

To package: `mvn package`, then run `java -jar target/quarkus-app/quarkus-run.jar`.

On startup, Flyway runs the scripts in `src/main/resources/db/migration` (e.g. `V1__description.sql`).

## Configuration (environment variables)

| Variable | Default |
|---|---|
| `DB_URL` | `jdbc:postgresql://localhost:5432/notifications` |
| `DB_USERNAME` / `DB_PASSWORD` | `notifications` / `notifications` (development only) |
| `RABBITMQ_HOST` / `RABBITMQ_PORT` | `localhost` / `5672` |
| `RABBITMQ_USERNAME` / `RABBITMQ_PASSWORD` | `guest` / `guest` (development only) |
| `SMTP_HOST` / `SMTP_PORT` | `localhost` / `1025` |
| `SMTP_USERNAME` / `SMTP_PASSWORD` | empty |
| `SMTP_FROM` | `no-reply@example.com` |
| `SMTP_START_TLS` | `OPTIONAL` (`DISABLED`, `OPTIONAL`, `REQUIRED`) |
| `SMTP_SSL` | `false` |

Never commit real credentials.

## Operational endpoints

- OpenAPI: `/q/openapi`
- Health: `/q/health`
- Prometheus metrics: `/q/metrics`
