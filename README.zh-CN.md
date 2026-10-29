# cua-driver

[English](README.md) | 中文

Munk 使用的 [trycua/cua](https://github.com/trycua/cua) `cua-driver` 补丁构建。

本仓库不存放上游源码。`upstream.json` 固定上游 tag 和 commit，`patches/capture-id.patch` 在该树上应用。GitHub Actions 按上游同一套目标编译，并把二进制发到 Release。

当前 pin：

| 项 | 值 |
| --- | --- |
| 上游 tag | `cua-driver-rs-v0.34.1` |
| 上游 commit | `0c69d9a2c8abbb5051a2df4a23f0fa166d5385dc` |
| 本仓库 Release | `v0.34.1-munk.1` |

补丁把 `capture_id` / `snapshot_id` 写进观察文本，并把视觉区域的 bounds 与中心点写进 `parse_visual_regions` 的文本结果。只看 MCP 文本的调用方可以复用同一帧并点击自绘控件。

## Release 产物

每个平台架构一个包，包内是可执行文件本身：

| 资产 | 内容 |
| --- | --- |
| `cua-driver-0.34.1-munk.1-darwin-arm64.tar.gz` | `cua-driver` |
| `cua-driver-0.34.1-munk.1-darwin-x64.tar.gz` | `cua-driver` |
| `cua-driver-0.34.1-munk.1-linux-x86_64.tar.gz` | `cua-driver` |
| `cua-driver-0.34.1-munk.1-linux-aarch64.tar.gz` | `cua-driver` |
| `cua-driver-0.34.1-munk.1-windows-x86_64.zip` | `cua-driver.exe`、`cua-driver-uia.exe` |
| `cua-driver-0.34.1-munk.1-windows-aarch64.zip` | `cua-driver.exe`、`cua-driver-uia.exe` |

`SHA256SUMS` 覆盖上述压缩包。Linux 在 Debian 11 容器里链接（glibc 2.31），并打开上游的 `portal-input` feature。macOS 与 Windows 二进制未做 Apple 公证或 Authenticode 签名。

上游驱动是 MIT。本仓库的补丁、pin 和构建脚本也是 MIT。
