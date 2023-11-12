[![Go Reference](https://pkg.go.dev/badge/github.com/raw0w/otelpgx.svg)](https://pkg.go.dev/github.com/raw0w/otelpgx)

# otelpgx

Provides [OpenTelemetry](https://github.com/open-telemetry/opentelemetry-go) 
instrumentation for the [jackc/pgx](https://github.com/jackc/pgx) library.

## Requirements

- go 1.18 (or higher)
- pgx v5 (or higher)

## Usage

Make sure you have a suitable pgx version:

```bash
go get github.com/raw0w/pgx/v5
```

Install the library:

```go
go get github.com/raw0w/otelpgx
```

Create the tracer as part of your connection:

```go
cfg, err := pgxpool.ParseConfig(connString)
if err != nil {
    return nil, fmt.Errorf("create connection pool: %w", err)
}

cfg.ConnConfig.Tracer = otelpgx.NewTracer()

conn, err := pgxpool.NewWithConfig(ctx, cfg)
if err != nil {
    return nil, fmt.Errorf("connect to database: %w", err)
}
```

See [options.go](options.go) for the full list of options.
