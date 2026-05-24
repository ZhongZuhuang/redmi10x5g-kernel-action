# Redmi 10X 5G Kernel Action

Device-specific GitHub Actions kernel builder for Redmi 10X 5G (`atom`) based on the `suhuli/Action-Build` workflow style.

Features:

- ReSukiSU integration.
- KPM image patching.
- ReSukiSU SUSFS-side support; external SUSFS kernel-4.14 patches are disabled by default for this legacy MTK tree.
- seccomp config enablement.
- zero-width UTF-8 exec argument hardening.
- AnyKernel3 artifact packaging.

Run `Build Redmi 10X 5G Kernel` from the Actions tab and download the generated AnyKernel3 artifact.
