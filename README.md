# Engineering Worklog Skill｜研发报工助手

把研发工作的技术任务、仿真测试、数据分析和阶段成果转成**企业报工系统可直接粘贴的中文字段**。适用于 Codex 等支持 Agent Skills（`SKILL.md`）的助手。

## 工作流

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
└── examples/
    └── worklog-example.md
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

如果目标目录已经存在，请先备份或更新现有目录，不要直接覆盖本地修改。若使用的 Codex 版本采用其他 Skill 根目录，请以本机 Skill 发现路径为准；关键是 Skill 文件夹内包含 `SKILL.md`。

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

## 仓库信息

- Repository：`Crazypsy92/engineering-worklog-skill`
- Description：`A reusable AI skill for structured daily work reporting, covering task planning, quantitative targets, working hours, deliverables, completion results, and progress tracking.`
- Skill name：`engineering-worklog`

> 仓库名、安装命令和项目索引链接保持一致。
