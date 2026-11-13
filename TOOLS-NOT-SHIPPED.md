# Included and excluded acquisition/research components

This release includes the injected original-read state machine, packet decoder
and pure identity decoder. Synthetic transport tests exercise those components;
they supply no serial/CAN backend or live launcher. See
[protocol boundaries](docs/protocols.md).

The standalone calibration workflow assumes a caller-owned exact matching
original. An end-to-end reader/logger is a separate planned deliverable.

The originating verified acquisition also uses private RH02 transport, identity
and launch helpers. Its direct serial route depends on Linux POSIX support,
can-isotp and LZ4, plus explicit identity/kernel inputs and a bounded session
with a restoration plan. It uses termios/fcntl rather than pyserial. Other
environment packages are not automatically dependencies of every workflow.

Private runtime tools and analyzers often depend on saved trace/capture exports.
A portable release needs explicit input/device selection, retained request
allowlists and traffic checks, and its own transport/negative tests. Copying a
single host-bound script does not supply that integration.

Ghidra scripts, restricted eTPU interpreters, loader/peripheral models and their
private projects remain research components. Their current scope is summarized
in [research progress](docs/research-progress.md); the source kit does not ship
every harness or claim a complete ECU simulator. Definition exporters consume
already established metadata and a matching private image, without needing
Ghidra installed or re-running the original instruction traces.

Firmware dumps, candidate binaries, kernel assets, donor images, stock cell
arrays, VIN/identity/security records, raw captures and Ghidra databases are
excluded. Source provenance does not grant access to those private inputs.
No live flashing, physical recovery or validated performance tune is supplied.
