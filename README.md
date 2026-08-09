# hulk-two-pass-review

Professional two-pass review system for code, marketing copy, and sales funnels.

## What It Does

Separates structural audits from polish audits so you fix what matters first.

- **Pass 1 — Structure:** Logic errors, broken flow, architectural debt, conversion leaks
- **Pass 2 — Polish:** Typos, weak CTAs, tone mismatches, visual hierarchy

## Install

### VS Code / Cursor / Copilot / ChatGPT / Codex / Kiro (Agent Plugins 1.0.0)

Install from this git URL in your client's plugin manager.

### Claude Code

```bash
claude install "https://github.com/Nate3point0/hulk-two-pass-review"
```

Or place the `.claude-plugin/` folder contents in your project root.

## Usage

```
/hulk-two-pass-review [code|copy|funnel] <your asset>
```

## Output

Ranked fix lists with severity scoring:
- `CRITICAL` — blocks ship
- `WARN` — fix before scale
- `NOTE` — nice to have

Every issue includes a concrete fix and business impact justification.

## License

MIT
