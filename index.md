---
layout: default
title: Health Data Benchmark Leaderboard
---

# Benchmark Leaderboard

- Last updated: 2026-02-21T23:08:56Z
- Benchmark version: `3.0.0` (major `3`)
- Runs included: `20260221T180302+0000`, `20260220T234636+0000`
- Policy: rank by `accuracy > cost > runtime`
- † = effective hybrid cost/runtime (`text_only + vision_only` components, reuse mode)
- ⚠️ = likely API failure (near-zero cost, <30s runtime, <50% accuracy) — excluded from recommendation
- Parenthesized counts show `correct/total` gold rows for that metric.
- `Not Reported` is the display name for benchmark `not_measured` rows (gold analyte was absent in the source PDF).
- **Tested** column = date the model was last benchmarked

## Current Recommendation

- `anthropic/claude-sonnet-4.6` + `vision_only`
- Status acc: 98.72%; measured recall: —; not reported acc: —
- Core value acc: 100.00%; cost: $0.73; runtime: 217.2s
- Last tested: 2026-02-20

## Leaderboard Insights

- If you can accept a `1.28` percentage-point status-accuracy drop (`98.72%` to `97.44%`), `GLM-5` text-only is a major cost-down option: `$0.16` vs `$0.73` for the top recommendation (`78.4%` cheaper), but with much slower runtime (`602.8s` vs `217.2s`).
- Within the `98.72%` top-accuracy tier, `Sonnet-4.6` vision-only is the strongest default because it is cheaper and faster than other tie peers such as `GPT-5.2` vision-only (`$0.77`, `349.3s`) and `Opus-4.6` variants.
- `Grok-4.1-Fast` looks attractive on cost (`$0.03` text-only) but is not quality-equivalent: core value accuracy is `96.88%` versus `100.00%` for several peers, so it fits cost-sensitive fallback use more than primary default use.
- `Gemini-3-Flash-Preview` errors are mainly missed present analytes, not absent-analyte confusion: `Not Reported Acc` stays at `100.00%`, while `Measured Recall` is materially lower (`82.35%` text-only, `68.63%` vision-only).
- `Gemini-3-Pro-Preview` should be treated as failure artifact, not genuine low quality, in this run: repeated `34.62% (27/78)` status accuracy, `0.00% (0/51)` measured recall, and near-zero/unknown cost across multiple strategies indicate an API/path issue requiring clean retest.
- Freshness is good (all shown entries tested on `2026-02-20` or `2026-02-21`), but model-family interpretation still matters: the `Gemini-3.1` family is currently far stronger/more stable than `Gemini-3-Pro-Preview`, so older-family results should not be used as current ground truth without revalidation.

## Metric Definitions

- `Status Acc` — Overall measured-vs-not_measured classification rate across all gold analytes. Displayed as percent and, when available, `correct/total`.
- `Measured Recall` — Among analytes expected to be present (`status=measured`), the fraction predicted as measured.
- `Not Reported Acc` — Among analytes expected to be absent (`status=not_measured`), the fraction correctly left absent/marked missing.
- `Core Value Acc` — Exact value-match rate on core analytes (semantic match; `66` == `66.0`).
- `Ranking Cost` — For hybrid reuse mode: effective cost = `text_only + vision_only`.
- `Ranking Runtime` — For hybrid reuse mode: effective runtime = `text_only + vision_only`.
- `Tested` — Date of most recent benchmark run for that entry.

## Top 10 Snapshot (All-Up)

Model uses the active strategy modality (`text_only` -> text model, `vision_only` -> vision model). Hybrid rows label both as `(t)` and `(v)`.

| Rank | Model | Strategy | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Ranking Cost | Ranking Runtime | Tested |
|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `anthropic/claude-sonnet-4.6` | `vision_only` | 98.72% | — | — | 100.00% | $0.73 | 217.2s | 2026-02-20 |
| 2 | `openai/gpt-5.2` | `vision_only` | 98.72% | — | — | 100.00% | $0.77 | 349.3s | 2026-02-20 |
| 3 | `google/gemini-3.1-pro-preview` | `text_only` | 98.72% | — | — | 100.00% | $0.96 | 357.9s | 2026-02-20 |
| 4 | `anthropic/claude-opus-4.6` | `vision_only` | 98.72% | — | — | 100.00% | $1.21 | 210.0s | 2026-02-20 |
| 5 | `anthropic/claude-opus-4.6` | `text_only` | 98.72% | — | — | 100.00% | $1.24 | 221.2s | 2026-02-20 |
| 6 | `anthropic/claude-sonnet-4.6 (t)`<br>`anthropic/claude-sonnet-4.6 (v)` | `hybrid` | 98.72% | — | — | 100.00% | $1.54 | 438.9s | 2026-02-20 |
| 7 | `anthropic/claude-opus-4.6 (t)`<br>`anthropic/claude-opus-4.6 (v)` | `hybrid` | 98.72% | — | — | 100.00% | $2.45 | 431.2s | 2026-02-20 |
| 8 | `x-ai/grok-4.1-fast` | `text_only` | 98.72% | — | — | 96.88% | $0.03 | 253.8s | 2026-02-20 |
| 9 | `x-ai/grok-4.1-fast (t)`<br>`x-ai/grok-4.1-fast (v)` | `hybrid` | 98.72% | — | — | 96.88% | $0.05 | 418.2s | 2026-02-20 |
| 10 | `anthropic/claude-sonnet-4.6` | `text_only` | 98.72% | — | — | 93.75% | $0.81 | 221.7s | 2026-02-20 |

## Top 10 Snapshot (Text-Only)

One entry per text model; best result when tested multiple times.

| Rank | Text Model | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Cost | Runtime | Tested |
|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `google/gemini-3.1-pro-preview` | 98.72% | — | — | 100.00% | $0.96 | 357.9s | 2026-02-20 |
| 2 | `anthropic/claude-opus-4.6` | 98.72% | — | — | 100.00% | $1.24 | 221.2s | 2026-02-20 |
| 3 | `x-ai/grok-4.1-fast` | 98.72% | — | — | 96.88% | $0.03 | 253.8s | 2026-02-20 |
| 4 | `anthropic/claude-sonnet-4.6` | 98.72% | — | — | 93.75% | $0.81 | 221.7s | 2026-02-20 |
| 5 | `z-ai/glm-5` | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.16 | 602.8s | 2026-02-21 |
| 6 | `openai/gpt-5.2` | 97.44% | — | — | 100.00% | $0.64 | 246.6s | 2026-02-20 |
| 7 | `z-ai/glm-4.7` | 94.87% (74/78) | 94.12% (48/51) | 96.30% (26/27) | 100.00% | $0.15 | 2017.7s | 2026-02-21 |
| 8 | `qwen/qwen3.5-397b-a17b` | 93.59% | — | — | 100.00% | $0.39 | 1173.8s | 2026-02-20 |
| 9 | `moonshotai/kimi-k2.5` | 92.31% | — | — | 93.75% | $0.12 | 1147.0s | 2026-02-20 |
| 10 | `qwen/qwen3.5-plus-02-15` | 88.46% | — | — | 100.00% | $0.08 | 286.6s | 2026-02-20 |

## Top 10 Snapshot (Vision-Only)

One entry per vision model; best result when tested multiple times.

| Rank | Vision Model | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Cost | Runtime | Tested |
|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `anthropic/claude-sonnet-4.6` | 98.72% | — | — | 100.00% | $0.73 | 217.2s | 2026-02-20 |
| 2 | `openai/gpt-5.2` | 98.72% | — | — | 100.00% | $0.77 | 349.3s | 2026-02-20 |
| 3 | `anthropic/claude-opus-4.6` | 98.72% | — | — | 100.00% | $1.21 | 210.0s | 2026-02-20 |
| 4 | `google/gemini-3.1-pro-preview` | 97.44% | — | — | 100.00% | $1.00 | 368.8s | 2026-02-20 |
| 5 | `google/gemini-3-flash-preview` | 79.49% (62/78) | 68.63% (35/51) | 100.00% (27/27) | 100.00% | $0.06 | 102.0s | 2026-02-21 |
| 6 | `moonshotai/kimi-k2.5` | 78.21% | — | — | 96.88% | $0.09 | 218.8s | 2026-02-20 |
| 7 | `qwen/qwen3.5-plus-02-15` | 75.64% | — | — | 93.75% | $0.05 | 98.1s | 2026-02-20 |
| 8 | `qwen/qwen3.5-397b-a17b` | 75.64% | — | — | 93.75% | $0.06 | 116.3s | 2026-02-20 |
| 9 | `x-ai/grok-4.1-fast` | 43.59% | — | — | 6.25% | $0.02 | 164.4s | 2026-02-20 |
| 10 | `google/gemini-3-pro-preview` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 11.3s | 2026-02-21 |

---

## Full Ranked Table — All-Up

| Rank | Text Model | Vision Model | Strategy | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Ranking Cost | Ranking Runtime | Tested |
|---|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `anthropic/claude-sonnet-4.6` | `anthropic/claude-sonnet-4.6` | `vision_only` | 98.72% | — | — | 100.00% | $0.73 | 217.2s | 2026-02-20 |
| 2 | `openai/gpt-5.2` | `openai/gpt-5.2` | `vision_only` | 98.72% | — | — | 100.00% | $0.77 | 349.3s | 2026-02-20 |
| 3 | `google/gemini-3.1-pro-preview` | `google/gemini-3.1-pro-preview` | `text_only` | 98.72% | — | — | 100.00% | $0.96 | 357.9s | 2026-02-20 |
| 4 | `anthropic/claude-opus-4.6` | `anthropic/claude-opus-4.6` | `vision_only` | 98.72% | — | — | 100.00% | $1.21 | 210.0s | 2026-02-20 |
| 5 | `anthropic/claude-opus-4.6` | `anthropic/claude-opus-4.6` | `text_only` | 98.72% | — | — | 100.00% | $1.24 | 221.2s | 2026-02-20 |
| 6 | `anthropic/claude-sonnet-4.6` | `anthropic/claude-sonnet-4.6` | `hybrid` | 98.72% | — | — | 100.00% | $1.54 | 438.9s | 2026-02-20 |
| 7 | `anthropic/claude-opus-4.6` | `anthropic/claude-opus-4.6` | `hybrid` | 98.72% | — | — | 100.00% | $2.45 | 431.2s | 2026-02-20 |
| 8 | `x-ai/grok-4.1-fast` | `x-ai/grok-4.1-fast` | `text_only` | 98.72% | — | — | 96.88% | $0.03 | 253.8s | 2026-02-20 |
| 9 | `x-ai/grok-4.1-fast` | `x-ai/grok-4.1-fast` | `hybrid` | 98.72% | — | — | 96.88% | $0.05 | 418.2s | 2026-02-20 |
| 10 | `anthropic/claude-sonnet-4.6` | `anthropic/claude-sonnet-4.6` | `text_only` | 98.72% | — | — | 93.75% | $0.81 | 221.7s | 2026-02-20 |
| 11 | `z-ai/glm-5` | `google/gemini-3-flash-preview` | `text_only` | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.16 | 602.8s | 2026-02-21 |
| 12 | `z-ai/glm-5` | `google/gemini-3-pro-preview` | `text_only` | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.21 | 1097.6s | 2026-02-21 |
| 13 | `z-ai/glm-5` | `google/gemini-3-flash-preview` | `hybrid` | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.21† | 692.4s† | 2026-02-21 |
| 14 | `openai/gpt-5.2` | `openai/gpt-5.2` | `text_only` | 97.44% | — | — | 100.00% | $0.64 | 246.6s | 2026-02-20 |
| 15 | `google/gemini-3.1-pro-preview` | `google/gemini-3.1-pro-preview` | `vision_only` | 97.44% | — | — | 100.00% | $1.00 | 368.8s | 2026-02-20 |
| 16 | `openai/gpt-5.2` | `openai/gpt-5.2` | `hybrid` | 97.44% | — | — | 100.00% | $1.41 | 595.9s | 2026-02-20 |
| 17 | `google/gemini-3.1-pro-preview` | `google/gemini-3.1-pro-preview` | `hybrid` | 97.44% | — | — | 100.00% | $1.96 | 726.7s | 2026-02-20 |
| 18 | `z-ai/glm-4.7` | `google/gemini-3-pro-preview` | `text_only` | 94.87% (74/78) | 94.12% (48/51) | 96.30% (26/27) | 100.00% | $0.15 | 2017.7s | 2026-02-21 |
| 19 | `moonshotai/kimi-k2.5` | `moonshotai/kimi-k2.5` | `hybrid` | 94.87% | — | — | 96.88% | $0.21 | 1365.8s | 2026-02-20 |
| 20 | `qwen/qwen3.5-397b-a17b` | `qwen/qwen3.5-397b-a17b` | `text_only` | 93.59% | — | — | 100.00% | $0.39 | 1173.8s | 2026-02-20 |
| 21 | `qwen/qwen3.5-397b-a17b` | `qwen/qwen3.5-397b-a17b` | `hybrid` | 93.59% | — | — | 100.00% | $0.46 | 1290.1s | 2026-02-20 |
| 22 | `moonshotai/kimi-k2.5` | `moonshotai/kimi-k2.5` | `text_only` | 92.31% | — | — | 93.75% | $0.12 | 1147.0s | 2026-02-20 |
| 23 | `qwen/qwen3.5-plus-02-15` | `qwen/qwen3.5-plus-02-15` | `text_only` | 88.46% | — | — | 100.00% | $0.08 | 286.6s | 2026-02-20 |
| 24 | `google/gemini-3-flash-preview` | `google/gemini-3-pro-preview` | `text_only` | 88.46% (69/78) | 82.35% (42/51) | 100.00% (27/27) | 100.00% | $0.09 | 217.0s | 2026-02-21 |
| 25 | `google/gemini-3-flash-preview` | `google/gemini-3-flash-preview` | `text_only` | 88.46% (69/78) | 82.35% (42/51) | 100.00% (27/27) | 100.00% | $0.09 | 152.3s | 2026-02-21 |
| 26 | `qwen/qwen3.5-plus-02-15` | `qwen/qwen3.5-plus-02-15` | `hybrid` | 88.46% | — | — | 100.00% | $0.13 | 384.8s | 2026-02-20 |
| 27 | `google/gemini-3-flash-preview` | `google/gemini-3-flash-preview` | `hybrid` | 88.46% (69/78) | 82.35% (42/51) | 100.00% (27/27) | 100.00% | $0.15† | 244.1s† | 2026-02-21 |
| 28 | `google/gemini-3-pro-preview` | `google/gemini-3-flash-preview` | `vision_only` | 79.49% (62/78) | 68.63% (35/51) | 100.00% (27/27) | 100.00% | $0.06 | 102.0s | 2026-02-21 |
| 29 | `google/gemini-3-flash-preview` | `google/gemini-3-flash-preview` | `vision_only` | 79.49% (62/78) | 68.63% (35/51) | 100.00% (27/27) | 100.00% | $0.06 | 91.8s | 2026-02-21 |
| 30 | `z-ai/glm-4.7` | `google/gemini-3-flash-preview` | `vision_only` | 78.21% (61/78) | 66.67% (34/51) | 100.00% (27/27) | 100.00% | $0.06 | 91.4s | 2026-02-21 |
| 31 | `z-ai/glm-5` | `google/gemini-3-flash-preview` | `vision_only` | 78.21% (61/78) | 66.67% (34/51) | 100.00% (27/27) | 100.00% | $0.06 | 89.6s | 2026-02-21 |
| 32 | `moonshotai/kimi-k2.5` | `moonshotai/kimi-k2.5` | `vision_only` | 78.21% | — | — | 96.88% | $0.09 | 218.8s | 2026-02-20 |
| 33 | `qwen/qwen3.5-plus-02-15` | `qwen/qwen3.5-plus-02-15` | `vision_only` | 75.64% | — | — | 93.75% | $0.05 | 98.1s | 2026-02-20 |
| 34 | `qwen/qwen3.5-397b-a17b` | `qwen/qwen3.5-397b-a17b` | `vision_only` | 75.64% | — | — | 93.75% | $0.06 | 116.3s | 2026-02-20 |
| 35 | `z-ai/glm-4.7` | `google/gemini-3-flash-preview` | `text_only` | 55.13% (43/78) | 31.37% (16/51) | 100.00% (27/27) | 50.00% | $0.02 | 1916.9s | 2026-02-21 |
| 36 | `x-ai/grok-4.1-fast` | `x-ai/grok-4.1-fast` | `vision_only` | 43.59% | — | — | 6.25% | $0.02 | 164.4s | 2026-02-20 |
| 37 | `google/gemini-3-pro-preview` | `google/gemini-3-flash-preview` | `text_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 2.8s | 2026-02-21 |
| 38 | `google/gemini-3-pro-preview` | `google/gemini-3-pro-preview` | `text_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 3.5s | 2026-02-21 |
| 39 | `z-ai/glm-5` | `google/gemini-3-pro-preview` | `vision_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 11.3s | 2026-02-21 |
| 40 | `z-ai/glm-4.7` | `google/gemini-3-pro-preview` | `vision_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 11.5s | 2026-02-21 |
| 41 | `google/gemini-3-pro-preview` | `google/gemini-3-pro-preview` | `vision_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 12.2s | 2026-02-21 |
| 42 | `google/gemini-3-flash-preview` | `google/gemini-3-pro-preview` | `vision_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 12.4s | 2026-02-21 |
| 43 | `google/gemini-3-pro-preview` | `google/gemini-3-pro-preview` | `hybrid` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | —† | 15.7s† | 2026-02-21 |
| 44 | `google/gemini-3-pro-preview` | `google/gemini-3-flash-preview` | `hybrid` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | —† | 104.9s† | 2026-02-21 |
| 45 | `z-ai/glm-4.7` | `google/gemini-3-pro-preview` | `hybrid` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | —† | 229.1s† | 2026-02-21 |
| 46 | `google/gemini-3-flash-preview` | `google/gemini-3-pro-preview` | `hybrid` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | —† | 229.4s† | 2026-02-21 |
| 47 | `z-ai/glm-5` | `google/gemini-3-pro-preview` | `hybrid` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | —† | 1108.9s† | 2026-02-21 |

---

## Full Ranked Table — Text-Only

Vision Model column = configured hybrid pair (unused for text extraction).

| Rank | Text Model | Vision Model | Strategy | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Ranking Cost | Ranking Runtime | Tested |
|---|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `google/gemini-3.1-pro-preview` | `google/gemini-3.1-pro-preview` | `text_only` | 98.72% | — | — | 100.00% | $0.96 | 357.9s | 2026-02-20 |
| 2 | `anthropic/claude-opus-4.6` | `anthropic/claude-opus-4.6` | `text_only` | 98.72% | — | — | 100.00% | $1.24 | 221.2s | 2026-02-20 |
| 3 | `x-ai/grok-4.1-fast` | `x-ai/grok-4.1-fast` | `text_only` | 98.72% | — | — | 96.88% | $0.03 | 253.8s | 2026-02-20 |
| 4 | `anthropic/claude-sonnet-4.6` | `anthropic/claude-sonnet-4.6` | `text_only` | 98.72% | — | — | 93.75% | $0.81 | 221.7s | 2026-02-20 |
| 5 | `z-ai/glm-5` | `google/gemini-3-flash-preview` | `text_only` | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.16 | 602.8s | 2026-02-21 |
| 6 | `z-ai/glm-5` | `google/gemini-3-pro-preview` | `text_only` | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.21 | 1097.6s | 2026-02-21 |
| 7 | `openai/gpt-5.2` | `openai/gpt-5.2` | `text_only` | 97.44% | — | — | 100.00% | $0.64 | 246.6s | 2026-02-20 |
| 8 | `z-ai/glm-4.7` | `google/gemini-3-pro-preview` | `text_only` | 94.87% (74/78) | 94.12% (48/51) | 96.30% (26/27) | 100.00% | $0.15 | 2017.7s | 2026-02-21 |
| 9 | `qwen/qwen3.5-397b-a17b` | `qwen/qwen3.5-397b-a17b` | `text_only` | 93.59% | — | — | 100.00% | $0.39 | 1173.8s | 2026-02-20 |
| 10 | `moonshotai/kimi-k2.5` | `moonshotai/kimi-k2.5` | `text_only` | 92.31% | — | — | 93.75% | $0.12 | 1147.0s | 2026-02-20 |
| 11 | `qwen/qwen3.5-plus-02-15` | `qwen/qwen3.5-plus-02-15` | `text_only` | 88.46% | — | — | 100.00% | $0.08 | 286.6s | 2026-02-20 |
| 12 | `google/gemini-3-flash-preview` | `google/gemini-3-pro-preview` | `text_only` | 88.46% (69/78) | 82.35% (42/51) | 100.00% (27/27) | 100.00% | $0.09 | 217.0s | 2026-02-21 |
| 13 | `google/gemini-3-flash-preview` | `google/gemini-3-flash-preview` | `text_only` | 88.46% (69/78) | 82.35% (42/51) | 100.00% (27/27) | 100.00% | $0.09 | 152.3s | 2026-02-21 |
| 14 | `z-ai/glm-4.7` | `google/gemini-3-flash-preview` | `text_only` | 55.13% (43/78) | 31.37% (16/51) | 100.00% (27/27) | 50.00% | $0.02 | 1916.9s | 2026-02-21 |
| 15 | `google/gemini-3-pro-preview` | `google/gemini-3-flash-preview` | `text_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 2.8s | 2026-02-21 |
| 16 | `google/gemini-3-pro-preview` | `google/gemini-3-pro-preview` | `text_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 3.5s | 2026-02-21 |

---

## Full Ranked Table — Vision-Only

Text Model column = configured hybrid pair (unused for vision extraction).

| Rank | Text Model | Vision Model | Strategy | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Ranking Cost | Ranking Runtime | Tested |
|---|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `anthropic/claude-sonnet-4.6` | `anthropic/claude-sonnet-4.6` | `vision_only` | 98.72% | — | — | 100.00% | $0.73 | 217.2s | 2026-02-20 |
| 2 | `openai/gpt-5.2` | `openai/gpt-5.2` | `vision_only` | 98.72% | — | — | 100.00% | $0.77 | 349.3s | 2026-02-20 |
| 3 | `anthropic/claude-opus-4.6` | `anthropic/claude-opus-4.6` | `vision_only` | 98.72% | — | — | 100.00% | $1.21 | 210.0s | 2026-02-20 |
| 4 | `google/gemini-3.1-pro-preview` | `google/gemini-3.1-pro-preview` | `vision_only` | 97.44% | — | — | 100.00% | $1.00 | 368.8s | 2026-02-20 |
| 5 | `google/gemini-3-pro-preview` | `google/gemini-3-flash-preview` | `vision_only` | 79.49% (62/78) | 68.63% (35/51) | 100.00% (27/27) | 100.00% | $0.06 | 102.0s | 2026-02-21 |
| 6 | `google/gemini-3-flash-preview` | `google/gemini-3-flash-preview` | `vision_only` | 79.49% (62/78) | 68.63% (35/51) | 100.00% (27/27) | 100.00% | $0.06 | 91.8s | 2026-02-21 |
| 7 | `z-ai/glm-4.7` | `google/gemini-3-flash-preview` | `vision_only` | 78.21% (61/78) | 66.67% (34/51) | 100.00% (27/27) | 100.00% | $0.06 | 91.4s | 2026-02-21 |
| 8 | `z-ai/glm-5` | `google/gemini-3-flash-preview` | `vision_only` | 78.21% (61/78) | 66.67% (34/51) | 100.00% (27/27) | 100.00% | $0.06 | 89.6s | 2026-02-21 |
| 9 | `moonshotai/kimi-k2.5` | `moonshotai/kimi-k2.5` | `vision_only` | 78.21% | — | — | 96.88% | $0.09 | 218.8s | 2026-02-20 |
| 10 | `qwen/qwen3.5-plus-02-15` | `qwen/qwen3.5-plus-02-15` | `vision_only` | 75.64% | — | — | 93.75% | $0.05 | 98.1s | 2026-02-20 |
| 11 | `qwen/qwen3.5-397b-a17b` | `qwen/qwen3.5-397b-a17b` | `vision_only` | 75.64% | — | — | 93.75% | $0.06 | 116.3s | 2026-02-20 |
| 12 | `x-ai/grok-4.1-fast` | `x-ai/grok-4.1-fast` | `vision_only` | 43.59% | — | — | 6.25% | $0.02 | 164.4s | 2026-02-20 |
| 13 | `z-ai/glm-5` | `google/gemini-3-pro-preview` | `vision_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 11.3s | 2026-02-21 |
| 14 | `z-ai/glm-4.7` | `google/gemini-3-pro-preview` | `vision_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 11.5s | 2026-02-21 |
| 15 | `google/gemini-3-pro-preview` | `google/gemini-3-pro-preview` | `vision_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 12.2s | 2026-02-21 |
| 16 | `google/gemini-3-flash-preview` | `google/gemini-3-pro-preview` | `vision_only` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | — | 12.4s | 2026-02-21 |

---

## Full Ranked Table — Hybrid

†  = effective cost/runtime (`text_only + vision_only`).

| Rank | Text Model | Vision Model | Strategy | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Ranking Cost | Ranking Runtime | Tested |
|---|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `anthropic/claude-sonnet-4.6` | `anthropic/claude-sonnet-4.6` | `hybrid` | 98.72% | — | — | 100.00% | $1.54 | 438.9s | 2026-02-20 |
| 2 | `anthropic/claude-opus-4.6` | `anthropic/claude-opus-4.6` | `hybrid` | 98.72% | — | — | 100.00% | $2.45 | 431.2s | 2026-02-20 |
| 3 | `x-ai/grok-4.1-fast` | `x-ai/grok-4.1-fast` | `hybrid` | 98.72% | — | — | 96.88% | $0.05 | 418.2s | 2026-02-20 |
| 4 | `z-ai/glm-5` | `google/gemini-3-flash-preview` | `hybrid` | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.21† | 692.4s† | 2026-02-21 |
| 5 | `openai/gpt-5.2` | `openai/gpt-5.2` | `hybrid` | 97.44% | — | — | 100.00% | $1.41 | 595.9s | 2026-02-20 |
| 6 | `google/gemini-3.1-pro-preview` | `google/gemini-3.1-pro-preview` | `hybrid` | 97.44% | — | — | 100.00% | $1.96 | 726.7s | 2026-02-20 |
| 7 | `moonshotai/kimi-k2.5` | `moonshotai/kimi-k2.5` | `hybrid` | 94.87% | — | — | 96.88% | $0.21 | 1365.8s | 2026-02-20 |
| 8 | `qwen/qwen3.5-397b-a17b` | `qwen/qwen3.5-397b-a17b` | `hybrid` | 93.59% | — | — | 100.00% | $0.46 | 1290.1s | 2026-02-20 |
| 9 | `qwen/qwen3.5-plus-02-15` | `qwen/qwen3.5-plus-02-15` | `hybrid` | 88.46% | — | — | 100.00% | $0.13 | 384.8s | 2026-02-20 |
| 10 | `google/gemini-3-flash-preview` | `google/gemini-3-flash-preview` | `hybrid` | 88.46% (69/78) | 82.35% (42/51) | 100.00% (27/27) | 100.00% | $0.15† | 244.1s† | 2026-02-21 |
| 11 | `google/gemini-3-pro-preview` | `google/gemini-3-pro-preview` | `hybrid` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | —† | 15.7s† | 2026-02-21 |
| 12 | `google/gemini-3-pro-preview` | `google/gemini-3-flash-preview` | `hybrid` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | —† | 104.9s† | 2026-02-21 |
| 13 | `z-ai/glm-4.7` | `google/gemini-3-pro-preview` | `hybrid` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | —† | 229.1s† | 2026-02-21 |
| 14 | `google/gemini-3-flash-preview` | `google/gemini-3-pro-preview` | `hybrid` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | —† | 229.4s† | 2026-02-21 |
| 15 | `z-ai/glm-5` | `google/gemini-3-pro-preview` | `hybrid` | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | —† | 1108.9s† | 2026-02-21 |

---

## Benchmark Version Policy

| Bump | Meaning | Action required |
|------|---------|----------------|
| **Patch** (x.x.→) | No scoring impact (metadata, doc fixes) | None — old scores stay valid |
| **Minor** (x.→.0) | Additive (new docs, expanded analyte set) | Optional retest — existing scores comparable |
| **Major** (→.0.0) | Breaking (scoring formula, analyte scope, gold answer changes) | Full retest required — old scores excluded from ranking |


---

*Benchmark `v3.0.0` · 47 active entries · 2 run(s) · Generated 2026-02-21T23:08:56Z*
