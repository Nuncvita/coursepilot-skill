# ClawPro Input Output Schema

## 输入字段建议

### `course_name`

- 课程名称
- 示例：`数字信号处理`

### `exam_date_or_days_left`

- 考试日期或剩余天数
- 示例：`7 天后考试`

### `target_score`

- 目标分数
- 示例：`80+`

### `current_level`

- 当前基础水平
- 示例：`基础薄弱，课堂吸收不完整`

### `explanation_style`

- 用户偏好的解释方式
- 示例：`通俗解释、考试导向、多例题、少空话`

### `course_materials`

- 课程课件、教材节选等

### `homework_questions`

- 作业题与答案摘要

### `past_exam_questions`

- 往年题或真题改写样例

### `previous_qa_notes`

- 历史答疑或追问记录

## 输出字段建议

### `knowledge_map`

- 课程知识地图

### `topic_weight_table`

- 考点权重与优先级

### `personalized_notes`

- 个性化讲义

### `study_plan`

- 分天复习计划

### `practice_questions`

- 练习题、自测题或代表题

### `weak_points`

- 薄弱点与易错点

### `followup_updates`

- 用户追问后的讲义增补内容

### `final_crash_pack`

- 最终冲刺包

## 使用建议

- 输入字段可以按平台能力合并或拆分
- 如果平台字段数有限，可优先保留：
  - `course_name`
  - `exam_date_or_days_left`
  - `target_score`
  - `course_materials`
  - `past_exam_questions`
  - `previous_qa_notes`

## 设计原则

- 输入要覆盖课程材料、题目材料和用户偏好
- 输出要覆盖知识地图、讲义、计划、练习和追问更新
- 字段命名尽量稳定，便于后续迁移到其他 Agent / Skill 平台
