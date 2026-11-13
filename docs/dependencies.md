# Dependencies and source lineage

The file-only extraction, checksum, editing and planning commands use Python3.11+
and its standard library. LZ4 is optional for compressed read-protocol tests;
Black is a development formatter. See `requirements-dev.txt` for pinned versions.
No adapter, Ghidra, .NET or upstream application install is required for the
synthetic demo and basic offline workflow.

| Project | Contribution to the research/toolkit |
| --- | --- |
| [KernelMPC5566](https://github.com/FL0WL0W/KernelMPC5566) | Separately obtained pinned RAM reader; packet dialect and protocol fixtures |
| [ESP32-ECU-Flasher](https://github.com/FL0WL0W/ESP32-ECU-Flasher) | Stock E78 preparation/uploader sequence adapted into the host read state machine |
| [UniversalPatcher](https://github.com/joukoy/UniversalPatcher) | Calibration layout, checksum algorithms and retained signature data |
| [Ghidra](https://github.com/NationalSecurityAgency/ghidra) | Disassembly and original-instruction research; not a runtime dependency of these tools |
| [opendbc](https://github.com/commaai/opendbc) and [Cruze CAN definitions](https://github.com/doosedev/2011-Chevy-Cruze-CAN-DBC) | Signal-definition leads for separately qualified passive decoding |
| [E78_14T](https://github.com/sbarisic/E78_14T) and [EFIGenieE78](https://github.com/FL0WL0W/EFIGenieE78) | Donor-definition and MCU/peripheral references; not drop-in definitions or a required replacement firmware |

The originating RH02 route uses Elmue CANable SLCAN firmware and userspace
can-isotp; compressed reads use LZ4. Historical SocketCAN work also used
python-can. A package installed in the research environment is not necessarily
required by the current standalone toolkit.

GM-ECU-Simulator and the selected GMT900 reader patches are separate protocol
and host-code test workstreams. They are not required to edit an offline file
and do not establish Cruze BCM acquisition or full E78 engine simulation.

Exact revisions, source hashes and retained notices are recorded under
`vendor/` and in the [source guide](sources.md). Preserve component licenses;
third-party sources are not collectively relicensed or bundled wholesale.
