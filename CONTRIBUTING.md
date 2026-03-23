# Contributing to ColdBrew

Thank you for your interest in contributing to ColdBrew! This guide will help you get started.

## Development Setup

### Prerequisites

- **Go 1.25+** (latest stable)
- **golangci-lint** v2.8+ for linting
- **make** for build orchestration

### Getting Started

1. Fork the repository you want to contribute to
2. Clone your fork:
   ```bash
   git clone https://github.com/YOUR_USERNAME/PACKAGE_NAME.git
   cd PACKAGE_NAME
   ```
3. Run the tests to make sure everything works:
   ```bash
   make test
   ```

### Available Make Targets

Every package supports these standard targets:

```bash
make build    # go build ./...
make test     # go test -race ./...
make lint     # golangci-lint run
make bench    # go test -run=^$ -bench=. -benchmem ./...
make doc      # regenerate README.md via gomarkdoc
```

## Making Changes

### Code Style

- Follow standard Go conventions (`gofmt`, `goimports`)
- All exported symbols must have doc comments
- Use `context.Context` as the first parameter where applicable
- Configuration functions follow the "init-only" pattern (not thread-safe by design)

### Testing

- All changes must include tests
- Tests must pass with the race detector: `make test` (runs `go test -race ./...`)
- Run linting before submitting: `make lint`

### No Breaking Changes

ColdBrew is used by 100+ production microservices. **Breaking changes are not accepted**, especially anything that could break at runtime. This includes:

- Removing or renaming exported types, functions, or methods
- Changing function signatures
- Changing default behavior

If you need to deprecate something, add a doc comment and keep the old API working.

## Pull Request Process

1. Create a feature branch from `main` (or `master` for cookiecutter-coldbrew)
2. Make your changes with tests
3. Run `make lint` and `make test`
4. Run `make doc` if you changed any exported APIs or docstrings
5. Submit a pull request with:
   - A clear description of what the change does and why
   - Any relevant issue numbers
   - Confirmation that tests pass

### PR Checklist

- [ ] Tests added/updated
- [ ] `make lint` passes
- [ ] `make test` passes
- [ ] `make doc` run if exported APIs changed
- [ ] No breaking changes

## Package Dependency Order

When making changes that span multiple packages, work in dependency order:

```
options -> errors -> log -> tracing -> grpcpool -> interceptors -> data-builder -> core
```

## Reporting Issues

- Use the issue templates provided in each repository
- Include Go version, OS, and steps to reproduce
- For security issues, see [SECURITY.md](SECURITY.md)

## Questions?

Open a discussion or issue in the relevant repository. We're happy to help!
