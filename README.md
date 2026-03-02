# Auxi Releases

这个仓库用于在公有仓库中运行 GitHub Actions，从源码仓库构建 Auxi 桌面端二进制，并将产物发布到本仓库的 GitHub Releases。

> 注意：此仓库不包含 Auxi 源码，只用于构建与发布。

## 维护者使用方式

1. 在本仓库 `Settings -> Secrets and variables -> Actions` 中添加 Secret：
   - `AUXI_SOURCE_TOKEN`：对源码仓库有读取权限的 GitHub Token（如源码仓库为私有，需要能 clone）
2. 手动触发 Actions：`Actions -> Build & Release -> Run workflow`
   - `sourceRef`：要构建的源码 ref（branch/tag/commit），默认 `main`
   - `tag`：发布用的 tag（例如 `v0.1.0`），留空将自动生成

> 说明：workflow 会先完整运行单元测试与 E2E 集成测试；任一失败都会中止后续构建与发布。
