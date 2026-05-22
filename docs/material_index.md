# Material Index

## 说明

本目录是第 2.5 阶段的双层架构版本。  
它不是重新从第一阶段开始整理，而是基于第二阶段正式 Skill 包继续做结构重构。

## 主要输入来源

本阶段主要以以下第二阶段目录为输入：

- `stage02_skill_submission/coursepilot/`
- `stage02_skill_submission/99_logs/`

## 复制过来的文件

### samples

以下文件从第二阶段直接复制，并保留脱敏版本：

- `samples/sample_input_dsp.md`
- `samples/sample_output_knowledge_map.md`
- `samples/sample_output_personalized_notes.md`
- `samples/sample_output_study_plan.md`
- `samples/sample_output_final_crash_pack.md`
- `samples/sample_followup_update.md`

### docs

以下文件从第二阶段复制后保留：

- `docs/competition_intro_500字.md`
- `docs/demo_script_3_to_5_min.md`

## 在本阶段重写或重构的文件

### 双层总览

- `README.md`
- `00_README_双层架构说明.md`

### core 能力层

基于第二阶段以下文件提炼：

- `coursepilot/SKILL.md`
- `coursepilot/skill_prompt.md`
- `coursepilot/workflow.md`
- `coursepilot/references/user_learning_style.md`
- `coursepilot/references/output_templates.md`
- `coursepilot/references/safety_and_privacy.md`

生成：

- `core/capability_spec.md`
- `core/workflow_core.md`
- `core/output_templates.md`
- `core/user_learning_style.md`
- `core/evaluation_rules.md`
- `core/safety_and_privacy.md`

### platforms 平台层

基于第二阶段平台相关文件重构：

- 原 `coursepilot/SKILL.md`
  - 拆成 `platforms/chatgpt_skill/SKILL.md`
- 原 `coursepilot/skill_prompt.md`
  - 提炼为 `platforms/clawpro/clawpro_prompt.md`
- 原 `references/codebuddy_clawpro_usage_plan.md`
- 原 `docs/codebuddy_usage_record_template.md`
- 原 `docs/clawpro_setup_plan.md`

生成：

- `platforms/chatgpt_skill/*`
- `platforms/codebuddy_cli/*`
- `platforms/clawpro/*`

## 本阶段新增的文档

新增的 stage025 文档包括：

- `docs/architecture_explanation_for_judges.md`
- `docs/next_stage_codebuddy_cli_plan.md`
- `CoursePilot_Dual_Layer_Checklist.md`
- `99_logs/*`

## 结论

第 2.5 阶段的大部分内容属于“基于第二阶段成果的重构与提炼”，不是重新生成课程素材，也不是重新整理原始资料。它的核心价值在于把 CoursePilot 拆成更适合迁移和优化的双层结构。
