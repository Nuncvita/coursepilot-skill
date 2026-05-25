# CoursePilot：AI 个性化课程复习 Skill

> 上传课程 PPT、教材、作业、往年题和历史答疑，自动生成知识地图、个性化讲义、复习计划与考前冲刺包，并支持追问后讲义持续进化。

---

## 快速查看路径（推荐阅读顺序）

| # | 文件 | 看点 |
|---|---|---|
| 1 | `README.md` | 项目全景 ← 你在这里 |
| 2 | `core/capability_spec.md` | CoursePilot 能做什么、不能做什么 |
| 3 | `core/workflow_core.md` | 15 步处理流程 + 数据流 + 降级策略 |
| 4 | `core/learning_style_selector.md` | 7 种风格选择、风格预览、混合风格 |
| 5 | `platforms/clawpro/clawpro_prompt.md` | 可直接粘贴到 ClawPro 的独立 Prompt |
| 6 | `samples/sample_input_dsp.md` | DSP 课程输入样例 |
| 7 | `samples/sample_output_knowledge_map.md` | 输出样例：知识地图 |
| 8 | `samples/sample_output_personalized_notes.md` | 输出样例：个性化讲义 |
| 9 | `samples/sample_output_study_plan.md` | 输出样例：7 天复习计划 |
| 10 | `samples/sample_output_final_crash_pack.md` | 输出样例：考前冲刺包 |
| 11 | `samples/sample_followup_update.md` | 输出样例：追问后讲义进化 |
| 12 | `platforms/codebuddy_cli/codebuddy_optimization_record.md` | CodeBuddy CLI 优化记录 |

---

## 最短体验方式

### 方式一：直接阅读输入输出（1 分钟看懂）

打开 `samples/sample_input_dsp.md`（输入）→ 看任意一个 `sample_output_*.md`（输出），即可理解 CoursePilot 做了什么。

### 方式二：在 ClawPro 里跑一次（5 分钟体验）

1. 复制 `platforms/clawpro/clawpro_prompt.md` 全文
2. 粘贴到 ClawPro 的 Skill / Agent 角色设定
3. 把 `samples/sample_input_dsp.md` 的内容作为测试输入发给 Agent
4. 观察输出是否形成知识地图、讲义、计划和冲刺包

### 方式三：理解架构（2 分钟看懂设计）

依次阅读 `core/capability_spec.md` → `core/workflow_core.md` → `platforms/clawpro/clawpro_prompt.md`，理解双层 Skill 架构：core 定义能力，platforms 做平台适配。

---

## 目录结构

```
coursepilot/
├─ README.md                              ← 项目入口
├─ core/                                  ← 平台无关能力层
│  ├─ capability_spec.md                   ← 能力定义：输入/输出/关键能力/非目标
│  ├─ workflow_core.md                     ← 15 步处理流程 + 数据流 + 降级策略
│  ├─ output_templates.md                  ← 10 个输出模板
│  ├─ learning_style_selector.md           ← 7 种风格、预览机制、混合风格
│  ├─ user_learning_style.md              ← 默认 Nuncvita 风格 + 多风格规则
│  ├─ evaluation_rules.md                 ← 10 条质量检查规则
│  └─ safety_and_privacy.md               ← 安全/隐私/版权/诚信边界
├─ platforms/                             ← 平台适配层（不定义能力，只做适配）
│  ├─ chatgpt_skill/SKILL.md              ← ChatGPT Skill 轻量入口
│  ├─ codebuddy_cli/                      ← CodeBuddy CLI 优化文件
│  │  └─ codebuddy_optimization_record.md
│  └─ clawpro/                            ← ClawPro Skill/Agent 运行文件
│     ├─ clawpro_prompt.md                ← 独立可运行 Prompt
│     ├─ clawpro_setup_plan.md
│     ├─ clawpro_demo_steps.md
│     └─ clawpro_input_output_schema.md
├─ samples/                               ← 脱敏示例（DSP 数字信号处理课程）
│  ├─ sample_input_dsp.md
│  ├─ sample_output_knowledge_map.md
│  ├─ sample_output_personalized_notes.md
│  ├─ sample_output_study_plan.md
│  ├─ sample_output_final_crash_pack.md
│  └─ sample_followup_update.md
└─ docs/                                  ← 比赛辅助材料
   ├─ architecture_explanation_for_judges.md
   ├─ competition_intro_500字.md
   ├─ demo_script_3_to_5_min.md
   └─ material_index.md
```

| 目录 | 职责 |
|---|---|
| `core/` | 平台无关能力层 — 定义 CoursePilot 稳定的能力本体，不依赖任何平台 |
| `platforms/` | 平台适配层 — 把 core 层能力接入 ChatGPT Skill、CodeBuddy CLI、ClawPro |
| `samples/` | 脱敏演示 — 一组 DSP 课程的输入输出样例，展示功能全貌 |
| `docs/` | 比赛辅助 — 架构解释、作品简介、演示脚本、材料索引 |

---

## 作品亮点

### 核心能力

- **多资料融合** — 同时处理 PPT、教材、作业、真题和答疑，交叉比对给出考点权重
- **默认高效复习型 + 可配置学习风格** — 默认使用验证过的 Nuncvita 风格，同时支持 7 种粗分类风格选择
- **风格预览** — 用户上传资料后，可用 2-3 种风格预览同一知识点（每种 5-8 行），看到差异再选择
- **可进化讲义** — 用户追问后，高价值解释自动回写进讲义，不是一次性聊天
- **复习闭环** — 知识地图 → 讲义 → 练习 → 计划 → 冲刺包，各输出联动

### 工程化亮点

- **双层 Skill 架构** — core 层定义能力，platforms 层做适配；平台迁移只需改适配层
- **ClawPro 可运行 Prompt** — `platforms/clawpro/clawpro_prompt.md` 独立可运行，粘贴即用
- **CodeBuddy CLI 工程化优化** — 三轮官方工具优化，完整记录在 `platforms/codebuddy_cli/codebuddy_optimization_record.md`

---

## 注意事项

- 本仓库不包含完整教材、完整 PPT、完整真题原卷或完整原始聊天记录
- `samples/` 中的课程资料已脱敏，题目为改写样例
- 本项目用于**学习辅助、复习规划和知识整理**
- 不承诺押题，不承诺保证提分
- CoursePilot 的输出定位是复习工具，不是结果承诺工具
