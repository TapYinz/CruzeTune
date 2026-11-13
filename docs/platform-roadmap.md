# Linux-first Cruze tuning application roadmap

The current release is a Python research/calibration toolkit. The intended app
adds a touch-friendly interface for a Linux phone first, followed by Android.
The selected product name is **CruzeTune**: E78 tuning, logging and diagnostics.

| Stage | Deliverable | Completion criterion |
| --- | --- | --- |
| Existing core | Exact-image checksums, definitions, candidate tools and offline protocol tests | Included tools and results documented in the release report |
| 1: project and replay UI | Select saved logs, plot channels, scrub time and replay gauges | Deterministic time alignment; units, missing values and validity visible |
| 2: manual calibration editor | Tables, 2D/3D plots, comparison, bounded proposals and undo | Every edit tied to a supported profile; reproducible diff/checksum review |
| 3: portable acquisition | Explicit RH02/backend selection and read-only logging service | Transport/session tests and separately recorded target evidence |
| 4: guided logging | Parked setup plus idle, normal and qualified controlled-load recipes | No required phone interaction while driving; clear capture/abort states |
| 5: explainable helper | Goal-specific guidance and evidence-based candidate proposals | Traceable rationale, adequate measurements and unchanged protection strategy |
| 6: programming | Reviewed compatible writer, readback and recovery workflow | Physical target-specific validation separate from file/simulator tests |
| 7: Android | USB/host bridge, packaging and touch integration | Demonstrated backend/device compatibility; Python/terminal/root requirements stated where applicable |

Stages1–7 remain planned. Existing HTML research plots and isolated scripts are
not an integrated app. The first useful interface should work entirely with
saved data and supported offline files before adding vehicle access.

Logging recipes must distinguish measured mixture from commanded ratio, knock
correction from spark advance, and ECU estimates from measured output. Unknown
or invalid channels stay unavailable. A reported zero speed alone is not proof
that a vehicle is stationary. Controlled-load work requires appropriate operating
conditions and an operator arrangement that does not demand driver screen use.

The helper should explain table roles, input units, selection conditions and
expected measurable effects. Experimental shape bounds must not be described as
validated engine/transmission limits. No app can guarantee damage-free tuning.
Inadequate data should produce a clear explanation of what is missing rather
than invented boost, fuel or spark targets.

Public releases use synthetic/example data and user-supplied private images.
Keep raw firmware, identifiers, shadow material, vehicle captures and emulator
databases outside the source repository. External tools and their licenses stay
attributed independently; a research inventory is not a bundle of all upstream
applications or proof that every tool ran.
