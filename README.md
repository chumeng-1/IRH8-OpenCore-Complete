# IRH8 OpenCore Complete

Lenovo 小新 Pro 14 IRH8 的完整 EFI 与系统修复包，包含已验证的 Intel Iris Xe 显示加速和内建 DSP 麦克风。

## 已验证环境

- Lenovo 小新 Pro 14 IRH8
- Intel Core i5-13500H
- Intel Iris Xe, device ID `0xa7a0`
- Realtek ALC287
- macOS Tahoe 26.7.3 / 25G342
- OpenCore

## 显示

- WhateverXe `0.7.0` IRH8 known-good
- WhateverXe Graphics `0.4.1`
- AppleIntelTGLCompat `0.8.0`
- AMFIPass `1.4.1`
- 1536 MB VRAM
- Metal 2
- 2880 × 1800 internal display
- 1440 × 900 UI @ 120 Hz

## 麦克风

- AppleALC `1.9.8`
- SimpleHDA `1.0.1`
- RPLDmic `1.0.1`
- CoreAudio device: `内建 DSP 麦克风`
- 48000 Hz stereo Float32
- 实际采集 peak 与 mean_abs 均大于 0

## 下载

请使用仓库的 **Releases** 页面。推荐下载完整包：

```text
RPLDmic-IRH8-Complete-v1.0.0.zip
```

单独资产：

```text
RPLDmic-IRH8-EFI-v1.0.0.zip
RPLDmic-IRH8-Display-v1.0.0.zip
RPLDmicBridge-HAL-v1.0.0.zip
RPLDmic-IRH8-Release-v1.0.0-SHA256SUMS.txt
```

## 一次性成功顺序

1. 完整备份当前 EFI。
2. 把完整包中的 `EFI` 写入 U 盘 ESP。
3. 从该 U 盘 OpenCore 启动 macOS。
4. 运行 `Installer/install-graphics.command`。
5. 重启并继续从同一 EFI 启动。
6. 运行 `Installer/install-hal.command`。
7. 在系统设置中选择 `内建 DSP 麦克风`。
8. 运行 `Tools/verify-all.command`。
9. 显示与麦克风全部通过后，再写回内部 EFI。

完整教程位于完整包的 `docs/INSTALL.zh-CN.md`。

## 重要说明

- 发布 EFI 已清除真实 SMBIOS、MLB、UUID 和 ROM。
- 当前占位 SMBIOS 可用于显示与音频验收。
- 长期使用 iCloud、App Store 等服务时，应生成自己的 `MacBookPro16,2` SMBIOS。
- 这是特定硬件和特定 macOS 版本的 EFI，不是通用配置。
- 不要混用 WhateverXe 0.7.0 与 Graphics 0.4.4。
- 不要同时启用 WhateverGreen 与 WhateverXe。
- 不要同时启用 AMFIPass 与 AMFIAnchor。

## 第三方组件

完整包保留 WhateverXe、WhateverXe Graphics、AMFIPass、OpenCore Legacy Patcher、Apple AudioServerPlugIn 示例等上游许可证与声明。
