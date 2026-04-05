# Extractable Content

A reference guide for writing and structuring content that AI answer engines can reliably identify, extract, and cite.

## What "extractable" means

Extractable content is content that:
- Can be lifted from its page context and remain accurate and self-sufficient
- Directly answers a question without requiring surrounding context
- Is structured in a way that signals its meaning without rendering

AI systems process content at the block and sentence level, not the page level. Write accordingly.

## The direct answer principle

Every page section that targets a user question should open with a direct answer before elaborating.

```md
❌ Indirect — answer is buried:
"There are many ways to approach API rate limiting. Teams often
struggle with this topic because the right approach depends on
infrastructure, traffic patterns, and business requirements.
One popular approach is token bucket limiting, which..."

✅ Direct — answer leads:
"Token bucket is the most widely used rate limiting algorithm for
REST APIs. It allows short bursts while enforcing a steady
average rate, making it suitable for most API use cases."
```

## Sentence-level self-sufficiency

Each key sentence must be independently accurate without antecedents or implicit context.

```md
❌ Requires context:
"It supports the three protocols listed above and runs on
the platforms mentioned in the requirements section."

✅ Self-contained:
"Acme Monitor supports REST, GraphQL, and gRPC and runs on
macOS 12+, Windows 10+, and Ubuntu 20.04+."
```

## Structural signals AI systems use

| Structure | Why it extracts well | When to use |
|---|---|---|
| Numbered lists | Clearly bounded, ordered items | Steps, processes, ranked options |
| Bullet lists | Clearly bounded, parallel items | Features, requirements, options |
| Definition blocks | Name + description pattern | Terms, concepts, entity introductions |
| Tables | Multi-attribute, multi-entity comparison | Specs, pricing, compatibility, comparisons |
| FAQ blocks | Explicit Q + A pairing | Common questions, decision support |
| Code blocks | Exact, unambiguous technical content | Syntax, commands, config examples |

## Writing patterns for extractable content

### The definition pattern

```md
[Name] is [type of thing] that [does what] for [who].
[Optional: key differentiator or context sentence.]

Example:
Blue Widget Pro is a hardware monitoring device that tracks
power usage and temperature for industrial equipment. It
supports up to 64 sensor inputs and runs without a cloud
dependency.
```

### The capability pattern

```md
[Name] supports:
- [capability one]
- [capability two]
- [capability three]

Example:
Acme API Monitor supports:
- HTTP/HTTPS, WebSocket, and TCP monitoring
- Alert routing via email, Slack, and PagerDuty
- Custom check intervals from 10 seconds to 24 hours
```

### The constraint pattern

Explicitly stating limitations increases citation trust.

```md
[Name] does not support:
- [limitation one]
- [limitation two]

Example:
Acme API Monitor does not support:
- On-premise deployment (cloud-only)
- Monitoring of private network endpoints without a gateway agent
- SNMP or legacy TCP/IP protocol monitoring
```

### The requirement pattern

```md
[Name] requires:
- [requirement]
- [requirement]

Compatible with:
| Platform | Minimum version |
|---|---|
| macOS | 12.0 (Monterey) |
| Windows | 10 (build 19041+) |
| Ubuntu | 20.04 LTS |
```

### The outcome pattern

```md
When [trigger or action], [outcome].

Example:
When a monitored endpoint returns three consecutive errors,
Acme Monitor sends an alert within 30 seconds and logs the
full response for debugging.
```

## Content that extracts poorly

| Pattern | Why it extracts poorly |
|---|---|
| Long paragraphs with no structure | AI systems cannot identify extract boundaries |
| Vague adjectives without specifics | "Powerful" and "easy" cannot be cited as facts |
| "Learn more" / "contact us" dead ends | Blocks resolution of key questions |
| PDFs with key specs | Not crawlable or parseable by most AI systems |
| JavaScript-rendered content | May not be fetched in text-based retrieval |
| Locked-in prose without headers | No structural anchors for extraction |
| Implicit comparisons | Too ambiguous to cite honestly |

## Factual density

High-factual-density writing extracts better.

```md
❌ Low density:
"Our product has been praised by many companies for its
impressive performance and flexibility in a variety of
demanding enterprise environments."

✅ High density:
"Acme Monitor is used by over 400 engineering teams. Its
average detection-to-alert latency is under 15 seconds at
p99 across monitored endpoints."
```

## Metadata that supports extraction

```html
<!-- Date signals -->
<time datetime="2026-03-01">March 2026</time>

<!-- Author signals -->
<span itemprop="author">Sarah Chen</span>

<!-- Canonical anchor -->
<link rel="canonical" href="https://acme.com/docs/rate-limiting" />
```

And in JSON-LD:

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "datePublished": "2026-03-01",
  "dateModified": "2026-04-01",
  "author": {
    "@type": "Person",
    "name": "Sarah Chen"
  }
}
```

## Checklist

- [ ] Every targeted question answered in the opening sentence of its section
- [ ] No key fact requires assembling across multiple pages
- [ ] Features, specs, and requirements in list or table format
- [ ] Product names identical in body copy, schema, and headings
- [ ] Limitations and constraints stated explicitly
- [ ] Dates visible and current on time-sensitive pages
- [ ] All important content accessible without JavaScript rendering
- [ ] No key information locked in PDFs or behind authentication
