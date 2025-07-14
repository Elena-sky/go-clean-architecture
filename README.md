# go-clean-architecture

## Overview
This project implements Clean Architecture in Go.  
All business logic and models are in `internal/domain`, interaction with external systems is in `internal/adapters`.  
The application entry point is `cmd/main.go`.  
Packages in `pkg` are intended for external reuse.

This repository is an artifact of a 3-part video series about Clean Architecture using the Go programming language as an example.
- Part 3 – https://youtu.be/PqQyCFygiZg
- Part 2 – https://youtu.be/s_Bou_mChKs
- Part 1 – https://youtu.be/eVhIlhLl4e4

## Project Structure

```bash
golang-clean-architecture/
├── cmd/                       # Application entry point
│   └── main.go                # Application entry point: starts the app
├── go.mod                     # Go module dependencies
├── go.sum                     # Go module checksums
├── img.png                    # Architecture diagram or other image
├── internal/
│   ├── adapters/              # Adapters for external systems (API, DB, etc.)
│   │   ├── api/               # HTTP API controllers
│   │   │   ├── book/
│   │   │   │   ├── dto.go         # Data Transfer Objects for book API
│   │   │   │   ├── interface.go   # Book API interface
│   │   │   │   └── handlers.go    # Book API handlers
│   │   │   ├── author/
│   │   │   │   ├── controllers.go # Author API controllers
│   │   │   │   ├── dto.go         # Data Transfer Objects for author API
│   │   │   │   ├── interface.go   # Author API interface
│   │   │   │   └── handlers.go    # Author API handlers
│   │   │   ├── genre/
│   │   │   │   ├── controllers.go # Genre API controllers
│   │   │   │   ├── dto.go         # Data Transfer Objects for genre API
│   │   │   │   └── interface.go   # Genre API interface
│   │   │   └── interface.go       # Common API interface
│   │   └── db/                 # Database adapters
│   │       ├── book/
│   │       │   └── storage.go     # Book DB adapter implementation
│   │       └── author/
│   │           └── storage.go     # Author DB adapter implementation
│   ├── composites/            # Dependency injection and composition root
│   │   ├── author.go              # Author service composition
│   │   ├── book.go                # Book service composition
│   │   └── mongodb.go             # MongoDB client composition
│   ├── config/                 # Configuration files and logic
│   │   └── config.go              # Application configuration logic
│   └── domain/                 # Business logic and models
│       ├── book/
│       │   ├── model.go            # Book domain model
│       │   ├── service.go          # Book business logic/service
│       │   └── storage.go          # Book storage interface
│       ├── author/
│       │   ├── model.go            # Author domain model
│       │   ├── service.go          # Author business logic/service
│       │   └── storage.go          # Author storage interface
│       └── genre/
│           └── model.go            # Genre domain model
├── pkg/                        # Public libraries for external use
│   ├── client/
│   │   └── mongodb/
│   │       └── client.go           # MongoDB client implementation
│   └── logging/
│       └── logging.go              # Logging initialization and helpers