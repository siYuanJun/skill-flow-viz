# skill-flow-viz — 核心 Skill 执行流程可视化目录

> **欢迎来到 skill-flow-viz** 👋 本目录为 `skills/` 下的各核心 Skill 工程精心准备了一组**单页可视化 HTML**，把 `SKILL.md` 里「它到底怎么执行」友好地翻译成流程图 + 时间轴 + 触发/边界/产出信息卡 + 治理指标 + 关联 Skill。**希望能帮助您无需通读源码，就能在几秒内轻松掌握每个 Skill 的执行脉络。**
>
> **维护方式**：页面由 `skills/skill-flow-viz-generator/`（v2.0.0，fh-flow 标准）脚本自动生成，也可参照现有页面做 few-shot 模板交由大模型产出。所有页面共享统一的视觉语言（`assets/style.css` + `assets/flow.css`），观感一致、便于阅读。

## 温馨提示：这些 HTML 是「导览解说版」，方便您快速入门 🌱

为了让阅读体验尽可能轻松，这些页面**有意做了简化**——它们像是一份精心绘制的「导览地图」或「解说版」，帮您快速看懂某个 Skill 的主流程、触发/边界、关键产出与关联关系。**它是一张友好的概念示意图，用于快速理解，而非工程的全部细节。**

之所以特别说明，是想让您感受到：真实的每一个核心 Skill 工程，其实都**是一个完整、扎实的「项目体」**，而**远不止一个单一文件**。当它以文件形式落在 `skills/<skill>/` 目录下时，通常由下面这些相互协作的部分共同组成：

| 组成要素 | 说明 | 在 HTML 中的呈现 |
|---|---|---|
| `SKILL.md` | 主提示词：触发条件、执行步骤、约束规则 | 提炼为「流程骨架」 |
| `manifest.json` | 治理元数据：版本、能力声明、依赖 | 摘取部分治理指标 |
| `agents/interface.yaml` | 接口契约：输入/输出 schema、调用边界 | 通常不展开 |
| `evals/trigger-tests.yaml` | 触发测试：何时该用 / 不该用此 Skill | 凝练为触发/边界卡片 |
| `scripts/*.py` | 机械臂脚本：纯标准库、确定性数据抽取 | 幕后运行，页面不展开 |
| `references/*.md` | 引用内容：详细规范、镜像表、约束细则 | 幕后支撑，页面不展开 |
| `reports/*.json` | 自检 / 质量评估产出 | 摘取治理评分快照 |
| `CHANGELOG.md` 等 | 演进记录与运维约定 | 幕后留痕，页面不展开 |

**正因如此，这些 HTML 才刻意「举重若轻」**：呈现给您的是清爽的流程概念，而其背后，每个 Skill 工程都凝聚了多指令编排、脚本工具链、策略门控、约束红线等多重要素的协同——这份「看似简单、实则考究」的功底，正是 Skill 工程真正的价值所在。

> 当您希望深入了解某个工程的完整全貌（指令 + 脚本 + 策略 + 约束）时，欢迎随时回到 `skills/<skill>/` 目录查阅源码。HTML 是贴心的入口导览，源码才是工程的完整本体，二者相辅相成。

## 如何查看

- 先打开 **`index.html`** → 总览入口（按层分组，点击即可跳转到各 Skill 单页）。
- 点击任意 `<skill>.html` → 浏览流程图 + 时间轴 + 信息卡；如需了解更多细节，欢迎回到 `skills/<skill>/SKILL.md` 查看机器级内容。
- 流程图支持**画板式缩放 / 拖拽**（panzoom），可自由探索。

## HTML 与核心 Skill 一一对应

| HTML 文件 | 对应 Skill | 所属层 |
|---|---|---|
| `project-skill-builder.html` | project-skill-builder | 元工程层 |
| `AI-DEV-OPRO.html`（旧命名） | ai-dev-workflow | 工程协议层 |
| `UEP.html` | UEP | 工程协议层 |
| `meta-feature-dev.html` | meta-feature-dev | 元方法论层 |
| `meta-agent-collaboration.html` | meta-agent-collaboration | 元方法论层 |
| `meta-self-iteration.html` | meta-self-iteration | 元方法论层 |
| `planning-with-files-zh.html` | planning-with-files-zh | 工程过程层 |
| `test-microservice-python.html` | test-microservice-python | 工程过程层 |
| `api-test-harness.html` | api-test-harness | 工程过程层 |
| `debug-problem.html` | debug-problem | 排障修复层 |
| `debug-frontend-param.html` | debug-frontend-param | 排障修复层 |
| `debug-frontend-404.html` | debug-frontend-404 | 排障修复层 |
| `debug-backend-500.html` | debug-backend-500 | 排障修复层 |
| `doc-troubleshooting.html` | doc-troubleshooting | 排障修复层 |
| `docker-container-design.html` | docker-container-design | 基础设施层 |
| `rag-context-engine.html` | rag-context-engine | 基础设施层 |
| `project-cv-generator.html` | project-cv-generator | 行业解决方案层 |
| `ai-digital-employee.html` | ai-digital-employee | 行业解决方案层 |

**待补 HTML 的核心 Skill**：当前主表所有核心 Skill 均已生成对应可视化单页，无待补项。

## 目录结构

```
skill-flow-viz/
├── index.html              # 总览入口（按层分组跳转）
├── <skill>.html            # 各核心 Skill 单页可视化（18 个）
└── assets/
    ├── style.css           # 共享页面样式
    └── flow.css            # 流程图样式（含 .fh-node/.fh-arrow/.fh-gate/.fh-new）
```

## 维护约定（诚邀共同守护品质 🤝）

- 每个 HTML 都应**忠于原 `SKILL.md`**（只读抽取、不改动语义）；版本号、治理指标、触发/边界请随源 Skill 更新同步，让导览始终值得信赖。
- 新增或大改页面时，请沿用**同一视觉语言**（共享 `assets/style.css` + `assets/flow.css`），并记得在 `index.html` 登记，方便他人查找。
- 推荐优先使用 `skill-flow-viz-generator` 生成，可与全站保持零偏差；临时场景下，也欢迎直接把任一现有 HTML 当作 few-shot 模板交给大模型照改。

> 想了解更宏观的脉络，欢迎参阅上层映射文档：[`核心Skill工程目录映射.md`](../核心Skill工程目录映射.md) 的「可视化目录」章节。感谢您的阅读与共建 🙏
