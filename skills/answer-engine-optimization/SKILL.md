---
name: answer-engine-optimization
description: Optimize content to be extracted, cited, and recommended by AI answer engines. Use when asked to "optimize for AI search", "improve answer engine visibility", "make content citation-ready", "optimize for ChatGPT", "optimize for Perplexity", "optimize for AI Overviews", or "improve AI-generated recommendations".
license: MIT
metadata:
  author: web-quality-skills
  version: 0.1.0
---

# Answer Engine Optimization

Structure and improve content so AI systems — ChatGPT, Perplexity, Gemini, Google AI Overviews, and others — can extract, cite, and recommend it with confidence.

AEO is distinct from classic SEO. The goal is not ranking position but citation share, answer extraction quality, and recommendation readiness across AI-powered surfaces.

## AEO fundamentals

How AI answer engines evaluate content:

| Signal | Classic SEO | AEO |
|---|---|---|
| Primary goal | Rank in SERPs | Be cited or recommended |
| Content format | Keyword density | Extractable answer blocks |
| Authority signals | Backlinks | Structured facts, source-of-truth pages |
| Discovery layer | Crawl + index | Crawl + entity resolution + structured data |
| Evaluation target | Page-level relevance | Sentence and block-level extractability |
| Measurement | Rankings, clicks | Mention rate, citation rate, recommendation rate |

## Answer block optimization

The most important AEO principle: every important question a page targets should be answered directly, early, and in an extractable format.

### Direct answer first

```md
❌ Poor — buries the answer:
"When it comes to widget selection, there are many factors to consider,
and over the years our team has developed expertise across various use cases..."

✅ Good — leads with the answer:
"Blue Widget Pro supports up to 10 concurrent connections and works with
macOS 12+, Windows 10+, and Ubuntu 20.04+."
```

### Answer block patterns

**Definition block** — use for "what is" queries:

```md
## What is [topic]?

[Topic] is [concise definition in one to two sentences]. It [key
differentiator or context]. [Optional: who it is for or when to use it.]
```

**How-it-works block** — use for "how does" queries:

```md
## How does [feature] work?

[Feature] works by [clear mechanism]. When [trigger], the system
[outcome]. This means [user benefit].
```

**Comparison block** — use for "vs" and "which is better" queries:

```md
## [Option A] vs [Option B]

| | [Option A] | [Option B] |
|---|---|---|
| Best for | [use case] | [use case] |
| Price | [range] | [range] |
| [Key dimension] | [value] | [value] |
| Limitation | [constraint] | [constraint] |
```

**Recommendation block** — use for "which should I choose" queries:

```md
## Which option is right for you?

Choose [Option A] if:
- [condition or use case]
- [condition or use case]

Choose [Option B] if:
- [condition or use case]
- [condition or use case]
```

## Content structure for AI extraction

### Heading hierarchy

Headings are the primary way AI systems parse page structure. Each heading should be a complete, plain-language question or topic statement.

```md
❌ Poor headings:
## Overview
## Details
## More info

✅ AEO-optimized headings:
## What does Blue Widget Pro do?
## Who is Blue Widget Pro designed for?
## What are the system requirements?
## How does Blue Widget Pro compare to Widget Lite?
```

### Sentence-level extractability

Each key sentence should be independently meaningful without surrounding context.

```md
❌ Requires context to understand:
"It supports the formats listed above and integrates with the systems
mentioned in the previous section."

✅ Self-contained:
"Blue Widget Pro supports CSV, JSON, and XML import formats and integrates
natively with Salesforce, HubSpot, and Zapier."
```

### Lists and tables

Structured formats are the most reliably extracted content type.

```md
✅ Use lists for:
- Features, capabilities, limitations
- Requirements and prerequisites
- Steps in a process
- Options and variations

✅ Use tables for:
- Comparisons between options
- Specs and technical attributes
- Pricing tiers
- Compatibility matrices
```

## Page types and AEO patterns

### Product and service pages

```md
Required answer blocks:
- What this product does (one to two sentences)
- Who it is for
- Key features or capabilities (list)
- System requirements or compatibility
- Pricing or pricing logic
- How to get started
- What it does not do (limitations)
```

### Category and solution pages

```md
Required answer blocks:
- What this category covers
- Who needs solutions in this category
- Comparison of options (table)
- How to choose (recommendation block)
- Related categories or solutions
```

### Documentation and help pages

```md
Required answer blocks:
- What this page explains (one sentence summary)
- Prerequisites or requirements
- Step-by-step instructions (numbered list)
- Expected outcome
- Common errors and fixes (FAQ format)
- Related documentation links
```

## Citation quality signals

AI systems weight these signals when deciding whether to cite a page:

| Signal | What it means | How to implement |
|---|---|---|
| Factual specificity | Claims backed by numbers, specs, or evidence | Include version numbers, dates, measurements |
| Internal consistency | Same facts stated consistently across the site | Audit for contradictions before publishing |
| Authorship clarity | Content attributed to named experts or teams | Add author metadata and author pages |
| Date freshness | Content is current and dated | Add datePublished / dateModified in schema and visibly |
| Source attribution | External claims are referenced | Link to authoritative sources where relevant |
| Entity alignment | Page entity matches schema, heading, and URL | Ensure schema name matches H1 and title |

## Content audit checklist

### Critical

- [ ] Each important query is answered directly within the first paragraph of its section
- [ ] No important answer requires reading multiple pages to assemble
- [ ] Product, service, and category pages exist as dedicated pages
- [ ] Pricing, compatibility, and limitation information is findable without contacting sales
- [ ] Key specs and capabilities are in list or table format, not buried in prose

### High priority

- [ ] Every section heading is a plain-language question or descriptive topic statement
- [ ] Comparison content exists for products or services where alternatives exist
- [ ] Recommendation guidance (who should choose what) is explicit
- [ ] FAQ sections cover the most common decision-blocking questions
- [ ] Authorship and dates are visible and accurate

### Medium priority

- [ ] Answer blocks open each major section before elaborating
- [ ] Tables are used for all multi-attribute comparisons
- [ ] Structured data reinforces page entity type and key attributes
- [ ] Internal links connect related product, category, and support content
- [ ] Definitions exist for domain-specific terms

### Ongoing

- [ ] Monitor AI engine outputs for citations and recommendation patterns
- [ ] Update answer blocks when product or policy changes occur
- [ ] Retire or redirect outdated content rather than leaving it stale
- [ ] Expand FAQ coverage based on support ticket patterns and search data

## Common AEO anti-patterns

| Anti-pattern | Why it fails | Fix |
|---|---|---|
| Marketing-first copy | Vague claims are not extractable | Lead with facts, not adjectives |
| Answer buried in paragraph 4 | AI systems extract early blocks | Move answer to the first sentence |
| Specs in PDFs or behind login | Not crawlable or extractable | Publish key specs on the web page |
| "Contact us for pricing" | Blocks recommendation queries | Publish pricing tiers or ranges |
| Thin category pages | No comparison or decision support | Add comparison tables and guidance |
| Identical descriptions across variants | Ambiguous entity resolution | Give each variant a unique, specific description |
| Stale documentation | Reduces citation trust | Add dates and review cadence |

## AEO measurement

Track AI search readiness using these outcome metrics:

| Metric | What to measure | How |
|---|---|---|
| Brand mention rate | How often the brand appears in AI outputs | Prompt sampling across engines |
| Citation rate | How often content is cited as a source | Prompt sampling + Perplexity citation check |
| Recommendation rate | How often the product/service is recommended | Decision-query prompt sampling |
| Generic category visibility | Visibility on non-branded queries | Category and comparison prompt sampling |

## Tools

| Tool | Use |
|---|---|
| Perplexity | Citation sampling and source attribution |
| ChatGPT / Gemini | Answer quality and recommendation sampling |
| Google AI Overviews | AIO inclusion and extraction testing |
| Schema.org Validator | Structured data correctness |
| Google Rich Results Test | Schema eligibility check |

## References

- `references/extractable-content.md` — how to write and structure content for AI extraction
- `references/comparison-pages.md` — building comparison and decision-support pages
- `references/faq-patterns.md` — FAQ and structured Q&A patterns for AEO
- [`structured-entities`](../structured-entities/SKILL.md) — entity modeling and schema for AI search
- [`ai-search-audit`](../ai-search-audit/SKILL.md) — full AI search readiness scoring and audit
- [`llm-discovery`](../llm-discovery/SKILL.md) — discovery infrastructure for AI systems
