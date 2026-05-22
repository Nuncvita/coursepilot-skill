# ClawPro Setup Plan

## Skill / Agent 名称

- `CoursePilot`

## 描述

- 一个面向教育场景的 AI 个性化课程复习 Skill / Agent，用于将课件、教材节选、作业、往年题和历史答疑整理成知识地图、考点权重、个性化讲义、复习计划与考前冲刺包。

## 输入字段建议

- `course_name`
- `exam_date_or_days_left`
- `target_score`
- `current_level`
- `explanation_style`
- `course_materials`
- `homework_questions`
- `past_exam_questions`
- `previous_qa_notes`

## 输出字段建议

- `knowledge_map`
- `topic_weight_table`
- `personalized_notes`
- `study_plan`
- `practice_questions`
- `weak_points`
- `followup_updates`
- `final_crash_pack`

## 是否需要知识库

- 如平台支持，建议开启知识库或文件上传能力
- 如果知识库支持分批上传，优先上传脱敏课程材料节选、样例输入和结构化参考
- 如当前平台不适合建知识库，也可以先走“手动输入样例 + Prompt”验证流程

## 文件上传如何处理

- 优先上传脱敏节选而不是原始整套资料
- 先用 DSP 样例测试稳定性
- 避免上传完整教材、完整 PPT、完整真题原卷

## DSP 样例测试步骤

1. 创建 `CoursePilot` Skill / Agent
2. 粘贴 `clawpro_prompt.md`
3. 配置输入字段
4. 输入 DSP 样例资料
5. 测试知识地图输出
6. 测试个性化讲义输出
7. 测试 7 天复习计划输出
8. 测试追问后讲义更新
9. 测试最终冲刺包输出

## 需要截图的页面

- Skill / Agent 创建页
- Prompt 配置页
- 输入字段配置页
- DSP 样例输入页
- 知识地图输出页
- 个性化讲义输出页
- 追问补讲义输出页
- 最终冲刺包输出页

## 如果可以发布，如何记录 SkillHub / 产品平台链接

- 记录发布时间
- 记录发布页链接
- 截图发布成功页
- 在比赛说明文档中附上链接与截图

## 如果无法发布，如何证明运行效果

- 用截图保留完整输入输出链路
- 用录屏展示 DSP 样例的连续运行过程
- 在演示视频中明确说明这是平台运行态而不是静态文档
