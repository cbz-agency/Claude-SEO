# SEO Action Plan — sigma.no/en/

**Site:** https://sigma.no/en/
**Overall Score:** 54/100
**Date:** 2026-02-28

---

## Critical — Fix Immediately (Week 1)

### 1. Add Organization Schema to Homepage
**Impact:** Google Knowledge Panel eligibility, AI entity disambiguation, +AI citation probability
**Effort:** 1 hour
```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "@id": "https://sigma.no/#organization",
  "name": "Sigma IT",
  "url": "https://sigma.no/en/",
  "foundingDate": "1991",
  "logo": { "@type": "ImageObject", "url": "https://sigma.no/assets/images/sigma-logo.png" },
  "address": { "@type": "PostalAddress", "addressLocality": "Oslo", "addressCountry": "NO" },
  "sameAs": ["https://www.linkedin.com/company/sigma-it-consulting"]
}
</script>
```

### 2. Add WebSite Schema with SearchAction to Homepage
**Impact:** Sitelinks Search Box in Google SERPs
**Effort:** 30 minutes
```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "@id": "https://sigma.no/#website",
  "name": "Sigma IT",
  "url": "https://sigma.no/en/",
  "potentialAction": {
    "@type": "SearchAction",
    "target": { "@type": "EntryPoint", "urlTemplate": "https://sigma.no/en/search/?q={search_term_string}" },
    "query-input": "required name=search_term_string"
  }
}
</script>
```

### 3. Fix LCP — Preload Hero Image
**Impact:** Estimated 400–800ms LCP improvement
**Effort:** 30 minutes
```html
<link rel="preload" as="image" href="/media/hero.webp"
      fetchpriority="high" type="image/webp">
<img src="/media/hero.webp" fetchpriority="high" loading="eager"
     width="1920" height="1080" alt="Sigma IT">
```

### 4. Fix CLS — Add Image Dimensions Everywhere
**Impact:** CLS reduction from ~0.15 to <0.1
**Effort:** 2–4 hours (template change in CMS)
- Add `width` and `height` attributes to every `<img>` tag
- Add `aspect-ratio` CSS to image containers

### 5. Fix CLS — Reserve Cookie Banner Height
**Impact:** Eliminates largest single CLS source
**Effort:** 15 minutes
```css
#CybotCookiebotDialog { min-height: 120px; }
```

### 6. Add og:image to All Pages
**Impact:** Social shares will show visual preview; ~30–45% CTR increase on LinkedIn/Twitter shares
**Effort:** 1 hour (CMS template)
```html
<meta property="og:image" content="https://sigma.no/media/og-social.jpg">
<meta property="og:type" content="website">
<meta property="og:locale" content="en_GB">
<meta name="twitter:card" content="summary_large_image">
```

### 7. Add Sitemap Directive to robots.txt
**Impact:** Ensures Google/Bing discover sitemap without Search Console submission
**Effort:** 5 minutes
```
Sitemap: https://sigma.no/sitemap.xml
```

---

## High Priority — Fix Within 1 Week

### 8. Verify and Fix Hreflang
**Impact:** Prevents EN/NO pages from competing as duplicates; correct language targeting
**Effort:** 2–4 hours
```html
<!-- On /en/ pages -->
<link rel="alternate" hreflang="en" href="https://sigma.no/en/[path]/">
<link rel="alternate" hreflang="nb" href="https://sigma.no/[path]/">
<link rel="alternate" hreflang="x-default" href="https://sigma.no/[path]/">
```
- Verify bidirectionality: NO pages must reference EN, EN pages must reference NO
- Confirm in Google Search Console → International Targeting

### 9. Add Author Bylines and Staff Profiles
**Impact:** Directly addresses QRG Expertise requirement; E-E-A-T uplift
**Effort:** 1–2 days
- Add author bio to every insights/blog post
- Create 5–6 named expert profiles with photo, title, credentials, LinkedIn URL
- Add `Person` schema to profile pages

### 10. Expand English Service Pages to 800+ Words Each
**Impact:** Removes thin content penalty; topical authority for IT consulting keywords
**Effort:** 2–3 days of copywriting
Priority pages:
1. Cloud Services
2. Application/Software Development
3. IT Consulting
4. Data & Analytics (if exists)
5. Cybersecurity (if exists)

Each page needs: methodology, technology specifics, team context, a linked case study.

### 11. Fix Core Web Vitals — Async/Defer Scripts
**Impact:** INP improvement, TBT reduction, LCP improvement
**Effort:** 2–4 hours
```html
<!-- Add async to GTM -->
<script async src="https://www.googletagmanager.com/gtm.js?id=GTM-XXXXXX"></script>
<!-- Move non-critical analytics to Window Loaded trigger in GTM -->
```

### 12. Convert Hero Image to WebP
**Impact:** 30–50% file size reduction → LCP improvement
**Effort:** Enable Umbraco ImageSharp WebP pipeline (config change)
```html
<picture>
  <source srcset="/media/hero.avif" type="image/avif">
  <source srcset="/media/hero.webp" type="image/webp">
  <img src="/media/hero.jpg" alt="..." width="1920" height="1080" fetchpriority="high">
</picture>
```

### 13. Enable HTML Edge Caching (Cloudflare)
**Impact:** 100–400ms TTFB improvement for non-Norwegian visitors
**Effort:** 1 hour (Cloudflare Page Rules)
- Enable "Cache Everything" for `sigma.no/en/*` for anonymous users
- Edge Cache TTL: 1 hour

---

## Medium Priority — Fix Within 1 Month

### 14. Add FAQ Sections to All Service Pages
**Impact:** #1 action for AI Overviews inclusion and Featured Snippets
**Effort:** 1 day
- 5–7 FAQs per service page (Cloud, Dev, Consulting)
- Use `FAQPage` JSON-LD schema on each page
- Write in concise Q&A format for maximum AI extractability

### 15. Create 3 English-Language Case Studies
**Impact:** E-E-A-T Experience score, conversion driver, AI citation signal
**Effort:** 3–5 days
Format: Client challenge → Sigma approach (named technologies) → Measurable outcome
One per primary service: Cloud, App Dev, IT Consulting

### 16. Add BreadcrumbList Schema to All Inner Pages
**Impact:** Breadcrumb display in SERPs, improved site structure signals
**Effort:** 2 hours (CMS template)
```json
{ "@type": "BreadcrumbList", "itemListElement": [
  { "@type": "ListItem", "position": 1, "name": "Home", "item": "https://sigma.no/en/" },
  { "@type": "ListItem", "position": 2, "name": "Services", "item": "https://sigma.no/en/services/" }
]}
```

### 17. Create GenAI/LLM Services Page
**Impact:** Capture highest-growth category in IT consulting search queries
**Effort:** 2–3 days
- Cover: AI strategy consulting, LLM implementation, RAG systems, MLOps, responsible AI
- Minimum 1,000 words with methodology and case reference

### 18. Rewrite Homepage to 600+ Words
**Impact:** Removes thin content flag; keyword coverage; E-E-A-T uplift
**Effort:** Half day
- Add specific value proposition with differentiators
- Include credibility block: "Founded 1991 · 1,000+ consultants · Oslo & Kraków"
- Add service category links with descriptive anchor text

### 19. Add Service Schema to All Service Pages
**Impact:** Service rich results in SERPs, AI category matching
**Effort:** 2 hours (CMS template)

### 20. Add Font Preload and font-display: swap
**Impact:** Eliminates FOIT (invisible text), reduces CLS
**Effort:** 1 hour
```html
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="preload" as="font" href="/fonts/primary.woff2" type="font/woff2" crossorigin>
```
```css
@font-face { font-display: swap; }
```

### 21. Add Preconnect Hints for Third-Party Origins
**Impact:** 100–300ms load time improvement per third-party connection
**Effort:** 30 minutes
```html
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="preconnect" href="https://www.googletagmanager.com">
<link rel="preconnect" href="https://snap.licdn.com">
```

### 22. Fix Title Tags and Meta Descriptions (Top 10 Pages)
**Impact:** CTR improvement in SERPs; keyword relevance
**Effort:** 2–3 hours
- Lead with primary keyword, not brand name
- Add geo-specificity ("...across Norway and the Nordics")
- Include a CTA in meta description

### 23. Add LocalBusiness Schema for Oslo Office
**Impact:** Local pack eligibility; Knowledge Panel address
**Effort:** 1 hour

### 24. Replace Generic Anchor Text with Contextual Copy
**Impact:** Internal link equity distribution; keyword relevance
**Effort:** 2–3 hours
- Replace all "Learn more" / "Read more" with descriptive text
- e.g., "Explore our cloud migration services"

---

## Low Priority — Backlog

### 25. Create llms.txt at sigma.no/llms.txt
**Impact:** Emerging AI crawler standard for LLM content permissions
**Effort:** 1 hour

### 26. Add JobPosting Schema to Career Listings
**Impact:** Google for Jobs rich results → increased recruitment visibility
**Effort:** 2 hours (CMS template for job posts)

### 27. Add BlogPosting/Article Schema to Insights Content
**Impact:** Article rich results, author byline in SERPs
**Effort:** 2 hours (CMS template)

### 28. Add Sustainability/ESG Page
**Impact:** Vendor qualification criteria for Nordic enterprise clients
**Effort:** 1 day

### 29. Self-Host Google Fonts
**Impact:** Eliminates external DNS lookup; 100–300ms load improvement
**Effort:** 2–4 hours

### 30. Update robots.txt with AI Crawler Policy
**Impact:** Controls AI training vs. AI search crawler access
**Effort:** 30 minutes
See recommended robots.txt in FULL-AUDIT-REPORT.md

### 31. Fix Twitter Card Type
**Impact:** Large image previews on X/Twitter shares
**Effort:** 5 minutes
`<meta name="twitter:card" content="summary_large_image">`

### 32. Add Image Sitemaps for Case Study Pages
**Impact:** Image Search visibility for branded visual queries
**Effort:** 2 hours

---

## Implementation Roadmap

| Week | Focus | Actions |
|------|-------|---------|
| **Week 1** | Schema + CWV + Quick Wins | Items 1–7 |
| **Week 2** | Hreflang + Content + Performance | Items 8–13 |
| **Month 2** | Content depth + AI readiness | Items 14–24 |
| **Backlog** | Polish + emerging standards | Items 25–32 |

---

## Expected Score After Implementation

| Phase | Est. Score | Change |
|-------|-----------|--------|
| Current | 54/100 | — |
| After Week 1 (Critical) | ~62/100 | +8 |
| After Week 2 (High) | ~70/100 | +16 |
| After Month 2 (Medium) | ~78/100 | +24 |

---

*Action plan generated from: seo-technical + seo-content + seo-schema + seo-sitemap + seo-performance + seo-visual subagents*
*Full findings: FULL-AUDIT-REPORT.md | Date: 2026-02-28*
