# FAQ Patterns

A reference guide for building FAQ and structured Q&A content that AI answer engines reliably extract, cite, and use in answer synthesis.

## Why FAQ content extracts well

FAQ blocks have the highest extraction rate of any content pattern because:
- The question provides the extraction anchor
- The answer is bounded and self-contained
- The Q&A format mirrors how answer engines compose outputs
- FAQPage schema creates machine-readable Q+A pairs

## FAQ placement strategy

| Page type | Where to add FAQ |
|---|---|
| Product pages | After features and specs |
| Category pages | After comparison tables |
| Pricing pages | After the pricing table |
| Documentation pages | After each major procedure |
| Comparison pages | After the recommendation block |
| Blog posts | At the end of the article |

## FAQ question types

Cover all five question types for complete AEO coverage:

| Type | Example | Why it matters |
|---|---|---|
| Definition | "What is [product]?" | Anchors entity recognition |
| Capability | "Does [product] support [feature]?" | Feeds feature queries |
| Comparison | "How does [product] compare to [X]?" | Feeds comparison queries |
| Decision | "Is [product] right for [use case]?" | Feeds recommendation queries |
| Troubleshooting | "Why is [thing] not working?" | Feeds support queries |

## Writing FAQ answers

### Answer length guide

| Query type | Ideal answer length |
|---|---|
| Definition | 1–3 sentences |
| Yes/No capability | 1 sentence + context |
| Comparison | 2–4 sentences or a short table |
| Decision/recommendation | 3–5 sentences with conditional guidance |
| Process/how-to | Numbered steps, 3–7 items |

### The yes/no + context pattern

Never answer with only "yes" or "no". Always add the useful context.

```md
❌ Too thin:
Q: Does Acme Monitor support GraphQL?
A: Yes.

✅ Useful:
Q: Does Acme Monitor support GraphQL?
A: Yes. Acme Monitor supports GraphQL monitoring via HTTP endpoint
checks and response body validation. It can assert on specific
fields in the response JSON and alert on unexpected values or
latency thresholds.
```

### The conditional recommendation pattern

```md
Q: Is Acme Monitor right for a small startup?

A: Yes, if you are running fewer than 20 endpoints and want a
quick setup without infrastructure overhead. Acme Monitor's free
tier covers up to 10 monitors with 1-minute check intervals.
For larger teams or more complex routing needs, consider upgrading
to the Pro plan or evaluating full-stack observability platforms.
```

### The comparison answer pattern

```md
Q: How does Acme Monitor compare to Pingdom?

A: Acme Monitor focuses on API-level monitoring — it validates
response bodies, headers, and latency for REST, GraphQL, and gRPC
endpoints. Pingdom focuses on uptime monitoring for web pages and
simple HTTP endpoints. Choose Acme Monitor for API teams and
Pingdom for website uptime use cases.
```

## FAQ HTML pattern

```html
<section class="faq">
  <h2>Frequently asked questions</h2>

  <details>
    <summary>What does Acme Monitor do?</summary>
    <p>
      Acme Monitor checks the availability, latency, and response
      correctness of REST, GraphQL, and gRPC APIs on a schedule
      you define. It sends alerts when checks fail and logs
      response data for debugging.
    </p>
  </details>

  <details>
    <summary>Does Acme Monitor support on-premise deployment?</summary>
    <p>
      No. Acme Monitor is a cloud-hosted service. For monitoring
      private network endpoints, a gateway agent is available on
      Pro and Enterprise plans.
    </p>
  </details>
</section>
```

## FAQPage schema

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What does Acme Monitor do?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Acme Monitor checks the availability, latency, and response correctness of REST, GraphQL, and gRPC APIs. It sends alerts when checks fail and logs response data for debugging."
      }
    },
    {
      "@type": "Question",
      "name": "Does Acme Monitor support on-premise deployment?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. Acme Monitor is a cloud-hosted service. A gateway agent is available for monitoring private network endpoints on Pro and Enterprise plans."
      }
    },
    {
      "@type": "Question",
      "name": "How does Acme Monitor compare to Pingdom?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Acme Monitor focuses on API-level monitoring including response body validation and GraphQL support. Pingdom focuses on website uptime monitoring. Choose Acme Monitor for API teams and Pingdom for website uptime use cases."
      }
    }
  ]
}
```

## Recommended FAQ coverage per page type

### Product page FAQ (minimum 5 questions)

```md
1. What does [product] do?
2. Who is [product] designed for?
3. What are [product]'s system requirements?
4. How does [product] compare to [main alternative]?
5. How much does [product] cost?
6. What does [product] not support?
7. How do I get started with [product]?
```

### Pricing page FAQ (minimum 4 questions)

```md
1. What is included in the free tier?
2. Can I switch plans later?
3. Is there a contract or commitment?
4. What payment methods are accepted?
5. What happens if I exceed my plan limits?
```

### Category page FAQ (minimum 4 questions)

```md
1. What is [category]?
2. What are the best [category] tools?
3. How do I choose between [option A] and [option B]?
4. What should I look for in a [category] solution?
```

## FAQ anti-patterns

| Anti-pattern | Why it fails | Fix |
|---|---|---|
| Questions no one asks | Doesn't address real queries | Base on support tickets and search data |
| One-word answers | Not extractable or useful | Always add context after yes/no |
| Duplicate FAQ across pages | Entity and answer ambiguity | Tailor FAQ to each page's specific entity |
| Schema answer differs from visible text | Schema mismatch | Keep schema text and visible text identical |
| FAQ buried below the fold | Reduces extraction chance | Place FAQ near top or after key sections |
| No FAQ on key commercial pages | Misses decision-query coverage | Add FAQ to all product and pricing pages |

## Checklist

- [ ] FAQ covers all five question types: definition, capability, comparison, decision, troubleshooting
- [ ] Every yes/no answer includes contextual detail
- [ ] All conditional recommendation answers include at least two use-case scenarios
- [ ] FAQPage schema is present and matches visible content exactly
- [ ] FAQ placed after key sections on commercial pages
- [ ] Questions are based on real user queries, not marketing assumptions
- [ ] FAQ updated when product, pricing, or capabilities change
