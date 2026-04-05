---
name: structured-entities
description: Model and publish structured entity pages and schema markup for AI search and answer engine readiness. Use when asked to "add structured data", "implement schema markup", "create entity pages", "improve organization schema", "add product schema", "build source-of-truth pages", or "improve AI entity recognition".
license: MIT
metadata:
  author: web-quality-skills
  version: 0.1.0
---

# Structured Entities

Build and maintain structured entity pages and JSON-LD schema so AI systems can confidently resolve, describe, and recommend the site's main entities — organizations, products, services, categories, authors, and more.

Structured entities are the foundation of AI-search authority. A site that cannot resolve its core entities clearly is unlikely to be cited or recommended reliably regardless of content quality.

## Why structured entities matter for AI search

| Without structured entities | With structured entities |
|---|---|
| AI must infer what the brand does from prose | AI resolves the brand from structured facts |
| Product names may be confused with competitors | Products have unique, schema-reinforced identities |
| Category coverage is ambiguous | Categories map to clear solution areas |
| Author authority is unclear | Authors have linked identity pages |
| Citations may go to competitors | Source-of-truth pages anchor citations |

## Entity types and priority

### Priority 1 — always required

| Entity | Page type | Schema type |
|---|---|---|
| Organization / brand | `/about`, `/company` | `Organization` |
| Website identity | Homepage | `WebSite` |
| Products | `/products/[name]` | `Product` |
| Services | `/services/[name]` | `Service` |

### Priority 2 — required for most sites

| Entity | Page type | Schema type |
|---|---|---|
| FAQ content | Any page with Q&A | `FAQPage` |
| How-to content | Process or guide pages | `HowTo` |
| Articles and guides | Blog, docs, editorial | `Article` |
| Breadcrumbs | All inner pages | `BreadcrumbList` |
| Authors | Blog, editorial, docs | `Person` |

### Priority 3 — situational

| Entity | Page type | Schema type |
|---|---|---|
| Local business | Location pages | `LocalBusiness` |
| Software application | App or tool pages | `SoftwareApplication` |
| Reviews | Product or service pages | `Review`, `AggregateRating` |
| Course or learning content | Educational pages | `Course` |

## Organization schema

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Acme Corp",
  "url": "https://acme.com",
  "logo": "https://acme.com/logo.png",
  "description": "Acme Corp builds developer tools for API testing and monitoring.",
  "foundingDate": "2019",
  "sameAs": [
    "https://twitter.com/acmecorp",
    "https://linkedin.com/company/acmecorp",
    "https://github.com/acmecorp"
  ],
  "contactPoint": {
    "@type": "ContactPoint",
    "contactType": "customer support",
    "email": "support@acme.com",
    "url": "https://acme.com/support"
  }
}
```

## WebSite schema

```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "Acme Corp",
  "url": "https://acme.com",
  "potentialAction": {
    "@type": "SearchAction",
    "target": {
      "@type": "EntryPoint",
      "urlTemplate": "https://acme.com/search?q={search_term_string}"
    },
    "query-input": "required name=search_term_string"
  }
}
```

## Product schema

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Acme API Monitor Pro",
  "url": "https://acme.com/products/api-monitor-pro",
  "image": "https://acme.com/images/api-monitor-pro.png",
  "description": "Acme API Monitor Pro provides real-time uptime monitoring and alerting for REST, GraphQL, and gRPC APIs.",
  "brand": {
    "@type": "Brand",
    "name": "Acme Corp"
  },
  "offers": {
    "@type": "Offer",
    "price": "49.00",
    "priceCurrency": "USD",
    "availability": "https://schema.org/InStock"
  },
  "additionalProperty": [
    {
      "@type": "PropertyValue",
      "name": "Supported protocols",
      "value": "REST, GraphQL, gRPC"
    },
    {
      "@type": "PropertyValue",
      "name": "Check interval",
      "value": "30 seconds"
    }
  ]
}
```

## Article schema

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "How to Monitor GraphQL APIs in Production",
  "description": "A practical guide to monitoring GraphQL API health, latency, and error rates.",
  "author": {
    "@type": "Person",
    "name": "Sarah Chen",
    "url": "https://acme.com/authors/sarah-chen"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Acme Corp",
    "logo": {
      "@type": "ImageObject",
      "url": "https://acme.com/logo.png"
    }
  },
  "datePublished": "2025-11-01",
  "dateModified": "2026-03-15"
}
```

## BreadcrumbList schema

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "https://acme.com"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Products",
      "item": "https://acme.com/products"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "API Monitor Pro",
      "item": "https://acme.com/products/api-monitor-pro"
    }
  ]
}
```

## Entity consistency rules

| Check | Rule |
|---|---|
| Name consistency | `schema name` = `<h1>` = `<title>` = navigation label |
| URL consistency | `schema url` = canonical tag = primary internal link |
| Description accuracy | Schema description reflects what the page actually says |
| Date accuracy | datePublished and dateModified reflect real dates |
| Rating accuracy | Only add aggregateRating if real reviews exist |
| Offer accuracy | Prices and availability must match live site values |

## Entity audit checklist

### Critical

- [ ] Organization schema present on About or homepage
- [ ] WebSite schema present on homepage
- [ ] Product/Service schema present on all product and service pages
- [ ] Schema names match H1 headings
- [ ] Schema URLs match canonical tags

### High priority

- [ ] Article schema on all editorial content
- [ ] BreadcrumbList on all inner pages
- [ ] Author schema on editorial and documentation pages
- [ ] FAQ schema on pages with Q&A content
- [ ] sameAs links on Organization schema

### Medium priority

- [ ] additionalProperty on products for key specs
- [ ] dateModified kept current on all schema
- [ ] SoftwareApplication schema for any app or tool
- [ ] Person schema for all named contributors
- [ ] Review and AggregateRating where genuine ratings exist

### Ongoing

- [ ] Validate schema after every major content update
- [ ] Remove schema for deprecated or retired pages
- [ ] Monitor for schema warnings in Google Search Console
- [ ] Audit entity name consistency across schema, headings, and nav

## Common entity mistakes

| Mistake | Why it matters | Fix |
|---|---|---|
| Schema name differs from H1 | Entity ambiguity | Match exactly |
| Empty or generic descriptions | Weak entity signal | Write specific, accurate descriptions |
| Ratings without real reviews | Misleading | Remove until genuine |
| Prices not kept current | Breaks recommendation trust | Automate or review regularly |
| sameAs links to wrong profiles | Misidentification | Verify each external link |
| No author on editorial content | Weak authority signal | Add author pages and schema |

## Validation tools

| Tool | Use |
|---|---|
| [Google Rich Results Test](https://search.google.com/test/rich-results) | Validate schema eligibility |
| [Schema.org Validator](https://validator.schema.org/) | Full schema correctness check |
| [Google Search Console](https://search.google.com/search-console) | Monitor schema errors at scale |

## References

- `references/organization.md` — organization and brand entity patterns in depth
- `references/product.md` — product and service entity modeling
- `references/faq-howto.md` — FAQ, HowTo, and structured Q&A schema
- [`answer-engine-optimization`](../answer-engine-optimization/SKILL.md) — content structure for AI citation
- [`ai-search-audit`](../ai-search-audit/SKILL.md) — full AI search readiness scoring
- [Schema.org](https://schema.org/)
- [Google Structured Data Documentation](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)
