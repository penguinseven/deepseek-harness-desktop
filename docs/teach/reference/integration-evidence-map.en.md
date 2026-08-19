# Integration Evidence Map

[中文](integration-evidence-map.md)

Copy this template for a real Harness or Web UI. Every fact must point to a
file, command output, official document, or repeatable experiment.

## Target

- **Target project and version:**
- **Integration phase:** assessment / prototype / implementation / release
- **Target platforms:**
- **Required Native capabilities:**

## Five-layer evidence

| Layer | Confirmed facts | Evidence location | Unknowns |
| --- | --- | --- | --- |
| Host |  |  |  |
| Carrier |  |  |  |
| Client |  |  |  |
| Profile |  |  |  |
| Native |  |  |  |

## Carrier-pattern decision

- **Selection:** thin host / sidecar / static Client / transport prerequisite
- **Rationale:**
- **Rejected patterns and evidence:**

## Compatibility tracer contract

| Stage | Contract | Owner | Health/completion signal | Failure handling | Verification command |
| --- | --- | --- | --- | --- | --- |
| Startup |  |  |  |  |  |
| Health |  |  |  |  |  |
| Presentation |  |  |  |  |  |
| Shutdown |  |  |  |  |  |
| Recovery |  |  |  |  |  |

## Public and internal boundary

| Capability | Public contract or internal | Consumer | Lifetime | Rationale |
| --- | --- | --- | --- | --- |
|  |  |  |  |  |

## Runtime closure

| Dependency | Source and version | Virtual/physical path | ABI/architecture | License | Package verification |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |

## Unknown experiments

| Unknown | Smallest experiment | Expected observation | Result | Design effect |
| --- | --- | --- | --- | --- |
|  |  |  |  |  |

## Completion gate

- [ ] Every layer has evidence or is marked absent/unknown.
- [ ] Every unknown has an executable experiment or external decision owner.
- [ ] The tracer covers startup, health, presentation, shutdown, and recovery.
- [ ] At least one headless smoke proves the end-to-end path.
- [ ] The implementation needs no undeclared path or global developer tool.
