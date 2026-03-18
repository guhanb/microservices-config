# microservices-config

This is the **central configuration repository** for all microservices.
Spring Cloud Config Server reads configuration from this repository.

## Structure

```
microservices-config/
├── user-service/
│   ├── application.properties          (default)
│   ├── application-dev.properties      (development)
│   ├── application-qa.properties       (qa/testing)
│   └── application-prod.properties     (production)
├── product-service/   (same 4 files)
├── order-service/     (same 4 files)
└── payment-service/   (same 4 files)
```

## How to Use

1. Push this repo to your GitHub account
2. Update `spring.cloud.config.server.git.uri` in config-server's application.properties
3. Start Config Server — it will read from this repo automatically

## How to Refresh Config (Without Restart)

```bash
POST http://localhost:8888/actuator/busrefresh
```

All services will pick up new config instantly via RabbitMQ + Spring Cloud Bus.
