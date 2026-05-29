---
name: headline-template-writer
description: Generate platform-ready Chinese headlines from any event, news item, trend, article idea, product update, or social topic by selecting reusable headline templates, adapting the angle to the audience and platform, and avoiding clickbait, unsupported claims, sensitive framing, or unsafe factual leaps. Use when the user asks for 标题, 爆款标题, 头条标题, 改写标题, 起标题, 选题标题, headline variants, or asks to apply a title library/template to an event.
metadata:
  short-description: 用标题模板把事件改写成可用标题
---

# Headline Template Writer

Use this skill to turn any event or topic into headline options. It is not limited to social news. It can handle sports, entertainment, lifestyle, health, policy, business, product, education, workplace, local events, or creator topics.

## Workflow

1. Identify the topic type: social/life, sports, entertainment, health, finance/business, tech/product, education, workplace, local, or other.
2. Identify the audience and platform if given. If not given, default to Chinese information-feed users and clear, direct wording.
3. Do a risk check:
   - Avoid unsupported claims, diagnosis, guilt assignment, conspiracy, ethnic/regional attacks, and fabricated details.
   - For health, legal, finance, policy, or fast-changing factual topics, say when source verification is needed before publishing.
   - If the user asks for "today/latest/current" facts and no source is provided, verify current facts before treating them as true.
4. Pick 3-6 suitable patterns from `references/title_patterns.md`.
5. When the user asks to "调用标题库", "参考爆文库", "按之前爆文写", or wants examples, also read `references/raw_title_bank.md` and use the raw titles as style/structure references.
6. Generate titles that preserve the factual core, change the angle, and make the reader benefit clear.
7. If asked for many titles, group by pattern. Otherwise return a concise list.

## Output Rules

- Default count: 20 titles unless the user gives another number.
- Keep Chinese titles concise, usually 18-32 Chinese characters when possible.
- Mark each title's pattern when useful or requested.
- Do not write pure news bulletin headlines unless the user asks.
- Prefer "ordinary reader benefit" angles: what changed, who is affected, what to watch, what mistake to avoid, why people argue.
- Never promise virality or present guesses as facts. Mark inference with "这是推断" or "可能是".

## Pattern Reference

Read `references/title_patterns.md` when generating titles or when the user asks for the template library.

Read `references/raw_title_bank.md` when the user asks to use the 爆文库/标题库, wants examples from prior data, or wants title patterns derived from the scraped Toutiao sample.
