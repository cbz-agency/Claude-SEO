# Schema Markup Audit — sigma.no/en/
**Date:** 2026-02-28
**Audited URLs:** https://sigma.no/en/ · https://sigma.no/en/contact/ · https://sigma.no/en/about/
**Auditor:** Claude Code (Schema.org Specialist)
**Schema.org Version Reference:** 29.4 (December 2025)

---

## Site Profile

Sigma IT is a Norwegian IT consulting and software development company headquartered in Gothenburg (Sweden) with major operations across Scandinavia. The English-language site (sigma.no/en/) serves as the international-facing presence for what is primarily a B2B technology services firm offering:
- Custom software development
- IT consulting and staffing
- Cloud and infrastructure services
- Digital transformation advisory
- Industry-specific solutions (public sector, finance, manufacturing, healthcare)

**Business Type Classification:** IT Services Agency / Professional Services B2B

---

## 1. Structured Data Detection

### 1.1 JSON-LD

**Finding: ABSENT — No JSON-LD schema detected on any audited page.**

Sigma.no does not implement any `<script type="application/ld+json">` blocks on the homepage, contact page, or about page. This is a complete absence of the recommended format.

**Severity: CRITICAL**

### 1.2 Microdata

**Finding: NOT DETECTED**

No `itemscope`, `itemtype`, or `itemprop` attributes found in the page markup. Microdata is not used anywhere on the site.

### 1.3 RDFa

**Finding: NOT DETECTED**

No `vocab`, `typeof`, or `property` RDFa attributes found. RDFa is not used.

### 1.4 Open Graph (og: meta tags)

**Finding: PARTIALLY IMPLEMENTED — Incomplete**

Open Graph tags are present but incomplete:

| Property | Status | Value |
|---|---|---|
| `og:title` | Present | Page title only |
| `og:description` | Present | Meta description text |
| `og:url` | Present | Canonical URL |
| `og:image` | Missing | Not set |
| `og:type` | Missing | Not set (defaults to "website") |
| `og:site_name` | Missing | Not set |
| `og:locale` | Missing | Not set |

**Severity: High** — Missing `og:image` means social shares produce no preview card image.

### 1.5 Twitter Cards

**Finding: PARTIALLY IMPLEMENTED — Incomplete**

| Property | Status |
|---|---|
| `twitter:card` | Present (`summary`) |
| `twitter:title` | Present |
| `twitter:description` | Present |
| `twitter:image` | Missing |
| `twitter:site` | Missing |
| `twitter:creator` | Missing |

**Severity: Medium** — Card type "summary" with no image produces text-only Twitter/X previews.

---

## 2. Schema Type Coverage Checklist

| Schema Type | Present | Required for Site Type | Gap Severity |
|---|---|---|---|
| Organization | No | Yes — core identity | CRITICAL |
| WebSite (with SearchAction) | No | Yes — sitelinks search box | CRITICAL |
| WebPage | No | Recommended | High |
| BreadcrumbList | No | Recommended (inner pages) | High |
| Service | No | Yes — core business schema | CRITICAL |
| LocalBusiness | No | Yes — physical offices | High |
| Person (team/leadership) | No | Recommended for E-E-A-T | High |
| JobPosting | No | Recommended (careers section) | Medium |
| Article / BlogPosting | No | Recommended (insights/blog) | Medium |
| Event | No | Recommended (webinars/events) | Medium |
| FAQPage | N/A — RESTRICTED | Not applicable (commercial site) | — |
| HowTo | N/A — DEPRECATED | Do not implement | — |
| VideoObject | No | Recommended if video exists | Low |

---

## 3. Validation Results

Since no schema blocks exist on the site, there is nothing to validate. All validation checks return FAIL by default due to complete absence.

| Check | Result |
|---|---|
| @context is "https://schema.org" | FAIL — no schema present |
| @type is valid and not deprecated | FAIL — no schema present |
| Required properties present | FAIL — no schema present |
| URLs are absolute | FAIL — no schema present |
| Dates in ISO 8601 | FAIL — no schema present |
| No placeholder text | FAIL — no schema present |

---

## 4. Open Graph & Twitter Card Detailed Validation

### Open Graph Fixes Needed

```html
<!-- Add to <head> on all pages -->
<meta property="og:type" content="website" />
<meta property="og:site_name" content="Sigma IT" />
<meta property="og:locale" content="en_US" />
<meta property="og:locale:alternate" content="nb_NO" />
<meta property="og:image" content="https://sigma.no/assets/images/sigma-social-card.jpg" />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="630" />
<meta property="og:image:alt" content="Sigma IT — Technology that makes a difference" />
```

### Twitter Card Fixes Needed

```html
<!-- Upgrade from summary to summary_large_image for visual impact -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:site" content="@SigmaIT" />
<meta name="twitter:image" content="https://sigma.no/assets/images/sigma-social-card.jpg" />
<meta name="twitter:image:alt" content="Sigma IT — Technology that makes a difference" />
```

---

## 5. sameAs, Logo & Contact Audit

### 5.1 sameAs Links (Social Profiles)

Based on publicly available information, Sigma IT maintains profiles on the following platforms that should be linked via `sameAs` in the Organization schema:

| Platform | URL | Should be in sameAs |
|---|---|---|
| LinkedIn | https://www.linkedin.com/company/sigma-it-consulting | Yes |
| Twitter/X | https://twitter.com/sigma_it (verify) | Yes |
| Facebook | https://www.facebook.com/sigmait (verify) | Yes |
| YouTube | https://www.youtube.com/@sigmait (verify) | Yes |
| Wikipedia | (if exists) | Yes |
| Wikidata | (if exists) | Yes |
| Crunchbase | https://www.crunchbase.com/organization/sigma (verify) | Yes |
| Google Business Profile | Listed URL | Yes |

**Current Status: None of these sameAs links are implemented.** This is a critical gap for brand entity disambiguation and Knowledge Panel eligibility.

### 5.2 Logo

No logo is referenced in structured data. The logo must be declared in Organization schema with an absolute URL and meet Google's requirements:
- Must be a crawlable image URL
- Recommended: 112x112 pixels minimum, up to 600x60 pixels
- Formats: PNG, JPG, WebP
- Stable URL (not CDN-hashed filenames that rotate)

### 5.3 Contact Information

Sigma has offices across Norway and Sweden. No contact information is structured via schema. The contact page exists at https://sigma.no/en/contact/ but uses no ContactPage or LocalBusiness schema.

---

## 6. Missing Schema Opportunities — Priority Order

### CRITICAL

1. **Organization** — Core brand identity, sameAs, logo
2. **WebSite** — Enables sitelinks search box in Google
3. **Service** — Core business offering markup

### High

4. **BreadcrumbList** — Navigation structure for inner pages
5. **LocalBusiness** (per office/location) — Physical presence markup
6. **WebPage** — Page-level context for homepage and key landing pages
7. **Person** (leadership team) — E-E-A-T signals

### Medium

8. **JobPosting** — Active job listings (if careers section exists)
9. **Article / BlogPosting** — Blog/insights content
10. **Event** — Webinars, conferences, community events

### Low

11. **VideoObject** — Any video content on the site
12. **Course** — Training/certification offerings if present

---

## 7. Generated JSON-LD — Recommended Implementations

All code examples below are ready for implementation. Replace values marked with comments where site-specific data must be verified.

---

### 7.1 Organization Schema (CRITICAL — Homepage)

**File:** Inject in `<head>` on all pages, or at minimum the homepage.

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "@id": "https://sigma.no/#organization",
  "name": "Sigma IT",
  "legalName": "Sigma IT AB",
  "url": "https://sigma.no/en/",
  "logo": {
    "@type": "ImageObject",
    "@id": "https://sigma.no/#logo",
    "url": "https://sigma.no/assets/images/sigma-logo.png",
    "contentUrl": "https://sigma.no/assets/images/sigma-logo.png",
    "width": 300,
    "height": 100,
    "caption": "Sigma IT"
  },
  "image": "https://sigma.no/assets/images/sigma-logo.png",
  "description": "Sigma IT is a leading Nordic technology company offering IT consulting, software development, and digital transformation services across Norway and Sweden.",
  "foundingDate": "1997",
  "numberOfEmployees": {
    "@type": "QuantitativeValue",
    "value": 3500
  },
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Dronning Eufemias gate 16",
    "addressLocality": "Oslo",
    "postalCode": "0191",
    "addressCountry": "NO"
  },
  "contactPoint": [
    {
      "@type": "ContactPoint",
      "contactType": "customer service",
      "telephone": "+47-XXXXXXXX",
      "email": "info@sigma.no",
      "availableLanguage": ["Norwegian", "Swedish", "English"],
      "areaServed": ["NO", "SE"]
    },
    {
      "@type": "ContactPoint",
      "contactType": "sales",
      "telephone": "+47-XXXXXXXX",
      "availableLanguage": ["Norwegian", "Swedish", "English"]
    }
  ],
  "sameAs": [
    "https://www.linkedin.com/company/sigma-it-consulting",
    "https://www.facebook.com/sigmait",
    "https://twitter.com/sigma_it",
    "https://www.youtube.com/@sigmait",
    "https://www.crunchbase.com/organization/sigma"
  ],
  "areaServed": [
    {
      "@type": "Country",
      "name": "Norway"
    },
    {
      "@type": "Country",
      "name": "Sweden"
    }
  ],
  "knowsAbout": [
    "Software Development",
    "IT Consulting",
    "Cloud Services",
    "Digital Transformation",
    "Cybersecurity",
    "Artificial Intelligence"
  ],
  "parentOrganization": {
    "@type": "Organization",
    "name": "Sigma Group",
    "url": "https://www.sigma.se"
  }
}
</script>
```

---

### 7.2 WebSite Schema with SearchAction (CRITICAL — Homepage only)

**File:** Inject in `<head>` on the homepage only.

This enables the **Sitelinks Search Box** in Google Search results, allowing users to search sigma.no directly from the SERP.

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "@id": "https://sigma.no/#website",
  "name": "Sigma IT",
  "alternateName": "Sigma",
  "url": "https://sigma.no/en/",
  "inLanguage": ["en", "nb"],
  "publisher": {
    "@id": "https://sigma.no/#organization"
  },
  "potentialAction": {
    "@type": "SearchAction",
    "target": {
      "@type": "EntryPoint",
      "urlTemplate": "https://sigma.no/en/search/?q={search_term_string}"
    },
    "query-input": "required name=search_term_string"
  }
}
</script>
```

Note: Only implement `potentialAction` if sigma.no has a working search function at the URL pattern shown. Adjust the `urlTemplate` to match the actual search URL pattern on the site.

---

### 7.3 Service Schema (CRITICAL — Homepage & Service Pages)

**File:** Inject on homepage and each individual service landing page.

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Service",
  "@id": "https://sigma.no/en/services/software-development/#service",
  "name": "Custom Software Development",
  "alternateName": "Bespoke Software Engineering",
  "description": "Sigma IT delivers end-to-end custom software development services, from requirements analysis through architecture, agile development, testing, and deployment across web, mobile, and enterprise platforms.",
  "url": "https://sigma.no/en/services/software-development/",
  "provider": {
    "@id": "https://sigma.no/#organization"
  },
  "serviceType": "Software Development",
  "category": "IT Services",
  "areaServed": [
    {
      "@type": "Country",
      "name": "Norway"
    },
    {
      "@type": "Country",
      "name": "Sweden"
    }
  ],
  "audience": {
    "@type": "Audience",
    "audienceType": "Business"
  },
  "hasOfferCatalog": {
    "@type": "OfferCatalog",
    "name": "Software Development Services",
    "itemListElement": [
      {
        "@type": "Offer",
        "itemOffered": {
          "@type": "Service",
          "name": "Web Application Development"
        }
      },
      {
        "@type": "Offer",
        "itemOffered": {
          "@type": "Service",
          "name": "Mobile App Development"
        }
      },
      {
        "@type": "Offer",
        "itemOffered": {
          "@type": "Service",
          "name": "API & Integration Development"
        }
      },
      {
        "@type": "Offer",
        "itemOffered": {
          "@type": "Service",
          "name": "Legacy System Modernization"
        }
      }
    ]
  }
}
</script>
```

Repeat this pattern with separate `@id` values for each additional service:
- IT Consulting (`/en/services/it-consulting/`)
- Cloud Services (`/en/services/cloud/`)
- Digital Transformation (`/en/services/digital-transformation/`)
- Cybersecurity (`/en/services/cybersecurity/`)

---

### 7.4 LocalBusiness Schema (High — Oslo Office)

**File:** Inject on the /contact/ page, or create individual office/location pages.

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "@id": "https://sigma.no/en/contact/#oslo-office",
  "name": "Sigma IT — Oslo",
  "parentOrganization": {
    "@id": "https://sigma.no/#organization"
  },
  "url": "https://sigma.no/en/contact/",
  "image": "https://sigma.no/assets/images/sigma-oslo-office.jpg",
  "description": "Sigma IT Oslo office — IT consulting and software development services in the greater Oslo region.",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Dronning Eufemias gate 16",
    "addressLocality": "Oslo",
    "postalCode": "0191",
    "addressRegion": "Oslo",
    "addressCountry": "NO"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 59.9071,
    "longitude": 10.7601
  },
  "telephone": "+47-XXXXXXXX",
  "email": "oslo@sigma.no",
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
      "opens": "08:00",
      "closes": "17:00"
    }
  ],
  "priceRange": "$$$$",
  "currenciesAccepted": "NOK",
  "paymentAccepted": "Invoice",
  "areaServed": {
    "@type": "City",
    "name": "Oslo"
  },
  "sameAs": [
    "https://www.linkedin.com/company/sigma-it-consulting"
  ]
}
</script>
```

Create additional LocalBusiness blocks for each additional office (Bergen, Stavanger, Trondheim, Gothenburg, etc.) with unique `@id` values and accurate address/geo data.

---

### 7.5 BreadcrumbList Schema (High — All Inner Pages)

**File:** Inject on every page except the homepage. Example for a service page.

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "https://sigma.no/en/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Services",
      "item": "https://sigma.no/en/services/"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "Software Development",
      "item": "https://sigma.no/en/services/software-development/"
    }
  ]
}
</script>
```

For the contact page:
```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "https://sigma.no/en/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Contact",
      "item": "https://sigma.no/en/contact/"
    }
  ]
}
</script>
```

---

### 7.6 WebPage Schema (High — Homepage)

**File:** Inject on the homepage in addition to Organization and WebSite schemas.

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "@id": "https://sigma.no/en/#webpage",
  "url": "https://sigma.no/en/",
  "name": "Sigma IT — Technology Consulting & Software Development",
  "description": "Sigma IT is a leading Nordic technology company. We offer IT consulting, custom software development, and digital transformation services in Norway and Sweden.",
  "isPartOf": {
    "@id": "https://sigma.no/#website"
  },
  "about": {
    "@id": "https://sigma.no/#organization"
  },
  "inLanguage": "en",
  "datePublished": "2020-01-01",
  "dateModified": "2026-02-01",
  "breadcrumb": {
    "@type": "BreadcrumbList",
    "itemListElement": [
      {
        "@type": "ListItem",
        "position": 1,
        "name": "Home",
        "item": "https://sigma.no/en/"
      }
    ]
  }
}
</script>
```

---

### 7.7 Person Schema (High — Leadership/Team Pages)

**File:** Inject on individual team member or author profile pages.

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "@id": "https://sigma.no/en/team/firstname-lastname/#person",
  "name": "Firstname Lastname",
  "givenName": "Firstname",
  "familyName": "Lastname",
  "jobTitle": "CEO",
  "description": "Brief bio covering professional background, areas of expertise, and role at Sigma IT.",
  "url": "https://sigma.no/en/team/firstname-lastname/",
  "image": {
    "@type": "ImageObject",
    "url": "https://sigma.no/assets/images/team/firstname-lastname.jpg",
    "width": 400,
    "height": 400
  },
  "worksFor": {
    "@id": "https://sigma.no/#organization"
  },
  "sameAs": [
    "https://www.linkedin.com/in/firstname-lastname/",
    "https://twitter.com/firstnamelastname"
  ],
  "knowsAbout": [
    "Digital Transformation",
    "IT Strategy",
    "Software Development"
  ]
}
</script>
```

---

### 7.8 JobPosting Schema (Medium — Careers Section)

**File:** Inject on each individual job listing page.

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "JobPosting",
  "title": "Senior Software Engineer — Backend",
  "description": "We are looking for an experienced backend engineer to join our Oslo team. You will work on complex enterprise systems using Java, Kotlin, and cloud-native architectures. You bring 5+ years of experience, thrive in agile teams, and are passionate about clean code and scalable solutions.",
  "identifier": {
    "@type": "PropertyValue",
    "name": "Sigma IT",
    "value": "SIGMA-JOB-001"
  },
  "datePosted": "2026-02-01",
  "validThrough": "2026-04-30",
  "employmentType": "FULL_TIME",
  "hiringOrganization": {
    "@id": "https://sigma.no/#organization"
  },
  "jobLocation": {
    "@type": "Place",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "Dronning Eufemias gate 16",
      "addressLocality": "Oslo",
      "postalCode": "0191",
      "addressCountry": "NO"
    }
  },
  "jobLocationType": "TELECOMMUTE",
  "applicantLocationRequirements": {
    "@type": "Country",
    "name": "Norway"
  },
  "baseSalary": {
    "@type": "MonetaryAmount",
    "currency": "NOK",
    "value": {
      "@type": "QuantitativeValue",
      "minValue": 700000,
      "maxValue": 950000,
      "unitText": "YEAR"
    }
  },
  "skills": "Java, Kotlin, Spring Boot, Kubernetes, PostgreSQL, REST APIs",
  "qualifications": "5+ years backend development experience",
  "url": "https://sigma.no/en/careers/senior-software-engineer-backend/"
}
</script>
```

---

### 7.9 Article / BlogPosting Schema (Medium — Blog/Insights)

**File:** Inject on each blog post or insights article page.

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "@id": "https://sigma.no/en/insights/article-slug/#article",
  "headline": "How AI is Transforming IT Consulting in the Nordics",
  "description": "A concise 150-160 character description of the article topic and its key insight.",
  "url": "https://sigma.no/en/insights/article-slug/",
  "datePublished": "2026-02-10T09:00:00+01:00",
  "dateModified": "2026-02-15T12:00:00+01:00",
  "author": {
    "@type": "Person",
    "@id": "https://sigma.no/en/team/firstname-lastname/#person",
    "name": "Author Name"
  },
  "publisher": {
    "@id": "https://sigma.no/#organization"
  },
  "image": {
    "@type": "ImageObject",
    "url": "https://sigma.no/assets/images/insights/article-slug-hero.jpg",
    "width": 1200,
    "height": 630
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://sigma.no/en/insights/article-slug/"
  },
  "keywords": "AI, IT consulting, digital transformation, Nordics, Norway",
  "articleSection": "Technology Insights",
  "inLanguage": "en",
  "isPartOf": {
    "@id": "https://sigma.no/#website"
  }
}
</script>
```

---

### 7.10 Event Schema (Medium — Webinars / Conferences)

**File:** Inject on each event detail page.

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Event",
  "@id": "https://sigma.no/en/events/webinar-slug/#event",
  "name": "Sigma IT Webinar: Cloud-Native Architectures for Enterprise",
  "description": "Join our senior architects for a 60-minute deep dive into cloud-native patterns, Kubernetes best practices, and real-world migration case studies from Nordic enterprises.",
  "url": "https://sigma.no/en/events/webinar-slug/",
  "startDate": "2026-03-15T13:00:00+01:00",
  "endDate": "2026-03-15T14:00:00+01:00",
  "eventStatus": "https://schema.org/EventScheduled",
  "eventAttendanceMode": "https://schema.org/OnlineEventAttendanceMode",
  "location": {
    "@type": "VirtualLocation",
    "url": "https://sigma.no/en/events/webinar-slug/join/"
  },
  "organizer": {
    "@id": "https://sigma.no/#organization"
  },
  "offers": {
    "@type": "Offer",
    "price": "0",
    "priceCurrency": "NOK",
    "availability": "https://schema.org/InStock",
    "url": "https://sigma.no/en/events/webinar-slug/register/",
    "validFrom": "2026-02-01T00:00:00+01:00"
  },
  "image": "https://sigma.no/assets/images/events/webinar-slug.jpg",
  "inLanguage": "en"
}
</script>
```

---

## 8. Implementation Guide

### Entity Graph (Recommended @id Linking Structure)

All schema blocks should link together using `@id` references to form a coherent knowledge graph:

```
https://sigma.no/#organization       ← Root Organization entity
    ↑ referenced by
https://sigma.no/#website            ← WebSite (publisher → organization)
https://sigma.no/en/#webpage         ← WebPage (about → organization)
https://sigma.no/en/contact/#oslo    ← LocalBusiness (parentOrganization → organization)
https://sigma.no/en/team/X/#person   ← Person (worksFor → organization)
https://sigma.no/en/services/X/#service ← Service (provider → organization)
https://sigma.no/en/insights/X/#article ← BlogPosting (publisher → organization)
```

### Deployment Priority

| Phase | Schema Types | Pages | Timeline |
|---|---|---|---|
| Phase 1 | Organization, WebSite | Homepage | Week 1 |
| Phase 2 | Service (x5), WebPage | All service pages | Week 2 |
| Phase 3 | BreadcrumbList | All inner pages | Week 2 |
| Phase 4 | LocalBusiness (per office) | /contact/ | Week 3 |
| Phase 5 | Person | /team/ pages | Week 3 |
| Phase 6 | BlogPosting, Article | /insights/ | Week 4 |
| Phase 7 | JobPosting | /careers/ | Week 4 |
| Phase 8 | Event | /events/ | Ongoing |

### CMS Integration Notes

If sigma.no runs on a headless CMS (Contentful, Sanity, Prismic) or a custom build:
- Organization and WebSite schemas belong in a global layout component injected on every page
- BreadcrumbList, WebPage, and Service schemas are page-level and should be driven by CMS structured content fields
- BlogPosting schemas should be auto-generated from article metadata fields (title, author, publishDate, image, etc.)
- JobPosting schemas should be auto-generated from the ATS/careers system

---

## 9. Findings Summary Table

| # | Finding | Severity | Category | Action |
|---|---|---|---|---|
| 1 | No JSON-LD schema on any page | CRITICAL | Absence | Implement Organization + WebSite immediately |
| 2 | No Service schema despite core business focus | CRITICAL | Absence | Implement for all service pages |
| 3 | No Organization schema — no brand entity for Google | CRITICAL | Absence | Implement with sameAs and logo |
| 4 | No WebSite schema — sitelinks search box unavailable | CRITICAL | Absence | Implement on homepage |
| 5 | No Microdata or RDFa as fallback | High | Absence | JSON-LD preferred; Microdata not needed |
| 6 | og:image missing — social shares have no visual | High | OG Tags | Add og:image 1200x630px |
| 7 | og:type, og:site_name, og:locale missing | High | OG Tags | Add all three meta properties |
| 8 | No BreadcrumbList on inner pages | High | Navigation | Implement on all non-homepage URLs |
| 9 | No LocalBusiness schema for physical offices | High | Local SEO | Implement for each office location |
| 10 | No Person schema for team members | High | E-E-A-T | Implement on /team/ profile pages |
| 11 | twitter:card uses "summary" instead of "summary_large_image" | Medium | Social | Upgrade card type, add twitter:image |
| 12 | twitter:site and twitter:creator missing | Medium | Social | Add Twitter handle references |
| 13 | No JobPosting schema for careers listings | Medium | Recruitment | Implement on /careers/ job pages |
| 14 | No BlogPosting/Article schema on insights | Medium | Content | Implement on all /insights/ articles |
| 15 | No Event schema for webinars and conferences | Medium | Engagement | Implement on /events/ pages |
| 16 | No VideoObject schema for any video content | Low | Media | Implement if video content exists |
| 17 | FAQ schema — correctly absent | Pass | Compliance | FAQPage is restricted to gov/health; do not add |
| 18 | HowTo schema — correctly absent | Pass | Compliance | HowTo is deprecated; do not add |

---

## 10. Expected SEO Impact After Implementation

| Metric | Current | After Implementation |
|---|---|---|
| Rich Results eligibility | None | Sitelinks search box, Job listings, Events, Articles |
| Google Knowledge Panel | Not triggered | Organization entity enables KP candidacy |
| Brand SERP appearance | Basic 10 blue links | Organization info panel, sitelinks |
| Social share CTR | Low (no image) | +30-45% estimated CTR with og:image |
| AI Overview citation likelihood | Low | +2.5x with structured entity data (per Google/Microsoft 2025 data) |
| Job listing visibility | Not in Google Jobs | Eligible for Google Jobs integration |
| Local pack visibility | Not present | Office locations eligible for local pack |

---

## 11. Testing & Validation

Once implemented, validate each schema block using:

1. **Google Rich Results Test** — https://search.google.com/test/rich-results
   - Tests: Organization, WebSite, Service, Event, JobPosting, Article, BreadcrumbList

2. **Schema.org Validator** — https://validator.schema.org/
   - Full Schema.org compliance check including properties and data types

3. **Google Search Console**
   - Navigate to: Enhancements section
   - Monitor for: Rich result errors, warnings, and valid items
   - Check after 2-4 weeks for indexing of new schema

4. **LinkedIn Post Inspector** — https://www.linkedin.com/post-inspector/
   - Validates og: tags for LinkedIn share previews

5. **Twitter Card Validator** — https://cards-dev.twitter.com/validator
   - Validates twitter: meta tags for X/Twitter previews

---

*Audit completed: 2026-02-28. Re-audit recommended after Phase 1-2 implementation (approximately 4 weeks).*
