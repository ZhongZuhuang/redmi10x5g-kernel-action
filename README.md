# Redmi 10X 5G Kernel Action

基于 `suhuli/Action-Build` 思路整理的红米 10X 5G 一键内核编译项目。

## 目标机型

- 机型: Redmi 10X 5G
- 代号/配置: `atom`
- SoC: MediaTek Dimensity 820 / MT6873
- 内核源码: `MiCode/Xiaomi_Kernel_OpenSource:bomb-q-oss`
- 默认 defconfig: `atom_user_defconfig`
- 内核版本: 4.14.x

> `bomb-q-oss` 分支同时包含 `atom` 与 `bomb` 配置。本项目默认构建红米 10X 5G 的 `atom_user_defconfig`。

## 已集成功能

- ReSukiSU: 默认启用。
- KPM: 默认启用，构建后用 `patches/patch_linux` 注入。
- SUSFS: 默认尝试集成 `susfs4ksu` 的 kernel-4.14 补丁。
- seccomp: 默认启用 `CONFIG_SECCOMP` 和 `CONFIG_SECCOMP_FILTER`。
- 零宽字符修复: 默认应用本仓库的 `patches/zero_width_exec_fix_4.14.patch`。
- AnyKernel3 打包: 自动上传可刷入 zip。
- 手动触发 GitHub Actions 编译。

## 使用方法

1. 打开仓库的 `Actions`。
2. 选择 `Build Redmi 10X 5G Kernel`。
3. 点击 `Run workflow`。
4. 推荐保持默认参数：
   - `DEVICE`: `atom`
   - `ENABLE_RESUKISU`: `true`
   - `ENABLE_KPM`: `true`
   - `ENABLE_SUSFS`: `true`
   - `ENABLE_SECCOMP`: `true`
   - `FIX_ZERO_WIDTH`: `true`
5. 编译完成后，在 workflow run 的 `Artifacts` 下载：
   - `AnyKernel3_ReSukiSU_Redmi10X5G_...zip`
   - `build-logs-...`

## 注意

- 这是非 GKI 4.14 旧内核，ReSukiSU/SUSFS/KPM 组合对源码兼容性要求高；如果上游 patch 发生变化，第一次编译可能需要根据日志微调补丁。
- 默认使用 `atom_user_defconfig`。如果你要给 Redmi 10X Pro 5G / `bomb` 编译，在 workflow 输入里把 `DEVICE` 改为 `bomb`。
- 刷入前请自行备份 `boot.img`。本仓库只负责编译和打包，不自动刷机。

## 主要来源

- 原工作流参考: https://github.com/suhuli/Action-Build
- 小米内核源码: https://github.com/MiCode/Xiaomi_Kernel_OpenSource/tree/bomb-q-oss
- ReSukiSU: https://github.com/ReSukiSU/ReSukiSU
- SUSFS: https://gitlab.com/simonpunk/susfs4ksu
- AnyKernel3: https://github.com/osm0sis/AnyKernel3
