---
name: hulk-two-pass-review
description: >
  Professional two-pass review system for code, marketing copy, and sales funnels.
  Pass 1 audits structure, logic, and architecture. Pass 2 audits polish, tone,
  conversion mechanics, and surface-level errors. Outputs ranked fix lists with
  severity scoring. De-HULKed — clear, direct, no fluff.

  Activate when the user says: "review this", "audit my code", "check my copy",
  "funnel review", "landing page audit", "two-pass review", "code review",
  "email sequence audit", or any variant of asking for structured feedback on
  code, copy, or conversion assets.
---

# hulk-two-pass-review

A two-pass review framework that separates structural problems from polish
problems. Most reviewers mix both — you get overwhelmed by typo notes when the
funnel logic is broken. This skill enforces separation so fixes happen in the
right order.

---

## Invoke

```
/hulk-two-pass-review [code|copy|funnel] <paste or path>
```

---

## Philosophy

| Pass | Question | What It Finds | Fix Order |
|------|----------|---------------|-----------|
| **Pass 1 — Structure** | "Does this work?" | Logic errors, missing steps, broken flow, architectural debt, conversion leaks | Fix first — everything else is lipstick |
| **Pass 2 — Polish** | "Does this sell?" | Typos, weak CTAs, muddy headlines, tone mismatches, visual hierarchy, loading speed | Fix second — only after structure is sound |

**Rule:** Never report a Pass 2 issue if a Pass 1 issue blocks the same area.

---

## Pass 1 — Structure Audit

### Code Reviews

Checklist (stop at first failure in each chain):

1. **Entry Points** — Are inputs validated? Are edge cases handled?
2. **Control Flow** — Can any branch hang, leak, or exit silently?
3. **Dependencies** — Are imports pinned? Are there circular deps?
4. **Error Handling** — Are errors caught, logged, and surfaced to the user?
5. **State Management** — Is mutable state isolated? Are race conditions possible?
6. **Performance** — Is there O(n²) where O(n) works? Unbounded memory growth?
7. **Security** — Injection surfaces, secret exposure, auth bypasses?

Output format:
```
[SEVERITY] [LINE/RANGE] [CATEGORY] — Description
  → Fix: Concrete change
  → Why: Business impact if left unfixed
```

Severity scale: `CRITICAL` (blocks ship) / `WARN` (fix before scale) / `NOTE` (nice to have)

### Copy Reviews (Landing Pages, Emails, Ads)

1. **Promise Clarity** — Can a stranger state the offer in one sentence?
2. **Credibility Stack** — Proof elements present? In the right order?
3. **Friction Audit** — How many decisions does the reader make before buying?
4. **Single Action** — Is there one clear next step per section?
5. **Objection Handling** — Top 3 objections addressed before they arise?
6. **Risk Reversal** — Guarantee, refund, or trial visible above the fold?

### Funnel Reviews

1. **Traffic-to-Lead Ratio** — Is the lead magnet specific enough to attract buyers, not browsers?
2. **Lead-to-Sale Bridge** — How many emails between opt-in and offer? Is each one earning its send?
3. **Upsell Logic** — Is the bump/upsell a natural extension or a random add-on?
4. **Abandonment Recovery** — Cart/browse/email abandonment sequences active?
5. **Tracking Integrity** — Can you attribute revenue to source, creative, and landing variant?

---

## Pass 2 — Polish Audit

### Surface Check

- Typos, grammar, broken links
- Mobile rendering (check on actual device, not just inspector)
- Load speed: < 2s first paint, < 4s interactive
- Image alt text, meta descriptions, OG tags

### Conversion Polish

- Headline: Specific result + timeframe + without-pain formula?
- CTA button copy: Action verb + value, not "Submit"
- Color contrast on primary CTA (WCAG AA minimum)
- Form fields: Minimum viable fields (name + email beats 8-field forms)
- Social proof placement: Above fold, near CTA, at decision points

### Tone Consistency

- Voice matches audience (corporate ≠ street, technical ≠ fluffy)
- No mixed metaphors or jargon without explanation
- Consistent person (I/we/you) throughout

---

## Output Template

```
═══════════════════════════════════════════════
  TWO-PASS REVIEW: [Asset Name]
  Reviewer: hulk-two-pass-review v1.0.0
═══════════════════════════════════════════════

── PASS 1: STRUCTURE ──
Found [N] structural issues

[CRITICAL] [Location] — [Issue]
  → Fix: [Action]
  → Why: [Impact]

[WARN] [Location] — [Issue]
  → Fix: [Action]
  → Why: [Impact]

── PASS 2: POLISH ──
Found [N] polish issues
(Only reported because Pass 1 is clean in these areas)

[WARN] [Location] — [Issue]
  → Fix: [Action]

── PRIORITY QUEUE ──
1. [Highest impact structural fix]
2. [Next structural fix]
3. [First polish fix]
...

── ESTIMATED FIX TIME ──
[Structural fixes: X min] + [Polish fixes: Y min] = Total Z min
```

---

## Agent Decision Tree

```
User: "Review my landing page"

1. Classify asset type (code / copy / funnel)
2. Run Pass 1 — Structure Audit
   → If CRITICAL found: report only CRITICAL + WARN, stop
   → If no CRITICAL: report all structural, continue
3. Run Pass 2 — Polish Audit (only on areas Pass 1 cleared)
4. Output Priority Queue
5. Report estimated fix time
```

---

## Rules

1. **Never mix passes.** Structure first, polish second. No exceptions.
2. **Always cite location.** Line numbers for code, section names for copy.
3. **Every issue needs a fix.** Don't flag without prescribing.
4. **Severity is not opinion.** CRITICAL = blocks function or revenue. WARN = friction or risk. NOTE = optimization.
5. **Respect the de-HULK mandate.** Clear, direct, actionable. No military metaphors, no aggression, no fluff.
