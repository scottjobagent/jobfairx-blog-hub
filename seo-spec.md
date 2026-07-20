# JobFairX Blog — SEO Implementation Spec (all 4 posts)
_Research-backed, July 2026. Give this to the dev with the Review Hub. Everything below is ready to paste._

## Why these steps (30-second version of the research)

- **Images:** Google reads alt text + the surrounding paragraph + the filename together. Descriptive kebab-case filenames, natural one-sentence alt text (no keyword stuffing), WebP format, explicit width/height (prevents layout shift, a Core Web Vitals factor), lazy-load everything below the fold, `og:image` set per post. (Google Search Central)
- **AI Overviews:** 78% of AI Overviews contain a list — our posts are built around lists/tables on purpose. FAQ blocks in Q&A form + FAQPage schema + answer-first openings are the passage-level pattern that gets lifted. Content must be in raw HTML (ours is — coded components, no JS rendering). (SEOProfy AIO study)
- **E-E-A-T:** real author entity with a bio page, org schema, visible published/updated dates, cited sources. Stats pages must be refreshed every 3–6 months — stale stats fall out of AIOs.
- **Freshness cadence:** put a quarterly 30-min "stats refresh" on the calendar for every post with benchmarks. Update the number, bump dateModified.

## Site-wide (do once)

1. **Author page:** create `/employer/resources/authors/scott-lobenberg` (photo, 2–3 sentence bio, LinkedIn link). Link every byline to it. This is the entity Google/LLMs attach credibility to.
2. **Image pipeline:** serve WebP (keep PNG fallback via `<picture>` if easy), always set `width`/`height` attributes, `loading="lazy"` on below-fold images only (never the first image), `decoding="async"`.
3. **OG tags per post:** `og:title`, `og:description`, `og:image` (the post's chart), `og:type=article`.
4. **Canonical** self-referencing on every post; posts included in the XML sitemap with `lastmod`.
5. **Breadcrumbs:** Employers → Resources → [Post], with BreadcrumbList schema (nice-to-have).
6. **Validate every post** in Google's Rich Results Test after publishing schema. Then request indexing in GSC for each new URL on publish day.

## Image SEO — exact specs per image

| Post | Filename (rename to this) | Alt text | Notes |
|---|---|---|---|
| Cost Per Hire | `cost-per-hire-by-industry-2026.webp` | "Bar chart of 2026 U.S. cost per hire by industry, from $2,700 in retail to $16,000–$20,000 in legal, with healthcare highlighted at $9,000–$12,000" | First image — do NOT lazy-load. Set as og:image. |
| Why Hospitals Struggle | `healthcare-time-to-fill-by-industry-2026.webp` | "Time to fill by industry: logistics 12 days, retail 24.6, IT 30, health services 49 days, and 78 days to recruit an experienced RN" | First image — no lazy-load. og:image. |
| Recruiting Metrics | `recruiting-funnel-benchmarks-2026.webp` | "Recruiting funnel: of 180 applicants, about 5 reach an interview and 1 is hired, per CareerPlug 2025 data" | First image — no lazy-load. og:image. |
| (all coded components) | n/a — they're HTML, which is the point | n/a | Components render as text Google reads natively; better than any image. |

Numbers live in the alt text on purpose — that's the descriptive-not-stuffed pattern, and it's what makes the chart quotable to AI crawlers that read alt text.



---

## /employer/resources/cost-per-hire

**Article schema (paste in `<head>` or body as `<script type="application/ld+json">`, fill real dates):**

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Cost Per Hire: What It Is, 2026 Benchmarks by Industry, and How to Lower It",
  "description": "Average cost per hire is $5,475 in 2026 (SHRM) \u2014 $9,000+ in healthcare. See benchmarks by industry, the SHRM formula, and 6 ways to bring your number down.",
  "author": {
    "@type": "Person",
    "name": "Scott Lobenberg",
    "jobTitle": "Founder",
    "url": "https://jobfairx.com/about-us",
    "worksFor": {
      "@type": "Organization",
      "name": "JobFairX",
      "url": "https://jobfairx.com"
    }
  },
  "publisher": {
    "@type": "Organization",
    "name": "JobFairX",
    "url": "https://jobfairx.com",
    "logo": {
      "@type": "ImageObject",
      "url": "https://jobfairx.com/logo.png"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://jobfairx.com/employer/resources/cost-per-hire"
  },
  "datePublished": "2026-07-XX",
  "dateModified": "2026-07-XX",
  "image": "https://jobfairx.com/employer/resources/images/chart-cost-per-hire-by-industry.webp"
}
```

**FAQPage schema (answers match on-page FAQ copy):**

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is a good cost per hire?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Below your industry benchmark, trending down. For hourly and entry-level roles, under $3,000. Against the $5,475 U.S. average, anything under roughly $2,000 is strong \u2014 but read it together with time to fill."
      }
    },
    {
      "@type": "Question",
      "name": "What should be included in cost per hire?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Everything recruiting touches: recruiter and sourcer compensation (allocated), job boards, advertising, agencies, software, background checks, referral bonuses, interviewer time, and events. SHRM's formula: total internal + external recruiting costs divided by total hires."
      }
    },
    {
      "@type": "Question",
      "name": "Why is healthcare cost per hire so high?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Credentialing, licensure verification, a shrinking candidate pool, and competition. Healthcare hires cost $9,000-$12,000 and health services roles take the longest to fill of any industry at 49 days (Workable). NSI puts one RN turnover at $60,090."
      }
    },
    {
      "@type": "Question",
      "name": "Does cost per hire include onboarding?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Under the SHRM standard, no \u2014 it stops at the accepted offer. Some teams separately track cost per productive hire including onboarding and ramp; keep it separate so benchmark comparisons stay apples-to-apples."
      }
    }
  ]
}
```


---

## /employer/resources/why-hospitals-struggle-entry-level-clinical-hiring

**Article schema (paste in `<head>` or body as `<script type="application/ld+json">`, fill real dates):**

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Why Hospitals Struggle to Fill Entry-Level Clinical Roles \u2014 and What Actually Works",
  "description": "Hospitals take 49 days to fill roles while entry-level candidates decide in days. The 7 reasons clinical hiring stalls \u2014 and what actually fixes each one.",
  "author": {
    "@type": "Person",
    "name": "Scott Lobenberg",
    "jobTitle": "Founder",
    "url": "https://jobfairx.com/about-us",
    "worksFor": {
      "@type": "Organization",
      "name": "JobFairX",
      "url": "https://jobfairx.com"
    }
  },
  "publisher": {
    "@type": "Organization",
    "name": "JobFairX",
    "url": "https://jobfairx.com",
    "logo": {
      "@type": "ImageObject",
      "url": "https://jobfairx.com/logo.png"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://jobfairx.com/employer/resources/why-hospitals-struggle-entry-level-clinical-hiring"
  },
  "datePublished": "2026-07-XX",
  "dateModified": "2026-07-XX",
  "image": "https://jobfairx.com/employer/resources/images/chart-time-to-fill-by-industry.webp"
}
```

**FAQPage schema (answers match on-page FAQ copy):**

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Why do hospitals struggle with virtual job fairs?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Usually because they run them like virtual versions of the booth-and-banner fair: a lobby, some chat, no scheduled interviews. The format isn't the problem \u2014 the missing interview structure is. Virtual events work when every attendee is matched, screened, and booked into a time slot."
      }
    },
    {
      "@type": "Question",
      "name": "What makes it hard to fill clinical roles through job fairs?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Three things: generic audiences (a general job fair delivers few credentialed clinical candidates), no pre-screening (managers interview unqualified walk-ins), and no same-day interviews (resumes go in a pile and momentum dies). Fix those three and the format works."
      }
    },
    {
      "@type": "Question",
      "name": "How much does an unfilled nursing position cost?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "NSI's 2026 report puts RN turnover cost at $60,090 per nurse, with the average hospital losing $4.2-6.2 million annually. Every 1-point change in RN turnover costs or saves about $295,000 a year."
      }
    },
    {
      "@type": "Question",
      "name": "What's the fastest way to hire entry-level clinical staff?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Compress screening and interviewing into a single event day. Candidates matched to your roles self-schedule interviews, your team meets 20-100+ pre-qualified candidates in one day, and offers go out while candidates are still engaged."
      }
    }
  ]
}
```


---

## /employer/resources/how-to-choose-a-nurse-job-fair

**Article schema (paste in `<head>` or body as `<script type="application/ld+json">`, fill real dates):**

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "How to Choose a Nurse Job Fair: A Hospital Hiring Guide",
  "description": "7 criteria for picking a nurse job fair that produces hires, an honest comparison of event types, and what large hospital systems do differently.",
  "author": {
    "@type": "Person",
    "name": "Scott Lobenberg",
    "jobTitle": "Founder",
    "url": "https://jobfairx.com/about-us",
    "worksFor": {
      "@type": "Organization",
      "name": "JobFairX",
      "url": "https://jobfairx.com"
    }
  },
  "publisher": {
    "@type": "Organization",
    "name": "JobFairX",
    "url": "https://jobfairx.com",
    "logo": {
      "@type": "ImageObject",
      "url": "https://jobfairx.com/logo.png"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://jobfairx.com/employer/resources/how-to-choose-a-nurse-job-fair"
  },
  "datePublished": "2026-07-XX",
  "dateModified": "2026-07-XX"
}
```

**FAQPage schema (answers match on-page FAQ copy):**

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is the best entry-level job fair service for nurses?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The one that delivers pre-screened, scheduled interviews rather than booth traffic. Evaluate any service on seven criteria: pre-screening, scheduled interviews, clinical audience, show rate, multi-location support, flat pricing, and same-day reporting."
      }
    },
    {
      "@type": "Question",
      "name": "Which job fairs do large hospital systems use?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Typically a mix: their own open houses for brand, school fairs for new grad pipeline, and recurring healthcare-specific virtual events for volume interviewing \u2014 run on a standing monthly or bi-monthly cadence per region rather than as one-offs."
      }
    },
    {
      "@type": "Question",
      "name": "How much does a nurse job fair cost for employers?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Hosting your own runs $800-$3,000+ in hard costs plus weeks of staff time. Specialty virtual events run a few hundred to a few thousand dollars flat \u2014 JobFairX events start at $495 with 20+ scheduled interviews included. Compare everything on cost per scheduled interview, then cost per hire."
      }
    },
    {
      "@type": "Question",
      "name": "Are virtual job fairs effective for nurse recruiting?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Yes, when they're interview-structured: pre-screened clinical candidates, self-scheduled slots, same-day decisions. They're weak when they replicate the booth model on a screen. The format isn't the variable \u2014 the interview structure is."
      }
    }
  ]
}
```


---

## /employer/resources/recruiting-metrics

**Article schema (paste in `<head>` or body as `<script type="application/ld+json">`, fill real dates):**

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "10 Recruiting Metrics That Actually Matter in 2026",
  "description": "Only 3% of applicants reach an interview and 1 in 180 gets hired. The 10 recruiting metrics worth tracking, with formulas and 2026 benchmarks for each.",
  "author": {
    "@type": "Person",
    "name": "Scott Lobenberg",
    "jobTitle": "Founder",
    "url": "https://jobfairx.com/about-us",
    "worksFor": {
      "@type": "Organization",
      "name": "JobFairX",
      "url": "https://jobfairx.com"
    }
  },
  "publisher": {
    "@type": "Organization",
    "name": "JobFairX",
    "url": "https://jobfairx.com",
    "logo": {
      "@type": "ImageObject",
      "url": "https://jobfairx.com/logo.png"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://jobfairx.com/employer/resources/recruiting-metrics"
  },
  "datePublished": "2026-07-XX",
  "dateModified": "2026-07-XX",
  "image": "https://jobfairx.com/employer/resources/images/chart-recruiting-funnel.webp"
}
```

**FAQPage schema (answers match on-page FAQ copy):**

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What are the most important recruiting metrics?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "If you can only track three: cost per interview, interview show rate, and time to fill. They expose channel waste, scheduling failure, and process speed \u2014 the three places most recruiting budgets leak."
      }
    },
    {
      "@type": "Question",
      "name": "What is a good application-to-interview rate?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The cross-industry benchmark is 3% (CareerPlug, 10M+ applications). Well below that suggests screening bottlenecks or mistargeted postings; well above it with poor interview outcomes suggests screening that's too loose."
      }
    },
    {
      "@type": "Question",
      "name": "How do you measure recruiting effectiveness?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Per channel, per quarter: spend divided by interviews (cost per interview), interviews divided by hires, and 90-day retention of those hires. Effectiveness is a channel property, not a team property \u2014 measure it where the money goes."
      }
    },
    {
      "@type": "Question",
      "name": "What is a good offer acceptance rate?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "85%+ is strong. The 2026 range runs 69-92% by sector, with healthcare near 77%. Below 80%, look at process speed first \u2014 most declined offers were accepted somewhere faster."
      }
    }
  ]
}
```


---

## Publish-day checklist (per post, ~10 min)

1. Slug + meta title + meta description from the post's publishing notes.
2. Paste both schema blocks; fill datePublished/dateModified; validate in Rich Results Test.
3. Images: renamed filename, alt text from table above, width/height set, WebP.
4. Cross-links OUT already in the copy — verify they resolved.
5. Backlink pass: add the 2–3 links FROM existing posts listed in the publishing notes.
6. GSC → URL inspection → Request indexing.
7. Add the post to the sitemap with today's lastmod (usually automatic).

## The ranking reality check

On-page gets us eligible; the cluster + internal links get us competitive; time and refreshes get us to the top. These are KD 0–13 keywords against a DR 39 domain with proven employer-page rankings — #1 is realistic on most of them within 2–4 months IF the publish-day checklist actually happens every time, especially the backlink pass and the quarterly stat refresh.
