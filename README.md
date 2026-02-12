# ojs-proto

Protocol Buffer definitions for the [Open Job Spec](https://openjobspec.org) (OJS) gRPC protocol binding.

This repository contains the canonical `.proto` files that define the `ojs.v1` gRPC service and message types. These definitions are the machine-readable counterpart to the [OJS gRPC Binding Specification](../spec/spec/ojs-grpc-binding.md).

## Overview

The Open Job Spec is an open, language-agnostic, backend-agnostic standard for background job processing. The gRPC binding provides a high-performance protocol for job ingestion, worker coordination, real-time streaming, and system management.

### Architecture

```
ojs-core.md          (Layer 1: Core)       -- Job envelope, lifecycle, operations
ojs-json-format.md   (Layer 2: Wire)       -- JSON serialization rules
ojs-grpc-binding.md  (Layer 3: Protocol)   -- gRPC mapping (this package)
ojs-http-binding.md  (Layer 3: Protocol)   -- HTTP/REST mapping
```

## Directory Structure

```
ojs-proto/
  proto/
    ojs/
      v1/
        job.proto          # Job envelope, states, retry/unique policies, errors
        queue.proto        # Queue operations (list, stats, pause/resume, dead letter)
        worker.proto       # Worker coordination (fetch, ack, nack, heartbeat, streaming)
        workflow.proto     # Workflow types (create, get, cancel workflows)
        events.proto       # Lifecycle events and event streaming
        service.proto      # OJSService gRPC definition + system messages
  buf.yaml                 # Buf module configuration
  buf.gen.yaml             # Code generation configuration
  generated/
    go/                    # Generated Go code
    ts/                    # Generated TypeScript code
```

## Proto Files

| File | Description |
|------|-------------|
| `job.proto` | Core job types: `Job`, `JobState`, `RetryPolicy`, `UniquePolicy`, `JobError`, `EnqueueOptions`, and enqueue/get/cancel request/response messages |
| `queue.proto` | Queue management: `QueueInfo`, `QueueStatistics`, list/stats/pause/resume RPCs, and dead letter operations |
| `worker.proto` | Worker protocol: `WorkerState`, fetch/ack/nack/heartbeat RPCs, and `StreamJobs` streaming |
| `workflow.proto` | Workflow orchestration: `Workflow`, `WorkflowStep`, `WorkflowState`, and create/get/cancel RPCs |
| `events.proto` | Event system: `Event` message and `StreamEvents` streaming |
| `service.proto` | The `OJSService` gRPC service definition with all RPCs, plus system messages (`Manifest`, `Health`) and cron messages |

## Conformance Levels

The `OJSService` RPCs are organized by conformance level:

| Level | Name | Required RPCs |
|-------|------|---------------|
| 0 | Core | `Manifest`, `Health`, `Enqueue`, `Fetch`, `Ack`, `Nack`, `ListQueues` |
| 1 | Reliable | Level 0 + `GetJob`, `CancelJob`, `Heartbeat`, `ListDeadLetter`, `RetryDeadLetter`, `DeleteDeadLetter` |
| 2 | Scheduled | Level 1 + `RegisterCron`, `UnregisterCron`, `ListCron` |
| 3 | Orchestration | Level 2 + `CreateWorkflow`, `GetWorkflow`, `CancelWorkflow` |
| 4 | Advanced | Level 3 + `EnqueueBatch`, `QueueStats`, `PauseQueue`, `ResumeQueue` |
| Optional | Any level | `StreamJobs`, `StreamEvents` |

Unsupported RPCs MUST return `UNIMPLEMENTED`.

## Code Generation

### Prerequisites

Install [Buf](https://buf.build/docs/installation):

```bash
# macOS
brew install bufbuild/buf/buf

# npm
npm install -g @bufbuild/buf
```

### Generate Code

```bash
# Lint proto files
buf lint

# Check for breaking changes
buf breaking --against '.git#branch=main'

# Generate Go and TypeScript code
buf generate
```

### Using Generated Code

**Go:**

```go
import ojsv1 "github.com/openjobspec/ojs-proto/gen/go/ojs/v1"

job := &ojsv1.Job{
    Type:  "email.send",
    Queue: "default",
    Args:  []*structpb.Value{
        structpb.NewStringValue("user@example.com"),
        structpb.NewStringValue("welcome"),
    },
}
```

**TypeScript:**

```typescript
import { OJSService } from "./generated/ts/ojs/v1/service_pb";
```

## Specification References

- [OJS Core Specification](../spec/spec/ojs-core.md) -- Job envelope, lifecycle, operations
- [OJS gRPC Binding](../spec/spec/ojs-grpc-binding.md) -- gRPC protocol mapping
- [OJS HTTP Binding](../spec/spec/ojs-http-binding.md) -- HTTP/REST protocol mapping
- [OJS Retry Policy](../spec/spec/ojs-retry.md) -- Retry policy specification
- [OJS Unique Jobs](../spec/spec/ojs-unique-jobs.md) -- Job deduplication
- [OJS Workflows](../spec/spec/ojs-workflows.md) -- Workflow primitives
- [OJS Cron](../spec/spec/ojs-cron.md) -- Periodic job scheduling
- [OJS Events](../spec/spec/ojs-events.md) -- Lifecycle event vocabulary
- [OJS Conformance](../spec/spec/ojs-conformance.md) -- Conformance levels

## License

Apache 2.0 -- see [LICENSE](./LICENSE).
