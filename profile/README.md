<p align="center">
  <img src="https://docs.coldbrew.cloud/assets/images/coldbrew.png" alt="ColdBrew" width="120">
</p>

<h1 align="center">ColdBrew</h1>

<p align="center">
  <strong>A Go microservice framework for building production-grade gRPC services</strong>
</p>

<p align="center">
  <a href="https://docs.coldbrew.cloud">Documentation</a> &middot;
  <a href="https://docs.coldbrew.cloud/getting-started">Getting Started</a> &middot;
  <a href="https://docs.coldbrew.cloud/packages">Packages</a> &middot;
  <a href="https://docs.coldbrew.cloud/howto">How-To Guides</a>
</p>

---

ColdBrew is a collection of Go libraries for creating cloud-native microservices. It provides ready-made components for gRPC servers with HTTP gateways, structured logging, distributed tracing, metrics, error tracking, and circuit breaking — all wired together with sensible defaults.

**Production-proven:** Powers 100+ microservices, handling peaks of ~70k QPS per service.

### Packages

| Package | Description |
|---------|-------------|
| [**core**](https://github.com/go-coldbrew/core) | gRPC server + HTTP gateway, health checks, metrics, signal handling, graceful shutdown |
| [**interceptors**](https://github.com/go-coldbrew/interceptors) | gRPC server/client interceptors for logging, tracing, metrics, errors, retries |
| [**errors**](https://github.com/go-coldbrew/errors) | Enhanced errors with stack traces, gRPC status codes, error notification (Sentry/Rollbar) |
| [**log**](https://github.com/go-coldbrew/log) | Structured logging with pluggable backends (go-kit, zap, logrus) |
| [**tracing**](https://github.com/go-coldbrew/tracing) | Distributed tracing via OpenTelemetry, OpenTracing, Jaeger, New Relic |
| [**options**](https://github.com/go-coldbrew/options) | Request-scoped key-value store using context |
| [**grpcpool**](https://github.com/go-coldbrew/grpcpool) | Round-robin gRPC connection pool |
| [**data-builder**](https://github.com/go-coldbrew/data-builder) | Dependency injection with automatic resolution and parallel execution |

### Package Dependencies

```text
options → errors → log → tracing → grpcpool → interceptors → data-builder → core
```

### Quick Start

```bash
# Install cookiecutter
brew install cookiecutter  # or: pip install cookiecutter

# Generate a new service
cookiecutter gh:go-coldbrew/cookiecutter-coldbrew

# Build and run
cd YourService/
make run
```

Your service starts with gRPC + REST gateway, Prometheus metrics, health checks, and Swagger UI — all out of the box.

### License

All ColdBrew packages are licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
