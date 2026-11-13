# Transport and protocol boundaries

This repository supplies a standalone host toolkit. The file commands work
without an adapter; the read/programming libraries use an injected transport.
No physical transport backend or live launcher is included in this release.

## Layers

| Layer | Role in the originating research | Shipped here |
| --- | --- | --- |
| RH02 USB firmware | Elmue CANable SLCAN; verified classical CAN with silent-open `OS` | Source/usage summaries, no adapter firmware |
| Host transport | Direct Linux serial framing and userspace ISO-TP | Injected application-payload interface only |
| Stock E78 services | Identity comparison, published access/preparation and RAM upload | Bounded read state machine and fake-peer regression tests |
| Running RAM kernel | Pinned KernelMPC5566 Version1.1, ready payload `99` | Packet planning/decoding; kernel obtained separately |
| Main-flash read | Kernel `35`, sequenced `36/76`, terminal `37/77` | Two-pass state machine with partial-data/error records |
| Programming | Inventory, complete physical blocks, terminal status and readback | Offline planner and injected programming core/tests |
| Restoration | Returning from the kernel to normal engine operation | Evidence summary; no automatic live restoration command |

The same service number can mean different things in stock software and the
running kernel. An ISO-TP library does not establish the stock preparation,
uploader, kernel dialect or recovery procedure. KernelMPC5566 entry is
`0x40014000`; addresses and commands from other kernels are not substitutes.

The originating RH02 reader obtained two matching 3MiB main-flash reads and
confirmed stock identity after a complete power cycle. That is evidence for the
recorded target and host, not validation of another adapter or a portable live
launcher. The main-flash coverage synthesizes64 bytes in ECC ranges
`0x3FE0..0x3FFF` and `0x1FFE0..0x1FFFF`; shadow memory is separate.

## What still needs implementation or validation

1. Package the live RH02 transport separately with explicit device selection,
   fixed operation scope, bounded timeouts and reproducible host tests.
2. Keep stock identity/preparation, RAM upload, kernel readiness and restoration
   as distinct states. A completed read does not itself restore engine control.
3. Establish physical programming, interrupted-write recovery and post-write
   acceptance before presenting a supported live writer.
4. Validate calibration changes against suitable measured engine response.
   File consistency and simulator success do not establish a performance tune.

Read [acquisition](acquisition.md), [current research](research-progress.md), and
[release verification](../RELEASE-REPORT.md) for the established evidence.
