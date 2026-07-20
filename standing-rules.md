# JobFairX Blog — Standing Production Rules
_Applies to every post, every week. The scheduled drafting sessions follow these._

1. **NEVER use raw screenshots of jobfairx.com in posts.** Rebuild any product UI, pricing, comparison, or event page as coded HTML/CSS components (see jfx-components-snippets.html — 7 components, .jfx- prefixed). Charts are the exception: generated fresh as images from data, descriptive filenames + sentence alt text with the numbers in it.
2. Voice: Scott Lobenberg, founder. Casual-confident, short sentences, no filler, no AI-isms ("leverage", "streamline", "I'd love to" banned). Direct, honest, willing to say where JobFairX is NOT the answer.
2b. **Avoid em dashes.** Use commas, periods, colons, or parentheses instead. En dashes in numeric ranges (56-102 days) are fine. Max 2-3 em dashes per post, only where nothing else works. Scott's explicit rule.
3. Product accuracy: JobFairX = pre-qualified, self-scheduled interviews on event day. Never "post your job," never "resume database." Verified first-party stats OK to cite: 91% average interview show rate, 35 avg interviews/employer, 8 avg hires/employer (from live event pages); pricing $495/$895/$1,495.
4. Structure per post: answer-first opening (2-3 sentences that answer the title), question-phrased H2s, sourced stats with quotable standalone lines, one honest caveat section, 4-question FAQ, soft one-line CTA.
5. Every draft ships with: full markdown, coded components + charts, meta title/description, slug, BlogPosting + FAQPage JSON-LD (BlogPosting matches the site convention), cross-links to >=3 existing posts, and a 2-3 item backlink list (links to add FROM old posts on publish day).
6. SEO template fixes (verified by DOM audit Jul 2026): og:type=article, per-post og:image, descriptive sentence alts, WebP + width/height, lazy-load below fold only, bump dateModified on refreshes.
7. Each new post gets added to the Review Hub (index.html) as a new toggle in its week, with its own "SEO — before & after publish" panel.
8. Publish rhythm: drafts written Mon + Wed; Scott publishes Tue + Thu. Stay 2+ weeks ahead.
