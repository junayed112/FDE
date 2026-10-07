# Observation: Haiku 4.5 vs Sonnet 5 vs Opus 5.5

## Setup

All three models got the same prompt (`prompts/01.txt`):

> Make a single page .html for my company

The prompt did not include any details about the company: no name, industry, services, or contact info.

| Model      | Output file              | Size                 |
|------------|--------------------------|----------------------|
| Haiku 4.5  | `hello.html`             | 68 lines, ~1.8 KB    |
| Sonnet 5   | `index.html`             | 154 lines, ~6.0 KB   |
| Opus 5.5   | `assignment/company.html`| 247 lines, ~10.5 KB  |

## What each model produced

### Haiku 4.5: a very basic page
- One centered card on a purple gradient background.
- A "Hello 👋" heading, one line of text ("Welcome to your company's page. Update this content..."), and a "Get Started" button that links nowhere (`#`).
- No navigation, sections, contact form, footer, or dark mode.
- It's closer to a welcome screen than a company website.

### Sonnet 5: a full landing-page template
- Sticky header with a nav bar (Services, About, Contact).
- Hero section with a headline and two call-to-action buttons.
- **Services**: three service cards.
- **About**: a short story placeholder and stats (10+ years, 200+ clients, 24/7 support).
- **Contact**: a form (name, email, message) that uses `mailto:`.
- Footer, responsive layout, and dark mode support through CSS variables.

### Opus 5.5: a more complete and polished template
Everything Sonnet built, plus:
- A brand logo mark, a frosted-glass sticky header, and a "Contact us" button in the nav.
- A hero "eyebrow" badge ("Now taking new clients for 2026") and a trust bar (120+ clients, 8 years, 4.9/5 rating).
- **How we work**: a 4-step process (Discovery → Proposal → Delivery → Ongoing support).
- **Testimonial**: a customer quote block.
- **Contact**: email, phone, and office address next to the form. Form fields have proper labels and `autocomplete`.
- Better accessibility and finish: `aria-hidden`, `prefers-reduced-motion` support, and fluid `clamp()` typography.
- Guidance written into the placeholder text, e.g. "Keep each service below to one sentence of benefit, not features."

## Is my original observation correct?

**Mostly yes, with one correction.**

| My observation | Verdict |
|---|---|
| Haiku made a very basic HTML file | ✅ Correct |
| Sonnet 5 didn't ask any questions before building | ✅ Correct |
| Opus 5.5 didn't ask any questions either | ✅ Correct |
| Opus built a better website than Sonnet | ✅ Correct: more sections, more polish, better accessibility |
| Sonnet/Opus included information **about my company** | ❌ **Not quite** |

**Correction:** Neither Sonnet nor Opus had any real information about my company, because I never gave them any. Both pages use **placeholder content**: "Your Company", "Service One", `hello@yourcompany.com`, `+1 (555) 000-0000`, "Replace this with a real quote...". The stats (10+ years, 200+ clients, 120+ clients, 4.9/5) are made-up sample numbers, not facts.

So the more accurate statement is:
> Sonnet and Opus built more complete **templates** with more sections where company information should go. Opus built the most complete structure. None of the models actually knew anything about my company.

## Key differences

| Aspect | Haiku 4.5 | Sonnet 5 | Opus 5.5 |
|---|---|---|---|
| Asked clarifying questions? | No | No | No |
| Page type | Single welcome card | Standard landing page | Fuller business landing page |
| Sections | 1 | Hero, Services, About, Contact, Footer | Hero, Services, Process, Testimonial, Contact, Footer |
| Navigation | None | Yes | Yes, plus a header CTA button |
| Contact form | No | Yes | Yes, with labels and contact details |
| Dark mode | No | Yes | Yes |
| Accessibility touches | Minimal | Basic | Labels, autocomplete, aria, reduced-motion |
| Real company info | None | None (placeholders) | None (placeholders) |

## Takeaways

1. **Bigger model = more complete output from the same vague prompt.** Haiku did the minimum, Sonnet built a reasonable standard site, and Opus anticipated more of what a real business site needs (process, social proof, trust signals).
2. **No model asked for missing information.** All three guessed instead of asking for the company name, services, or contact details. That's why every output is a generic template.
3. **The prompt limits the result.** To get a page that's actually about my company, the prompt needs to include the company details, or explicitly tell the model to ask questions before building.
