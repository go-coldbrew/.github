<p align="center">
  <img src="https://docs.coldbrew.cloud/assets/images/coldbrew.png" alt="ColdBrew" width="120">
</p>

<h1 align="center">ColdBrew</h1>

<p align="center">
  <strong>A Kubernetes-native Go microservice framework for building production-grade gRPC services</strong>
</p>

<p align="center">
  <a href="https://docs.coldbrew.cloud">Documentation</a> &middot;
  <a href="https://docs.coldbrew.cloud/getting-started">Getting Started</a> &middot;
  <a href="https://docs.coldbrew.cloud/packages">Packages</a> &middot;
  <a href="https://docs.coldbrew.cloud/howto">How-To Guides</a> &middot;
  <a href="https://docs.coldbrew.cloud/config-reference">Config Reference</a>
</p>

---

ColdBrew is a collection of Go libraries for creating cloud-native microservices. Built for Kubernetes, follows [12-factor](https://12factor.net/) principles, production-proven at 100+ microservices handling ~70k QPS each.

### What You Get Out of the Box

| Feature | Description |
|---------|-------------|
| **gRPC + REST Gateway** | Define your API once in protobuf — get gRPC, REST, and Swagger docs automatically via [grpc-gateway](https://grpc-ecosystem.github.io/grpc-gateway/) |
| **Structured Logging** | Pluggable backends (slog default, zap, logrus) with per-request context fields and trace ID propagation |
| **Distributed Tracing** | [OpenTelemetry](https://opentelemetry.io/), [Jaeger](https://www.jaegertracing.io/), and [New Relic](https://newrelic.com/) support with automatic span creation |
| **Prometheus Metrics** | Built-in request latency, error rate, and circuit breaker metrics at `/metrics` |
| **Error Tracking** | Stack traces, gRPC status codes, and async notification to [Sentry](https://sentry.io/), Rollbar, or Airbrake |
| **Resilience** | Client-side circuit breaking and retries via interceptors |
| **Fast Serialization** | [vtprotobuf](https://github.com/planetscale/vtprotobuf) codec enabled by default — faster gRPC marshalling with automatic fallback |
| **Kubernetes-native** | Health/ready probes, graceful SIGTERM shutdown, structured JSON logs, env var config via [envconfig](https://github.com/kelseyhightower/envconfig) or compatible `env:`-tag loaders |
| **Swagger / OpenAPI** | Interactive API docs auto-served at `/swagger/` from your protobuf definitions |
| **Profiling** | Go pprof endpoints at `/debug/pprof/` for CPU, memory, goroutine, and trace profiling |
| **gRPC Reflection** | Server reflection enabled by default — works with [grpcurl](https://github.com/fullstorydev/grpcurl), grpcui, and Postman |
| **HTTP Compression** | Automatic gzip and zstd compression for all HTTP gateway responses (content-negotiated) |
| **Request Validation** | [Protovalidate](https://github.com/bufbuild/protovalidate) annotations enforced automatically on both gRPC and HTTP requests |
| **Container-aware Runtime** | Auto-tunes GOMAXPROCS to match container CPU limits via [automaxprocs](https://github.com/uber-go/automaxprocs) |
| **CI/CD Pipelines** | Ready-to-use GitHub Actions and GitLab CI workflows for build, test, lint, and benchmarks |
| **Local Dev Stack** | Docker Compose with 19 services across 18 profiles + obs group — databases, caches, brokers, AWS/GCP emulators, Grafana, Jaeger |

### Packages

| Package | Description |
|---------|-------------|
| [**core**](https://github.com/go-coldbrew/core) | gRPC server + HTTP gateway, health checks, metrics, signal handling, graceful shutdown |
| [**interceptors**](https://github.com/go-coldbrew/interceptors) | gRPC server/client interceptors for logging, tracing, metrics, errors, retries |
| [**errors**](https://github.com/go-coldbrew/errors) | Enhanced errors with stack traces, gRPC status codes, error notification (Sentry/Rollbar) |
| [**log**](https://github.com/go-coldbrew/log) | Structured logging with pluggable backends (slog default, zap, logrus) |
| [**tracing**](https://github.com/go-coldbrew/tracing) | Distributed tracing via OpenTelemetry, Jaeger, New Relic |
| [**options**](https://github.com/go-coldbrew/options) | Request-scoped key-value store using context |
| [**grpcpool**](https://github.com/go-coldbrew/grpcpool) | Round-robin gRPC connection pool |
| [**data-builder**](https://github.com/go-coldbrew/data-builder) | Dependency injection with automatic resolution and parallel execution |
| [**workers**](https://github.com/go-coldbrew/workers) | Background worker lifecycle with panic recovery, restart, tracing, and metrics |

### Package Dependencies

```text
options → errors → log → tracing → grpcpool → interceptors → data-builder → core
                                                               workers ↗
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
