# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 1.0.0 (2026-02-16)


### Features

* **codegen:** add Java, Python, Ruby, and Rust generation targets ([3114221](https://github.com/openjobspec/ojs-proto/commit/3114221aee81715728b401cc646636b0947f5089))
* **proto:** add on_exhaustion action to RetryPolicy ([d3228a6](https://github.com/openjobspec/ojs-proto/commit/d3228a6d961d25dd870e05c2e22daa9d7e6e33a9))
* **proto:** add queue management and dead letter operations ([790de65](https://github.com/openjobspec/ojs-proto/commit/790de650181628a15b902d0df8caa84b3a6eb219))
* **proto:** add real-time event streaming definitions ([a6f1f27](https://github.com/openjobspec/ojs-proto/commit/a6f1f27258c4c685162b8890671a2cf63542333f))
* **proto:** add specversion field to Job message ([233a108](https://github.com/openjobspec/ojs-proto/commit/233a108addae9232f6ed5911b792700ecf1a4166))
* **proto:** add worker coordination protocol ([34b8ffa](https://github.com/openjobspec/ojs-proto/commit/34b8ffa719318da6fbf953f7a301ce0ceb0fa258))
* **proto:** add workflow orchestration types ([a0ba337](https://github.com/openjobspec/ojs-proto/commit/a0ba337b2c14317eff9d280b57e34576a446fe0e))
* **proto:** define core job envelope and lifecycle types ([80a5c29](https://github.com/openjobspec/ojs-proto/commit/80a5c299c5bb31714dbbebc4f90c3a1a95e5349d))
* **proto:** define OJS gRPC service with conformance levels ([3a7d7c2](https://github.com/openjobspec/ojs-proto/commit/3a7d7c2e5aa623984e428c47fbd20e0d8bf1ca59))
* **proto:** extend unique jobs with granular keys and replace-except-schedule ([4effade](https://github.com/openjobspec/ojs-proto/commit/4effade7a828be408d54309464b5fe41004dd33c))

## [Unreleased]

### Added
- Protocol Buffer definitions for OJS v1 gRPC binding (`proto/ojs/v1/`)
- `OJSService` gRPC service with all core operations (Enqueue, Fetch, Ack, Fail, Heartbeat, Cancel, GetJob)
- Streaming RPCs for worker coordination and real-time events
- Buf configuration (`buf.yaml`, `buf.gen.yaml`) for linting and code generation
- Generated Go code (`gen/`) and TypeScript code (`generated/`)
- README with architecture overview and usage instructions
