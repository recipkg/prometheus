# Prometheus 指标监控配方

```toml
format = "recipkg/1"

[package]
name = "prometheus"
version = "0.1.0"
kind = "software"
description = "采集并保存带标签的时间序列指标，提供 PromQL 查询、规则评估与 HTTP API。"
entry = "BUILD_PROMPT.md"

[dependencies.quality]
git = "https://github.com/recipkg/recipkg.git"
rev = "7f05425ae9843b7e8ce15cb80917977eedb36bdd"
subdir = "recipes/software-quality"

[dependencies.design]
git = "https://github.com/recipkg/design-directions.git"
rev = "6fdba350d1effa2d50dc0185095bb91ca7a699ee"
```

固定目标是 `prometheus/prometheus` v3.15.1，源码提交 `bae3eced0a5369e050e83ea73bc381d7c4b1a719`，许可证 Apache-2.0。来源、观察边界和依赖锁定见 `SOURCES.md`、`COVERAGE.md`。

重建范围包括 Prometheus Server、内置表达式浏览器、PromQL、抓取与服务发现、TSDB、本地规则评估、HTTP API，以及 `promtool` 的配置和规则检查能力。Alertmanager、Pushgateway、exporter、Grafana 和远程存储属于可连接的独立组件；不得把它们的服务实现算入本配方。

`quality` 提供数据完整性、配置验证、错误恢复、权限和可测量性能的工程合同。`design` 只用于实际存在的表达式浏览器和运维界面；它不要求把监控产品改造成通用卡片式仪表盘。递归依赖完整材料随归档打包。

本配方处于提取阶段。固定版本的逐项配置语义、PromQL 完整兼容、平台矩阵、真实负载性能和独立重建均未全部验证；见 `COVERAGE.md`。
