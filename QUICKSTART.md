# Quickstart (<10 minutes)

## Path A — promptfoo (needs Node 18+, no API keys)
```bash
cd evalkit
npx --yes promptfoo@latest validate -c promptfoo/promptfooconfig.yaml   # schema check
npx --yes promptfoo@latest eval -c promptfoo/promptfooconfig.yaml --no-cache --no-share  # offline echo smoke run
npx --yes promptfoo@latest view   # optional local report
```
The default "echo" provider proves wiring only. An offline `promptfoo eval` with echo is **expected to fail** (nearly all assertions) until you plug in a real agent — that does not mean the pack is broken. To evaluate your agent, edit `providers:` to point at it (http, exec, or file provider) and set `defaultTest.options.provider` to a judge model. Follow judge rules in docs/PACK-FORMAT.md.

If npx is unavailable, check syntax: `python3 -c "import yaml;yaml.safe_load(open('promptfoo/promptfooconfig.yaml'))"`.

## Path B — spreadsheet (no code)
1. Open `packs/support-bot/cases.csv` and `sheets/scoring-template.csv` in any spreadsheet app.
2. Send each `input` (with `context` as system info) to your agent; paste the reply into `agent_answer`.
3. Score each rubric 1–5 using `rubrics/*.yaml`. Only score rubrics listed in that case's `rubric_ids`.
4. overall_pass_fail = pass if every applicable rubric ≥4; fail if any ≤2; else partial.
5. Re-run after every change; add a case for each real failure.

Evals are a quality process, not a guarantee.
