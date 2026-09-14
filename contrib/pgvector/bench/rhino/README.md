# Rhino-Bird IVFFlat 自适应构建复现材料

本目录用于展示本项目在 OpenTenBase / pgvector 中对 IVFFlat 索引构建与诊断能力的增强。

原有 IVFFlat 构建路径主要使用 Elkan K-Means。当其估算内存超过 `maintenance_work_mem` 时，索引构建可能失败。本项目保留原有 Elkan 路径，并在 Elkan 内存不足、Yinyang 可以满足内存约束时，自动切换到更低内存的 Yinyang K-Means 构建路径。同时增加了 IVFFlat 参数与构建内存诊断能力。

## 交付文档

本目录同时提供两份完整的项目说明材料：

- [IVFFlat 内存自适应构建与诊断增强：技术报告与复现指南](docs/IVFFlat_Adaptive_Build_Technical_Report.pdf)  
  介绍项目背景、Elkan / Yinyang 自适应构建设计、配置诊断能力、核心实验结果，以及最小复现方式。建议首次了解本项目时先阅读此文档。

- [IVFFlat 实验环境与详细实验数据](docs/IVFFlat_Experiment_Environment_and_Results.pdf)  
  记录正式实验环境、数据集信息、版本与 Commit、K-Means 内存估算、构建时间、Recall@10、低内存成功/失败结果以及自动化测试证据，用于进一步核验实验结果。

## 快速复现

在 OpenTenBase 仓库根目录执行：

```bash
bash contrib/pgvector/bench/rhino/reproduce_smoke.sh
