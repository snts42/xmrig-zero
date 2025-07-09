# XMRig-Zero (Multi-Platform Automated Builds)

This repository provides automated, multi-platform builds of [XMRig](https://xmrig.com/) with the **minimum developer donation (fee) set to 0%** by default.

- **Platforms:** Windows x64, Linux (static, Ubuntu 22.04 Jammy, Ubuntu 24.04 Noble), macOS (x64 and arm64)
- **Automatic builds:** Always builds and uploads the latest official XMRig release, patched for 0% fee.
- **No more hardcoded dev fee:** You can truly set the donation to zero if you want.

## Why use this?

In the official XMRig binaries, even if you try to set the developer donation to 0%, there is always a hardcoded minimum fee of 1% that cannot be bypassed through configuration.

**In this version:**
- The donation patch is applied automatically.
- You can set the donation level to 0%, and the miner will respect it.
- When you run the miner, the effective donate level will actually be zero.

---

## Download

See [Releases](https://github.com/snts42/xmrig-zero/releases) for pre-built binaries.

---

## Donate

**If you are considering using this version, please donate to the XMRig developers:**

* XMR: `48edfHu7V9Z84YzzMa6fUueoELZ9ZRXq9VetWzYGzKt52XU5xvqgzYnDK9URnRoJMk1j8nLwEVsaSWJ4fhdUyZijBGUicoD`

---

## How it works

This repository’s [GitHub Actions workflow](.github/workflows/build.yml):
- Checks for the latest upstream XMRig release
- Patches the hardcoded donation fee to allow zero
- Builds for multiple platforms, packages, and uploads binaries to releases

---

**Not affiliated with the official XMRig team.  
This repository just automates builds with a zero-fee patch for the community.**

Happy mining! ⛏️