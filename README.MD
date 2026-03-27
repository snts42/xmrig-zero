# XMRig-Zero (Multi-Platform Automated Builds)

Automated, multi-platform builds of [XMRig](https://github.com/xmrig/xmrig) with the **minimum developer donation set to 0%**.

- **Upstream source:** [xmrig/xmrig](https://github.com/xmrig/xmrig) — built from the latest official tagged release
- **Platforms:** Windows x64, Linux (static/Alpine, Ubuntu 22.04 Jammy, Ubuntu 24.04 Noble), macOS (x64 and arm64)
- **Automatic builds:** Checks for a new upstream release daily and publishes a matching release here
- **License:** [GPL-3.0](LICENSE) — Copyright (C) 2016-2025 xmrig.com

---

## Why use this?

In the official XMRig binaries, even if you set `donate-level` to `0` in the config, a hardcoded minimum of 1% in the source (`kMinimumDonateLevel`) overrides it and the miner still donates.

**In this version, two patches are applied before building:**

1. `src/donate.h` — both `kDefaultDonateLevel` and `kMinimumDonateLevel` are set to `0`
2. `src/config.json` — `donate-level` and `donate-over-proxy` are set to `0`

The result is that setting `donate-level: 0` in your config is fully respected.

---

## Download

See [Releases](https://github.com/snts42/xmrig-zero/releases) for pre-built binaries and `SHA256SUMS`.

To verify your download:
```sh
sha256sum -c SHA256SUMS
```
This checks that the file you downloaded matches the hash generated at build time. Note: unlike the official XMRig releases, `SHA256SUMS` here is not GPG-signed — but the hashes themselves are computed in the open on GitHub Actions runners, and the full build log is publicly auditable.

---

## Donate

**If you use this build, please consider donating to the XMRig developers:**

* XMR: `48edfHu7V9Z84YzzMa6fUueoELZ9ZRXq9VetWzYGzKt52XU5xvqgzYnDK9URnRoJMk1j8nLwEVsaSWJ4fhdUyZijBGUicoD`

---

## How it works

The [GitHub Actions workflow](.github/workflows/build.yml):
1. Fetches the latest upstream XMRig release tag from [xmrig/xmrig](https://github.com/xmrig/xmrig/releases)
2. Applies the 0% donation patch to `src/donate.h` and `src/config.json`
3. Builds natively on each platform (Windows MSVC, Alpine static, Ubuntu 22.04, Ubuntu 24.04, macOS x64, macOS arm64)
4. Packages each binary with `config.json` and platform extras (Windows includes `WinRing0x64.sys` and example scripts)
5. Generates a `SHA256SUMS` file and publishes everything to a GitHub Release

Each release description includes the exact upstream tag and patch details.

---

## Source & License

This repository builds [xmrig/xmrig](https://github.com/xmrig/xmrig) unmodified except for the donation patch described above.  
XMRig is licensed under the [GNU General Public License v3.0](https://github.com/xmrig/xmrig/blob/master/LICENSE).  
This repository's [LICENSE](LICENSE) is the same GPL-3.0 as the upstream project.

**Not affiliated with the official XMRig team.**

Happy mining! ⛏️