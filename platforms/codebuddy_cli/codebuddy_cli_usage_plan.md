# CodeBuddy CLI Usage Plan

## 第三阶段为什么要使用 CodeBuddy CLI

在第 2.5 阶段之后，`CoursePilot` 已经从单层 Skill 包升级为双层结构。  
第三阶段使用 `CodeBuddy CLI` 的目的，是让官方工具参与后续工程化优化、结构检查和使用留痕。

## CodeBuddy CLI 在本项目中的角色

`CodeBuddy CLI` 的角色是：

- 检查双层架构是否清晰
- 检查 `core` 是否真正平台无关
- 检查 `platforms` 是否真正平台相关
- 优化关键文档表达
- 检查样例是否适合比赛展示
- 记录官方工具侧参与证据

## 它要优化哪些文件

建议重点优化：

- `coursepilot/README.md`
- `core/capability_spec.md`
- `core/workflow_core.md`
- `core/output_templates.md`
- `platforms/chatgpt_skill/SKILL.md`
- `platforms/clawpro/clawpro_prompt.md`
- `samples/`
- `docs/architecture_explanation_for_judges.md`

## 它不负责什么

`CodeBuddy CLI` 不负责：

- 重新生成第一阶段归档
- 回头重做第二阶段全部文件
- 凭空新增大体积资料
- 替代 CoursePilot 的能力层逻辑
- 替代 ClawPro 的平台运行与展示

## 建议的执行顺序

1. 在 `stage025_dual_layer_architecture/coursepilot` 下运行
2. 先让它检查结构，再优化关键文件
3. 再检查样例和演示文档
4. 最后生成或更新优化记录

## 需要保留哪些截图或日志证据

- CodeBuddy CLI 打开目录的画面
- 输入首轮 Prompt 的画面
- 修改关键文件前后的摘要
- 生成优化记录的画面
- 终端执行结果或日志文件

## 后续如何写进作品说明文档

建议对外表述为：

> 在双层架构雏形完成后，进一步使用 CodeBuddy CLI 对能力层与平台层的边界、关键 Prompt 和比赛展示文档进行了官方工具侧优化，并保留了结构调整记录与截图。

## 强调

CodeBuddy CLI 是官方工具参与和工程化优化环节，用于检查、优化和留痕，不是凭空替代 CoursePilot 能力层的系统本体。
