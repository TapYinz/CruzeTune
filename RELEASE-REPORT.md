# CruzeTune release verification

Updated2026-11-12 on native Linux ARM64 with Python3.14.8. This release brings
the standalone toolkit up to the current reviewed portable tools and research
metadata. It does not bundle the originating private workspace or claim a
completed phone app, supported live writer or validated performance tune.

## Current content

- 108 metadata-only research records spanning15,893 logical cells, including
  qualified base-spark and VCP spark work. Stock cell values are not distributed.
- Exact-image extraction,17-checksum audit/correction, pedal-A worksheets and
  matched A/B/C experimental candidate generation, with immutable outputs.
- Injected original-read/programming state machines and raw/LZ4 protocol tests;
  no live adapter backend or launcher.
- Source attribution, evidence summaries, dependency/transport guides and the
  Linux-first application roadmap. The existing licenses remain in place.

## Executed verification

All64 tests passed in108.390seconds with the exact private image and separately
pinned public kernel supplied through external paths. Neither input was copied
into this repository. The A/B/C builder reproduced the unchanged private draft
SHA-256 `c2dd06b5134798bb836d10b5215bbac6f00acb57ee371ac9d279437cefead53f`.
The catalog checks reconstructed all108 records and15,893 logical cells;
wrong images/record hashes, existing output paths and invalid proposals fail.

Public execution discovers64 cases:19 pass and45 explicitly skip without their
private image/kernel inputs. With LZ4 absent, two additional compressed cases
skip. Public CI supplies LZ4 but no private firmware or published kernel asset.
Black25.11.0 checks24 Python files; the synthetic demo and release validator
check the reviewed source-only package. Exact-image and kernel guards remain.

From the repository root:

```sh
python3 -m pip install -r requirements-dev.txt
python3 -m black --check tools tests scripts examples
python3 examples/synthetic/demo.py
PYTHONPATH=tools PYTHONDONTWRITEBYTECODE=1 python3 -m unittest discover -s tests -v
python3 scripts/validate_release.py
```

The workflow targets Python3.11 and3.14. Optional local integration inputs use
`E78_PRIVATE_BASELINE` and `E78_KERNEL_IMAGE`, with their exact digest checks.
Hosted run results remain inspectable under the repository's Actions tab.

## Public-release review

The owner explicitly requested public visibility. Both previous commits were
inspected:54 unique text blobs across53 paths, with no firmware or capture
payloads found. The remote had only main, no tags, releases, PRs, issues or build
artifacts. Both prior CI logs were reviewed. Scoped identifier/credential/path
checks passed; automated patterns are not an exhaustive privacy guarantee.

The current manifest allows71 source/documentation/metadata files plus itself.
It records sizes/hashes, checks JSON and local Markdown links, and rejects
unexpected files, binary data and symlinks. No raw firmware, candidate binary,
VIN, adapter serial, shadow value, security exchange or Ghidra database is a
release input. Original research records remain private and unchanged.

## Evidence limits

The original RH02 read is separate physical evidence. A fake peer, corrected
checksum, metadata export or emulator result does not establish physical flash
writing, interrupted-write recovery, loaded response, power gains or combustion
safety. The A/B/C example remains experimental and all candidates retain
`flash_ready=false`. Cam targets and a complete92-AKI/crackle tune remain open.

The related GM-ECU-Simulator correction is submitted as
[PR4](https://github.com/hjtrbo/GM-ECU-Simulator/pull/4):27 core and six wizard
cases passed in .NET9 CI, including the Windows application build. Those are
separate protocol/UI-model checks, not additional E78 firmware tests or full
ECU simulation.
