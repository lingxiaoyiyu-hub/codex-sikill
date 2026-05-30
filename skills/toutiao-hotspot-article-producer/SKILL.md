---
name: toutiao-hotspot-article-producer
description: Headline and article production workflow for Toutiao hot topics. Use when the user wants a Toutiao/今日头条/头条号 agent to search today's热点, verify sources, generate topic options first, wait for the user's choice, then write the selected article using a style sample. Coordinates hotspot-topic-planner and headline-template-writer.
---

# Toutiao Hotspot Article Producer

## Goal

Run a two-stage Toutiao content workflow:

1. Search and verify current hotspots, then generate topic options.
2. After the user chooses one topic, write the full article.

Do not write the article during stage 1.

## Required Supporting Skills

Use these skills when available:

- `hotspot-topic-planner`: gather current hotspots, normalize sources, score topic value, and screen risk.
- `headline-template-writer`: turn verified hotspot facts into Toutiao-style topic titles using reusable title structures.

If a supporting skill is unavailable, continue manually with the same rules.

## Stage 1: Hotspot Verification And Topic Options

Trigger this stage when the user provides a hotspot, asks for today's hot topics, or asks for Toutiao topic ideas.

Steps:

1. Search current public sources or ingest the user's provided hotspot list.
2. Verify whether each hotspot is real, recent, and still active.
3. Prefer official notices, authoritative media, platform hot lists, party statements, and cross-platform reports.
4. Separate verified facts from interpretation.
5. Screen risk: privacy, minors, medical, legal, finance, disasters, active criminal cases, unverified accusations, political sensitivity, and identity-group attacks.
6. Use `headline-template-writer` to generate 3-5 topic options from suitable hotspots.
7. Each topic must include title, writing direction, core angle, title structure, source basis, and risk note.
8. Stop and ask the user to choose a topic.

Stage 1 output format:

```markdown
## 一、热点核查

热点名称：...

是否真实发生：是 / 否 / 未确认

是否仍为当天或近期热点：是 / 否 / 未确认

主要来源：

1. 来源名称：...
   链接：...
   关键信息：...

事实争议：无明显争议 / 存在争议：...

风险判断：低 / 中 / 高

风险点：...

## 二、选题推荐

### 选题 1

标题：...

写作方向：...

核心看点：...

标题结构：...

来源依据：...

风险提醒：...

## 三、最推荐选题

最推荐：选题 X

推荐理由：...

请你选择一个选题，我再进入文章写作阶段。
```

## Stage 2: Write The Selected Article

Trigger this stage only when the user explicitly chooses a topic, such as "写选题2" or names one selected title.

Steps:

1. Re-check the selected topic's key facts with current sources.
2. Analyze the user's style sample if provided. Keep this analysis internal unless the user asks to see it.
3. Write a 1500-2000 Chinese-character Toutiao article.
4. Use plain language, clear logic, and a discussion-friendly angle.
5. Do not invent facts, numbers, private details, motives, or psychological descriptions.
6. Mark inference with "这是推断" or "可能是".
7. Include sources at the end.

Stage 2 output format:

```markdown
## 标题

...

## 摘要

...

## 正文

...

## 事实来源

1. 来源名称：...
   链接：...
```

## Style Guidance

For Toutiao article writing:

- Start from a visible phenomenon or contradiction.
- Explain why ordinary readers should care.
- Break down background, key parties, and conflict.
- Explain causes and possible influence.
- End with a restrained judgment.

Avoid:

- Clickbait such as "震惊", "全网炸了", "彻底沸腾".
- Unsupported accusations.
- Rumors presented as facts.
- Copying other people's title or article structure.

## Source Rules

If a fact cannot be verified, write "未找到可靠来源".

If current heat cannot be confirmed, write "未确认仍为当天或近期热点".

For fast-changing facts, search current sources before answering.

## Final Checks

Before finishing:

- Stage 1 must not include the article body.
- Stage 2 must only run after the user chooses a topic.
- Topic options must include writing direction and risk note.
- Article facts must be source-backed.
- No unsupported data, people relationships, or conclusions.
