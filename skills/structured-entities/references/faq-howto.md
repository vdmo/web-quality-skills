# FAQ, HowTo & Structured Q&A Schema

> Deep-reference for `skills/structured-entities/SKILL.md`

## Why FAQ and HowTo Schema Win AI Citations

FAQ and HowTo schema are the highest-yield structured data types for AI answer engines. AI models prefer to pull answers from clearly delineated Q&A and step-by-step content because it maps directly to user query patterns. A well-structured FAQ can appear verbatim in AI-generated answers, making it a primary vector for brand visibility in AI search.

## FAQPage Schema

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is Widget Pro and who is it for?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Widget Pro is an enterprise-grade widget management platform designed for teams of 10 or more. It includes cloud sync, real-time collaboration, and a 5-year warranty. It is ideal for operations managers and IT teams needing reliable widget infrastructure."
      }
    },
    {
      "@type": "Question",
      "name": "How much does Widget Pro cost?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Widget Pro is priced at AUD $299 per unit with volume discounts available for orders of 10 or more. Enterprise licensing starts at AUD $2,500 per year. A free 30-day trial is available with no credit card required."
      }
    },
    {
      "@type": "Question",
      "name": "Does Widget Pro integrate with existing systems?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Yes. Widget Pro integrates with Salesforce, HubSpot, Slack, and Zapier out of the box. A REST API and webhooks are available for custom integrations. Full API documentation is at https://example.com/docs/api."
      }
    }
  ]
}
```

## FAQ Writing Rules for AI Extraction

AI models evaluate FAQ answers on these criteria:

| Criterion | Bad Example | Good Example |
|-----------|-------------|---------------|
| Question specificity | "What is this?" | "What does Widget Pro do for enterprise teams?" |
| Answer completeness | "It's great for teams." | Full sentence with context, numbers, and next step |
| Answer length | 3 words | 40–120 words (sweet spot for AI extraction) |
| Contains URLs | None | Direct link to relevant page |
| Uses entity names | "our product" | Brand name + product name in full |
| Avoids hedging | "It might work with..." | "Widget Pro integrates with X, Y, Z" |

## HowTo Schema

For instructional content that AI models surface in step-by-step responses:

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "How to Set Up Widget Pro in Under 10 Minutes",
  "description": "A step-by-step guide to installing and configuring Widget Pro for your team.",
  "totalTime": "PT10M",
  "estimatedCost": {
    "@type": "MonetaryAmount",
    "currency": "AUD",
    "value": "0"
  },
  "tool": [
    { "@type": "HowToTool", "name": "Widget Pro installer" },
    { "@type": "HowToTool", "name": "Admin credentials" }
  ],
  "supply": [
    { "@type": "HowToSupply", "name": "Widget Pro license key" }
  ],
  "step": [
    {
      "@type": "HowToStep",
      "name": "Download the installer",
      "text": "Go to example.com/download and click Download Widget Pro. Select your operating system version.",
      "url": "https://example.com/setup#step1",
      "image": "https://example.com/images/setup-step1.png"
    },
    {
      "@type": "HowToStep",
      "name": "Run the installer",
      "text": "Double-click the downloaded file and follow the on-screen prompts. Accept the license agreement and choose your installation directory.",
      "url": "https://example.com/setup#step2",
      "image": "https://example.com/images/setup-step2.png"
    },
    {
      "@type": "HowToStep",
      "name": "Enter your license key",
      "text": "When prompted, paste your license key from your welcome email. Click Activate. The system will validate online and complete setup.",
      "url": "https://example.com/setup#step3",
      "image": "https://example.com/images/setup-step3.png"
    },
    {
      "@type": "HowToStep",
      "name": "Invite your team",
      "text": "Navigate to Settings > Team and click Invite Members. Enter email addresses and assign roles. Team members will receive an invitation email.",
      "url": "https://example.com/setup#step4",
      "image": "https://example.com/images/setup-step4.png"
    }
  ]
}
```

## HowToSection for Multi-Part Guides

For longer guides with sections:

```json
"step": [
  {
    "@type": "HowToSection",
    "name": "Installation",
    "itemListElement": [
      { "@type": "HowToStep", "name": "Download", "text": "..." },
      { "@type": "HowToStep", "name": "Install", "text": "..." }
    ]
  },
  {
    "@type": "HowToSection",
    "name": "Configuration",
    "itemListElement": [
      { "@type": "HowToStep", "name": "Set preferences", "text": "..." },
      { "@type": "HowToStep", "name": "Connect integrations", "text": "..." }
    ]
  }
]
```

## QAPage Schema (Community Q&A)

For pages with a single accepted answer (support, community):

```json
{
  "@context": "https://schema.org",
  "@type": "QAPage",
  "mainEntity": {
    "@type": "Question",
    "name": "Why is Widget Pro showing a sync error?",
    "text": "I installed Widget Pro yesterday and it keeps showing sync error 403. I'm on Windows 11.",
    "answerCount": 2,
    "acceptedAnswer": {
      "@type": "Answer",
      "text": "Error 403 on sync usually means your firewall is blocking the Widget Pro sync endpoint. Add an exception for sync.example.com:443 in your firewall settings and restart the service.",
      "upvoteCount": 47,
      "dateCreated": "2024-10-01",
      "author": { "@type": "Person", "name": "Acme Support" }
    },
    "suggestedAnswer": [
      {
        "@type": "Answer",
        "text": "Also check that your proxy settings aren't intercepting SSL traffic.",
        "upvoteCount": 12
      }
    ]
  }
}
```

## SpecialAnnouncement (for time-sensitive AI visibility)

```json
{
  "@context": "https://schema.org",
  "@type": "SpecialAnnouncement",
  "name": "Widget Pro 4.0 Release",
  "text": "Widget Pro 4.0 is now available with 40% faster sync and new mobile apps for iOS and Android.",
  "datePosted": "2025-01-15",
  "expires": "2025-03-31",
  "category": "https://www.wikidata.org/wiki/Q10373",
  "announcementLocation": { "@id": "https://example.com/#organization" }
}
```

## FAQ Topic Coverage Strategy

AI models extract FAQ answers when they match query intent. Cover all five intent categories:

| Intent Category | Example Questions | AI Use Case |
|-----------------|-------------------|--------------|
| What is it | "What does X do?", "What is X?" | Definition queries |
| How much / pricing | "How much does X cost?", "Is X free?" | Commerce queries |
| Comparison | "X vs Y?", "Is X better than Y?" | Comparison queries |
| How to use | "How do I set up X?", "How to integrate X" | Task queries |
| Troubleshooting | "Why is X not working?", "X error fix" | Support queries |
| Eligibility | "Who can use X?", "Requirements for X" | Qualification queries |

## Common FAQ/HowTo Schema Mistakes

| Mistake | AI Impact | Fix |
|---------|-----------|-----|
| Question is vague | Not matched to real queries | Use exact user phrasing from search data |
| Answer is one sentence | Insufficient for AI extraction | Write 40–120 word complete answers |
| Answers use "we" / "our" | Brand unclear to AI | Name brand explicitly in every answer |
| HowTo steps have no images | Lower visual result eligibility | Add step screenshots |
| FAQ on every page | Diluted authority | One canonical FAQ page per topic |
| No `totalTime` on HowTo | Missing quick-answer metadata | Always add ISO 8601 duration |
| Mixed FAQPage + HowTo | Schema type confusion | Use separate pages for each type |

## Checklist

- [ ] FAQPage has at least 5 questions covering all intent categories
- [ ] Each answer is 40–120 words
- [ ] Answers name the brand and product explicitly (no "we" / "our")
- [ ] Answers include specific numbers, dates, or URLs where relevant
- [ ] HowTo includes `totalTime` in ISO 8601 format
- [ ] Each HowToStep has `name`, `text`, and `image`
- [ ] HowToStep images resolve and show the step visually
- [ ] HowTo has `tool` and `supply` arrays where applicable
- [ ] QAPage `acceptedAnswer` has highest `upvoteCount`
- [ ] SpecialAnnouncements have `expires` date set
- [ ] FAQ page is canonicalized (not duplicated across pages)
- [ ] FAQ covers: what, price, comparison, how-to, troubleshooting

## Tools

- [Google FAQ Rich Results Test](https://search.google.com/test/rich-results)
- [Schema.org FAQPage](https://schema.org/FAQPage)
- [Schema.org HowTo](https://schema.org/HowTo)
- [People Also Ask Scraper](https://alsoasked.com/) — mine real user questions
- [Answer Socrates](https://answerthepublic.com/) — question research tool
