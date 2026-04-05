# Product & Service Entity Modeling

> Deep-reference for `skills/structured-entities/SKILL.md`

## Why Product Schema Drives AI Commerce Citations

AI shopping assistants and answer engines use `Product` schema to surface pricing, availability, ratings, and comparison data. Without it, product pages are treated as generic content — never cited in product recommendation queries or price-check responses.

## Core Product Schema

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "@id": "https://example.com/products/widget-pro/#product",
  "name": "Widget Pro",
  "description": "The Widget Pro is a premium enterprise widget with 5-year warranty and cloud sync.",
  "sku": "WGT-PRO-001",
  "gtin14": "00012345678905",
  "mpn": "WGT-PRO-001",
  "brand": {
    "@type": "Brand",
    "name": "Acme",
    "@id": "https://example.com/#brand"
  },
  "manufacturer": {
    "@id": "https://example.com/#organization"
  },
  "image": [
    "https://example.com/images/widget-pro-front.jpg",
    "https://example.com/images/widget-pro-side.jpg"
  ],
  "url": "https://example.com/products/widget-pro/",
  "category": "Business > Enterprise Tools > Widgets",
  "offers": {
    "@type": "Offer",
    "url": "https://example.com/products/widget-pro/",
    "priceCurrency": "AUD",
    "price": "299.00",
    "priceValidUntil": "2025-12-31",
    "availability": "https://schema.org/InStock",
    "itemCondition": "https://schema.org/NewCondition",
    "shippingDetails": {
      "@type": "OfferShippingDetails",
      "shippingRate": {
        "@type": "MonetaryAmount",
        "value": "0",
        "currency": "AUD"
      },
      "deliveryTime": {
        "@type": "ShippingDeliveryTime",
        "handlingTime": { "@type": "QuantitativeValue", "minValue": 1, "maxValue": 2, "unitCode": "DAY" },
        "transitTime": { "@type": "QuantitativeValue", "minValue": 2, "maxValue": 5, "unitCode": "DAY" }
      }
    },
    "hasMerchantReturnPolicy": {
      "@type": "MerchantReturnPolicy",
      "returnPolicyCategory": "https://schema.org/MerchantReturnFiniteReturnWindow",
      "merchantReturnDays": 30,
      "returnMethod": "https://schema.org/ReturnByMail",
      "returnFees": "https://schema.org/FreeReturn"
    }
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.7",
    "reviewCount": "128",
    "bestRating": "5",
    "worstRating": "1"
  },
  "review": [
    {
      "@type": "Review",
      "reviewRating": { "@type": "Rating", "ratingValue": "5" },
      "author": { "@type": "Person", "name": "Jane Smith" },
      "reviewBody": "Best widget we've used. Setup was fast and support was excellent.",
      "datePublished": "2024-11-15"
    }
  ]
}
```

## SoftwareApplication Schema

For SaaS and digital products:

```json
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "@id": "https://example.com/app/#software",
  "name": "Widget Dashboard",
  "operatingSystem": "Web, iOS, Android",
  "applicationCategory": "BusinessApplication",
  "offers": {
    "@type": "Offer",
    "price": "49.00",
    "priceCurrency": "USD"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.5",
    "ratingCount": "320"
  },
  "featureList": "Real-time analytics, Multi-user access, API integration, Mobile apps",
  "screenshot": "https://example.com/app/screenshot.png",
  "softwareVersion": "3.2.1",
  "releaseNotes": "https://example.com/app/changelog"
}
```

## Multiple Offers (Pricing Tiers)

```json
"offers": [
  {
    "@type": "Offer",
    "name": "Starter",
    "price": "0",
    "priceCurrency": "USD",
    "description": "Up to 5 users, 10GB storage",
    "availability": "https://schema.org/InStock"
  },
  {
    "@type": "Offer",
    "name": "Pro",
    "price": "49.00",
    "priceCurrency": "USD",
    "description": "Unlimited users, 1TB storage, priority support",
    "availability": "https://schema.org/InStock"
  },
  {
    "@type": "Offer",
    "name": "Enterprise",
    "price": "0",
    "priceCurrency": "USD",
    "description": "Custom pricing — contact sales",
    "availability": "https://schema.org/InStock"
  }
]
```

## Service Schema

For agencies, consultancies, and professional services:

```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "@id": "https://example.com/services/seo-audit/#service",
  "name": "SEO Audit Service",
  "description": "Comprehensive technical SEO audit with actionable recommendations.",
  "provider": { "@id": "https://example.com/#organization" },
  "serviceType": "SEO Consulting",
  "areaServed": "AU",
  "offers": {
    "@type": "Offer",
    "price": "1500.00",
    "priceCurrency": "AUD"
  },
  "hasOfferCatalog": {
    "@type": "OfferCatalog",
    "name": "SEO Services",
    "itemListElement": [
      { "@type": "Offer", "itemOffered": { "@type": "Service", "name": "Technical Audit" } },
      { "@type": "Offer", "itemOffered": { "@type": "Service", "name": "Content Gap Analysis" } }
    ]
  }
}
```

## AI Comparison Optimization

AI models generate product comparison tables from structured data. Optimize for this:

| Field | Why AI Uses It | Best Practice |
|-------|----------------|---------------|
| `name` | Comparison header | Concise, brand + model format |
| `description` | Feature summary | Lead with differentiator, <160 chars |
| `offers.price` | Price comparison | Always include currency |
| `aggregateRating` | Trust signal | Include `reviewCount`, not just rating |
| `featureList` | Feature diff table | Pipe-separated or comma list |
| `category` | Group comparison | Use standard taxonomy strings |
| `sku` / `gtin` | Product identity | Required for shopping integrations |

## Common Product Schema Mistakes

| Mistake | AI Impact | Fix |
|---------|-----------|-----|
| Price without `priceCurrency` | Ignored by shopping AI | Always pair price + currency |
| Missing `priceValidUntil` | Stale pricing cached | Set 6–12 month future date |
| No `availability` field | Product treated as discontinued | Always set InStock/OutOfStock |
| `description` is marketing copy | Factual queries go unanswered | State specs, not slogans |
| No `aggregateRating` | Not cited in best-of queries | Implement review markup |
| Missing `brand` link | Product orphaned from brand entity | Link to Brand `@id` |
| Single image only | Limited visual representation | Provide 3+ angles |

## Checklist

- [ ] `@id` uses canonical product URL fragment
- [ ] `name` is brand + model format
- [ ] `description` leads with key differentiator, under 160 chars
- [ ] `sku` and/or `gtin` present for physical products
- [ ] `brand` links to Brand `@id`
- [ ] `offers.price` and `offers.priceCurrency` both present
- [ ] `offers.priceValidUntil` set to future date
- [ ] `offers.availability` set explicitly
- [ ] `offers.shippingDetails` present for e-commerce
- [ ] `offers.hasMerchantReturnPolicy` present
- [ ] `aggregateRating` includes `reviewCount`
- [ ] At least 3 product images
- [ ] `featureList` populated for SoftwareApplication
- [ ] All offers have `priceCurrency`

## Tools

- [Google Merchant Center Product Feed](https://support.google.com/merchants/answer/7052112)
- [Schema.org Product Validator](https://validator.schema.org/)
- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Open Graph + Schema Debugger](https://www.opengraph.xyz/)
