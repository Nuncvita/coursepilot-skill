# CodeBuddy CLI Optimization Record

## 使用日期

- 日期：2026-05-22

## 使用工具

- CodeBuddy CLI

## 操作目录

- 目录：`stage03_codebuddy_optimized/coursepilot`

## 本轮目标

1. 检查双层架构是否清晰（core 平台无关、platforms 只做适配）
2. 检查并优化 8 个重点文件的结构与内容
3. 确保 core 层无平台专属内容、platforms 层无能力定义重复
4. 生成优化记录

## 输入 Prompt 摘要

- Prompt 文件：`platforms/codebuddy_cli/codebuddy_cli_prompt_first_pass.md`
- 要求：对双层 Skill 架构做第一轮检查与优化，重点优化 README、capability_spec、workflow_core、output_templates、SKILL.md、clawpro_prompt、sample_followup_update、architecture_explanation_for_judges

## CodeBuddy 修改了哪些文件

| # | 文件 | 修改类型 |
|---|---|---|
| 1 | `README.md` | 重写 |
| 2 | `core/capability_spec.md` | 重写 |
| 3 | `core/workflow_core.md` | 重写 |
| 4 | `core/output_templates.md` | 重写 |
| 5 | `platforms/chatgpt_skill/SKILL.md` | 重写 |
| 6 | `platforms/clawpro/clawpro_prompt.md` | 重写 |
| 7 | `samples/sample_followup_update.md` | 重写 |
| 8 | `docs/architecture_explanation_for_judges.md` | 重写 |

## 修改前问题

### 结构性问题

1. README.md 目录结构不完整，缺少文件级细节和 workflow 概览
2. capability_spec.md 缺少与 workflow 的映射关系，能力无优先级排序
3. workflow_core.md 步骤间缺少数据流说明，无异常/降级处理，无与模板的对应关系
4. output_templates.md 模板与 workflow 步骤无映射，缺少输出组合策略
5. SKILL.md frontmatter name 小写与项目名不一致，核心文件引用为平铺列表
6. clawpro_prompt.md 与 core 层内容大量重复（9 步 vs 13 步口径不一致），不利于维护
7. sample_followup_update.md 缺少"更新前后 diff"对比
8. architecture_explanation_for_judges.md 缺少"为什么不用单层"的反证论证和文字版架构图

### 内容性问题

1. README.md 缺少核心价值提炼，"后续如何用 CodeBuddy CLI/ClawPro"段落对评委价值低
2. capability_spec.md "非目标"列表单薄，缺少降级策略
3. workflow_core.md 无分支/条件逻辑，无异常处理
4. output_templates.md 权重表模板证据字段未要求标明来源类型
5. clawpro_prompt.md 工作流程只有 9 步但 workflow_core 有 13 步，口径不一致
6. sample_followup_update.md 没有对比展示更新前后的讲义差异
7. architecture_explanation_for_judges.md 缺少架构图和平台层原则说明

## 修改后改进

### README.md

- 新增"核心价值"5 条提炼（多资料融合/考点权重/个性化讲义/追问进化/复习闭环）
- 新增 ASCII 架构图，直观展示双层分工
- 补全目录结构到文件级（含每个文件的用途说明）
- 新增 Workflow 一览（13 步流程链）
- 精简"版本边界"，移除对评委价值低的 CodeBuddy CLI/ClawPro 使用说明

### core/capability_spec.md

- 核心能力改为优先级排序表格（P0/P1/P2）
- 输入类型分为"必要输入"和"增强输入"，每项标注缺失时影响
- 新增"降级策略"段落（4 条规则）
- 输出类型新增与 workflow 步骤的对应关系
- "非目标"从 5 条扩展到 8 条，表格化，增加"不替代教师""不做实时答疑""不存储用户数据"

### core/workflow_core.md

- 新增 ASCII 数据流总览图
- 每个步骤新增"输入来源"和"流入"说明
- 新增"异常与降级处理"表格（5 种场景及降级策略）
- 新增"步骤与输出模板对应关系"表格（8 个模板映射到 13 步）
- Note Update 步骤标注"触发条件：用户主动追问"

### core/output_templates.md

- 新增"概述"和"输出组合策略"表格（4 种场景的推荐输出组合）
- 每个模板新增与 workflow 步骤的对应标注
- 知识地图模板：示例补充"优先级依据"字段
- 权重表模板：证据字段要求标明来源类型
- 易错点清单模板：纠正方式要求"可快速执行，不需要再查资料"
- 冲刺包模板：检查清单要求"可自问自答的判断题"
- 讲义更新模板：更新位置要求"章节 + 具体插入点"

### platforms/chatgpt_skill/SKILL.md

- frontmatter name 从小写 `coursepilot` 改为 `CoursePilot`
- description 更新，更准确描述核心能力
- 核心文件引用从平铺列表改为表格（文件 + 用途）
- "How To Apply" 步骤从机械列举改为带意图说明的 6 步
- 新增"When To Use"中"not predictions or guarantees"的限定
- 新增追问时"Apply the Note Update template"的明确指引

### platforms/clawpro/clawpro_prompt.md

- 新增"能力层核心文件"表格，引用 core 层 6 个文件，而非重复全部规则
- 工作流程从 9 步对齐到 13 步（与 workflow_core 一致），每步增加简要说明
- 新增数据流图（ASCII）
- 输入类型改为表格，标注"必要/增强"
- 质量检查改为引用 evaluation_rules.md，只保留最关键的 7 条自检项
- 安全边界改为引用 safety_and_privacy.md，只保留 6 条核心边界
- 新增"ClawPro 运行时只需粘贴本文件 + 查阅 core 层"的定位说明

### samples/sample_followup_update.md

- 新增"场景说明"段落，解释本示例展示的核心差异化能力
- 新增"讲义更新 Diff"：展示更新前后的讲义节选对比（这是最关键的改进）
- 新增更新后讲义中的"一句话口令"
- 结尾对比表从 2 列扩展到 4 行对比（普通总结器 vs CoursePilot 的 4 个维度）

### docs/architecture_explanation_for_judges.md

- 新增"反证：为什么不用单层架构"对比表（5 个维度）
- 新增 ASCII 架构总览图（含 core 6 个文件和 platforms 3 个子目录）
- 能力层说明从纯列表改为表格（能力 + 文件 + 核心内容）
- 平台层说明新增"关键原则：平台层不重复定义能力规则，只做适配和引用"
- ClawPro 说明增加具体文件引用
- 双层架构价值从 4 条扩展到 4 条，每条更具体

## 截图位置

- 终端首页：（待人工补充）
- 输入 Prompt：（待人工补充）
- 修改摘要：（待人工补充）
- 记录文件：`platforms/codebuddy_cli/codebuddy_optimization_record.md`

## 可写入说明文档的一句话

"在双层架构雏形基础上，使用 CodeBuddy CLI 对核心能力定义、工作流数据流、输出模板映射、平台层口径一致性和比赛展示材料进行了第一轮官方工具侧优化，补充了降级策略、异常处理、架构图和追问 diff 示例，并保留了操作记录。"

## 待人工确认项

| # | 确认项 | 说明 |
|---|---|---|
| 1 | capability_spec.md 新增的 3 条非目标是否合适 | "不替代教师""不做实时答疑""不存储用户数据"是新加的边界，需确认是否与项目定位一致 |
| 2 | workflow_core.md 5 种降级场景是否充分 | 当前定义了 5 种异常场景，实际使用中可能有更多需补充 |
| 3 | clawpro_prompt.md 是否能在 ClawPro 中独立运行 | 本轮改为"引用 core 层"模式，需确认 ClawPro 是否支持跨文件引用，如不支持需回退为内联模式 |
| 4 | sample_followup_update.md 的 diff 格式是否适合评委阅读 | 新增了更新前后对比，需确认这种展示方式是否直观 |
| 5 | README.md 中 ASCII 架构图在不同终端/Markdown 渲染器中是否正常 | ASCII 图可能在某些渲染环境下变形，需检查 |
| 6 | SKILL.md 的 frontmatter name 改为 `CoursePilot` 是否影响 ChatGPT Skill 注册 | 部分 Skill 平台对 name 字段格式有要求，需确认 |
| 7 | output_templates.md "7 天复习计划模板"改名"复习计划模板"是否合适 | 原 README 中引用的是"7 天"，但模板本身应支持多种天数 |

---

## 第二轮小修记录

### 本轮修改时间

- 日期：2026-05-22

### 本轮修改目标

1. 修正 SKILL.md frontmatter name 字段大小写问题
2. 将 clawpro_prompt.md 改为独立可运行版本（内联全部关键规则，移除本地文件依赖）
3. 如实记录本轮修改内容

### 修改了哪些文件

| # | 文件 | 修改类型 | 改动说明 |
|---|---|---|---|
| 1 | `platforms/chatgpt_skill/SKILL.md` | 小修 | frontmatter name 从 `CoursePilot` 改回 `coursepilot`，description 改为全小写 |
| 2 | `platforms/clawpro/clawpro_prompt.md` | 重写 | 从"引用 core 层文件"模式改为"内联全部关键规则"的独立可运行 Prompt |
| 3 | `platforms/codebuddy_cli/codebuddy_optimization_record.md` | 追加 | 追加本节第二轮小修记录 |

### SKILL.md 的 name 字段为什么改回 coursepilot

第一轮将 name 从 `coursepilot` 改为 `CoursePilot`，目的是与项目显示名保持一致。但 ChatGPT Skill（GPTs）的 YAML frontmatter 对 name 字段有格式要求：通常为全小写、不含空格的标识符，而非显示名。使用 `CoursePilot` 可能导致 Skill 注册失败或被平台截断。因此改回 `coursepilot`，正文中仍然使用 `CoursePilot` 作为产品显示名。

### clawpro_prompt.md 为什么改成独立可运行版本

第一轮将 clawpro_prompt.md 改成了"引用 core/*.md 本地文件"的精简版本，这在本地项目目录中阅读没有问题，但 ClawPro 的 Skill/Agent 角色设定是一个独立的文本框，运行时无法读取本地文件路径。如果 prompt 写着"详见 `../../core/workflow_core.md`"，在 ClawPro 里实际上不会加载任何内容，关键规则会缺失，导致 Skill 无法正确运行。因此本轮将全部关键规则（13 步流程、输入定义、输出格式、个性化规则、追问规则、来源规则、安全边界）直接内联进 prompt，确保粘贴即可运行。文件开头保留一句说明，表明 Prompt 来自 CoursePilot 能力层的规则抽象。

### 本轮没有修改哪些目录

- `core/`：未修改（共 6 个文件，均保持第一轮状态）
- `samples/`：未修改（共 6 个文件）
- `docs/`：未修改（共 5 个文件）
- `platforms/chatgpt_skill/chatgpt_skill_notes.md`：未修改
- `platforms/clawpro/` 其他文件（clawpro_setup_plan、clawpro_demo_steps、clawpro_input_output_schema）：未修改
- `README.md`：未修改

### 仍需人工确认什么

| # | 确认项 | 说明 |
|---|---|---|
| 1 | clawpro_prompt.md 长度是否超出 ClawPro 系统提示字数限制 | 内联全部规则后 prompt 较长，需在 ClawPro 中实测是否超出字数限制 |
| 2 | SKILL.md description 改为全小写是否符合 ChatGPT GPTs 注册规范 | 部分平台 description 支持正常大小写，需确认是否需要还原 |
| 3 | 第一轮待确认项 1~5、7 仍未解决 | capability_spec 非目标 / workflow 降级场景 / diff 格式 / ASCII 图渲染 / 复习计划模板名称 |

### 可写入比赛说明文档的一句话

"在第一轮双层架构优化基础上，通过第二轮小修修正了 ChatGPT Skill name 字段格式，并将 ClawPro 平台 Prompt 从依赖本地文件的精简引用版改为内联全部关键规则的独立可运行版本，确保 Prompt 可直接粘贴至 ClawPro 使用。"

---

## 第三轮小修记录：学习风格选择与预览机制

### 本轮修改时间

- 日期：2026-05-22

### 本轮修改目标

将 CoursePilot 从"单一默认学习风格"升级为"默认风格 + 可配置风格系统"，新增学习风格选择、风格预览、混合风格和随时切换能力。

### 修改或新增了哪些文件

| # | 文件 | 修改类型 | 改动说明 |
|---|---|---|---|
| 1 | `core/learning_style_selector.md` | **新增** | 完整定义 7 种粗分类风格、风格预览机制、混合风格机制、5 问题快速确认流程、默认降级规则 |
| 2 | `core/user_learning_style.md` | 修改 | 从单一风格规则升级为"默认 Nuncvita 风格 + 6 种可选风格"系统，新增风格选择流程说明 |
| 3 | `core/capability_spec.md` | 修改 | 新增 P1 优先级能力"学习风格选择与预览"；增强输入的"学习风格偏好"字段更新；新增关键能力详解第 7 节 |
| 4 | `core/workflow_core.md` | 修改 | 工作流从 13 步扩展到 15 步，新增"Style Preference Check"和"Optional Style Preview"两步；Data flow 图和步骤编号全部更新；异常处理表和模板映射表更新 |
| 5 | `core/output_templates.md` | 修改 | 模板从 8 个扩展到 10 个；新增模板 9"学习风格确认"和模板 10"风格预览"；输出组合策略表新增用户未提供偏好场景 |
| 6 | `platforms/clawpro/clawpro_prompt.md` | 修改 | 新增"二点五：学习风格选择与预览机制"整节（7 个子段）；工作流从 13 步更新到 15 步并重新编号所有步骤；异常处理表更新 |
| 7 | `samples/sample_input_dsp.md` | 修改 | 新增"学习风格选择"字段，展示混合风格选择记录 |
| 8 | `samples/sample_followup_update.md` | 修改 | 新增"追问中改变学习风格"小节，说明用户可在追问时切换风格 |
| 9 | `docs/architecture_explanation_for_judges.md` | 修改 | 新增"默认风格 + 可配置风格系统"亮点章节（6 条）；架构图中新增 learning_style_selector；能力层表格更新 |
| 10 | `README.md` | 修改 | 目录结构加入 learning_style_selector.md；workflow 步数从 13 更新为 15 |
| 11 | `platforms/codebuddy_cli/codebuddy_optimization_record.md` | 追加 | 追加本节第三轮记录 |

### 为什么要从"单一默认风格"升级为"默认风格 + 可配置风格"

第一轮的 user_learning_style.md 只定义了 Nuncvita 这种单一风格规则，虽然这种风格经验证有效，但不同学习者的基础、目标和时间千差万别。一个"零基础需要从零补课"的学生和一个"基础扎实只想刷真题冲 90+"的学生，用同一种讲义风格效果截然不同。

这次升级的核心理念是：保留 Nuncvita 风格作为默认（因为它是验证过的成功方案），但允许学习者在 7 种粗分类风格中选择最适合自己的，也支持对特定内容区段使用不同风格（混合风格）。

### 默认 Nuncvita 风格如何保留

- Nuncvita 风格完整保留在 `core/user_learning_style.md` 的核心规则部分
- 它作为"默认高效复习型"在 `learning_style_selector.md` 中定义为 7 种风格的第一个
- 用户跳过所有选择时自动使用此风格
- 此风格在 ClawPro Prompt 中也被明确列为默认风格

### 风格选择和风格预览如何工作

1. 用户上传资料后，如果未提供学习偏好，CoursePilot 通过最多 5 个选择题确认
2. 用户可直接选"默认"跳过，使用 Nuncvita 风格
3. 如果用户已上传资料，可要求风格预览：选取一个小知识点，用 2-3 种风格各讲 5-8 行
4. 预览后用户选择单一风格或混合风格
5. 所有输出开头记录当前风格配置
6. 用户随时可切换风格

### 是否只做小修，没有破坏双层架构

- core 层新增 `learning_style_selector.md`（平台无关能力）
- core 层现有文件只做增量修改（新增步骤、新增模板、新增能力定义），未删除任何原有内容
- platforms 层只改 clawpro_prompt.md（内联新规则，不依赖本地文件）
- 未新增目录、未删除目录、未引入大文件
- 双层架构分层原则保持：core 只定义能力，platforms 只做适配

### 仍需人工确认的内容

| # | 确认项 | 说明 |
|---|---|---|
| 1 | 7 种风格定义是否覆盖主流学习场景 | 当前定义了 7 种粗分类风格，是否需要增减 |
| 2 | workflow_core 现在 15 步是否合理 | Style Check 和 Style Preview 是可选步骤（不触发则跳过），是否适合作为独立步骤 |
| 3 | clawpro_prompt.md 加入风格机制后是否仍然足够独立 | 新增"二点五"节内联了全部风格规则，需在 ClawPro 中实测 |
| 4 | 10 个模板的新编号是否与其他引用文件一致 | 第一轮中 README 和 docs 引用了模板编号，需检查是否全部对齐 |
| 5 | 混合风格的实现细节是否需要在模板中补充 | 当前在 learning_style_selector.md 中定义了混合风格规则，但模板中未专门设计混合风格输出格式 |

### 可写入比赛说明文档的一句话

"CoursePilot 没有强制所有用户使用同一种讲义风格——它提供了基于真实成功案例的默认风格，同时支持 7 种粗分类风格选择、上传资料后的 2-3 种风格预览、指定内容区段的混合风格以及随时切换风格的灵活性，使不同基础、目标和时间紧迫度的学习者都能获得最适合自己的输出格式。"

---

## 第三阶段最终一致性检查记录

### 检查时间

- 日期：2026-05-22

### 本轮检查目标

对第三轮"学习风格选择与预览机制"修改后的所有文件，做最终一致性检查和小修，不重构、不大改。

### 检查了什么

**1. workflow_core.md 是否是 15 步工作流**

✅ 数据流总览图 Step 1-15 完整，步骤详细定义 Step 1-15 完整，编号连续无跳号。

**2. clawpro_prompt.md 是否同步为 15 步且独立可运行**

✅ 工作流总览图 15 步，步骤详解 1-15 完整，所有风格规则内联，无本地文件依赖。

**3. output_templates.md 模板编号是否一致**

⚠️ 发现并修复：`输出组合策略` 表格中"用户未提供风格偏好"行未更新为完整的模板 9/10 引用，已修复。当前 10 个模板编号连续，与步骤映射表一致。

**4. README.md / architecture_explanation_for_judges.md / capability_spec.md 中表述是否一致**

✅ README.md：`workflow_core.md ← 15 步平台无关工作流`，Workflow 一览 15 步。
⚠️ architecture_explanation_for_judges.md：`工作流 | workflow_core.md | 13 步流程...` 未更新 → 已修复为"15 步工作流 + 数据流"。
✅ capability_spec.md：核心能力 8 项，与 workflow 15 步对应一致。

**5. learning_style_selector.md 是否被 README 和相关 core 文件正确引用**

✅ README.md 目录结构已包含 `learning_style_selector.md ← 风格选择/预览/混合风格机制`。
✅ workflow_core.md Step 2-3 引用 `core/learning_style_selector.md`。
✅ clawpro_prompt.md "二点五"节内联了完整风格选择规则。

**6. sample_input_dsp.md 和 sample_followup_update.md 是否能体现 4 个要点**

✅ sample_input_dsp.md：包含"默认高效复习型/Nuncvita 风格"、"傅里叶变换性质风格预览"、"混合风格"三段。
✅ sample_followup_update.md：包含"追问中改变学习风格"小节。

**7. 是否仍有"保证押题/保证提分/不听课也能过"等风险表述**

✅ 全文检索：capability_spec.md、safety_and_privacy.md、clawpro_prompt.md、evaluation_rules.md 中均无此类表述；非目标表、安全边界均有"不保证押题/不保证提分"条目。

**8. 是否含有隐私/手机号/邮箱/账号等敏感信息**

✅ 全文检索：所有 `.md` 文件不含手机号、邮箱地址、账号信息。samples/ 目录已脱敏。

### 修了哪些小问题

| # | 文件 | 问题 | 修复 |
|---|---|---|---|
| 1 | `docs/architecture_explanation_for_judges.md` Line 60 | "13 步流程"未更新 | 改为"15 步工作流 + 数据流" |
| 2 | `core/output_templates.md` Line 13 | 输出组合策略表未更新 | 改为完整引用模板 9/10 的两阶段流程 |
| 3 | `platforms/clawpro/clawpro_prompt.md` Line 29 | 降级的"学习风格偏好"描述 | 已改为"先通过 5 个问题确认，用户跳过则使用默认高效复习型" |

### 还有哪些需要人工确认

| # | 确认项 | 说明 |
|---|---|---|
| 1 | workflow_core.md Step 2(Style Check) 和 Step 3(Style Preview) 作为可选步骤放在主流程中是否合适 | 当前做法是放在主流程里，用户跳过则直接进入 Step 4；另一种做法是完全作为条件分支不占独立步骤编号。需确认评委是否会对"15 步"中的可选步骤有疑问 |
| 2 | output_templates.md 新增的模板 9/10 是否需要在 samples/ 中补充对应示例输出 | 当前 samples/ 只有 6 个文件，未包含"学习风格确认输出"和"风格预览输出"的示例 |
| 3 | learning_style_selector.md 中的 7 种风格名称是否需要在英文平台文档中统一英文命名 | 当前 SKILL.md 和 clawpro_prompt.md 中混合中英文，需确认评委是否要求统一语言 |

### 可写入比赛说明文档的一句话

"第三轮在 CoursePilot 中新增了完整的学习风格选择与预览机制（7 种粗分类风格、风格预览、混合风格、随时切换），并通过最终一致性检查修复了 architecture_explanation_for_judges.md 和 output_templates.md 中的 2 处编号不一致问题，确保所有 8 个目标文件口径完全对齐。"
