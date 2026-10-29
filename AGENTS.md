# Prometheus recipe instructions

- Read `RECIPE.md`, `BUILD_PROMPT.md`, `ACCEPTANCE.md`, `COVERAGE.md`, `SOURCES.md`, and every locked dependency before changing the recipe.
- Treat upstream v3.15.1 commit `bae3eced0a5369e050e83ea73bc381d7c4b1a719` as the fixed behavior target. Recheck versioned documentation or source before asserting exact defaults or compatibility.
- Keep Alertmanager, exporters, Pushgateway, Grafana, and remote storage outside this package unless a separate recipe is explicitly added as a dependency.
- Preserve the distinction between a successful scrape, persisted sample, successful query, evaluated rule, and delivered notification.
- Mark source observations, upstream runtime results, independent rebuild results, and unknowns separately. Never report structural recipe validation as software acceptance.
- Keep performance claims tied to a repeatable workload, fixed environment, and recorded measurements. Do not invent latency, capacity, or throughput targets.
- Recipe payloads are UTF-8 Markdown only. Do not add source code, binaries, links-as-payload, or executable hooks.
