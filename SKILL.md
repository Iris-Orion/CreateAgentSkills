---
name: coolpaper
description: "Academic paper reading and analysis workflow for research articles, PDFs, arXiv papers, DOI links, conference/journal papers, and pasted paper text. Use when the user asks to read, summarize, explain, review, or deeply understand a paper, especially in Chinese, and wants answers organized around seven questions: problem, related work, method, experiments, further exploration, main summary, and what to learn next."
---

# Coolpaper

## Purpose

Analyze academic papers with a consistent seven-question framework. Prefer Chinese output unless the user asks for another language.

## Workflow

1. Identify the paper source: local PDF/text, URL, DOI, arXiv ID, title, or pasted excerpt.
2. Read enough of the paper to ground the answer: abstract, introduction, related work, method, experiments, limitations, conclusion, and references when available.
3. Track evidence while reading. Cite section names, page numbers, figure/table/equation numbers, or quoted terms when they are available.
4. Distinguish clearly between:
   - claims explicitly made by the paper,
   - reasonable inference from the paper,
   - external/contextual knowledge,
   - missing information.
5. If the paper text is incomplete, say which parts are unavailable and answer only to the supported depth.

## Seven Questions

Answer using these headings and order:

### Q1: 这篇论文试图解决什么问题？

State the research problem, why it matters, the gap in existing work, and the paper's target setting. Avoid reducing this to the paper title.

### Q2: 有哪些相关研究？

Group related work by research direction or method family. Name representative papers, models, systems, datasets, or theories when the paper provides them. Explain how the current paper differs from or builds on them.

### Q3: 论文如何解决这个问题？

Explain the core idea, method pipeline, model/system design, algorithm, assumptions, inputs/outputs, and main technical contribution. Use formulas or pseudocode only when they clarify the method.

### Q4: 论文做了哪些实验？

Summarize datasets, tasks, baselines, metrics, implementation details, ablations, robustness checks, user studies, or theoretical evaluations. Include main results and what each experiment is meant to prove. If there are no experiments, state what form of evidence the paper uses instead.

### Q5: 有什么可以进一步探索的点？

List concrete future work and open questions. Prefer points grounded in the paper's limitations, assumptions, error cases, missing ablations, scalability, generalization, reproducibility, application settings, or theoretical gaps.

### Q6: 总结一下论文的主要内容

Give a compact synthesis of the paper's motivation, method, evidence, and takeaway. This should be understandable to a technically literate reader who has not read the paper.

### Q7: 想要进一步了解论文

Provide a learning path for the user:

- prerequisite concepts to review,
- key sections/figures/tables/equations to reread,
- important references from the paper,
- suggested follow-up papers, datasets, codebases, or search terms,
- questions to ask when reproducing or extending the work.

## Output Style

- Use clear Chinese by default.
- Prefer concise paragraphs and short bullet lists.
- Keep technical names in their standard English form when translation would reduce precision.
- Include a short "证据与不确定性" note when any answer depends on inference or incomplete paper access.
- Do not invent experiments, baselines, citations, code availability, or limitations that are not supported.
