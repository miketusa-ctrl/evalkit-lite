# Pack format

A pack is a folder `packs/<name>/` with `README.md`, `cases.jsonl` (source of truth) and `cases.csv` (spreadsheet mirror).

## Case schema
| Field | Type | Notes |
|---|---|---|
| `id` | string | `<pack>-NNN`, unique, never reused |
| `input` | string | user message (or final turn) |
| `context` | string | system/business facts the agent may rely on (policy, account state) |
| `expected` | string | description of a good answer: must-do / must-not-do |
| `rubric_ids` | list[string] | rubric files in `rubrics/` that apply |
| `tags` | list[string] | e.g. `refund`, `angry`, `out_of_scope` |
| `difficulty` | `easy`\|`medium`\|`hard` | |

In CSV, lists are `;`-separated.

## Rubric template
Each `rubrics/<id>.yaml`: `id`, `name`, `measures` (one sentence), `scale` (1–5 with descriptor each), `pass_threshold` (default ≥4 pass, 3 partial, ≤2 fail), `examples` with one `pass`, `partial`, `fail` sample.

## Judge prompt requirements
- Output **strict JSON only**: `{"rubric_id": str, "score": 1-5, "verdict": "pass"|"partial"|"fail", "reason": str}`; reject and retry on parse failure.
- Give the judge the rubric text, case `context` and `expected`, and the answer — nothing else.
- Bias mitigations: score reasoning in `reason` before trusting score; ignore length (verbosity bias); one rubric per call; don't reveal which model produced the answer (self-preference); for pairwise, run both orders (position bias); calibrate against human labels (see scripts/calibrate-judge.md) before trusting.
