# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Protocol Buffer definitions for OJS v1 gRPC binding (`proto/ojs/v1/`)
- `OJSService` gRPC service with all core operations (Enqueue, Fetch, Ack, Fail, Heartbeat, Cancel, GetJob)
- Streaming RPCs for worker coordination and real-time events
- Buf configuration (`buf.yaml`, `buf.gen.yaml`) for linting and code generation
- Generated Go code (`gen/`) and TypeScript code (`generated/`)
- README with architecture overview and usage instructions
