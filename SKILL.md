---
name: coolpaper
description: "Academic paper reading and analysis workflow for research articles, PDFs, arXiv papers, DOI links, conference/journal papers, pasted paper text, and literature surveys. Use when the user asks to read, summarize, explain, triage, critique, review, compare, reproduce, present, or deeply understand a paper, especially in Chinese, combining S. Keshav's three-pass reading method with a seven-question framework: problem, related work, method, experiments, further exploration, main summary, and what to learn next."
---

# Coolpaper

## Purpose

Analyze academic papers with a two-layer workflow:

1. Use S. Keshav's three-pass method to choose the right reading depth.
2. Use the Q1-Q7 framework to produce a clear Chinese explanation unless the user asks for another language.

Do not default to maximum-detail reading. Match the depth to the user's goal and the available paper material.

## Workflow

1. Identify the user's purpose: quick triage, class presentation, paper review, reproduction, research planning, literature survey, writing support, method comparison, or general understanding.
2. Identify the paper source: local PDF/text, URL, DOI, arXiv ID, title, abstract, citation list, related-work section, or pasted excerpt.
3. State the available evidence. If the source is incomplete, say which sections or excerpts the analysis is based on.
4. Choose a reading pass:
   - First pass: quick relevance and quality triage.
   - Second pass: normal paper understanding and Q1-Q7 analysis.
   - Third pass: reviewer-level critique, reproduction planning, teaching, extension, or serious research planning.
5. Read enough to support the selected pass. Prefer abstract, introduction, headings, figures, tables, method, experiments, limitations, conclusion, and references.
6. Track evidence while reading. Cite section names, page numbers, figure/table/equation numbers, or quoted terms when available.
7. In the response, state the completed pass and what information would be needed for the next pass.

Distinguish clearly between:

- claims explicitly made by the paper,
- reasonable inference from the paper,
- external/contextual knowledge,
- missing information.

## First Pass: Triage

Use first pass when the user wants a quick read, when many papers must be filtered, or when only title/abstract/introduction is available.

Read:

- Title, abstract, introduction, headings, conclusion.
- References, looking for familiar authors, canonical papers, repeated topics, and important venues.

Produce the five Cs:

- Category: paper type, such as system design, algorithm, theory, empirical study, benchmark, survey, or position paper.
- Context: fields, assumptions, systems, theories, datasets, or related works it connects to.
- Correctness: whether the main assumptions and setup look plausible from the available material.
- Contributions: the authors' claimed main contributions.
- Clarity: whether the paper appears clearly structured and readable.

End with a reading decision:

- Stop: irrelevant, weak, or outside the current objective.
- Read background first: relevant but prerequisite concepts are missing.
- Continue to second pass: relevant and worth content-level reading.
- Keep as low-priority related work: useful later but not central now.

## Second Pass: Q1-Q7 Reading

Use second pass as the default for a single important paper. Understand the main content and evidence while skipping low-level proof details, derivations, and implementation minutiae unless they are central to the user's goal.

Inspect:

- Problem statement, motivation, related work, method, experiments, results, limitations, and conclusion.
- Figures, tables, algorithms, formulas, datasets, baselines, metrics, and evaluation curves.
- Graph quality: axis labels, baselines, uncertainty/error bars, statistical significance, and whether results support claims.
- References, terms, datasets, systems, or theories that need follow-up reading.

Answer using these headings and order:

### Q1: 这篇论文试图解决什么问题？

State the research problem, why it matters, the gap in existing work, and the paper's target setting. Avoid reducing this to the paper title.

### Q2: 有哪些相关研究？

Group related work by research direction or method family. Name representative papers, models, systems, datasets, venues, or theories when the paper provides them. Explain how the current paper differs from or builds on them.

### Q3: 论文如何解决这个问题？

Explain the core idea, method pipeline, model/system design, algorithm, assumptions, inputs/outputs, and main technical contribution. Use formulas or pseudocode only when they clarify the method.

### Q4: 论文做了哪些实验？

Summarize datasets, tasks, baselines, metrics, implementation details, ablations, robustness checks, user studies, theoretical evaluations, and graph/table evidence. Include main results and what each experiment is meant to prove. If there are no experiments, state what form of evidence the paper uses instead.

### Q5: 有什么可以进一步探索的点？

List concrete future work and open questions grounded in limitations, hidden assumptions, error cases, missing ablations, scalability, generalization, reproducibility, application settings, or theoretical gaps.

### Q6: 总结一下论文的主要内容

Give a compact synthesis of the paper's motivation, method, evidence, and takeaway. This should be understandable to a technically literate reader who has not read the paper.

### Q7: 想要进一步了解论文

Provide a learning path:

- prerequisite concepts to review,
- key sections/figures/tables/equations to reread,
- important references from the paper,
- suggested follow-up papers, datasets, codebases, venues, authors, or search terms,
- questions to ask when reproducing or extending the work.

## Third Pass: Reviewer-Level Reading

Use third pass for peer review, reproduction, teaching, method transfer, serious literature surveys, research planning, or when the user asks for weaknesses, assumptions, or future work.

Reconstruct and challenge:

- Rebuild the paper's structure from memory: problem definition, assumptions, method, experiment design, evidence chain, and conclusion.
- Virtually re-implement the paper by making the same assumptions and recreating the work at the level appropriate to the user's goal.
- Compare the reconstructed version with the actual paper to identify innovations, hidden assumptions, and weaknesses.
- Challenge definitions, assumptions, baselines, evaluation metrics, statistical claims, data choices, system constraints, and external validity.
- Check for missing related work, unsupported claims, unclear engineering conditions, data bias, and limits of applicability.
- Record methods, writing patterns, experiment designs, and future-work ideas that transfer to the user's own project.

When third pass is requested, still keep Q1-Q7 when useful, but add:

- Strengths and weaknesses tied to concrete evidence.
- Hidden assumptions and threats to validity.
- Reproduction or validation plan: required data, code, metrics, baselines, compute, and risks.
- Reusable value for the user's research, implementation, literature survey, or writing.

## Literature Survey

When the user is entering a new area or asks for a literature survey, use the three-pass method to organize search and filtering.

1. Use well-chosen keywords to find or evaluate 3-5 recent papers, then do a first pass on each.
2. Read related-work sections to find surveys, shared citations, repeated author names, and recurring venues.
3. Treat shared citations and recent work from recurring authors as candidate key papers.
4. Identify top conferences, journals, or venues in the field, then scan recent proceedings with first-pass reading.
5. Do a second pass on the strongest papers. If several papers depend on the same earlier work, add that work to the reading list.
6. Iterate until main directions, key authors, major methods, disagreements, and open problems become stable.

Survey output should include:

- scope and search entry points,
- paper clusters or themes,
- representative papers and why they matter,
- key authors, groups, venues, and timeline,
- method families and relationships,
- consensus, disagreements, gaps, and open problems,
- next reading list with priorities.

## Output Style

- Use clear Chinese by default.
- Start with `Completed pass: First/Second/Third pass` when the pass choice matters.
- Prefer concise paragraphs and short bullet lists.
- Keep technical names in their standard English form when translation would reduce precision.
- Include a short "证据与不确定性" note when any answer depends on inference or incomplete paper access.
- Do not invent experiments, baselines, citations, code availability, graph evidence, or limitations that are not supported.
