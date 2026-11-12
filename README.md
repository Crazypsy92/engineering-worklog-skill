# Engineering Worklog & Daily Review Skills｜研发报工与每日复盘

本仓库包含**两个独立的 AI Skills**：`engineering-worklog` 负责企业早晚报工，`daily-review` 负责全天**工作、学习、个人生活与杂项**的整理与复盘。均以中文输出，适用于支持 `SKILL.md` 的助手。

## 两个 Skill 的定位

| Skill | 什么时候用 | 输出侧重点 |
| --- | --- | --- |
| `engineering-worklog`（根目录 `SKILL.md`） | 早上计划、下班报工、加班报工 | 任务定义、定性目标、计划/实际数量、工时、输出物、每项完成百分比 |
| `daily-review`（`skills/daily-review/SKILL.md`） | 一天结束、整理昨日聊天与日志、Obsidian 日记、个人复盘 | 今日事宜、工作与学习、生活、问题与处理、实际结果、后续、个人思考 |

**区分原则：** 企业报工不自动包含私人事项；全天复盘不强制套用 8H 或逐条完成100%。尤其要区分“提出任务/讨论方案”和“已实际执行/验收通过”。

## 研发报工工作流

| 模式 | 使用时间 | 输出字段 |
| --- | --- | --- |
| 早间计划 | 上班时 | 任务详情（定义）、计划目标（定性）、计划数量（定量）、单位、计划工时H、计划输出物 |
| 晚间结果 | 下班前 | 完成结果、实际数量（定量）、实际工时H、实际输出物 |
| 完整日报 | 整理日报 | 以上10个字段，未知晚间信息保留待填写 |
| 简短加班 | 加班申请/补报 | 按需求精简，突出技术任务和产物，不自动设为8H |

默认普通白班**计划工时8H、单位“项”**。实际工时须由用户或日志确认；完成度、通过率和产物均不能编造。

## 核心写作原则

- 任务详情说明“对什么做什么”；计划目标说明“做到什么程度”；计划输出物说明“有什么东西可检查”。
- 晚间与早间逐项映射；如3个计划工作包产生4条结果，不能简单把数量改成4。
- 不混淆“完成测试”与“功能验收通过”；必须披露限制与遗留问题。
- 晚间完成结果逐项标注独立完成百分比（如“完成度100%”），不能只给整段总百分比；百分比表示计划执行进度，不等同测试通过率或最终验收率。
- 尽量符合企业报工表单的字符上限，输出短、实、可复制。

## 仓库结构

```text
.
├── SKILL.md
├── README.md
├── assets/
│   └── daily-record-template.md
├── examples/
│   └── worklog-example.md
└── skills/
    └── daily-review/
        ├── SKILL.md
        ├── assets/
        │   └── daily-review-template.md
        └── examples/
            └── sample-day.md
```

## 安装（Codex）

用户级安装（WSL/Linux）：

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/Crazypsy92/engineering-worklog-skill.git ~/.agents/skills/engineering-worklog
```

项目级安装：

```bash
mkdir -p .agents/skills
git clone https://github.com/Crazypsy92/engineering-worklog-skill.git .agents/skills/engineering-worklog
```

**安装第二个 Skill（WSL/Linux）：** 上述 clone 之后另执行：

```bash
ln -s "$HOME/.agents/skills/engineering-worklog/skills/daily-review" "$HOME/.agents/skills/daily-review"
```

这样两个 Skill 都是 `~/.agents/skills/` 的直属目录，能够被按约定扫描该目录的 Agent 识别。若已存在 `daily-review` 文件/目录，先检查再处理，不要盲目覆盖；若运行环境不跟随符号链接，可改用复制目录。更新时在克隆目录执行 `git pull`，符号链接指向的内容会同步更新。

如果目标目录已经存在，请先备份或更新本地修改。各版本 Codex 的 Skill 根路径可能不同，请以本机版本为准。

## 触发示例

早上：

```text
使用 engineering-worklog 帮我写今天的早间报工。计划8H。
今天做：通信流程检查、正常与异常报文测试、整理问题清单。
```

晚上：

```text
使用 engineering-worklog 帮我填写晚间报工，继承今天早上的3个工作包。
已完成：完成通信流程检查；执行12次测试，其中10次通过、2次发现异常；整理问题清单；实际工作8H。
只输出完成结果、实际数量、实际工时、实际输出物。
```

精简加班：

```text
使用 engineering-worklog，将今晚加班任务写成一行，领导一眼能看明白。
```

## 每日复盘示例（含工作与个人）

```text
使用 daily-review，总结2026/11/11星期三的全部聊天和原始记录。
分别整理工作研发、论文和技术学习、个人阅读/软件体验、问题与处理、未完成与明日重点。
注意：我的很多话是交给Codex的任务，只有实际运行结果才能写成已完成。
```

可以参考 [每日复盘模板](skills/daily-review/assets/daily-review-template.md) 和 [虚构示例](skills/daily-review/examples/sample-day.md)。**已按用户指定的 Obsidian 六章日志模板更新**：①今日事宜（工作事项/个人安排），②今日工作记录（项目→模块），③AI对话与问题记录（工作/个人），④个人记录与随手记，⑤日终回顾，⑥关联资料。个人工程事项只列在1.2个人安排和3.2个人对话中，**不得写进第二章工作记录**；今日事宜置顶，日终回顾在关联资料前。

**隐私约束：** 本仓库是 Public；只发布通用指令、空白模板和匿名虚构示例。真实个人日记、工作数据、照片、公司资料不自动上传 GitHub。

## 仓库信息

- Repository：`Crazypsy92/engineering-worklog-skill`
- Description：`A reusable AI skill for structured daily work reporting, covering task planning, quantitative targets, working hours, deliverables, completion results, and progress tracking.`
- Skill names：`engineering-worklog`、`daily-review`

> 仓库名、安装命令和项目索引链接保持一致。
