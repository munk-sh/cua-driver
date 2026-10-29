# cua-driver

English | [中文](README.zh-CN.md)

Patched builds of [trycua/cua](https://github.com/trycua/cua) `cua-driver` used by Munk.

This repository does not vendor the upstream source. `upstream.json` pins the upstream tag and commit. `patches/capture-id.patch` is applied on that tree. GitHub Actions builds the same platform targets as upstream and publishes the binaries as a Release.

Current pin:

| Item | Value |
| --- | --- |
| Upstream tag | `cua-driver-rs-v0.34.1` |
| Upstream commit | `0c69d9a2c8abbb5051a2df4a23f0fa166d5385dc` |
| This release | `v0.34.1-munk.1` |

The patch writes `capture_id` and `snapshot_id` into observation text, and writes each visual region's bounds and center into the `parse_visual_regions` text result. A caller that only sees MCP text can reuse the same frame and click custom-drawn controls.

## Release assets

One archive per platform and CPU architecture. Each archive contains the executable itself:

| Asset | Contents |
| --- | --- |
| `cua-driver-0.34.1-munk.1-darwin-arm64.tar.gz` | `cua-driver` |
| `cua-driver-0.34.1-munk.1-darwin-x64.tar.gz` | `cua-driver` |
| `cua-driver-0.34.1-munk.1-linux-x86_64.tar.gz` | `cua-driver` |
| `cua-driver-0.34.1-munk.1-linux-aarch64.tar.gz` | `cua-driver` |
| `cua-driver-0.34.1-munk.1-windows-x86_64.zip` | `cua-driver.exe`, `cua-driver-uia.exe` |
| `cua-driver-0.34.1-munk.1-windows-aarch64.zip` | `cua-driver.exe`, `cua-driver-uia.exe` |

`SHA256SUMS` covers those archives. Linux binaries are linked in a Debian 11 container (glibc 2.31) with upstream's `portal-input` feature enabled. macOS and Windows binaries are not Apple-notarized or Authenticode-signed.

The upstream driver is MIT. The patch, pin, and build scripts in this repository are MIT as well.
