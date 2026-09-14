# 数模多角色 AI 团队系统（Shumo AI Team）

> 一个面向全国大学生数学建模竞赛（CUMCM/高教社杯）的**多 Agent 常备制 AI 团队**完整配置包：7 个启用角色、26 项已挂载 Skill、三道验收门、证据链门禁与竞赛合规规则，开箱即用、跨赛题复用。

---

## 一、项目介绍

本仓库存放一套已经过完整搭建与技能挂载验证的**数模 AI 团队系统配置**（`TEAM-PACK.md`）。它把"一个聊天窗口"扩展成一支分工明确、可追溯、可复用的建模战队：

- **核心原理**：任务拆分、并行处理、上下文隔离——每个角色一个独立会话，只装自己那摊事，避免长会话压缩导致的规则稀释与幻觉；执行者与验收者严格分离。
- **常备制**：一次搭建，反复参赛。每道新赛题开一个全新 run（目录 + 全套独立会话），结束后封存留档，互不干扰。
- **证据链文化**：论文里每一个数字都能追溯到结果文件、运行记录与核验登记；不合格的结论在验收门被拦截，而不是带病提交。

## 二、这套系统是什么

一句话：**给 AI 装上一套数模竞赛的"组织架构 + 工作流程 + 专业技能 + 合规门禁"**。

| 组成 | 说明 |
|---|---|
| 角色架构 | 1 个总控（R0）+ 6 类执行/验收角色（R1/R3/R4/R5/R7/R8），独立会话并行协作 |
| 工作流 | 接题 → 审题调研 → 【拍板】 → 建模/数据 → 代码求解 → 论文成文 → 三道验收门 → 终审冻结 |
| 技能层 | 26 项按角色永久绑定的专业 Skill（文献检索/EDA/建模选型/求解器/图表/写作范式/评审/合规/本地版本快照/踩坑日志复用） |
| 质量门禁 | 数学核验、评委视角审查、跨材料一致性、代码实跑复现、竞赛合规清单 |
| 合规模块 | AI 工具使用声明 + 《AI工具使用详情》材料组织 + 匿名检查 + 提交包门禁 |

## 三、角色功能一览

| 角色 | 代号 | 职责要点 | 状态 |
|---|---|---|---|
| 总控管理者 | R0 | 拆解目标、建 run 档案、派工、中央路由、组织验收、状态板、复位封存；唯一可与所有子会话通信的角色 | 常驻 |
| 审题调研分析师 | R1 | 逐字逐问拆题、候选方法清单（每问≥2条）、文献与方法调研、可溯源引用 | ⭐核心 |
| 数据工程师 | R3 | 数据探查/清洗/特征构造、可复现预处理脚本、《数据说明书》；禁止改原始数据 | 🔶按需 |
| 建模师 | R4 | 每问建立数学模型：假设、符号表、方程推导、求解思路（伪代码）、适用性与局限 | ⭐核心 |
| 程序员·图表工程师 | R5 | 实现求解、实跑出结果、灵敏度/稳健性实验、一键复现；按竞赛规范绘制全部图件 | ⭐核心 |
| 论文撰写员 | R7 | 按标准结构撰写全文：摘要三段式、正文、图表引用、参考文献、附录、AI 声明 | ⭐核心 |
| 独立评审员 | R8 | 三道验收门（模型门/代码门/论文门）独立把关，三档结论，2 轮修复不过自动升级 | ⭐核心 |

### 角色编号说明

本项目角色编号存在跳号，属于架构迭代后的设计，并非文档遗漏。

- 原 R2（文献调研角色）职责合并至 R1「审题调研分析师」；
- 原 R6（图表角色）职责合并至 R5「程序员·图表工程师」。

保留原始编号、不重新连续编排，是为了兼容历史运行日志、Skill 绑定关系与会话记录，保证跨任务追踪的一致性。

**当前启用角色**：R0、R1、R3、R4、R5、R7、R8。

**必须人类拍板的节点**：选题、技术路线、关键假设、最终提交版本（AI 不代拍）。

## 四、每个 Skill 的作用（26 项挂载）

> 全部技能的完整绑定关系、使用约定与冲突裁决规则见 `TEAM-PACK.md` §5 登记表。

### 编排章程（R0 + 全队）
| Skill | 作用 |
|---|---|
| agent-team | 团队总章程：三类角色、身份证、落盘、验收闭环、反模式清单 |

### 审题与文献（R1）
| Skill | 作用 |
|---|---|
| math-problem-reader | 题面解读与交付物锁定：信号/约束拆分、模糊词转数学量、分问依赖图；未锁定交付物前禁止建模 |
| nature-academic-search | 多源文献检索、来源分级、引文审计与管理 |
| nature-ref-verifier | 参考文献多源交叉验证，防编造引用（支持中文文献降级核验） |
| paper-lookup | 11 个学术库免密钥检索，强制记录可溯源出处 |

### 数据（R3）
| Skill | 作用 |
|---|---|
| exploratory-data-analysis | 有界本地 EDA：缺失/泄漏审计、分布与离群敏感性、报告脚手架；禁自动插补/删异常/改原始数据 |

### 建模（R4）
| Skill | 作用 |
|---|---|
| math-model | 分问建模选型纪律（评价/机理/预测/优化/仿真族 route triage）、验证分级与降级规则、建模交接文档规范 |
| local-git-snapshot | 本地 Git 版本快照：每 run 独立纯本地 Git（无远程），代码产出即 add+commit 快照，支持 log/checkout/diff 回滚与对比；**禁止 push、禁止任何远程提交** |
| pitfall-log-reuse | 踩坑日志复用（PIT_shturl）：run 内踩坑自动追加五要素记录（关联commit/现象/根因/方案/经验），**写码与建模前必先查日志**，同类问题检索复用历史排查思路，规避重复踩坑 |

### 求解与图表（R5）
| Skill | 作用 |
|---|---|
| statistical-analysis | 统计检验选择、假设诊断、效应量与功效分析 |
| statsmodels | 统计建模族求解规范（OLS/GLM/时间序列/诊断） |
| scikit-learn | 经典 ML 求解规范（Pipeline 防泄漏、随机种子复现） |
| pymoo | 单/多目标优化求解规范（NSGA-II/III、约束处理、MCDM） |
| math-code | 代码服从模型、数值稳定性硬检查（条件数/容差扫描/多种子）、鲁棒性分级证据、结果登记表 |
| nature-figure | 投稿级学术图工作流（英文期刊向多面板组装） |
| scipilot-figure-skill | 可视化顾问：选图决策框架 + 中文期刊 CJK 适配 + 程序自检 + AI 读图闭环（国赛默认首选） |

### 论文（R7）
| Skill | 作用 |
|---|---|
| shumo-paper-paradigm | 2024 国赛 8 篇获奖论文内化写作范式：硬性格式、行文句式、写作逻辑、交付前 12 项自检 |
| math-abstract | 摘要证据门禁：首屏评委检查、数字预算、分问覆盖表、反模板残留 |
| math-latex | 竞赛 LaTeX 排版、浮动体、PDF 渲染检查、合规报告 |
| math-table | 符号表/结果表/三线表规范，符号跨文一致性门禁 |
| docx | Word 文档创建/编辑/校验/渲染验证（论文 docx 落地） |

### 质量枢纽与合规（R0）
| Skill | 作用 |
|---|---|
| math-hub | 竞赛质量枢纽：证据链协议（claim→result→figure→run）、最终提交门禁、六评分维度（dispatch 派发模式禁用） |
| math-compliance | 官方规则来源门禁、匿名检查、AI 使用披露（使用日志 + 逐条采纳登记）、提交清单与复现门禁 |

### 评审（R8）
| Skill | 作用 |
|---|---|
| math-verifier | 独立数学核验：量纲/公式回代/边界/守恒/可行性措辞，P0–P3 分级阻塞 |
| math-review | 评委视角风险审查：六评分维度映射、扣分风险标注、评委追问准备 |
| math-consistency | 摘要/正文/表图/附录/登记表跨材料数值-单位-场景一致性审查 |

> 每个技能的原始来源链接与来源说明，见文末【九、Skill 来源汇总表格】。

## 五、使用与启动步骤

1. **部署配置**：按 `TEAM-PACK.md` §10 部署检查清单，在新工作区建立 `.agent-team/` 常驻层（TEAM-PACK、roster、rules、runbook、skills 归档）；
2. **拉取技能**：按 `TEAM-PACK.md` §6 来源清单，从各公开仓库稀疏拉取技能归档（整目录、保持原结构）；
3. **就绪待命**：核对部署清单后团队进入 STANDBY；
4. **接题启动**：总指挥下发赛题 → 总控建 run 目录、落盘 brief → 按工作流 spawn 独立会话角色并行推进；
5. **拍板与交付**：技术路线与终版提交由总指挥拍板；全部验收通过后冻结文件（MD5 红线），复位待命接下一题。

## 六、如何加载这套配置

- **最小加载**：让 AI 主控读取 `TEAM-PACK.md` 并按 §0.2 部署步骤执行，即可在新环境复原整套团队；
- **编排原语映射**：文档中的 spawn / 独立会话 / 会话消息 / agentId 等原语，对应你所用平台的子代理机制（如 DeepSeek Harness 的 subagent / send_message / list_agents）；
- **本地化参数**：仅需填入工作区根路径与目标赛区/年份（非 2026 广东赛区则整体替换 §8 规则节）。

## 七、注意事项

- **脱敏声明**：本仓库不含任何密钥、令牌、账号、个人隐私与本地绝对路径；若部署者自行配置 API Key 提升检索限额，密钥只放本地环境变量，绝不写入仓库。
- **技能许可**：外部技能来自公开仓库（MIT 为主，docx 技能为 Anthropic 专有许可、仅限内部使用）；各技能版权归原作者，商业使用前请自查许可。
- **规则优先级**：题目官方要求 > 常驻竞赛规则 > 技能内置规范 > 个人偏好。
- **启动红线**：没有总指挥明确下发的赛题，团队不得启动任何 run、不得产出任何数模方案、技术路线或代码。
- **赛题隔离**：旧 run 与旧会话封存后永不复用、不改名、不覆盖；角色定义常驻复用。
- **持续备料**：技能需求清单中仅剩"数据清洗与预处理方法论"一项待补，其余需求均已由挂载技能覆盖（见 `TEAM-PACK.md` §7）。

## 八、文件说明

| 文件 | 内容 |
|---|---|
| `TEAM-PACK.md` | 完整可复用配置包：团队章程、架构总则、7 角色身份证、守则与工作链路、26 项 Skill 挂载登记表、外部技能来源清单、需求覆盖跟踪、常驻竞赛规则、运行手册、部署检查清单、附录 A/B/C（定制技能全文） |

---

## 九、Skill 来源汇总表格（v1.4 来源核查）

> 判定规则：外部素材生成的 Skill 附真实原始 URL（经 git ls-remote 实测可达，无编造）；用户手动自定义编写的 Skill 标注【来源：用户手动自定义编写】。详细信息见 `TEAM-PACK.md` §5.1 来源核查清单。

| Skill 名称 | 来源链接 / 来源说明 |
|---|---|
| agent-team | 【原始来源链接丢失】部署前已存在于工作区的编排技能（86 行原文归档），原始分发渠道未记录；如可提供出处则补录 |
| nature-academic-search | https://github.com/Yuan1z0825/nature-skills （skills/nature-academic-search，main） |
| nature-ref-verifier | https://github.com/Yuan1z0825/nature-skills （skills/nature-ref-verifier，main） |
| nature-figure | https://github.com/Yuan1z0825/nature-skills （skills/nature-figure，main；依赖 skills/nature-shared） |
| paper-lookup | https://github.com/K-Dense-AI/scientific-agent-skills （skills/paper-lookup，main） |
| exploratory-data-analysis | https://github.com/K-Dense-AI/scientific-agent-skills （skills/exploratory-data-analysis，main） |
| statistical-analysis | https://github.com/K-Dense-AI/scientific-agent-skills （skills/statistical-analysis，main） |
| statsmodels | https://github.com/K-Dense-AI/scientific-agent-skills （skills/statsmodels，main） |
| scikit-learn | https://github.com/K-Dense-AI/scientific-agent-skills （skills/scikit-learn，main） |
| pymoo | https://github.com/K-Dense-AI/scientific-agent-skills （skills/pymoo，main） |
| docx | https://github.com/K-Dense-AI/scientific-agent-skills （skills/docx，main；Anthropic 原版专有许可，仅内部使用） |
| scipilot-figure-skill | https://github.com/Haojae/scipilot-figure-skill （main，仓库根即技能目录） |
| math-hub | https://github.com/capwitf/My-MathModeling-skills （math-hub，master） |
| math-compliance | https://github.com/capwitf/My-MathModeling-skills （math-compliance，master） |
| math-problem-reader | https://github.com/capwitf/My-MathModeling-skills （math-problem-reader，master） |
| math-model | https://github.com/capwitf/My-MathModeling-skills （math-model，master） |
| math-code | https://github.com/capwitf/My-MathModeling-skills （math-code，master） |
| math-abstract | https://github.com/capwitf/My-MathModeling-skills （math-abstract，master） |
| math-latex | https://github.com/capwitf/My-MathModeling-skills （math-latex，master） |
| math-table | https://github.com/capwitf/My-MathModeling-skills （math-table，master） |
| math-verifier | https://github.com/capwitf/My-MathModeling-skills （math-verifier，master） |
| math-review | https://github.com/capwitf/My-MathModeling-skills （math-review，master） |
| math-consistency | https://github.com/capwitf/My-MathModeling-skills （math-consistency，master） |
| shumo-paper-paradigm | 【来源：用户手动自定义编写】（总指挥直接交付；全文收录于 TEAM-PACK.md 附录 A，文末附官方获奖论文展示页真实学习来源链接） |
| local-git-snapshot | 【来源：用户手动自定义编写】（总指挥直接交付；全文收录于 TEAM-PACK.md 附录 B；纯本地禁远程，无外部来源链接） |
| pitfall-log-reuse | 【来源：用户手动自定义编写】（总指挥直接交付；全文收录于 TEAM-PACK.md 附录 C；纯本地禁远程，无外部来源链接） |
| math-figure（依赖资产） | https://github.com/capwitf/My-MathModeling-skills （math-figure，master；归档时剔除约 25MB 示例图库） |
| nature-shared（依赖资产） | https://github.com/Yuan1z0825/nature-skills （skills/nature-shared，main） |

---

## 十、本地 Git 版本快照使用说明（local-git-snapshot Skill · 挂载 R4）

**两套空间，严格区分**：

| 空间 | 用途 | 规则 |
|---|---|---|
| 底座配置仓库 | 存放 Skill、roster 等团队配置 | 维持原样，**不存放任何赛题代码** |
| 赛题本地仓库 | 每道赛题 run 独立一个 | 接题时在 run 目录 `git init`，只管本题代码，**无远程关联** |

**代码提交流程**（每次产出完整数模代码——数据清洗/模型/绘图脚本等，在本题本地 Git 内）：

```
git add <新增/修改的代码文件>
git commit -m "备注信息：赛题名称，当前阶段，代码用途"
```

**版本操作**（仅作用于本题本地 Git）：

| 操作 | 命令 |
|---|---|
| 查看历史（commit id + 备注） | `git log` |
| 回退到某版本（写错回滚） | `git checkout <commit id>` |
| 对比两版本差异 | `git diff <commitA> <commitB>` |

**红线**：禁止 `git push`、不访问 GitHub 或任何远程仓库、不产生任何远程网络提交；所有 Git 操作仅在本地工作区完成。run 隔离：新赛题 = 全新独立本地 Git，互不干扰；run 封存时本题 Git 历史随目录只读留档。

**分工**：R0 接题时 `git init` 并记入 run brief；R3/R5 每次产出完整代码后执行 add+commit（备注三要素）；版本操作按总指挥指令经 R0 路由；R8 代码门实跑以最新 commit 快照为基线。

---

## 十一、踩坑日志复用机制说明（pitfall-log-reuse Skill · 挂载 R4，与本地 Git 配合）

**日志文档**：每道赛题 run 根目录维护 `PIT_shturl.md`（踩坑日志）——run 之间相互隔离，仅记录当前题目建模、代码调试中遇到的问题；接题时由 R0 创建空模板。

**自动写入**：建模、写代码、调试过程中一旦遇到**报错、逻辑缺陷、参数陷阱、模型异常**，自动追加一条记录（不等汇报指令），单条五要素：

| 要素 | 内容 |
|---|---|
| 关联 Git commit ID | 踩坑与修复所处代码版本（配合 local-git-snapshot） |
| 问题现象 | 报错信息 / 异常表现原文或忠实描述 |
| 问题根本原因 | 排查确认的根因（不是猜测） |
| 当时采用的解决方案 | 实际修复动作 |
| 关键经验总结 | 重点提炼可复用的判断依据与规避方法 |

旧记录**永久保留、只追加、不删除**（更正以"后续更正"附注追加）。

**核心能力——先查日志再动手**：每次开始编写代码 / 分析模型前，先读取查阅 PIT_shturl；再次遇到同类、相似问题时**优先检索日志**，复用过去的排查思路与解决方案，规避重复踩坑；日志作为内置参考知识库辅助判断、快速定位，检索命中注明"复用 PIT_shturl 记录 #N"。

**指令支持**（经 R0 路由）：新增踩坑记录 / 查看完整踩坑日志 / 检索相似坑点。

**边界**：仅记录赛题建模调试踩坑内容，不写入系统 Skill 框架内容；文档保存在当前 run 本地，**不上传任何远程仓库**。R8 验收可引用日志记录验证问题是否真修复（经验复用闭环）。

---

*本系统由 AI 多角色协作搭建与验证；配置版本 v1.4（对应团队花名册 v2.9 快照；v1.4 = 补充角色编号说明并优化 README 角色介绍）。*
