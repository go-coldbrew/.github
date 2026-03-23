## ColdBrew

**A Go microservice framework for building production-grade gRPC services.**

ColdBrew powers **100+ microservices** serving **70k+ QPS each** in production. It provides a batteries-included foundation for gRPC services with built-in observability, resilience, and HTTP gateway support.

### Features

- **gRPC + HTTP Gateway** — Automatic REST gateway via grpc-gateway
- **Observability** — Prometheus metrics, OpenTelemetry distributed tracing, structured logging
- **Resilience** — Circuit breaking with Prometheus metrics, retries
- **Error Tracking** — Sentry, Rollbar, Airbrake with async notification and stack traces
- **Developer Experience** — Cookiecutter template to generate a production-ready service in seconds

### Packages

| Package | Description |
|---------|-------------|
| [core](https://github.com/go-coldbrew/core) | Main entry point: gRPC server, HTTP gateway, health checks, metrics, graceful shutdown |
| [interceptors](https://github.com/go-coldbrew/interceptors) | Chained gRPC interceptors: logging, tracing, Prometheus, circuit breaking, retries |
| [errors](https://github.com/go-coldbrew/errors) | Enhanced errors with stack traces, gRPC status codes, error notification |
| [log](https://github.com/go-coldbrew/log) | Structured logging with pluggable backends (zap, logrus, go-kit) |
| [tracing](https://github.com/go-coldbrew/tracing) | Distributed tracing: OpenTelemetry, OpenTracing, NewRelic |
| [options](https://github.com/go-coldbrew/options) | Request-scoped key-value metadata via context |
| [grpcpool](https://github.com/go-coldbrew/grpcpool) | Round-robin gRPC connection pool |
| [data-builder](https://github.com/go-coldbrew/data-builder) | Dependency injection with automatic resolution and parallel execution |

### Get Started

```bash
# Generate a new service from the template
pip install cookiecutter
cookiecutter gh:go-coldbrew/cookiecutter-coldbrew

# Or add ColdBrew to an existing project
go get github.com/go-coldbrew/core
```

### Links

- [Documentation](https://docs.coldbrew.cloud) — Guides, architecture, and API reference
- [Cookiecutter Template](https://github.com/go-coldbrew/cookiecutter-coldbrew) — Generate a new service
- [pkg.go.dev](https://pkg.go.dev/github.com/go-coldbrew/core) — Go package documentation
