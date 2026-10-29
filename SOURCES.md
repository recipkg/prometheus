# Prometheus 配方来源

资料核验日期：2026-10-29。

## 固定上游

- 仓库：[prometheus/prometheus](https://github.com/prometheus/prometheus)
- 版本：[`v3.15.1`](https://github.com/prometheus/prometheus/releases/tag/v3.15.1)，发布日期 2026-10-21。
- 标签对象：`291390e28c0686b824af4596102cd23b49d785d4`
- 标签指向的源码提交：[`bae3eced0a5369e050e83ea73bc381d7c4b1a719`](https://github.com/prometheus/prometheus/tree/bae3eced0a5369e050e83ea73bc381d7c4b1a719)。版本与提交由 Git 标签引用核验。
- 许可证：[`LICENSE`](https://github.com/prometheus/prometheus/blob/bae3eced0a5369e050e83ea73bc381d7c4b1a719/LICENSE)，Apache-2.0。
- GitHub API 元数据快照：66,854 stars，仓库大小 295,170 KB。星数会变化且仅用于记录选择背景。

## 核心资料

- [Prometheus 官方概览](https://prometheus.io/docs/introduction/overview/)：数据模型、拉取采集、PromQL、独立节点及生态组件边界。
- [官方数据模型](https://prometheus.io/docs/concepts/data_model/)：标签维度的时间序列。
- [官方存储文档](https://prometheus.io/docs/prometheus/latest/storage/)：本地 TSDB、WAL、块、保留、快照和远端读写。网页文档会滚动更新；使用时须与固定版核对。
- [官方配置文档](https://prometheus.io/docs/prometheus/latest/configuration/configuration/)：scrape jobs、规则、发现与重载配置。
- [官方 HTTP API](https://prometheus.io/docs/prometheus/latest/querying/api/)：即时/区间查询、状态与管理接口。
- [官方规则与告警](https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/)：规则定义和评估行为。
- [官方 promtool 文档](https://prometheus.io/docs/prometheus/latest/command-line/promtool/)：配置、规则及数据工具入口。

## 已定点查看的源码

- [`cmd/prometheus/main.go`](https://github.com/prometheus/prometheus/blob/bae3eced0a5369e050e83ea73bc381d7c4b1a719/cmd/prometheus/main.go)：服务启动、抓取/发现、存储、规则、通知和 Web handler 组件的组装。
- [`scrape/scrape.go`](https://github.com/prometheus/prometheus/blob/bae3eced0a5369e050e83ea73bc381d7c4b1a719/scrape/scrape.go)：目标抓取与样本写入实现。
- [`rules/manager.go`](https://github.com/prometheus/prometheus/blob/bae3eced0a5369e050e83ea73bc381d7c4b1a719/rules/manager.go)：记录/告警规则组的管理和评估。
- [`tsdb/db.go`](https://github.com/prometheus/prometheus/blob/bae3eced0a5369e050e83ea73bc381d7c4b1a719/tsdb/db.go)：本地数据库配置、WAL 和 TSDB 生命周期。
- [`web/api/v1/api.go`](https://github.com/prometheus/prometheus/blob/bae3eced0a5369e050e83ea73bc381d7c4b1a719/web/api/v1/api.go)：版本化 HTTP API 实现入口；完整响应语义仍待逐项核对。

本次通过固定源码路径、官方文档和版本元数据进行选择性观察，未下载完整源码树。来源观察不等于运行结果，也不能证明配方覆盖完整。

## Recipkg 依赖

- `quality`：Recipkg `recipes/software-quality`，提交 `7f05425ae9843b7e8ce15cb80917977eedb36bdd`。
- `design`：`recipkg/design-directions`，提交 `6fdba350d1effa2d50dc0185095bb91ca7a699ee`，递归包含 `design-foundations`。完整锁定版本以归档 `LOCK.md` 为准。
