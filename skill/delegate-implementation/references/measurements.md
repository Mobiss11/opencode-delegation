# Historical measurement notes

Numbers recorded from small local runs when the routing heuristic was authored. **These are historical claims without fresh validation** — not a quality ranking, not a fixed quota conversion, not a savings prediction for any other lead/worker pair or task family. Consult only while actively comparing or calibrating routing, and re-measure on representative accepted work with provider-dashboard usage before relying on any figure here.

## GPT-led delegation A/B (two local runs)

- A long lead session delegating used **more** GPT tokens than a fresh direct run.
- A fresh lead delegating a bounded duplicate-warning feature used roughly **56–63% fewer** GPT input/output/cache tokens than a fresh direct run.
- Caveats: n=2; session length confounded with delegation; GPT-subscription-only. No bearing on Alibaba or GLM plans.

## DeepSeek Flash High vs Max (12-run local coding check)

- High passed 6/6 tasks, Max 5/6; Max used about **twice the reasoning tokens** and cost **39% more**.
- Caveats: small sample; supports a routing hypothesis, not a universal ranking. Raw runs were not re-inspected during this update.

## GLM-5.3-Flash vs DeepSeek High (one-turn test, three Python functions with edge cases, two runs per worker)

- GLM-5.3-Flash and DeepSeek High each passed 6/6 complete test suites; GLM-5.3 passed 3/3 single runs.
- Median latency about **56 s** (GLM Flash) vs **6 s** (DeepSeek High); one Flash run took four steps rather than one.
- Caveats: single-turn toy scope; no evidence about full-repo edits or multi-file changes. GLM Coding Plan credits and DeepSeek API charges are **different budget dimensions**; verify GLM credits in the provider dashboard, not OpenCode's USD cost field.

## Qwen / Alibaba Token Plan

- Qwen routing is configured but **not yet calibrated**; nothing here supports any claim of Qwen delegation savings.
- On 2026-09-30 the user changed the active route to Qwen3.8 Max → DeepSeek V4.1 Flash High/Max, exclusively through Alibaba Token Plan. The earlier Qwen Flash smoke check below describes the previous route, not validation of these replacement workers. Catalog availability and both variant IDs were verified; comparative quality and plan savings remain unmeasured.

### Live configuration/skill check, 2026-09-29

- Qwen3.8 Flash edited this skill and extracted the historical reference. It returned PARTIAL after the lead requested a handoff: 1429 words versus the requested maximum of 1100. The lead completed compression, corrected an overly categorical savings statement, and integrated the user's later GLM-specific requirements. These are real review/integration costs.
- Qwen3.8 Max separately reviewed the profile configuration and four routing scenarios. It found consistent routes, repair limits and permission boundaries. This review preceded the later GLM-Flash restriction; final routing was checked statically by the lead against documented last-match permission semantics.
- Both model requests completed. This was an editing/review smoke check under a GPT lead, **not** an end-to-end Max-orchestrated coding task, controlled A/B, coding-quality benchmark or allowance measurement. Duration/token/plan usage totals were not returned in the completion reports and are unknown.

## GLM accounting source for future calibration

Reviewed 2026-09-29: [Z.AI plan overview](https://docs.z.ai/devpack/overview) and [plan accounting revision](https://docs.z.ai/devpack/notice/usage-revision). The new credits system weights input, cached input and output differently; legacy plans may retain different accounting. Identify the user's actual plan before applying rates. No account usage was accessed during this change, so rapid depletion cannot be attributed to a measured cause. The GLM profile reduces duplicate research, repeated context and same-plan worker usage; its actual savings still require representative usage measurements.
