# Dev task: add the cost-per-hire scenario math to /employer/hiring-event-pricing

Scott's decision (Jul 20, 2026): the pricing/scenario table was removed from the cost-per-hire blog post
(informational SERP; nothing commercial ranks there — verified against the live Google results). The table is
strong conversion content, so it moves HERE, where buyers already are. Suggested placement: directly under the
three pricing tiers, before "All Packages Include."

Suggested heading: **What does this do to your cost per hire?**
Intro line: The U.S. average cost per hire is $5,475 (SHRM, 2025). Here's the same math on a flat-rate event.

```html
<table class="jfx-scenario">
  <tr><th>If you hire...</th><th>Starter ($495)</th><th>Growth ($895)</th><th>Pro ($1,495)</th></tr>
  <tr><td>1 person</td><td>$495/hire</td><td>$895/hire</td><td>$1,495/hire</td></tr>
  <tr><td>3 people</td><td>$165/hire</td><td>$298/hire</td><td>$498/hire</td></tr>
  <tr><td>5 people</td><td>$99/hire</td><td>$179/hire</td><td>$299/hire</td></tr>
  <tr><td>10 people</td><td>$50/hire*</td><td>$90/hire</td><td>$150/hire</td></tr>
</table>
<p class="jfx-note">*Ten hires on a Starter event means converting half of its 20+ interviews. Possible, but Growth is the realistic tier at that volume.</p>
<p class="jfx-note">Against a $5,475 national average (or $9,000+ in healthcare), even a single Starter-event hire comes in under 10% of the average.</p>
```

Style the table to match the existing pricing page (or reuse .jfx- table styles from jfx-components-snippets.html).
