# Coolpaper

`coolpaper` 是一个用于阅读和分析学术论文的 Codex skill。它会围绕七个固定问题组织输出，适合分析 PDF、arXiv 论文、DOI 链接、会议/期刊论文、本地论文文本或用户粘贴的论文内容。

## 功能

- 识别论文要解决的核心问题
- 梳理相关研究和论文定位
- 解释方法、模型、系统或算法设计
- 总结实验设置、指标、基线和主要结果
- 提出进一步探索方向
- 用简洁中文总结论文主要内容
- 给出继续学习论文的路径

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

在 Codex 中显式调用：

```text
Use $coolpaper to analyze this paper: <论文链接或本地路径>
```

中文示例：

```text
使用 $coolpaper 阅读这篇论文，并围绕 Q1-Q7 分析：C:\papers\example.pdf
```

也可以直接粘贴论文标题、摘要、arXiv 链接、DOI 或论文正文片段：

```text
使用 $coolpaper 分析 arXiv:2501.12345
```

## 输出框架

`coolpaper` 默认按以下七个问题输出：

1. Q1: 这篇论文试图解决什么问题？
2. Q2: 有哪些相关研究？
3. Q3: 论文如何解决这个问题？
4. Q4: 论文做了哪些实验？
5. Q5: 有什么可以进一步探索的点？
6. Q6: 总结一下论文的主要内容
7. Q7: 想要进一步了解论文

默认使用中文回答，并在信息不足时标注证据和不确定性，避免编造实验、引用、代码可用性或论文结论。
