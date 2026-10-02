# StormByte Suite

Focused C++26 libraries and the tools that keep them buildable on Linux, Windows, and macOS.

The public surface is intentionally small. Each module does one job. Third-party types stay private. Text and binary data that cross a DLL / `.so` boundary use suite types, not `std::string` by value.

Docs: [dev.stormbyte.org](https://dev.stormbyte.org/StormByte/)  
Author: [David C. Manuelda](https://github.com/StormBytePP) · [Sponsor](https://github.com/sponsors/StormBytePP)

## Libraries

| Repository | Role |
|---|---|
| [StormByte](https://github.com/StormByte-Suite/StormByte) | Foundation every other module links: platform, `Expected`, exceptions, `Error`/`Fault`, little-endian serialization, `CString` / `WCString`, `BinaryData`, `Size` / `ByteSize`, UUID v4, bitmasks, clonable types, `ThreadLock`, concepts |
| [StormByte-System](https://github.com/StormByte-Suite/StormByte-System) | Processes with pipes, chaining, device classification, host info, thread name, environment expansion. POSIX and Windows, one API |
| [StormByte-Buffer](https://github.com/StormByte-Suite/StormByte-Buffer) | FIFO, SharedFIFO, Ring, Producer/Consumer, Hopper, Sink, Bridge, Pumper, pipelines and buffered I/O |
| [StormByte-Config](https://github.com/StormByte-Suite/StormByte-Config) | Human-readable text and versioned binary configuration documents: values, comments, groups, lists, `Save` / `Load` |
| [StormByte-Logger](https://github.com/StormByte-Suite/StormByte-Logger) | Streaming logger: levels, headers, hierarchical components, `Scope`, `ThreadedLog`, redaction, hex dumps |
| [StormByte-Crypto](https://github.com/StormByte-Suite/StormByte-Crypto) | Hash, compress, encrypt, sign and key agreement. Crypto++ stays private; installed headers never mention `CryptoPP::` |
| [StormByte-Database](https://github.com/StormByte-Suite/StormByte-Database) | One API over SQLite, PostgreSQL and MariaDB. Inherit the backend; build the schema on top |
| [StormByte-Network](https://github.com/StormByte-Suite/StormByte-Network) | Inherit `Client` or `Server`. Framed packets, Buffer pipelines, IPv4/IPv6. POSIX and Winsock stay private |
| [StormByte-Multimedia](https://github.com/StormByte-Suite/StormByte-Multimedia) | Decode, encode and containers without raw FFmpeg types; codecs enabled only if present |

Headers live under `StormByte/…`. Namespace root is `StormByte`. Shared vs static follows CMake `BUILD_SHARED_LIBS`.

Needs a C++26 compiler and CMake 3.28 or newer.

```bash
git clone https://github.com/StormByte-Suite/StormByte.git
cd StormByte
cmake -S . -B build
cmake --build build
```

Each module’s README lists its exact dependencies and pins. Do not treat the suite as a single mega-repo: Base does not implement Buffer, Crypto, Network, or the rest.

## Tools

| Repository | Role |
|---|---|
| [StormByte-BuildMaster](https://github.com/StormByte-Suite/StormByte-BuildMaster) | Short CMake DSL for vendoring CMake and Meson projects. Declare components and edges in any order; BuildMaster materializes stages, `IMPORTED` targets and the usual third-party graph without the spaghetti |

## Design

- Split on purpose. Link only what you use.
- Inherit, do not wrap vendor types in public headers.
- Failures are typed (`Expected`, `Fault`) with stable domains (`StormByte.…`).
- Cross-platform: Linux, Windows, macOS.
- Original sources: LGPL v3 or later, or a commercial license from the copyright holder (see each repo’s `LICENSE`). StormByte-BuildMaster may use a different license — check that repo.

## Support

Issues and PRs on the module they belong to.  
Sponsorship: [github.com/sponsors/StormBytePP](https://github.com/sponsors/StormBytePP)
