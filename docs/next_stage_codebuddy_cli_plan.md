# Next Stage CodeBuddy CLI Plan

## 第三阶段目标

第三阶段的目标是让 `CodeBuddy CLI` 正式参与 `CoursePilot` 的工程化优化和使用留痕。

## 操作目录

- `stage025_dual_layer_architecture/coursepilot`

## 建议输入文件

- `platforms/codebuddy_cli/codebuddy_cli_prompt_first_pass.md`
- `platforms/codebuddy_cli/codebuddy_cli_usage_plan.md`
- `platforms/codebuddy_cli/codebuddy_cli_checklist.md`
- `platforms/codebuddy_cli/codebuddy_optimization_record_template.md`

## 建议执行步骤

1. 进入 `coursepilot` 目录
2. 启动 `CodeBuddy CLI`
3. 将 `codebuddy_cli_prompt_first_pass.md` 作为首轮任务输入
4. 让其先做结构审查，再做必要优化
5. 要求其生成或更新 `codebuddy_optimization_record.md`
6. 保存终端日志和截图

## 第三阶段重点优化对象

- `README.md`
- `core/capability_spec.md`
- `core/workflow_core.md`
- `core/output_templates.md`
- `platforms/chatgpt_skill/SKILL.md`
- `platforms/clawpro/clawpro_prompt.md`
- `samples/`

## 第三阶段输出建议

建议输出到新目录，例如：

- `stage03_codebuddy_optimized`

这样可以保留第 2.5 阶段的结构基线。

## 需要保留的证据

- 终端运行截图
- 输入 Prompt 截图
- 修改摘要
- `codebuddy_optimization_record.md`
- 优化前后对比说明

## 进入第四阶段前的交接条件

在进入 `ClawPro` 阶段前，至少应满足：

- 双层架构已被官方工具检查过
- `clawpro_prompt.md` 已被优化过一轮
- 样例文件已被复核为适合比赛展示
- 已经保留了官方工具参与记录
