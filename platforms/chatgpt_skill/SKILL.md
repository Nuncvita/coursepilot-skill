---
name: coursepilot
description: coursepilot is an ai-powered personalized course review skill for turning course materials, textbook excerpts, assignments, past exam questions, and tutoring conversations into structured study notes, knowledge maps, exam-weighted topic analysis, study plans, and final exam crash packs. Use this skill when the user wants to organize learning materials, prepare for exams, generate personalized lecture notes, analyze likely key topics, or iteratively update notes based on follow-up questions.
---

# CoursePilot — ChatGPT Skill Adapter

This is the ChatGPT-skill adapter for CoursePilot. It is intentionally lightweight: the platform entry file points to the capability layer instead of duplicating all domain rules inline.

# When To Use

Use this skill when the user wants to:

- organize course materials for exam preparation
- turn PPTs, textbook excerpts, assignments, past exams, and tutoring notes into structured study outputs
- generate personalized lecture notes or study plans
- identify likely key topics from repeated course evidence (not predictions or guarantees)
- update notes after follow-up questions so that insights persist

# Core References

Read the following core-layer files as needed. Do not duplicate their contents here.

| File | Purpose |
|---|---|
| `../../core/capability_spec.md` | Supported inputs, outputs, key capabilities, non-goals, and degradation strategies |
| `../../core/workflow_core.md` | 13-step platform-independent processing flow with data-flow diagram |
| `../../core/output_templates.md` | 8 output templates with required fields and quality checks |
| `../../core/user_learning_style.md` | Rules for adapting tone, explanation order, and note structure |
| `../../core/evaluation_rules.md` | 10 quality checks to run before finalizing outputs |
| `../../core/safety_and_privacy.md` | Copyright, privacy, academic-integrity, and over-promise limits |

# How To Apply The Core Layer

1. **Understand scope**: Read `capability_spec.md` to check supported inputs/outputs and what CoursePilot does NOT do.
2. **Follow the flow**: Use `workflow_core.md` to process inputs step by step. Each step has clear inputs and outputs.
3. **Use templates**: Apply `output_templates.md` when generating structured outputs. Each template maps to specific workflow steps.
4. **Adapt style**: Apply `user_learning_style.md` rules to adjust tone and structure.
5. **Self-check**: Run `evaluation_rules.md` checks before finalizing.
6. **Enforce boundaries**: Apply `safety_and_privacy.md` to avoid copyright, privacy, and over-promise issues.

# Platform Notes

- This file is an adapter entry, not the full knowledge base.
- Keep outputs practical, revision-oriented, and course-grounded.
- Do not turn this file into a large dump of all CoursePilot rules.
- When in doubt, refer to the core layer files instead of guessing.

# Output Expectations

When possible, produce one or more of:

- knowledge map
- topic weighting
- personalized notes
- study plan
- practice items
- final crash pack

If the user asks follow-up questions, treat them as possible note updates rather than isolated chat. Apply the Note Update template from `output_templates.md`.
