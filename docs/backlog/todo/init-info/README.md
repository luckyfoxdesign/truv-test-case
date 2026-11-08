---
type: research
status: done
language: en
---

# Truv case study source documents

English is the primary presentation language. Each document has an English and Russian edition with the same filename:

| Document | English | Russian |
|---|---|---|
| Original assignment | [Case brief](en/brief.md) | [Исходное задание](ru/brief.md) |
| Part 1 | [Funnel analysis](en/funnel-analysis.md) | [Анализ воронки](ru/funnel-analysis.md) |
| Part 2 | [Financial assumptions](en/financial-assumptions.md) | [Финансовые допущения](ru/financial-assumptions.md) |
| Part 3 | [Recommendations](en/recommendations.md) | [Рекомендации](ru/recommendations.md) |
| Part 4 | [Hypotheses](en/hypotheses.md) | [Гипотезы](ru/hypotheses.md) |
| Supporting reference | [Original Dashboard behavior](en/verification-behavior.md) | [Исходное поведение Dashboard](ru/verification-behavior.md) |

The original assignment was supplied in English; the research and behavior reference were supplied in Russian. Original documents were moved into their language folders and given stable filenames. Their wording, section order and figures are preserved; trailing ASCII whitespace is normalized and frontmatter records their original filenames. Translated editions link to their source through `translation_of`.

The translations retain all figures, calculations, event names, limitations, and experiment boundaries. They do not claim measured UX improvements or actual lost revenue. The source hypotheses remain historical research notes; subsequent requested prototype changes, such as the fixed EXP-04 progress panel, are explained in the prototype.

After editing a language edition, update its counterpart as needed. This repository publishes only the research documents and their index. Website sources, synchronization tools, workspace instructions and deployment configuration are maintained separately.
