# go-clean-architecture

# Overview
This project implements Clean Architecture in Go. 
All business logic and models are in internal/domain, interaction with external systems is in internal/adapters. 
The application entry point is cmd/main.go. 
Packages in pkg are intended for external reuse.

# Project Structure

```bash
golang-clean-architecture/
├── cmd/                    # Application entry point
│   └── main.go
├── go.mod                  # Go module dependencies
├── go.sum
├── img.png                 # Image (e.g., architecture diagram)
├── internal/               # Internal packages (private to the project)
│   ├── adapters/           # Adapters for external systems
│   │   ├── api/            # HTTP API controllers
│   │   │   ├── book/
│   │   │   │   └── controllers.go
│   │   │   ├── interface.go
│   │   │   └── user/
│   │   │       └── controllers.go
│   │   └── db/
│   │       └── book/
│   │           └── storage.go
│   └── domain/             # Business logic and models
│       ├── book/
│       │   ├── dto.go      # Book DTOs
│       │   ├── model.go    # Book model
│       │   ├── service.go  # Book service
│       │   └── storage.go  # Book storage interface
│       └── user/
│           └── model.go    # User model
├── pkg/                    # Public libraries for external use
│   └── client/
│       └── mongodb/
│           └── mongodb.go  # MongoDB client
```
