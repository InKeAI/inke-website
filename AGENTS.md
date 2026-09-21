# Repository Guidelines

## Documentation and Decisions

开始 **IMPLEMENTATION** 前，先阅读 `docs/README.md`，再阅读其中与当前任务相关的需求、决策、约束、问题调查和踩坑记录。

任务/需求基线与代码必须先对齐。发现出入时 **ABORT**：停止改代码、停止写 `docs/`，先把差异摊开并达成一致。只有基线与实现一致之后，才在 `docs/` 做文档落地。

重大决策记录为 `docs/adr/` 下的 `ADR(Architecture Decision Record)`。新增或更新 ADR 时，同步更新 `docs/README.md`，添加链接和一句摘要。值得长期保留的需求、问题调查和踩坑可以记录到 `docs/`，并在 `docs/README.md` 建立同样的信息锚点。

## Deprecation Marking

任何 属性/功能/类/模块/文档 被明确"已弃用"时，**必须**在其定义处添加所属语言/框架的 Deprecated 标识（如 JSDoc `@deprecated`、`[Obsolete]`、`@Deprecated` 等），并在标识中注明弃用原因、替代方案与迁移指引。

仅在 `docs/` 中追加一段"记录"不视为完成弃用：`docs/` 负责沉淀决策背景，Deprecated 标识负责让弃用在定义处与调用点持续可见，并可被 IDE、lint、静态检查等工具识别。弃用状态变化时，两边同步更新。

## Test Organization

`test/` 必须按被测能力或业务领域再分一层，使用 `test/<capability-group>/` 组织测试。分组名使用小写连字符形式，直接表达测试对象，例如 `channel-lifecycle`、`service-contract`；不能仅以 `misc`、`temp` 或无语义的编号作为分组名。

- `test/` 根目录只放测试总览或确有必要的全局测试配置，不直接堆放测试脚本、平台脚本或组内辅助模块。
- 测试入口、组内辅助模块、专属 fixture 和本地运行依赖放在所属组内。
- 需要体现执行顺序时，在组内使用 `00_` 等前缀；编号不替代能力分组。
- 新增或调整分组时，同步修改构建产物路径、导入/类型检查路径、Git 忽略规则和文档命令，并验证该组的入口能够从项目根目录运行。
