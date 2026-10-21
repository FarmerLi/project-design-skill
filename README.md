# 项目需求与设计 Skill · 0.4

## 主文档位置

本技能的主文档目录为 `/Users/farmerli/projects/local/project-design-skill`，后续修改和校验均以此目录为准；技能入口为 [SKILL.md](SKILL.md)。原工作区的 `work/project-design-skill` 已迁移，不再维护或重建。

随迁移保留的 `reference-review.md`、`source-manifest.json` 和 `validation-results.json` 为历史维护记录；其中的哈希、行数及验证结果不代表本次同步后的状态，最新优化验证说明见 [VALIDATION.md](VALIDATION.md)。

面向研发管理者，从目标、现有方案或需求变化出发，按需完成价值可行性、方案概要、场景需求和交付分析。

本版增强通用分析主干，保留建模方法和技术方案的适配器机制。业务系统、开发工具、SDK、数据处理或跨系统项目按实际需要选择分析维度，不绑定某套元模型。

## 职责划分

| 内容 | 职责 |
|---|---|
| [SKILL.md](SKILL.md) | 描述技能用途、输入产出，以及什么时候使用什么能力 |
| `references/` | 具体分析方法、方案适配和必要的工作约定 |
| 项目根目录的 `PROJECT_CONTEXT.md` | 需求管理系统、文档、代码及分析产物的位置与来源约定 |
| 被分析项目的文档 | 业务事实、需求、设计、有效决策与交接状态 |

本技能不附带 AGENTS.md 接入模板，也不要求用户修改项目 AGENTS.md。项目已有指令按宿主规则正常生效，不由本技能替换。

## 使用

将整个技能包放到可访问的位置，在会话中指定实际入口：

> 请读取 `/实际位置/project-design/SKILL.md`，帮我分析这个项目。本轮只澄清目标：……

如果宿主已经发现本技能，可以使用 `$project-design`。按技能目录安装时，目录名使用 `project-design`，并保留 references 和 agents 的相对位置。

提供已有项目或资料时，也说明实际位置。分析产物默认保存到被分析项目的 `docs/project-analysis/`，可指定其他目录；不要把业务资料写入技能包。

## 项目上下文文件

用被分析项目根目录的 `PROJECT_CONTEXT.md` 记录必要的稳定信息：

- 需求管理系统名称、项目链接、空间／项目 ID 和需求定位方式；
- 业务文档、设计文档与代码的位置；
- 分析产物目录，以及概览、决策和交接文件的实际位置；
- 需求状态、详细规则和当前实现分别以哪些来源为依据。

首次持续分析时，助手根据已知资料从 [模板](assets/project-context.template.md) 建立文件；也可以手动复制并填写。未知项保留待核实，无需一次填完全部信息；已有等价配置可以沿用。

该文件记录“资源在哪里”，不重复保存需求正文、工作进展或业务决策。使用规则见 [项目上下文配置](references/shared/project-context.md)。

## 能力

```text
SKILL.md
references/
  entry/context.md              既有项目现状、材料缺口和继续分析
  stages/                       目标、可行性、概要、细化、协作影响、交付
  changes/impact.md             任意阶段的变更分析
  selection/                    建模方法选择、技术选型
  adapters/                     应用选定的建模方法与技术方案
  shared/project-context.md     项目资源配置的读取和维护
  shared/working-contract.md    结论、决策版本与交接约定
  shared/analysis-spec.md       信息、操作、规则、协作、口径与契约的最小规格
  shared/readiness.md           按交接用途检查充分性及证据
  shared/design-input.md        设计输入索引、双向追溯与变更传播
  examples/analysis-slices.md   跨系统、统计与无状态 SDK 的分析示例
assets/project-context.template.md 项目上下文模板
agents/openai.yaml               技能展示与调用信息
```

这些是可组合的能力，不是每次必须走完的顺序：

- 新项目只有目标，可以从目标与价值讨论开始。
- 已有概要，可以直接细化近期要做的场景。
- 既有项目新增能力，先了解有关现状，再分析增量。
- 修改已约定的需求，先定位变化及影响，再局部修订。
- 选型和应用方案分开；建模方法和技术方案分别选择。

适配器包括轻量模块设计、本体设计和技术方案适配。本体适配器使用用户实际选定的外部规范，本包不再包含特定元模型映射；正式输出特定格式时需要读取选定规范。详见 [适配器目录](references/adapters/catalog.md)。

## 通用分析如何做到可检验

- [通用分析规格](references/shared/analysis-spec.md) 明确相关维度要定义到什么程度，并允许说明不适用，避免只输出功能名称。
- [协作与影响链](references/stages/collaboration.md) 独立检查跨边界影响、失败后果、重复和反向变化，技术实现由适配器决定。
- [就绪检查](references/shared/readiness.md) 以证据和实际交接范围判断充分性，区分业务确认、设计就绪和运行验证。
- [设计输入与追溯](references/shared/design-input.md) 固定输入版本和权威定义，双向连接需求、设计、验收及变更影响。

例如“导入后自动可检索”需要说明保存成功与索引成功的区别、失败如何恢复、删除与晚到结果如何处理；一个无状态函数则可以只交付调用契约与验收案例。详见 [分析切片](references/examples/analysis-slices.md)。

## 继续分析

持续分析通过项目文档保存有效结论，而不依赖聊天历史完整保留。恢复时可以说：

> 请使用项目需求与设计技能。项目位于……，先读 PROJECT_CONTEXT.md，再依据当前概览和交接继续下一项工作。

[现状与恢复方法](references/entry/context.md)说明读取顺序，[工作约定](references/shared/working-contract.md)说明状态和交接内容。普通一次性咨询不要求建立全套文档。

## 旧版接入

旧的多技能入口改用根目录 SKILL.md。此前如果手动合并过本包的 AGENTS 片段，可移除该片段；保留项目自身规则。更新技能包不会自动修改其他项目的配置。

已有项目需求、决策和交接文档仍可使用，不必重新生成。

## 验证与来源

检查范围见 [VALIDATION.md](VALIDATION.md)。格式与引用检查不代表真实访谈效果或第三方模型兼容性已验证。

本包独立编写。此次深入参考 [ontology-driven-dev 的固定版本](https://github.com/sharptoolbox/ontology-driven-dev/tree/49a9eff8b17349adaa860b355e82e6154c35dc82) 中的需求探索规范、建模约束、合同需求与模型示例，并核对开发指导中的追溯设计。吸收明确职责、独立影响分析、确定性输入和双向一致性检查；不引入其专属模型、技术底座、固定 UI、每阶段硬暂停或报表数量要求。未复制上游源码、完整规范或模板。
