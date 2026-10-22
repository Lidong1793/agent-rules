---
name: frontend-no-subtitles
description: 在用户要求删除前端副标题、精简界面文案，或明确要求无副标题的页面设计时使用。清理页面、区块、卡片和弹窗中的装饰性文字，保留功能所需的信息。普通前端开发请求无需自动套用此技能。
---

# 前端文案精简

## 适用范围

按用户指定的页面或组件执行。保留现有功能、交互和用户数据。用户明确要求的副标题或提供的文案优先保留。

## 文案规则

- 标题后直接呈现内容或操作。除非用户明确要求或提供文案，删除标题下方的介绍句、宣传标语、重复解释，以及标题上方的装饰性小字（eyebrow / kicker）。
- 通过布局、间距、字体层级和对齐建立视觉层次，避免为填充留白编写说明文案。
- 保留正常的分区标题、字段标签、必要的输入提示、错误提示和状态信息。
- 保留用户撰写的笔记正文，以及影响操作决策的计数、限制和说明。

## 执行与检查

1. 阅读目标组件及关联样式，识别标题周围的重复或装饰性文案。
2. 删除多余文案，调整因此产生的留白，清理本次修改造成的无用样式或变量。
3. 检查相关页面的标题区域，确认内容和操作仍然完整、易于辨认。
4. 根据改动范围检查桌面和窄屏布局，并运行项目要求的相关验证。

## 参考

- https://github.com/pbakaus/impeccable/blob/main/.vibe/skills/impeccable/reference/distill.md
- https://github.com/modelstudioai/OpenAgentPack/blob/main/apps/webui/.agents/skills/design-taste-frontend/SKILL.md
