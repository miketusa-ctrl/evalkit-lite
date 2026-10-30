# Harlo Agent Eval Kit

Ready-to-run evaluation packs for AI agents and chatbots: golden test cases, scoring rubrics, judge-prompt rules, a promptfoo config, and a no-code spreadsheet scoring path.

> **Evals are a quality process, not a guarantee.** Passing these packs means your agent behaved well on these cases — not that it will behave well everywhere. Re-run on every change and keep adding cases from real failures.

## Tiers
| Tier | What you get | License |
|---|---|---|
| **Lite** (free) | Support-bot pack (20 cases), 4 rubrics, promptfoo config, scoring sheet | MIT — [LICENSE](LICENSE) |
| **Pro** ($39) | + lead-qual, rag-docs, tool-calling-ops, personal-assistant packs, 12 rubrics, CI regression workflow, judge calibration | Single-org — [licenses/PRO-LICENSE.md](licenses/PRO-LICENSE.md) |
| **Team** ($99) | Pro + use on client work | Client-work — [licenses/TEAM-LICENSE.md](licenses/TEAM-LICENSE.md) |

Pro: 4 more packs (22 cases each), 12 rubrics, judge prompt, CI gate, calibration, Pro Guide (docs/PRO-GUIDE.md). Team adds docs/PACK-AUTHORING.md.

## Quick start
See [QUICKSTART.md](QUICKSTART.md). Short version:
```bash
npx --yes promptfoo@latest validate -c promptfoo/promptfooconfig.yaml
npx --yes promptfoo@latest eval -c promptfoo/promptfooconfig.yaml --no-cache
```
No API keys needed — the default provider is an offline echo. Or score by hand with [sheets/scoring-template.csv](sheets/scoring-template.csv).

## Layout
- [docs/PACK-FORMAT.md](docs/PACK-FORMAT.md) — case schema, rubric template, judge-prompt rules
- [docs/for-agents.md](docs/for-agents.md) — brief for AI agents using this kit
- [packs/support-bot/](packs/support-bot/) — Lite pack (cases.jsonl, cases.csv)
- [rubrics/](rubrics/) — scoring rubrics (1–5 scale)
- [promptfoo/promptfooconfig.yaml](promptfoo/promptfooconfig.yaml)
- [scripts/calibrate-judge.md](scripts/calibrate-judge.md), [scripts/calibrate_judge.py](scripts/calibrate_judge.py)
- [.github/workflows/eval-regression.yml](.github/workflows/eval-regression.yml)

## Using with Muse
Packs are plain JSONL/CSV and work for evaluating assistants built for Muse or any other platform. Harlo is not affiliated with Meta.

## Related Harlo kits
Support, Lead Qual, and Security kits cover building those agents; this kit tests them.

All companies, people, and numbers in test data are fictional.

Contact: digitalpromohub.support@gmail.com

## Buy

- Pro ($39): https://payhip.com/b/b1jJq
- Team ($99): https://payhip.com/b/bhLlp
- Lite (free): https://github.com/miketusa-ctrl/evalkit-lite
