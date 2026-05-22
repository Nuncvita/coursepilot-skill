# ChatGPT Skill Notes

## 这是什么

本目录下的 `SKILL.md` 是 `CoursePilot` 的平台层适配文件，用于 `ChatGPT Skill` 或类似 Skill 入口格式。

## 它和 core 层的关系

- `SKILL.md` 负责说明“何时使用这个 Skill”
- `core/` 负责说明“CoursePilot 到底怎么工作”

也就是说：

- `platforms/chatgpt_skill/SKILL.md` 是入口
- `core/*.md` 是能力主体

## 为什么不把所有规则都塞回 SKILL.md

如果把全部能力、模板、风格、安全规则重新塞进 `SKILL.md`，会重新回到第二阶段的单层结构问题：

- 平台入口过重
- 后续难维护
- 不利于迁移到其他平台

所以这里刻意保持 `SKILL.md` 轻量，把稳定知识留在 `core/`。

## 它如何用于比赛材料

这个适配文件可以作为：

- “CoursePilot 已具备标准 Skill 入口文件”的证据
- “平台层与能力层已分离”的工程化说明
- 面向评委解释可迁移性的材料之一

## 它不是什么

- 它不是 `ClawPro` 配置文件
- 它不是 `CodeBuddy CLI` 指令文件
- 它不是完整平台运行结果
