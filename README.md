# CrossSuperObject-FPC

> Cross‑platform **fork** of the classic *SuperObject* JSON toolkit, adapted for modern Delphi versions and FreePascal on Windows and Linux.

## Why this fork?

The original SuperObject (by Henri Gourvest) targets Delphi 7‑XE and Windows‐only RTL.  
This fork updates the code base so that it compiles **out of the box** with:

* **FreePascal ≥ 3.2** (FPC mode Delphi) on Windows & Linux x86‑64  
* **Delphi XE2 … 11** (up to `VER340`)  
* 32‑bit and 64‑bit targets

## What was changed
| Area | Change |
|------|--------|
| **FPC compatibility** | Added `{$IFDEF FPC}{$MODE DELPHI}{$ENDIF}` to every unit; replaced Win-API specific types with RTL equivalents. |
| **Cross-platform API** | Wrapped Windows-only functions (`GetTickCount64`, `SetDynamicTimeZoneInformation`, etc.) in `{$IFDEF MSWINDOWS}`; introduced Unix implementations where feasible. |
| **Unicode / RTL** | Removed hard-wired `AnsiString` in favour of `UnicodeString` / `UTF8String` under FPC; fixed code-page warnings. |
| **Conditional Defines** | Added support for Delphi XE3–11 (`VER290..VER340`). |
| **Bug-fixes** | Fixed several compiler hints, range-check warnings and an overflow in `jsonInt` when using FPC 64-bit. All patches enumerated in [`PATCHES.md`](PATCHES.md). |

*(See `git log` for detailed per-file diffs.)*

## Getting started

### Delphi / Windows

```
git clone https://github.com/pisarev/CrossSuperObject-FPC.git
dcc32 demo.dpr  // or open in IDE and Build
```

### FreePascal / Linux

```
git clone https://github.com/YOUR_USERNAME/CrossSuperObject-FPC.git
fpc -MDelphi -S2 -O2 -B src/superobject.pas
```

No extra defines are required.

## Versioning

Tags follow the original numbering plus suffix **`-fpc`**.

| Upstream | This fork |
|----------|-----------|
| 1.2.2    | **1.2.2-fpc** |
| 1.2.3    | 1.2.3-fpc (planned) |

## License

SuperObject is dual-licensed **MPL 1.1 / LGPL**. This fork keeps the same license.  
See original header and `LICENSE.superobject`.

---

Maintained by Yuriy Pisarev — patches welcome!
