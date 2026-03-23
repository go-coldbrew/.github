# Contributing to ColdBrew

Thank you for your interest in contributing to ColdBrew! This guide will help you get started.

## Getting Started

### Prerequisites

- [Go 1.25+](https://go.dev/dl/)
- [golangci-lint](https://golangci-lint.run/welcome/install-local/)
- [gomarkdoc](https://github.com/princjef/gomarkdoc) (for regenerating README docs)
- [buf](https://buf.build/) (for protobuf work in core/cookiecutter)

### Development Setup

Each ColdBrew package is an independent Go module with its own repository:

```bash
# Clone the package you want to work on
git clone https://github.com/go-coldbrew/<package-name>.git
cd <package-name>

# Build
make build

# Run tests with race detection
make test

# Run linter
make lint

# Run benchmarks
make bench
```

### Package Dependencies

Packages are organized in dependency order. If your change spans multiple packages, work in this order:

```
options → errors → log → tracing → grpcpool → interceptors → data-builder → core
```

## Making Changes

### Before You Start

1. **Open an issue first** — discuss the change before investing time in a PR. (Do not open public issues for security vulnerabilities; see [SECURITY.md](SECURITY.md) for private disclosure instructions.)
2. **Check existing issues** — someone may already be working on it
3. **One concern per PR** — keep changes focused and reviewable

### Code Style

- Follow standard Go conventions (`gofmt`, `go vet`)
- All exported functions and types must have doc comments
- Configuration functions follow the "init-only" pattern (called during startup, not thread-safe) — this is intentional and consistent across the codebase
- `context.Context` is always the first parameter

### Testing

- All changes must include tests
- Tests must pass with the race detector: `make test` (runs `go test -race ./...`)
- Linting must pass: `make lint`
- If you add or change exported APIs, regenerate the README: `make doc`

### Commit Messages

- Use clear, descriptive commit messages
- Start with a verb in imperative mood (e.g., "Add support for...", "Fix race condition in...")

## Submitting a Pull Request

1. Fork the repository
2. Create a feature branch from `main`
3. Make your changes with tests
4. Run `make test && make lint`
5. If you changed exported APIs or doc comments, run `make doc` and commit the updated `README.md`
6. Open a PR against `main`

### PR Checklist

- [ ] Tests pass (`make test`)
- [ ] Linter passes (`make lint`)
- [ ] README regenerated if APIs changed (`make doc`)
- [ ] No breaking changes (ColdBrew is used by 100+ services in production)
- [ ] Doc comments added for new exported APIs

## Important Guidelines

### No Breaking Changes

ColdBrew powers 100+ microservices in production. Breaking changes — especially runtime breakage — are not acceptable. If you need to deprecate something, add a new API alongside the old one.

### Documentation

READMEs are auto-generated from Go doc comments using [gomarkdoc](https://github.com/princjef/gomarkdoc). To update documentation:

1. Edit the doc comments in the Go source code
2. Run `make doc` to regenerate `README.md`
3. Commit the updated `README.md` along with your code changes

Full documentation lives at [docs.coldbrew.cloud](https://docs.coldbrew.cloud).

## Getting Help

- Open an issue on the relevant package repository
- Check the [How-To Guides](https://docs.coldbrew.cloud/howto) for usage examples
- Review the [Packages](https://docs.coldbrew.cloud/packages) page for API documentation

## License

By contributing to ColdBrew, you agree that your contributions will be licensed under the Apache License 2.0.
