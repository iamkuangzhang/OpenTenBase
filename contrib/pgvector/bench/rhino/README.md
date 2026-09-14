# Rhino-Bird IVFFlat 自适应构建复现材料

本目录用于展示本项目在 OpenTenBase / pgvector 中对 IVFFlat 索引构建与诊断能力的增强。

原有 IVFFlat 构建路径主要使用 Elkan K-Means。当其估算内存超过 `maintenance_work_mem` 时，索引构建可能失败。本项目保留原有 Elkan 路径，并在 Elkan 内存不足、Yinyang 可以满足内存约束时，自动切换到更低内存的 Yinyang K-Means 构建路径。同时增加了 IVFFlat 参数与构建内存诊断能力。

## 快速复现

在 OpenTenBase 仓库根目录执行：

```bash
bash contrib/pgvector/bench/rhino/reproduce_smoke.sh
