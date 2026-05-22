# CodeBuddy CLI Prompt First Pass

请在当前目录对 `CoursePilot` 双层 Skill 架构做第一轮官方工具侧检查与优化。

## 目标

1. 检查双层架构是否清晰
2. 检查 `core` 是否平台无关
3. 检查 `platforms` 是否平台相关
4. 优化 `README.md`
5. 优化 `core/capability_spec.md`
6. 优化 `core/workflow_core.md`
7. 优化 `platforms/clawpro/clawpro_prompt.md`
8. 检查 `samples/` 是否适合比赛展示
9. 生成或更新 `platforms/codebuddy_cli/codebuddy_optimization_record.md`

## 约束

- 不要删除核心文件
- 不要引入大文件
- 不要复制完整教材、完整 PPT、完整真题原卷
- 不要泄露隐私信息
- 不要加入“保证押题”“保证提分”等表述
- 不要把 `CodeBuddy CLI` 写成 CoursePilot 的核心能力本体

## 重点检查项

### 结构

- `core` 是否只保留平台无关能力、规则和模板
- `platforms` 是否只保留平台适配内容
- `chatgpt_skill`、`codebuddy_cli`、`clawpro` 三层分工是否清楚

### 内容

- `README.md` 是否足够清晰，适合评委和开发者快速理解
- `core/capability_spec.md` 是否准确表达输入、输出、关键能力和非目标
- `core/workflow_core.md` 是否没有平台专属动作
- `platforms/clawpro/clawpro_prompt.md` 是否可以独立复制使用
- `samples/` 是否脱敏、不过长、能体现 DSP 成功案例与“追问后讲义进化”

### 记录

- 请生成或更新 `platforms/codebuddy_cli/codebuddy_optimization_record.md`
- 记录本轮修改目标、修改文件、优化点、待人工确认项

## 输出要求

请先给出：

1. 结构性问题
2. 内容性问题
3. 建议修改方案

然后再进行必要修改，并输出：

1. 修改了哪些文件
2. 为什么这样改
3. 还需要人工确认什么
