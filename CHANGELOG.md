# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0](https://github.com/openjobspec/ojs-proto/compare/v0.1.0...v0.2.0) (2026-02-28)


### Features

* add specification for middleware ordering ([4d3cdc7](https://github.com/openjobspec/ojs-proto/commit/4d3cdc7a90700928f038022666dd14ccc128093b))
* define cron expression validation rules ([c947517](https://github.com/openjobspec/ojs-proto/commit/c947517db14685c82bbaf3a95e802d5c0e7fbf67))


### Bug Fixes

* correct JSON schema for workflow step definition ([ffc0018](https://github.com/openjobspec/ojs-proto/commit/ffc00185054de82dc08c736f215345f5a0c1c12c))
* correct RFC 2119 keyword usage ([aae13c5](https://github.com/openjobspec/ojs-proto/commit/aae13c54d29fa67700c7eabfa185d1157ada4501))


### Performance Improvements

* optimize data processing loop ([71ebd95](https://github.com/openjobspec/ojs-proto/commit/71ebd954f292912c72b5a260c8762a4cfc387778))

## [Unreleased]

### Added
- Protocol Buffer definitions for OJS v1 gRPC binding (`proto/ojs/v1/`)
- `OJSService` gRPC service with all core operations (Enqueue, Fetch, Ack, Fail, Heartbeat, Cancel, GetJob)
- Streaming RPCs for worker coordination and real-time events
- Buf configuration (`buf.yaml`, `buf.gen.yaml`) for linting and code generation
- Generated Go code (`gen/`) and TypeScript code (`generated/`)
- README with architecture overview and usage instructions
