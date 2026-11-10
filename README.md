# E78 Tuning

A reproducible research and offline calibration toolkit for GM E78 projects, with a worked case from a 2011 Chevrolet Cruze LT. Start with your own private original, establish what the software actually does, propose one documented change, and review a checksummed candidate.

**Current release scope: research through offline candidate review. Physical flash programming, interrupted-write recovery, loaded calibration validation, and a complete performance or crackle tune have not been validated by this project.** No live flashing launcher is included.

The worked profile is the installed OS **12644082**, EngineOper **55581437**, exact baseline SHA-256 `3b9b58421977ae2a5fb0f5d4d1bf71702cd97922109a215cab1ba9405e3920ba`. Its factory-stock provenance has not been established. Same ECU family or OS number does not establish binary compatibility. The tools deliberately reject a different baseline.

## Start here

1. Read the [replication workflow](docs/replication.md) and [minimal tool/file inventory](docs/minimum-kit.md).
2. Run the synthetic example and public offline tests, with no ECU or firmware needed:

   ```sh
   python3 examples/synthetic/demo.py
   PYTHONPATH=tools python3 -m unittest discover -s tests -v
   ```

3. Read the [discoveries and evidence limits](docs/discoveries.md), [exact-image profile](definitions/README.md), and [worked pedal example](examples/pedal-response.md).
4. For different software, follow the [new-project adaptation checklist](docs/adapting.md). Replacing a digest check is not a port.
5. Review [what remains before an actual tune](docs/tuning-and-validation.md).

## What is established

| Stage | Evidence from the worked case | Included here |
| --- | --- | --- |
| Acquisition | Two matching physical 3 MiB reads and restored original diagnostic identities | Sanitized procedure and pinned upstream references; originals and live reader are excluded |
| Image interpretation | Five calibration segments, all 17 recorded checksums, ten static table definitions | Exact-image offline core, layout constants, source ledger and address catalog |
| Runtime interpretation | Fixed stock diagnostic/RAM reads and limited stationary table comparison | Findings and tested-scope catalog; no automatic vehicle workflow |
| Editing | A 17-cell pedal-A draft, checksums and bounded diff reviewed offline | CSV export/build, checksum correction, physical-block planning |
| Programming | Protocol state machine tested with simulated flash callbacks | Injected-transport research core; no adapter/unlock/loader/reset launcher |
| Actual tune | Physical write/recovery and controlled loaded validation unresolved | Explicit dependencies and review templates |

## Repository map

- `tools/`: a minimal six-module core plus optional definition exporter and synthetic demo. The worksheet workflow uses the Python standard library.
- `vendor/`: pinned UniversalPatcher signature XML and its license/provenance.
- `definitions/`: exact-image addresses and interpretation; research definitions are not blanket edit approval.
- `examples/`: synthetic checks and a documented, explicitly experimental pedal edit.
- `docs/`: full discovery catalog, capability boundaries, acquisition notes, adaptation and publication plan.
- `templates/`: portable project identity, session, change and review records.
- `.agents/skills/e78-public-release/`: reusable source-only packaging/check procedure.
- Scoped `AGENTS.md` files: instructions for evidence research, tools, definitions and examples.

Private firmware, captures, identity, candidates and Ghidra databases stay outside Git. Nothing in this repository grants authorization to operate a vehicle or programmer. Keep protections and diagnostic integrity; do not use a reference address or a successful checksum as a calibration safety limit.

Code and documentation are distributed under GPL-3.0-or-later; third-party notices and exact-source provenance are retained. See [LICENSE](LICENSE) and [vendor provenance](vendor/README.md). No OEM firmware or donor image is distributed.
