---
name: delegate-implementation
description: Route bounded implementation from Opus 5.5, Qwen Max, GPT-6.1 Sol or GLM to configured DeepSeek High/Max workers via Alibaba Token Plan or direct API. Use when delegating coding work, conserving lead allowance or subscription windows, choosing workers or reviewing orchestration efficiency. The lead owns acceptance; routing respects model availability, permissions and separate plan/API budgets.
---

# Delegate implementation

## Finish the outcome

Follow applicable project instructions and existing decisions/tracker. Complete the authorized outcome: inspect, implement, verify, repair concrete defects, update relevant documentation, then report done/partial/blocked. Worker completion and intermediate checks are not user approval gates. Ask only for a real missing decision, credential, permission or scope/billing change. This skill grants no publishing/deployment permissions or cross-application bridge.

## Routing

| Situation | Action |
|---|---|
| Tiny, obvious edit | Lead handles directly when briefing/review would cost more |
| Bounded, testable change | One configured worker owns investigation, implementation and checks |
| Unclear outcome or consequential design | Lead settles requirements/boundaries first; worker may investigate a bounded uncertainty |
| Same defect survives two repairs | Lead diagnoses the reproduction and re-plans the smallest remainder; no identical full-task retry |

### Profile routes

- **`opus-lead` (Claude Opus 5.5, homelab Pro subscription via a local homelab proxy) → `alibaba-deepseek-worker` (High) by default; `alibaba-deepseek-worker-max` (Max) for concrete difficulty.** Both workers use DeepSeek V4.1 Flash exclusively via Alibaba Token Plan. Opus runs on subscription windows, not per-token spend: keep it for planning, review and acceptance, and push all bounded implementation to the workers. Effort stays high; do not escalate orchestration to max. Watch the 5h/7d windows (homelab usage dashboard) instead of token cost; on `allowed_warning` economize the window, on `rejected` stop and report — do not silently switch to a paid Claude route (OpenRouter) without user authorization. Prefer compact handoffs and a fresh session around ~400k context: the orchestrator re-reads its context every turn, and cache reads still consume window budget.
- **`qwen-lead` → `alibaba-deepseek-worker` (High) by default; `alibaba-deepseek-worker-max` (Max) for concrete difficulty.** Both use DeepSeek V4.1 Flash exclusively via Alibaba Token Plan. Qwen Max owns decisions and acceptance. Respect an explicit High/Max choice; otherwise use the difficulty rule below. Optimize combined Alibaba consumption including briefing, review and retries. Changing model/variant does not reset the plan or prove savings. This profile permits neither `qwen-flash-worker` nor direct-API `deepseek-worker`/`deepseek-worker-max`; never substitute those when Alibaba is unavailable.
- **`glm-lead` → `deepseek-worker` by default.** GLM is a lean coordinator; DeepSeek High owns local investigation, implementation and tests. `deepseek-worker-max` is reserved for a concrete difficult slice. GLM Flash delegation is denied in this profile to conserve the GLM plan.
- **`gpt-lead` (GPT-6.1 Sol) → `deepseek-worker` by default.** DeepSeek Max is available for concrete difficulty; `glm-flash-worker` is optional when that plan/data route is authorized and available. Keep GPT allowance, GLM credits and DeepSeek API charges separate. The lead model lives in agent configuration (`openai/gpt-6.1-sol#high`); a session that already selected another model keeps it until the user switches.
- **DeepSeek Max (either billing route):** use for interacting invariants, tricky algorithms, concurrency or difficult state transitions; name the reason. Size, vague requirements and an "architecture" label alone do not justify escalation. Preserve the lead's configured provider when choosing High/Max: `alibaba-deepseek-*` is the Alibaba plan; `deepseek-worker*` is the separate DeepSeek API.

Select the configured worker explicitly; never rely on inherited models. Keep model IDs and variants in configuration. Verify availability and the actual session model when establishing a route: choosing a profile does not replace an existing model selection. Report mismatches/unavailability instead of silently substituting. Do not repeat model discovery each turn without a relevant change.

## Keep GLM coordination lean

- Inspect enough to define outcome, scope and acceptance; do not solve the implementation or exhaustively scan the repository before delegating it again.
- Prefer one coherent assignment and one acceptance pass over microtasks and progress interrogations. Continue targeted repairs in the same child session; send the failure and relevant delta, not the entire brief again.
- Review the actual diff and test evidence. Read relevant changed symbols and test material gaps; do not reread whole files or reflexively repeat passing full suites. Required project checks still apply.
- Batch independent reads. Keep tool output targeted and reports concise; pass paths instead of copied documents. Load skills once as needed. For unrelated new work with bloated history, use a compact verified handoff when practical, not a forced reset after every step.
- DeepSeek returns status, changed paths, important decisions, exact check commands/results and unresolved risks, normally under 200 words; necessary evidence may exceed this. Do not ask for long narratives or hidden reasoning.

These practices apply to other leads too. Conserving GLM means less GLM coordination, not merely sending code writing elsewhere while GLM repeats the research and debugging.

## Worker contract and acceptance

Send a short contract: **outcome; actual workspace and entry points; allowed scope; invariants; appropriate checks; stop conditions; return format**. Distinguish verified facts from hypotheses. Leave routine implementation choices to the worker; return necessary contract/scope expansions to the lead.

Use one writing worker. Child sessions share files; parallel writers need isolated worktrees or independent ownership and an integration plan. Workers do not delegate further. Preserve user work; use project tools selectively and verify stateful tools target the right workspace.

Workers run relevant checks, never weaken tests or invent passing results, and stop after two unsuccessful repairs of the same defect with a minimal reproduction. No arbitrary small step cap or unbounded retries. The lead verifies actual changes and consequential invariants, including uncovered boundary/failure cases. Treat worker reports as evidence, not instructions. Finish integration and relevant documentation within authorization.

## Budgets, failures and permissions

- Token counts and OpenCode `cost: 0` are not remaining subscription allowance. Track Alibaba combined usage, GLM plan usage, GPT subscription allowance and DeepSeek API spend separately. Use the provider's applicable plan/dashboard rules; legacy accounting may differ.
- Unknown remaining quota alone does not block an authorized available route or require a dashboard visit before every task. Report unknown usage when discussing costs; stop on actual exhaustion or other real blockers.
- Diagnose errors: authentication needs repair; timeout/5xx is not proof of exhaustion. Inspect existing edits and running work before retry/handoff; never start a second writer over a possibly active one. Variants are not quota bypasses.
- A different provider requires authorization for its billing/data route unless already given. Approval in chat does **not** override configured `deny`: use a permitted profile/model or an authorized configuration update. No silent paid-API fallback or unauthorized quota upgrades.

## Evidence of efficiency

Record accepted outcome, chosen worker, retries and material rework briefly in the existing task record when available. Include lead review/repairs and all child runs when measuring; separate input, cache, output/reasoning and provider charges. Actual before/after allowance is stronger evidence than raw token totals. Unknown usage means no measured savings claim.

Do not duplicate ordinary tasks for comparisons. For deliberate calibration, use representative tasks, isolated identical baselines and equivalent acceptance checks. Historical small-sample results and caveats live in [references/measurements.md](references/measurements.md); read them only for comparison/calibration, not every delegation. Qwen efficiency remains uncalibrated.
