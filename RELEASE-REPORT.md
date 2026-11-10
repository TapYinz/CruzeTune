# Release candidate verification

Prepared 2026-11-10 UTC. Published privately to https://github.com/TapYinz/E78-Tuning on 2026-11-10 UTC. GitHub confirmed PRIVATE visibility; the initial remote commit and all53 uploaded file blobs matched the reviewed local release. This report records package verification, not vehicle validation.

## Environment and actual checks

Host: native Kali Linux ARM64, kernel6.12.92-sdm845-nh, Python3.14.8. No ECU commands, adapter access or release compilation occurred.

- Synthetic checksum demo passed: known CRC vector, invented wordsum buffer, mutation detection and exact-baseline rejection.
- Public suite:31 tests discovered, eight passed and23 private-input cases explicitly skipped. Command: `PYTHONPATH=tools PYTHONDONTWRITEBYTECODE=1 python3 -m unittest discover -s tests -v`.
- Private core port verification: all26 then-existing core/public tests passed with the untouched original supplied from external private storage, in87.064seconds. Includes six correction tests, ten simulated programming tests, four pedal tests and six public checks. No baseline was copied into the public tree.
- Optional exporter: five additional tests passed with external private baseline in0.073seconds. All1473 table cells and axes roundtripped exactly; changed/missing/synthetic baseline rejection, CSV cell addresses, hashes and output preservation passed. Three of these cases need the private image; two run publicly.
- The public port preserves exact baseline/signature guards. Five minimal core modules remain byte-identical to the research copies; candidate module changes only input/signature paths. Optional exporter preserves build(data); its wrapper records unavailable private trace provenance explicitly.

The full suite was checked in the core and exporter batches described above, not claimed as a single31-test private invocation. Public CI targets Python3.11/3.14; only3.14.8 has been executed locally so far. CI configuration is supplied but no hosted CI run is claimed.

Release validation checks an explicit allowlist, all shipped text sizes/hashes, JSON syntax, local Markdown links, symlinks/binary exclusion and scoped sensitive-string patterns. Independent read-only review passed the51-file frozen stage: validator, synthetic demo, eight public tests/23 explicit skips, source hashes, exact-image guards and GPL/provenance were checked. No material content blocker or known VIN/serial/token was found in the public payload. The final added release skill was separately validated with the skill-creator validator. Release-validator negative cases rejected an unexpected file, a symlink and an injected credential token. Final manifest validation includes the release skill. Regex checks are limited and do not independently establish all privacy or provenance claims.

## Boundaries

No original/candidate/donor firmware, raw capture, security exchange, private identity, hardware serial or Ghidra project is included. Original images remain private and untouched. Public source hashes identify privately retained research summaries; they do not provide public access to raw evidence.

No physical flash write, interrupted-write recovery, loaded tune, measured output gain, crackle calibration or whole-firmware simulation is validated. All research candidates remain flash_ready=false. The initial GitHub upload was verified against the complete manifest allowlist; no parent collection files were uploaded.
