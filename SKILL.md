---
name: project-design
description: 按当前问题开展需求澄清、领域与数据建模、技术方案与验证、交互设计或任务与验收拆分。用于项目想法、既有方案和需求变更的分析与设计；纯代码修复、部署执行及技能维护不适用。
---

# 项目需求与设计

帮助用户形成足以支持当前决定或后续工作的设计结论。输入可以是一句话、对话、文档、代码或变更；从当前问题进入，深度随用途增加。

## 默认工作方式

1. 明确本轮要解决的问题、范围和期望结果，复用已有信息。
2. 读取直接相关材料，选择下面需要的能力。发现具体依赖缺口时再扩读。
3. 先形成可评审的结论或方案，说明关键依据、取舍和未知。只追问会实质改变结论的问题，无依赖部分继续。
4. 用关键场景检查结论，完成本轮目的即可交付；已有连续推进授权时继续可推进部分。

临时咨询直接在对话交付。需要保存时优先更新已有主题；**单次保存也不要求创建项目配置、辅助目录、决策表、变更表、交接或评审报告**。只有当前正文、任务或已有记录无法承载必要信息时，才增加材料，具体见 [文档组织与保存](references/shared/document-structure.md)。

## 选择能力

以下能力可以独立使用；阶段编号仅用于兼容既有项目，不构成必经顺序。

| 当前问题 | 方法 |
|---|---|
| 为谁解决什么问题、做哪些范围 | [需求探索](references/stages/discovery.md)，按需补充 [价值与可行性](references/stages/feasibility.md) 或 [概要与范围](references/stages/outline.md) |
| 概念、关系、状态、数据或模型演进 | [领域与数据模型](references/stages/modeling.md) |
| 实现机制、技术比较、组件协作或关键 demo | [技术架构与验证](references/stages/architecture.md) |
| 用户任务、页面、反馈与恢复 | [交互与 UI 设计](references/stages/interaction.md) |
| 首批工作、故事、验收或执行任务 | [交付切片与任务](references/stages/issue-delivery.md)，按需使用 [行为与验收细化](references/stages/acceptance-detail.md) |
| 已有结论发生变化 | [变更分析](references/changes/impact.md) |
| 入口不明、了解现状或恢复工作 | [现状与恢复](references/entry/context.md) |

完整项目可以先明确需求，再往返完善模型、架构和交互，逐步细化近期交付。局部比较、草案或验证按自己的用途完成，不借用完整实施交接的标准扩大任务。

## 保留必要的设计质量

- 区分明确要求、现状事实、建议与待验证假设。已有有效决定直接复用，缺乏依据的业务政策、权限、阈值和失败后果保持待决。
- 设计说明目标、关键机制、取舍和适用条件。先解释整体关系，再展开影响本轮结论的细节；可逆且不影响当前工作的决定可以后置。
- 正常路径之外，检查会改变结论的重要失败、边界与恢复；跨对象或系统的连锁后果按需使用 [协作与影响链](references/shared/cross-boundary-analysis.md)。
- 当前规则在原主题维护，设计与验收通过必要引用关联。已确定变更更新相关内容，尚未复核的下游如实标记；样例和代码观察不自动成为业务要求。
- 自检本轮内容及必要引用。用户或项目要求独立评审，或复杂交接、重大变更需要额外把关时，按 [阅读检查](references/shared/document-structure.md#交付前的阅读检查) 安排；普通交付不以子 Agent 评审为前提。实际委派再读 [协作规则](references/shared/agent-collaboration.md)。
- 如实报告设计、实际运行与交付的范围和证据。分析不自动授权应用开发、部署或无关外部写入；明确 demo 请求包含其常规可逆工作。

## 在需要时增加支撑

| 需要 | 补充方法 |
|---|---|
| 复杂规则、查询口径、权限等需要精确表达 | [分析规格](references/shared/analysis-spec.md)，只展开相关维度 |
| 跨人或跨阶段交接、较多关联项需要追踪 | [输入与追溯](references/shared/design-traceability.md)、[交接检查](references/shared/readiness.md) |
| 长期恢复入口分散，需要共享配置 | [项目上下文](references/shared/project-context.md)；已有配置直接沿用 |
| 处理决定状态、版本或持续恢复 | [工作约定](references/shared/working-contract.md) |
| 已明确保存文档或写入任务 | [文档维护](references/integrations/document-maintenance.md)、[任务落地](references/integrations/task-tracking.md)，按实际动作选择 |
| 需要校准分析深度 | [分析切片示例](references/examples/analysis-slices.md)，示例不构成项目事实 |
