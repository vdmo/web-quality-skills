# Organization & Brand Entity Patterns

> Deep-reference for `skills/structured-entities/SKILL.md`

## Why Organization Schema Matters for AI

AI models build a knowledge graph of entities from structured data. An `Organization` schema is often the first entity a crawler resolves to understand who is behind a site. Incomplete or inconsistent Organization markup causes LLMs to hallucinate company details, mix up brands, or omit attribution in citations.

## Core Organization Schema

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "@id": "https://example.com/#organization",
  "name": "Acme Corp",
  "legalName": "Acme Corporation Pty Ltd",
  "url": "https://example.com",
  "logo": {
    "@type": "ImageObject",
    "url": "https://example.com/logo.png",
    "width": 512,
    "height": 512
  },
  "description": "Acme Corp builds widgets for enterprise customers worldwide.",
  "foundingDate": "2010",
  "numberOfEmployees": { "@type": "QuantitativeValue", "value": 250 },
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Main St",
    "addressLocality": "Melbourne",
    "addressRegion": "VIC",
    "postalCode": "3000",
    "addressCountry": "AU"
  },
  "contactPoint": [
    {
      "@type": "ContactPoint",
      "contactType": "customer support",
      "email": "support@example.com",
      "availableLanguage": "English"
    }
  ],
  "sameAs": [
    "https://www.linkedin.com/company/acme-corp",
    "https://twitter.com/acmecorp",
    "https://en.wikipedia.org/wiki/Acme_Corp"
  ],
  "knowsAbout": ["widget manufacturing", "enterprise solutions"],
  "hasOfferCatalog": {
    "@type": "OfferCatalog",
    "name": "Acme Products",
    "url": "https://example.com/products"
  }
}
```

## Brand Schema (for product brands)

```json
{
  "@context": "https://schema.org",
  "@type": "Brand",
  "@id": "https://example.com/#brand",
  "name": "Acme",
  "logo": "https://example.com/brand-logo.png",
  "description": "The Acme brand stands for reliability and innovation.",
  "url": "https://example.com"
}
```

## Entity Disambiguation with sameAs

`sameAs` is the most powerful signal for AI disambiguation. Link to:

| Source | Value |
|--------|-------|
| Wikipedia | Authoritative entity match |
| Wikidata | Machine-readable identity |
| LinkedIn | Business verification |
| Crunchbase | Startup/company data |
| Google Knowledge Graph | Direct KG link |
| Industry registries | Domain authority |

```json
"sameAs": [
  "https://en.wikipedia.org/wiki/Acme_Corp",
  "https://www.wikidata.org/wiki/Q12345",
  "https://www.linkedin.com/company/acme-corp",
  "https://www.crunchbase.com/organization/acme-corp"
]
```

## @id Consistency Rules

The `@id` field is how LLMs resolve entity identity across pages. Violations cause split entities:

```
# WRONG — different @id on each page creates duplicate entities
Homepage:  "@id": "https://example.com/"
About:     "@id": "https://example.com/about/#org"
Contact:   "@id": "https://example.com/contact/#organization"

# RIGHT — canonical @id used everywhere
All pages: "@id": "https://example.com/#organization"
```

## LocalBusiness Extension

For location-based organizations:

```json
{
  "@context": "https://schema.org",
  "@type": ["Organization", "LocalBusiness"],
  "@id": "https://example.com/#organization",
  "name": "Acme Melbourne",
  "priceRange": "$$",
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
      "opens": "09:00",
      "closes": "17:00"
    }
  ],
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": -37.8136,
    "longitude": 144.9631
  }
}
```

## WebSite + SearchAction

Helps AI models surface your site's search capability:

```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "@id": "https://example.com/#website",
  "url": "https://example.com",
  "name": "Acme Corp",
  "publisher": { "@id": "https://example.com/#organization" },
  "potentialAction": {
    "@type": "SearchAction",
    "target": {
      "@type": "EntryPoint",
      "urlTemplate": "https://example.com/search?q={search_term_string}"
    },
    "query-input": "required name=search_term_string"
  }
}
```

## Common Organization Schema Mistakes

| Mistake | Impact | Fix |
|---------|--------|-----|
| Missing `@id` | Entity not resolved | Add canonical fragment URL |
| Inconsistent `name` across pages | Brand confusion in AI | Normalize to one canonical name |
| No `sameAs` links | Cannot disambiguate entity | Add Wikipedia + LinkedIn at minimum |
| Logo URL returns 404 | Logo not cached by crawlers | Verify URL, use stable CDN |
| Missing `legalName` | Compliance gap, trust signals | Add full registered name |
| `description` over 160 chars | Truncated in AI summaries | Keep under 160 characters |
| No `knowsAbout` | Topic association missing | Add 3–8 relevant topic strings |

## Checklist

- [ ] Organization `@id` is a consistent canonical URL fragment
- [ ] `name` matches brand name used site-wide
- [ ] `legalName` matches business registration
- [ ] `logo` URL resolves and meets size requirements (min 112×112px)
- [ ] `description` is under 160 characters and factual
- [ ] `sameAs` includes Wikipedia and/or Wikidata
- [ ] `sameAs` includes LinkedIn and primary social profiles
- [ ] `address` is complete for LocalBusiness variants
- [ ] `contactPoint` includes support contact type
- [ ] `knowsAbout` lists 3–8 topic strings
- [ ] WebSite schema links `publisher` to Organization `@id`
- [ ] Schema present on homepage, About, and Contact pages

## Tools

- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Schema.org Validator](https://validator.schema.org/)
- [Wikidata Entity Lookup](https://www.wikidata.org/wiki/Special:Search)
- [Google Knowledge Panel Tool](https://support.google.com/knowledgepanel/answer/9163198)
