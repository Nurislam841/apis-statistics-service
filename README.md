# Statistics Service (Go + Clean Architecture + REST)

## Overview

This project is a standalone **Statistics Service** implemented in **Go**, following **Clean Architecture principles**.

The service is responsible for processing and exposing statistical data related to the system (e.g., aggregated metrics, summaries, calculated values). It provides RESTful HTTP endpoints and is structured to ensure modularity, maintainability, and scalability.

---

## Architecture

The project follows Clean Architecture layering:

```
cmd → adapter → usecase → repository → entity
```

### Layer Responsibilities

* **entity/**
  Core domain models and business rules related to statistics.

* **usecase/**
  Business logic for calculating, aggregating, and retrieving statistics.

* **repository/**
  Data abstraction layer (data access interface and implementation).

* **adapter/http/**
  HTTP handlers and routing configuration.

* **cmd/**
  Application entry point and server initialization.

This structure ensures:

* Clear separation of concerns
* Dependency inversion
* Testable business logic
* Extensible service architecture

---

## Project Structure

```
apis-statistics-service-master/
│
├── cmd/
│   └── main.go
│
├── internal/
│   ├── adapter/
│   │   └── http/
│   │       ├── handler.go
│   │       └── router.go
│   │
│   ├── entity/
│   │   └── statistics.go
│   │
│   ├── repository/
│   │   └── statistics_repository.go
│   │
│   └── usecase/
│       └── statistics_usecase.go
│
├── go.mod
└── go.sum
```

---

## Domain Model

### Statistics Entity

The core entity represents statistical data and may include:

* Aggregated counts
* Calculated metrics
* Summaries
* Derived values

All domain-specific logic is isolated in the `usecase` layer.

---

## API Endpoints

The service exposes REST endpoints for retrieving statistical data.

Typical operations include:

```
GET /statistics
GET /statistics/{id}
```

Additional endpoints may provide aggregated or filtered results depending on implementation inside `handler.go`.

All routes are defined in:

```
internal/adapter/http/router.go
```

---

## How to Run

### 1. Clone repository

```bash
git clone <your-repository-url>
cd apis-statistics-service-master
```

### 2. Install dependencies

```bash
go mod tidy
```

### 3. Run the service

```bash
go run cmd/main.go
```

The HTTP server will start on the port configured in `main.go`.

---

## Design Principles

* Clean Architecture
* Repository pattern
* Layered service structure
* Interface-based design
* Separation of domain and infrastructure

---

## What This Project Demonstrates

* REST API implementation in Go
* Service-oriented design
* Clean Architecture usage
* Statistical data handling and aggregation logic
* Structured and scalable backend service development
