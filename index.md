---
layout: default
title: Health Data Benchmark Leaderboard
---

# Benchmark Leaderboard

- Last updated: 2026-02-22T02:09:26Z
- Benchmark version: `3.0.0` (major `3`)
- Runs included: `20260222T002221+0000`, `20260221T232400+0000`, `20260221T180302+0000`, `20260220T234636+0000`
- Policy: rank by `accuracy > cost > runtime`
- † = effective hybrid cost/runtime (`text_only + vision_only` components, reuse mode)
- ⚠️ = likely API failure (near-zero cost, <30s runtime, <50% accuracy) — excluded from ranking
- ✖ = incomplete/failed strategy run (timeouts, missing extraction, preflight failure) — excluded from ranking
- Parenthesized counts show `correct/total` gold rows for that metric.
- `Not Reported` is the display name for benchmark `not_measured` rows (gold analyte was absent in the source PDF).
- **Tested** column = date the model was last benchmarked

## Current Recommendation

- `google/gemini-3-pro-preview` + `text_only`
- Status acc: 98.72% (77/78); measured recall: 98.04% (50/51); not reported acc: 100.00% (27/27)
- Core value acc: 100.00%; cost: $0.60; runtime: 325.5s
- Last tested: 2026-02-21

## Leaderboard Insights

<!-- Regenerate with LLM judgment after reviewing tables below. -->
<!-- Key questions: Who improved? Who dropped? Any new cost-down options at equivalent accuracy? -->

## Metric Definitions

- `Status Acc` — Overall measured-vs-not_measured classification rate across all gold analytes. Displayed as percent and, when available, `correct/total`.
- `Measured Recall` — Among analytes expected to be present (`status=measured`), the fraction predicted as measured.
- `Not Reported Acc` — Among analytes expected to be absent (`status=not_measured`), the fraction correctly left absent/marked missing.
- `Core Value Acc` — Exact value-match rate on core analytes (semantic match; `66` == `66.0`).
- `Ranking Cost` — For hybrid reuse mode: effective cost = `text_only + vision_only`.
- `Ranking Runtime` — For hybrid reuse mode: effective runtime = `text_only + vision_only`.
- `Run Status` — `Complete` means all benchmark docs finished successfully for that strategy; partial/failed runs are shown but not ranked.
- `Tested` — Date of most recent benchmark run for that entry.

## Top 10 Snapshot (All-Up)

One row per active-modality model (`text_only` dedupes by text model, `vision_only` dedupes by vision model). Hybrid rows remain per `(text, vision)` pair and label both as `(t)` and `(v)`.

| Rank | Model | Strategy | Run Status | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Ranking Cost | Ranking Runtime | Tested |
|---|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `google/gemini-3-pro-preview` | `text_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.60 | 325.5s | 2026-02-21 |
| 2 | `google/gemini-3-pro-preview (t)`<br>`google/gemini-3-flash-preview (v)` | `hybrid` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.70† | 478.1s† | 2026-02-21 |
| 3 | `anthropic/claude-sonnet-4.6` | `vision_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.72 | 302.5s | 2026-02-22 |
| 4 | `anthropic/claude-opus-4.6` | `vision_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.20 | 353.4s | 2026-02-22 |
| 5 | `anthropic/claude-opus-4.6` | `text_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.25 | 364.7s | 2026-02-22 |
| 6 | `anthropic/claude-sonnet-4.6 (t)`<br>`anthropic/claude-sonnet-4.6 (v)` | `hybrid` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.53† | 701.1s† | 2026-02-22 |
| 7 | `anthropic/claude-opus-4.6 (t)`<br>`anthropic/claude-opus-4.6 (v)` | `hybrid` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $2.45† | 718.2s† | 2026-02-22 |
| 8 | `x-ai/grok-4.1-fast (t)`<br>`x-ai/grok-4.1-fast (v)` | `hybrid` | Complete | 98.72% | — | — | 96.88% | $0.05 | 418.2s | 2026-02-20 |
| 9 | `x-ai/grok-4.1-fast` | `text_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 93.75% | $0.03 | 322.1s | 2026-02-22 |
| 10 | `anthropic/claude-sonnet-4.6` | `text_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 93.75% | $0.81 | 398.5s | 2026-02-22 |

## Top 10 Snapshot (Text-Only)

One entry per text model; best result when tested multiple times.

| Rank | Text Model | Run Status | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Cost | Runtime | Tested |
|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `google/gemini-3-pro-preview` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.60 | 325.5s | 2026-02-21 |
| 2 | `anthropic/claude-opus-4.6` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.25 | 364.7s | 2026-02-22 |
| 3 | `x-ai/grok-4.1-fast` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 93.75% | $0.03 | 322.1s | 2026-02-22 |
| 4 | `anthropic/claude-sonnet-4.6` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 93.75% | $0.81 | 398.5s | 2026-02-22 |
| 5 | `z-ai/glm-4.7` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.10 | 1723.1s | 2026-02-21 |
| 6 | `z-ai/glm-5` | Complete | 97.44% (76/78) | 96.08% (49/51) | 100.00% (27/27) | 100.00% | $0.15 | 548.0s | 2026-02-21 |
| 7 | `openai/gpt-5.2` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.68 | 532.8s | 2026-02-22 |
| 8 | `google/gemini-3.1-pro-preview` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $1.01 | 598.1s | 2026-02-22 |
| 9 | `moonshotai/kimi-k2.5` | Complete | 94.87% (74/78) | 94.12% (48/51) | 96.30% (26/27) | 96.88% | $0.21 | 1075.3s | 2026-02-22 |
| 10 | `google/gemini-3-flash-preview` | Complete | 93.59% (73/78) | 90.20% (46/51) | 100.00% (27/27) | 100.00% | $0.11 | 182.0s | 2026-02-21 |

## Top 10 Snapshot (Vision-Only)

One entry per vision model; best result when tested multiple times.

| Rank | Vision Model | Run Status | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Cost | Runtime | Tested |
|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `anthropic/claude-sonnet-4.6` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.72 | 302.5s | 2026-02-22 |
| 2 | `anthropic/claude-opus-4.6` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.20 | 353.4s | 2026-02-22 |
| 3 | `google/gemini-3-pro-preview` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.66 | 383.4s | 2026-02-21 |
| 4 | `openai/gpt-5.2` | Complete | 88.46% (69/78) | 84.31% (43/51) | 96.30% (26/27) | 100.00% | $0.63 | 481.0s | 2026-02-22 |
| 5 | `google/gemini-3.1-pro-preview` | Complete | 87.18% (68/78) | 80.39% (41/51) | 100.00% (27/27) | 100.00% | $0.59 | 353.5s | 2026-02-22 |
| 6 | `google/gemini-3-flash-preview` | Complete | 80.77% (63/78) | 70.59% (36/51) | 100.00% (27/27) | 100.00% | $0.06 | 114.5s | 2026-02-21 |
| 7 | `qwen/qwen3.5-397b-a17b` | Complete | 76.92% (60/78) | 64.71% (33/51) | 100.00% (27/27) | 96.88% | $0.04 | 167.6s | 2026-02-22 |
| 8 | `qwen/qwen3.5-plus-02-15` | Complete | 75.64% (59/78) | 62.75% (32/51) | 100.00% (27/27) | 93.75% | $0.05 | 144.2s | 2026-02-22 |
| 9 | `x-ai/grok-4.1-fast` | Complete | 43.59% | — | — | 6.25% | $0.02 | 164.4s | 2026-02-20 |

---

## Full Ranked Table — All-Up

One row per active-modality model (`text_only` dedupes by text model, `vision_only` dedupes by vision model). Hybrid rows remain per `(text, vision)` pair and label both as `(t)` and `(v)`.

| Rank | Model | Strategy | Run Status | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Ranking Cost | Ranking Runtime | Tested |
|---|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `google/gemini-3-pro-preview` | `text_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.60 | 325.5s | 2026-02-21 |
| 2 | `google/gemini-3-pro-preview (t)`<br>`google/gemini-3-flash-preview (v)` | `hybrid` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.70† | 478.1s† | 2026-02-21 |
| 3 | `anthropic/claude-sonnet-4.6` | `vision_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.72 | 302.5s | 2026-02-22 |
| 4 | `anthropic/claude-opus-4.6` | `vision_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.20 | 353.4s | 2026-02-22 |
| 5 | `anthropic/claude-opus-4.6` | `text_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.25 | 364.7s | 2026-02-22 |
| 6 | `anthropic/claude-sonnet-4.6 (t)`<br>`anthropic/claude-sonnet-4.6 (v)` | `hybrid` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.53† | 701.1s† | 2026-02-22 |
| 7 | `anthropic/claude-opus-4.6 (t)`<br>`anthropic/claude-opus-4.6 (v)` | `hybrid` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $2.45† | 718.2s† | 2026-02-22 |
| 8 | `x-ai/grok-4.1-fast (t)`<br>`x-ai/grok-4.1-fast (v)` | `hybrid` | Complete | 98.72% | — | — | 96.88% | $0.05 | 418.2s | 2026-02-20 |
| 9 | `x-ai/grok-4.1-fast` | `text_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 93.75% | $0.03 | 322.1s | 2026-02-22 |
| 10 | `anthropic/claude-sonnet-4.6` | `text_only` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 93.75% | $0.81 | 398.5s | 2026-02-22 |
| 11 | `z-ai/glm-5 (t)`<br>`google/gemini-3-pro-preview (v)` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.03 | 101.4s | 2026-02-21 |
| 12 | `z-ai/glm-4.7` | `text_only` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.10 | 1723.1s | 2026-02-21 |
| 13 | `z-ai/glm-5` | `text_only` | Complete | 97.44% (76/78) | 96.08% (49/51) | 100.00% (27/27) | 100.00% | $0.15 | 548.0s | 2026-02-21 |
| 14 | `z-ai/glm-4.7 (t)`<br>`google/gemini-3-flash-preview (v)` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.16† | 1814.4s† | 2026-02-21 |
| 15 | `z-ai/glm-5 (t)`<br>`google/gemini-3-flash-preview (v)` | `hybrid` | Complete | 97.44% (76/78) | 96.08% (49/51) | 100.00% (27/27) | 100.00% | $0.21† | 647.8s† | 2026-02-21 |
| 16 | `google/gemini-3-pro-preview` | `vision_only` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.66 | 383.4s | 2026-02-21 |
| 17 | `openai/gpt-5.2` | `text_only` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.68 | 532.8s | 2026-02-22 |
| 18 | `google/gemini-3-flash-preview (t)`<br>`google/gemini-3-pro-preview (v)` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.88† | 619.8s† | 2026-02-21 |
| 19 | `google/gemini-3.1-pro-preview` | `text_only` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $1.01 | 598.1s | 2026-02-22 |
| 20 | `openai/gpt-5.2 (t)`<br>`openai/gpt-5.2 (v)` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $1.32† | 1013.8s† | 2026-02-22 |
| 21 | `google/gemini-3-pro-preview (t)`<br>`google/gemini-3-pro-preview (v)` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $1.38† | 854.6s† | 2026-02-21 |
| 22 | `google/gemini-3.1-pro-preview (t)`<br>`google/gemini-3.1-pro-preview (v)` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $1.60† | 951.6s† | 2026-02-22 |
| 23 | `moonshotai/kimi-k2.5 (t)`<br>`moonshotai/kimi-k2.5 (v)` | `hybrid` | Complete | 94.87% (74/78) | 94.12% (48/51) | 96.30% (26/27) | 96.88% | $0.03 | 214.0s | 2026-02-22 |
| 24 | `moonshotai/kimi-k2.5` | `text_only` | Complete | 94.87% (74/78) | 94.12% (48/51) | 96.30% (26/27) | 96.88% | $0.21 | 1075.3s | 2026-02-22 |
| 25 | `google/gemini-3-flash-preview` | `text_only` | Complete | 93.59% (73/78) | 90.20% (46/51) | 100.00% (27/27) | 100.00% | $0.11 | 182.0s | 2026-02-21 |
| 26 | `google/gemini-3-flash-preview (t)`<br>`google/gemini-3-flash-preview (v)` | `hybrid` | Complete | 93.59% (73/78) | 90.20% (46/51) | 100.00% (27/27) | 100.00% | $0.18† | 276.8s† | 2026-02-21 |
| 27 | `openai/gpt-5.2` | `vision_only` | Complete | 88.46% (69/78) | 84.31% (43/51) | 96.30% (26/27) | 100.00% | $0.63 | 481.0s | 2026-02-22 |
| 28 | `qwen/qwen3.5-plus-02-15` | `text_only` | Complete | 88.46% (69/78) | 84.31% (43/51) | 96.30% (26/27) | 96.88% | $0.08 | 453.2s | 2026-02-22 |
| 29 | `qwen/qwen3.5-plus-02-15 (t)`<br>`qwen/qwen3.5-plus-02-15 (v)` | `hybrid` | Complete | 88.46% (69/78) | 84.31% (43/51) | 96.30% (26/27) | 96.88% | $0.13† | 597.4s† | 2026-02-22 |
| 30 | `google/gemini-3.1-pro-preview` | `vision_only` | Complete | 87.18% (68/78) | 80.39% (41/51) | 100.00% (27/27) | 100.00% | $0.59 | 353.5s | 2026-02-22 |
| 31 | `qwen/qwen3.5-397b-a17b` | `text_only` | Complete | 83.33% (65/78) | 74.51% (38/51) | 100.00% (27/27) | 100.00% | $0.06 | 344.9s | 2026-02-22 |
| 32 | `qwen/qwen3.5-397b-a17b (t)`<br>`qwen/qwen3.5-397b-a17b (v)` | `hybrid` | Complete | 83.33% (65/78) | 74.51% (38/51) | 100.00% (27/27) | 100.00% | $0.10† | 512.5s† | 2026-02-22 |
| 33 | `google/gemini-3-flash-preview` | `vision_only` | Complete | 80.77% (63/78) | 70.59% (36/51) | 100.00% (27/27) | 100.00% | $0.06 | 114.5s | 2026-02-21 |
| 34 | `qwen/qwen3.5-397b-a17b` | `vision_only` | Complete | 76.92% (60/78) | 64.71% (33/51) | 100.00% (27/27) | 96.88% | $0.04 | 167.6s | 2026-02-22 |
| 35 | `qwen/qwen3.5-plus-02-15` | `vision_only` | Complete | 75.64% (59/78) | 62.75% (32/51) | 100.00% (27/27) | 93.75% | $0.05 | 144.2s | 2026-02-22 |
| 36 | `x-ai/grok-4.1-fast` | `vision_only` | Complete | 43.59% | — | — | 6.25% | $0.02 | 164.4s | 2026-02-20 |
| 37 | `z-ai/glm-4.7 (t)`<br>`google/gemini-3-pro-preview (v)` | `hybrid` | Complete | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | $0.75† | 229.1s† | 2026-02-21 |
| ✖ | `moonshotai/kimi-k2.5` | `vision_only` | Partial (1/3 docs) | 57.69% (45/78) | 35.29% (18/51) | 100.00% (27/27) | 46.88% | $0.05 | 1549.8s | 2026-02-22 |

---

## Full Ranked Table — Text-Only

| Rank | Text Model | Run Status | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Ranking Cost | Ranking Runtime | Tested |
|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `google/gemini-3-pro-preview` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.60 | 325.5s | 2026-02-21 |
| 2 | `google/gemini-3-pro-preview` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.64 | 363.6s | 2026-02-21 |
| 3 | `anthropic/claude-opus-4.6` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.25 | 364.7s | 2026-02-22 |
| 4 | `x-ai/grok-4.1-fast` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 93.75% | $0.03 | 322.1s | 2026-02-22 |
| 5 | `anthropic/claude-sonnet-4.6` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 93.75% | $0.81 | 398.5s | 2026-02-22 |
| 6 | `z-ai/glm-4.7` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.10 | 1723.1s | 2026-02-21 |
| 7 | `z-ai/glm-5` | Complete | 97.44% (76/78) | 96.08% (49/51) | 100.00% (27/27) | 100.00% | $0.15 | 548.0s | 2026-02-21 |
| 8 | `openai/gpt-5.2` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.68 | 532.8s | 2026-02-22 |
| 9 | `google/gemini-3.1-pro-preview` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $1.01 | 598.1s | 2026-02-22 |
| 10 | `z-ai/glm-5` | Complete | 94.87% (74/78) | 94.12% (48/51) | 96.30% (26/27) | 100.00% | $0.13 | 1573.6s | 2026-02-21 |
| 11 | `moonshotai/kimi-k2.5` | Complete | 94.87% (74/78) | 94.12% (48/51) | 96.30% (26/27) | 96.88% | $0.21 | 1075.3s | 2026-02-22 |
| 12 | `google/gemini-3-flash-preview` | Complete | 93.59% (73/78) | 90.20% (46/51) | 100.00% (27/27) | 100.00% | $0.11 | 182.0s | 2026-02-21 |
| 13 | `google/gemini-3-flash-preview` | Complete | 93.59% (73/78) | 90.20% (46/51) | 100.00% (27/27) | 100.00% | $0.12 | 176.8s | 2026-02-21 |
| 14 | `qwen/qwen3.5-plus-02-15` | Complete | 88.46% (69/78) | 84.31% (43/51) | 96.30% (26/27) | 96.88% | $0.08 | 453.2s | 2026-02-22 |
| 15 | `qwen/qwen3.5-397b-a17b` | Complete | 83.33% (65/78) | 74.51% (38/51) | 100.00% (27/27) | 100.00% | $0.06 | 344.9s | 2026-02-22 |
| 16 | `z-ai/glm-4.7` | Complete | 64.10% (50/78) | 45.10% (23/51) | 100.00% (27/27) | 50.00% | $0.09 | 1376.3s | 2026-02-21 |

---

## Full Ranked Table — Vision-Only

| Rank | Vision Model | Run Status | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Ranking Cost | Ranking Runtime | Tested |
|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `anthropic/claude-sonnet-4.6` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.72 | 302.5s | 2026-02-22 |
| 2 | `anthropic/claude-opus-4.6` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.20 | 353.4s | 2026-02-22 |
| 3 | `google/gemini-3-pro-preview` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.66 | 383.4s | 2026-02-21 |
| 4 | `google/gemini-3-pro-preview` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.69 | 463.5s | 2026-02-21 |
| 5 | `google/gemini-3-pro-preview` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.76 | 437.8s | 2026-02-21 |
| 6 | `google/gemini-3-pro-preview` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.78 | 529.1s | 2026-02-21 |
| 7 | `openai/gpt-5.2` | Complete | 88.46% (69/78) | 84.31% (43/51) | 96.30% (26/27) | 100.00% | $0.63 | 481.0s | 2026-02-22 |
| 8 | `google/gemini-3.1-pro-preview` | Complete | 87.18% (68/78) | 80.39% (41/51) | 100.00% (27/27) | 100.00% | $0.59 | 353.5s | 2026-02-22 |
| 9 | `google/gemini-3-flash-preview` | Complete | 80.77% (63/78) | 70.59% (36/51) | 100.00% (27/27) | 100.00% | $0.06 | 114.5s | 2026-02-21 |
| 10 | `google/gemini-3-flash-preview` | Complete | 79.49% (62/78) | 68.63% (35/51) | 100.00% (27/27) | 100.00% | $0.06 | 99.7s | 2026-02-21 |
| 11 | `google/gemini-3-flash-preview` | Complete | 79.49% (62/78) | 68.63% (35/51) | 100.00% (27/27) | 100.00% | $0.06 | 100.0s | 2026-02-21 |
| 12 | `google/gemini-3-flash-preview` | Complete | 78.21% (61/78) | 66.67% (34/51) | 100.00% (27/27) | 100.00% | $0.06 | 91.3s | 2026-02-21 |
| 13 | `qwen/qwen3.5-397b-a17b` | Complete | 76.92% (60/78) | 64.71% (33/51) | 100.00% (27/27) | 96.88% | $0.04 | 167.6s | 2026-02-22 |
| 14 | `qwen/qwen3.5-plus-02-15` | Complete | 75.64% (59/78) | 62.75% (32/51) | 100.00% (27/27) | 93.75% | $0.05 | 144.2s | 2026-02-22 |
| 15 | `x-ai/grok-4.1-fast` | Complete | 43.59% | — | — | 6.25% | $0.02 | 164.4s | 2026-02-20 |
| ✖ | `moonshotai/kimi-k2.5` | Partial (1/3 docs) | 57.69% (45/78) | 35.29% (18/51) | 100.00% (27/27) | 46.88% | $0.05 | 1549.8s | 2026-02-22 |

---

## Full Ranked Table — Hybrid

†  = effective cost/runtime (`text_only + vision_only`).

| Rank | Text Model | Vision Model | Strategy | Run Status | Status Acc | Measured Recall | Not Reported Acc | Core Value Acc | Ranking Cost | Ranking Runtime | Tested |
|---|---|---|---|---|---:|---:|---:|---:|---:|---:|---|
| 1 | `google/gemini-3-pro-preview` | `google/gemini-3-flash-preview` | `hybrid` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $0.70† | 478.1s† | 2026-02-21 |
| 2 | `anthropic/claude-sonnet-4.6` | `anthropic/claude-sonnet-4.6` | `hybrid` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $1.53† | 701.1s† | 2026-02-22 |
| 3 | `anthropic/claude-opus-4.6` | `anthropic/claude-opus-4.6` | `hybrid` | Complete | 98.72% (77/78) | 98.04% (50/51) | 100.00% (27/27) | 100.00% | $2.45† | 718.2s† | 2026-02-22 |
| 4 | `x-ai/grok-4.1-fast` | `x-ai/grok-4.1-fast` | `hybrid` | Complete | 98.72% | — | — | 96.88% | $0.05 | 418.2s | 2026-02-20 |
| 5 | `z-ai/glm-5` | `google/gemini-3-pro-preview` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.03 | 101.4s | 2026-02-21 |
| 6 | `z-ai/glm-4.7` | `google/gemini-3-flash-preview` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.16† | 1814.4s† | 2026-02-21 |
| 7 | `z-ai/glm-5` | `google/gemini-3-flash-preview` | `hybrid` | Complete | 97.44% (76/78) | 96.08% (49/51) | 100.00% (27/27) | 100.00% | $0.21† | 647.8s† | 2026-02-21 |
| 8 | `google/gemini-3-flash-preview` | `google/gemini-3-pro-preview` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $0.88† | 619.8s† | 2026-02-21 |
| 9 | `openai/gpt-5.2` | `openai/gpt-5.2` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $1.32† | 1013.8s† | 2026-02-22 |
| 10 | `google/gemini-3-pro-preview` | `google/gemini-3-pro-preview` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $1.38† | 854.6s† | 2026-02-21 |
| 11 | `google/gemini-3.1-pro-preview` | `google/gemini-3.1-pro-preview` | `hybrid` | Complete | 97.44% (76/78) | 98.04% (50/51) | 96.30% (26/27) | 100.00% | $1.60† | 951.6s† | 2026-02-22 |
| 12 | `moonshotai/kimi-k2.5` | `moonshotai/kimi-k2.5` | `hybrid` | Complete | 94.87% (74/78) | 94.12% (48/51) | 96.30% (26/27) | 96.88% | $0.03 | 214.0s | 2026-02-22 |
| 13 | `google/gemini-3-flash-preview` | `google/gemini-3-flash-preview` | `hybrid` | Complete | 93.59% (73/78) | 90.20% (46/51) | 100.00% (27/27) | 100.00% | $0.18† | 276.8s† | 2026-02-21 |
| 14 | `qwen/qwen3.5-plus-02-15` | `qwen/qwen3.5-plus-02-15` | `hybrid` | Complete | 88.46% (69/78) | 84.31% (43/51) | 96.30% (26/27) | 96.88% | $0.13† | 597.4s† | 2026-02-22 |
| 15 | `qwen/qwen3.5-397b-a17b` | `qwen/qwen3.5-397b-a17b` | `hybrid` | Complete | 83.33% (65/78) | 74.51% (38/51) | 100.00% (27/27) | 100.00% | $0.10† | 512.5s† | 2026-02-22 |
| 16 | `z-ai/glm-4.7` | `google/gemini-3-pro-preview` | `hybrid` | Complete | 34.62% (27/78) | 0.00% (0/51) | 100.00% (27/27) | 0.00% | $0.75† | 229.1s† | 2026-02-21 |

---

## Benchmark Version Policy

| Bump | Meaning | Action required |
|------|---------|----------------|
| **Patch** (x.x.→) | No scoring impact (metadata, doc fixes) | None — old scores stay valid |
| **Minor** (x.→.0) | Additive (new docs, expanded analyte set) | Optional retest — existing scores comparable |
| **Major** (→.0.0) | Breaking (scoring formula, analyte scope, gold answer changes) | Full retest required — old scores excluded from ranking |


---

*Benchmark `v3.0.0` · 48 active entries · 4 run(s) · Generated 2026-02-22T02:09:26Z*
