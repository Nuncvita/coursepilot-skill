# CoursePilot：AI 个性化课程复习 Skill

## 一句话介绍

CoursePilot 把课件、教材节选、作业、往年题和历史答疑，整理成知识地图、考点权重、个性化讲义、复习计划和考前冲刺包，并支持追问后讲义持续进化。

## 核心价值

- **多资料融合**：不依赖单一来源，交叉比对 PPT、教材、作业、真题和答疑
- **考点权重分析**：基于多资料重复证据给出优先级，而非主观猜测
- **个性化讲义**：按用户风格调整表达，直接服务复习和做题
- **追问后讲义进化**：高价值追问回写进讲义，而非一次性聊天
- **复习闭环**：知识地图 → 讲义 → 练习 → 计划 → 冲刺包，各输出联动而非孤立文档

## 双层架构

```
┌─────────────────────────────────────────┐
│  platforms/  — 平台适配层                │
│  ┌──────────┬──────────┬──────────┐     │
│  │chatgpt   │codebuddy │clawpro   │     │
│  │_skill    │_cli      │          │     │
│  └──────────┴──────────┴──────────┘     │
├─────────────────────────────────────────┤
│  core/  — 平台无关能力层                 │
│  capability_spec / workflow / templates  │
│  learning_style / evaluation / safety   │
└─────────────────────────────────────────┘
```

- `core/`：平台无关能力层，沉淀稳定方法与规则
- `platforms/`：平台相关适配层，负责把能力层接入具体平台

优势：能力层稳定后可复用于多个平台；平台迁移时只需重写适配层，不必重写全部能力。

## 目录结构

```
coursepilot/
├─ README.md                        ← 项目入口
├─ core/                            ← 平台无关能力层
│  ├─ capability_spec.md             ← 输入/输出/关键能力/非目标
│  ├─ workflow_core.md               ← 15 步平台无关工作流
│  ├─ output_templates.md            ← 10 个输出模板
│  ├─ user_learning_style.md         ← 默认 Nuncvita 风格 + 多风格系统
│  ├─ learning_style_selector.md     ← 风格选择/预览/混合风格机制
│  ├─ evaluation_rules.md            ← 输出质量检查 10 条
│  └─ safety_and_privacy.md          ← 安全/隐私/版权/诚信规则
├─ platforms/                        ← 平台相关适配层
│  ├─ chatgpt_skill/                 ← ChatGPT Skill 入口
│  │  └─ SKILL.md
│  ├─ codebuddy_cli/                 ← CodeBuddy CLI 官方工具优化
│  │  ├─ codebuddy_cli_usage_plan.md
│  │  ├─ codebuddy_cli_prompt_first_pass.md
│  │  ├─ codebuddy_cli_checklist.md
│  │  └─ codebuddy_optimization_record_template.md
│  └─ clawpro/                      ← ClawPro Skill/Agent 配置
│     ├─ clawpro_prompt.md
│     ├─ clawpro_setup_plan.md
│     ├─ clawpro_demo_steps.md
│     └─ clawpro_input_output_schema.md
├─ samples/                          ← 脱敏示例（DSP 课程）
│  ├─ sample_input_dsp.md
│  ├─ sample_output_knowledge_map.md
│  ├─ sample_output_personalized_notes.md
│  ├─ sample_output_study_plan.md
│  ├─ sample_output_final_crash_pack.md
│  └─ sample_followup_update.md
└─ docs/                             ← 比赛与演示辅助
   ├─ architecture_explanation_for_judges.md
   ├─ competition_intro_500字.md
   ├─ demo_script_3_to_5_min.md
   ├─ material_index.md
   └─ next_stage_codebuddy_cli_plan.md
```

## Workflow 一览

CoursePilot 核心工作流共 15 步，形成闭环：

```
Intake → Style Check → Style Preview → Classification → Extraction
→ Cross-reference → Weighting → Personalization → Note Generation
→ Planning → Practice Generation → Follow-up Handling → Note Update
→ Final Pack → Quality Check
```

详细定义见 `core/workflow_core.md`，每个步骤的输出模板见 `core/output_templates.md`。

## 版本边界

- 当前版本是双层架构雏形，不是最终发布态
- 不包含网站、复杂前端或真实平台运行结果
- 不包含完整教材、完整 PPT、完整真题原卷或完整原始聊天记录
- 重点：结构清晰、适合比赛展示、便于工具优化与平台运行
