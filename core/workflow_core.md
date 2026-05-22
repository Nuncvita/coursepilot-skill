# Workflow Core

## 说明

本文件定义 CoursePilot 的平台无关工作流。这里描述的是能力层逻辑，不包含任何平台按钮、配置入口或上传界面操作。

## 数据流总览

```
[用户输入]
   │
   ▼
1. Intake ──────────► 输入概况 + 缺失材料提醒
   │
   ▼
2. Style Check ─────► 学习风格确认 / 风格选择记录
   │
   ▼
3. Style Preview ───► 风格预览片段（如用户要求）
   │
   ▼
4. Classification ──► 资料分类表 + 主口径优先级
   │
   ▼
5. Extraction ──────► 章节骨架 + 核心知识点清单
   │
   ▼
6. Cross-reference ─► 交叉映射结果 + 高频主题候选列表
   │
   ▼
7. Weighting ───────► 考点权重表 + 优先级列表
   │                          │
   ▼                          ▼
8. Personalization ◄─────────┘
   │
   ▼
9. Note Generation ─► 个性化讲义
   │
   ▼
10. Planning ───────► 分天复习计划
   │
   ▼
11. Practice Gen ───► 练习任务 + 自测题清单
   │
   ▼ (用户追问时)
12. Follow-up ──────► 定点答疑 + 追问解释结果
   │
   ▼
13. Note Update ────► 讲义更新内容 + 更新位置说明
   │
   ▼
14. Final Pack ─────► 最终冲刺包
   │
   ▼
15. Quality Check ──► 质量检查结果 + 待人工确认项
```

## 各步骤详细定义

### 1. Intake

- 接收课程资料和用户目标
- 识别课程名称、复习时间、目标分数和当前基础
- 记录已提供与未提供的材料
- **输入来源**：用户直接提供
- **流入**：Classification

输出：

- 输入概况
- 缺失材料提醒

### 2. Style Preference Check

- 检查用户是否已提供学习风格偏好
- 如果未提供，通过最多 5 个选择题确认（参见 `core/learning_style_selector.md`）
- 用户可直接选择"默认高效复习型"跳过所有问题
- 如果用户跳过，使用默认高效复习型 / Nuncvita 风格
- **输入来源**：Intake 的用户偏好字段
- **流入**：Style Preview（如用户选择预览）或 Classification（如跳过预览）
- **触发条件**：用户首次输入资料且未提供学习风格偏好

输出：

- 学习风格选择记录
- 当前风格配置（含主风格和辅助风格）

### 3. Optional Style Preview（风格预览）

- 如果用户已上传资料且希望预览不同风格，选取资料中一个小知识点
- 用 2-3 种候选风格各讲一小段（每种风格不超过 5-8 行）
- 预览后让用户选择一种风格或混合风格
- 预览只展示短片段，不替代完整讲义生成
- 如果用户跳过预览，直接使用当前选定的风格
- **输入来源**：Classification（已完成资料分类）+ Style Check 的候选风格
- **流入**：Classification（正式处理流程）
- **触发条件**：用户选择"我想先看看不同风格"或类似表述

输出：

- 风格预览片段（每种风格一小段讲解）
- 用户最终风格选择确认

### 4. Classification

- 按资料类型分类
- 区分 PPT、教材、作业、真题、答疑记录和补充说明
- 判断哪些材料更贴近课程主口径
- **输入来源**：Intake 的输出
- **流入**：Style Preview（如触发预览）或 Extraction

输出：

- 资料分类表
- 主口径优先级

### 5. Extraction

- 提取章节、概念、公式、例题、题型
- 标注定义、判定条件、常见误区和代表性问法
- 提取每章的核心骨架
- **输入来源**：Classification 的分类结果
- **流入**：Cross-reference

输出：

- 章节骨架
- 核心知识点清单

### 6. Cross-reference

- 交叉比对 PPT、教材、作业、真题和历史答疑
- 识别哪些主题反复出现
- 识别哪些题型跨资料重复出现
- 标注口径一致和口径冲突的地方
- **输入来源**：Extraction 的提取结果
- **流入**：Weighting

输出：

- 交叉映射结果
- 高频主题候选列表

### 7. Weighting

- 生成考点权重
- 综合资料出现频率、题型重要性、用户薄弱点和剩余时间
- 给出优先级和推荐复习顺序
- **输入来源**：Cross-reference 的高频候选 + Intake 的用户目标
- **流入**：Personalization、Planning

输出：

- 考点权重表
- 优先级列表

### 8. Personalization

- 套用用户学习风格（参见 `user_learning_style.md`）
- 调整解释顺序、题解密度、例子数量和速记层级
- 保证表达方式适合直接复习
- **输入来源**：Weighting 的优先级 + Style Check 的风格配置
- **流入**：Note Generation

输出：

- 风格应用说明
- 讲义表达策略

### 9. Note Generation

- 生成个性化讲义（参见 `output_templates.md` 模板 3）
- 组织记忆区、正文讲解、公式说明、例题入口、考试提醒和易错点
- 保持章节间结构一致
- **输入来源**：Extraction 的知识点 + Personalization 的风格策略 + Weighting 的优先级
- **流入**：Planning、Follow-up Handling

输出：

- 个性化讲义

### 10. Planning

- 生成复习计划（参见 `output_templates.md` 模板 4）
- 按剩余天数拆分学习任务
- 为每日安排目标、内容、练习、自测和预计时间
- 高权重章节优先安排
- **输入来源**：Weighting 的优先级 + Intake 的时间/目标 + Note Generation 的讲义
- **流入**：Practice Generation

输出：

- 分天复习计划

### 11. Practice Generation

- 生成练习题和自测题（参见 `output_templates.md` 模板 5）
- 优先覆盖高权重章节与用户薄弱点
- 提供代表题、模拟题和自测任务
- **输入来源**：Weighting 的优先级 + Note Generation 的讲义
- **流入**：用户使用（练习自测）

输出：

- 练习任务
- 自测题清单

### 12. Follow-up Handling

- 处理用户追问
- 区分概念不懂、公式不懂、推导不懂、不会做题或概念混淆
- 用课程主口径回答问题
- **输入来源**：用户追问 + Note Generation 的讲义
- **流入**：Note Update
- **触发条件**：用户主动追问

输出：

- 定点答疑
- 追问解释结果

### 13. Note Update

- 将追问解释补充回讲义（参见 `output_templates.md` 模板 8）
- 判断应加入正文、记忆区、易错点、对比表还是快判口令
- 保证更新不破坏原有结构
- **输入来源**：Follow-up Handling 的追问结果
- **流入**：回到 Note Generation 的后续迭代

输出：

- 讲义更新内容
- 更新位置说明

### 14. Final Pack

- 生成考前冲刺包（参见 `output_templates.md` 模板 7）
- 压缩高频考点、必背公式、典型题型、易错点和最后检查项
- 服务于最后复习阶段
- **输入来源**：Note Generation + Weighting + Practice Generation
- **流入**：Quality Check

输出：

- 最终冲刺包

### 15. Quality Check

- 检查结构是否完整（参见 `evaluation_rules.md`）
- 检查来源是否清楚
- 检查是否区分"资料明确出现"和"根据资料推测"
- 检查是否存在隐私、版权和过度承诺风险
- **输入来源**：全部前序输出
- **流入**：回到相关步骤修正（如有问题）

输出：

- 质量检查结果
- 待人工确认项

## 异常与降级处理

| 场景 | 降级策略 |
|---|---|
| 用户只提供单份资料 | 跳过 Cross-reference，明确提示"单资料模式，权重仅供参考" |
| 缺少复习时间和目标分数 | 不生成精确计划，改为输出复习优先级列表 |
| 资料严重不足（少于 2 页） | 输出"资料过少提醒"，建议补充后再生成 |
| 追问超出课程范围 | 明确告知超出范围，不编造来源 |
| 用户风格未指定 | 先通过 5 个问题确认，如用户跳过则使用默认高效复习型 |

## 步骤与输出模板对应关系

| 步骤 | 对应模板 |
|---|---|
| Style Preference Check | 模板 9：学习风格确认 |
| Style Preview | 模板 10：风格预览 |
| Extraction + Cross-reference | 模板 1：课程知识地图 |
| Weighting | 模板 2：考点权重表 |
| Note Generation | 模板 3：个性化讲义 |
| Planning | 模板 4：复习计划 |
| Practice Generation | 模板 5：模拟题 |
| Note Generation（易错点部分） | 模板 6：易错点清单 |
| Final Pack | 模板 7：最终冲刺包 |
| Note Update | 模板 8：追问后讲义更新 |
