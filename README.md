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

## 安装

推荐安装到 Codex 的 skills 目录：

```powershell
cd $env:USERPROFILE\.codex\skills
git clone https://github.com/Iris-Orion/CreateAgentSkills.git coolpaper
```

安装后目录结构应类似：

```text
%USERPROFILE%\.codex\skills\coolpaper
├── SKILL.md
├── README.md
└── agents
    └── openai.yaml
```

如果你已经把仓库克隆到了其他位置，也可以把整个 `coolpaper` 目录复制到：

```text
%USERPROFILE%\.codex\skills\coolpaper
```

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
