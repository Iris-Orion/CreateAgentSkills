# Coolpaper

`coolpaper` 是一个用于阅读和分析学术论文的 Agent Skill，可被 Claude Code 和 Codex 使用。它融合了 S. Keshav 的三遍阅读法和 Q1-Q7 论文分析框架，适合分析 PDF、arXiv 论文、DOI 链接、会议/期刊论文、本地论文文本、相关工作章节、引用列表或用户粘贴的论文内容。

## 功能

- 识别论文要解决的核心问题
- 按阅读目标选择 first pass、second pass 或 third pass
- 用 five Cs 快速判断论文是否值得继续读
- 梳理相关研究和论文定位
- 解释方法、模型、系统或算法设计
- 总结实验设置、指标、基线和主要结果
- 检查图表、指标、假设、弱点和可复现性
- 提出进一步探索方向
- 用简洁中文总结论文主要内容
- 给出继续学习论文的路径
- 支持文献综述中的论文聚类、关键作者/会议期刊识别和下一步阅读清单

## 安装到 Claude Code

Claude Code 会从 `~/.claude/skills/<skill-name>/SKILL.md` 加载个人 skills，也可以从项目内 `.claude/skills/<skill-name>/SKILL.md` 加载项目级 skills。本仓库根目录已经是一个完整 skill，因此直接克隆到 `coolpaper` 目录即可。

### 个人级安装

Linux / macOS:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Iris-Orion/CreateAgentSkills.git ~/.claude/skills/coolpaper
```

Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills"
git clone https://github.com/Iris-Orion/CreateAgentSkills.git "$env:USERPROFILE\.claude\skills\coolpaper"
```

安装后启动或重启 Claude Code：

```bash
claude
```

在 Claude Code 中直接调用：

```text
/coolpaper analyze this paper: <论文链接、本地路径或正文>
```

也可以让 Claude Code 根据 `SKILL.md` 的 `description` 自动触发，但显式调用 `/coolpaper` 最稳定。

### 项目级安装

如果只想在某个项目中启用：

```bash
mkdir -p .claude/skills
git clone https://github.com/Iris-Orion/CreateAgentSkills.git .claude/skills/coolpaper
```

在该项目目录中运行 `claude` 后使用：

```text
/coolpaper 对这篇论文做 second pass，并围绕 Q1-Q7 分析：<论文路径或链接>
```

### Claude Code 目录结构

安装后应包含：

```text
~/.claude/skills/coolpaper
├── SKILL.md
├── README.md
└── agents
    └── openai.yaml
```

`SKILL.md` 是 Claude Code 需要的入口文件；`agents/openai.yaml` 是给其他支持该元数据的 Agent 使用的附加信息，Claude Code 可忽略。

## 安装到 Codex

推荐把仓库安装到 Codex 的 skills 目录，目录名保持为 `coolpaper`。

### Windows

```powershell
cd $env:USERPROFILE\.codex\skills
git clone https://github.com/Iris-Orion/CreateAgentSkills.git coolpaper
```

### Linux / macOS

```bash
mkdir -p ~/.codex/skills
cd ~/.codex/skills
git clone https://github.com/Iris-Orion/CreateAgentSkills.git coolpaper
```

### 使用 CODEX_HOME

如果你设置了 `CODEX_HOME`，把 skill 安装到该目录下的 `skills` 文件夹：

```bash
mkdir -p "$CODEX_HOME/skills"
cd "$CODEX_HOME/skills"
git clone https://github.com/Iris-Orion/CreateAgentSkills.git coolpaper
```

Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force "$env:CODEX_HOME\skills"
cd "$env:CODEX_HOME\skills"
git clone https://github.com/Iris-Orion/CreateAgentSkills.git coolpaper
```

安装后目录结构应类似：

```text
~/.codex/skills/coolpaper
├── SKILL.md
├── README.md
└── agents
    └── openai.yaml
```

Windows 默认路径对应为：

```text
%USERPROFILE%\.codex\skills\coolpaper
```

如果你已经把仓库克隆到了其他位置，也可以把整个 `coolpaper` 目录复制到上面的 skills 目录。

## 在其他 agent 软件中使用

不同 agent 软件的 skill / memory / custom instruction 机制不同，但 `coolpaper` 的核心逻辑都在 `SKILL.md` 中。通用接入方式是：

1. 把本仓库克隆到本地。
2. 在你的 agent 软件中打开或引用 `SKILL.md`。
3. 将 `SKILL.md` 的内容作为该 agent 的自定义指令、项目规则、system prompt、memory、knowledge file 或 reusable prompt。
4. 使用时明确要求 agent 按 `coolpaper` 的 Q1-Q7 框架分析论文。

通用提示词示例：

```text
Use the instructions in coolpaper/SKILL.md to analyze this academic paper through Q1-Q7: <论文链接、本地路径或正文>
```

中文提示词示例：

```text
请按照 coolpaper/SKILL.md 中的论文阅读框架，围绕 Q1-Q7 分析这篇论文：<论文链接、本地路径或正文>
```

如果某个 agent 支持项目级规则文件，可以把 `SKILL.md` 的正文复制到该软件推荐的规则文件中；如果它支持知识库上传，可以直接上传 `SKILL.md`。

## 使用

### Claude Code

在 Claude Code 中显式调用：

```text
/coolpaper analyze this paper: <论文链接或本地路径>
```

中文示例：

```text
/coolpaper 使用 Q1-Q7 阅读这篇论文：C:\papers\example.pdf
```

### Codex

在 Codex 中显式调用：

```text
Use $coolpaper to analyze this paper: <论文链接或本地路径>
```

中文示例：

```text
使用 $coolpaper 阅读这篇论文，并围绕 Q1-Q7 分析：C:\papers\example.pdf
```

快速筛选论文：

```text
使用 $coolpaper 对这篇论文做 first pass，判断是否值得继续精读：<论文链接或摘要>
```

复现或审稿级阅读：

```text
使用 $coolpaper 对这篇论文做 third pass，重点分析假设、弱点、复现计划和可扩展方向：<论文路径>
```

文献综述：

```text
使用 $coolpaper 帮我围绕 <研究主题> 做文献综述，先聚类论文方向并给出下一步阅读清单。
```

也可以直接粘贴论文标题、摘要、arXiv 链接、DOI 或论文正文片段：

```text
使用 $coolpaper 分析 arXiv:2501.12345
```

## 输出框架

`coolpaper` 会先根据目标选择阅读深度：

- First pass: 快速判断论文类型、背景、可信度、贡献和清晰度。
- Second pass: 默认的内容级阅读，围绕 Q1-Q7 分析。
- Third pass: 审稿、复现、教学、拓展研究所需的深度阅读。

默认 Q1-Q7 输出框架：

1. Q1: 这篇论文试图解决什么问题？
2. Q2: 有哪些相关研究？
3. Q3: 论文如何解决这个问题？
4. Q4: 论文做了哪些实验？
5. Q5: 有什么可以进一步探索的点？
6. Q6: 总结一下论文的主要内容
7. Q7: 想要进一步了解论文

默认使用中文回答，并在信息不足时标注证据和不确定性，避免编造实验、引用、代码可用性或论文结论。
