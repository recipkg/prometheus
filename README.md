# Prometheus

**指标采集、时序存储、PromQL 查询与规则评估的重建配方。**

[![Recipkg package](https://img.shields.io/badge/Recipkg-software-3767d6)](https://github.com/recipkg/recipkg)
[![Upstream](https://img.shields.io/badge/upstream-v3.15.1-e6522c)](https://github.com/prometheus/prometheus/tree/bae3eced0a5369e050e83ea73bc381d7c4b1a719)
[![Coverage](https://img.shields.io/badge/coverage-extracting-f0ad4e)](COVERAGE.md)
[![License](https://img.shields.io/badge/license-Apache--2.0-blue)](SOURCES.md)

## 工作流

```mermaid
flowchart LR
  T[Exporter / 指标端点] -->|HTTP scrape| D[发现与抓取调度]
  D --> S[本地 TSDB / WAL]
  S --> Q[PromQL 与 HTTP API]
  S --> R[记录和告警规则]
  R -->|告警通知| A[外部 Alertmanager]
  Q --> UI[表达式浏览器]
  Q -.可选客户端.-> G[Grafana]
  S -.可选 remote write.-> X[外部远端存储]
```

## 配方范围

目标是固定版本 Prometheus Server 与 `promtool` 的可观察行为。Alertmanager、Grafana、exporter、Pushgateway 与远端存储都作为独立外部组件处理。

```sh
recipkg check .
recipkg pack . -o prometheus-0.1.0.recipe.tar.gz
recipkg check prometheus-0.1.0.recipe.tar.gz
```

阅读 [配方](RECIPE.md)、[完整重建提示词](BUILD_PROMPT.md)、[验收计划](ACCEPTANCE.md)、[覆盖状态](COVERAGE.md) 和 [来源](SOURCES.md)。打包检查只验证配方材料与递归依赖，不代表 Prometheus 已重建。
