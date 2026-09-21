# Work Self Skills

把自己的工作判断和表达习惯沉淀成可复用、可修改的 skills。先从 `report` 开始，后续每个 skill 在 `skills/` 下拥有独立目录。

## 当前状态

`report` v0.5：已吸收 5 条历史素材和 3 条用户实战修订，维护 9 条主规则。新增向熟悉同事索取资料的局部经验：说明背景与材料用途，先列信息需求，再列已掌握且希望深化的信息；按交付目的组织问题，并保留假设与已确认事实的区别。原始材料只保存在本地，skill 包含必要的脱敏证据；尚无独立的个人风格相似度或可直接发送比例数据。

这里的“蒸馏”指从案例与反馈中提炼显式规则和精选例子，不涉及训练或修改模型权重。规则必须能追溯到样本或用户的明确说明。

## 开始使用

1. 先阅读 [素材提交指南](docs/intake-guide.md)，直接在聊天里贴原文也可以。无需预先制作数据集。
2. 提交几条有代表性的样本，参考 [样本模板](templates/report-sample.md)。助手整理标签、提取候选规则，并区分你的原话与它的推断。
3. 用 [新汇报输入模板](templates/report-request.md) 给出一个新情境，生成初稿后按 [反馈模板](templates/report-feedback.md) 修改。修改会成为下一轮校准依据。
4. 用未参与规则提炼的案例检查效果，方法见 [评估说明](evals/report/README.md)。

可以从 6–10 条开始，其中留约 2 条作后续对照。这只是方便启动的建议，不是准确率保证或硬性门槛；先发 1 条也能开始。

## 目录

```text
skills/report/
  SKILL.md                    使用入口：生成、整理样本、校准
  agents/openai.yaml          技能名称与默认提示
  references/profile.md      个人规则及证据登记，当前待校准
  references/evidence.md     首批样本的必要脱敏摘录与解释
  references/scenarios.md    对象和汇报情境的通用兜底
  references/calibration.md  如何从样本更新规则
templates/                   样本、写作请求、改稿反馈
docs/intake-guide.md          素材和标签说明
evals/report/                评估方法与明确标注的合成案例
data-local/                  本地原始样本与保留测试，Git 忽略
```

## 加载技能

实际入口是 `skills/report/SKILL.md`，不是一个孤立的 `report.skill` 文本文件。技能采用标准的目录结构；支持显式调用，也允许按任务内容自动匹配。参见 [OpenAI 官方技能说明](https://learn.chatgpt.com/docs/build-skills)。

在未安装时，可以直接告诉助手：“读取本仓库 `skills/report/SKILL.md`，按 report skill 工作。”

需要本地发现时，将整个 `skills/report` 目录放到当前宿主的个人 skills 目录，或项目的 `.agents/skills/report`；保留 `references/` 和 `agents/`。当前桌面环境已有个人 skills 位于 `~/.codex/skills`，其他安装方式请以宿主实际位置为准。GitHub 存储、拉取更新和本地安装是独立步骤，不会自动同步。已存在同名技能时先比较，避免直接覆盖。

调用示例：

> 使用 $report。对象是直属老板，场景是阶段进度同步，希望他决定是否缩小本周范围。以下是已确认事实和仍不确定的信息……

## 数据边界

仓库设为私有；原始工作材料仍默认保存在被忽略的 `data-local/` 下。模板、方法和合成测试可以入库。真实样本只在完成脱敏、明确该批内容可进入此私有仓库后，才作为精选案例加入 skill。

脱敏时用稳定代号保留关系、时序和因果，不必保留真实姓名、客户信息、内部链接或精确商业数据。个人规则本身也可能包含内部信息，提交前同样检查。

`.gitignore` 只防止未跟踪文件被意外添加，不会清除已经提交的历史，也不是加密或访问控制。

## 后续增加其他 skills

新增 `skills/<name>/SKILL.md`，在同一目录维护它实际需要的参考材料；沿用“样本 → 有依据的规则 → 未见情境评估 → 用户改稿”的方式。只有经多个 skill 验证确实通用的偏好才提取共享，避免把汇报语气套到所有工作活动上。
