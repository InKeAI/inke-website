# Repository Guidelines

## Documentation and Decisions

开始 implementation 前，先阅读 `docs/README.md`，再阅读其中与当前任务相关的需求、决策、约束、问题调查和踩坑记录。

任务/需求基线与代码必须先对齐。发现出入时 **ABORT**：停止改代码、停止写 `docs/`，先把差异摊开并达成一致。只有基线与实现一致之后，才在 `docs/` 做文档落地。

重大决策记录为 `docs/adr/` 下的 `ADR(Architecture Decision Record)`。新增或更新 ADR 时，同步更新 `docs/README.md`，添加链接和一句摘要。值得长期保留的需求、问题调查和踩坑可以记录到 `docs/`，并在 `docs/README.md` 建立同样的信息锚点。