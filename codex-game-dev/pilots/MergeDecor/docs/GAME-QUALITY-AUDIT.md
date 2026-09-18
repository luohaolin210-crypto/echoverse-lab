# Merge Decor Game Quality Audit

- Project: H:\hello\merge-decor
- Scope: read-only pilot audit; no source, config, asset, save, or release file modified
- Audit date: 2026-09-18
- Engine evidence: Cocos Creator 3.8.7
- Evidence basis: source/config inspection, existing project tests, platform-boundary checks, and repository state
- Runtime test result: npm run check — platform boundaries PASS, core typecheck PASS, 200 passed, 0 failed
- REAL PLAYTEST: PENDING

## Executive Summary

Merge Decor has a tested slice covering tutorial, Generate, Merge, Order, reward, decoration placement, save/load, three areas, and progressive furniture thresholds. The loop is structurally real and is not merely a mock. The main quality risk is repetition: the inspected data uses one wood-focused merge chain and reuses furniture references across areas, so the strict area-difference Skin-Swap Gate fails for Coffee Corner to Reading Nook until the player decision/risk/feedback changes.

A missing area_complete audio asset was logged while the audio tests still passed. This must be resolved before claiming complete celebration feedback.

## CODE QUALITY

- npm run check passed: platform boundary check PASS; core TypeScript check PASS; test build and Node suite 200 passed, 0 failed.
- Cocos Creator 3.8.7 is the declared target.
- Merge, generator, energy, order, decoration, save/load, tutorial, platform, audio, and visual contracts are covered.
- No tracked changes were found in the project worktree after the audit.
- No source/config/asset/save/release change was intentionally made.

## GAMEPLAY QUALITY

### Core loop

| Question | Static/source result |
| --- | --- |
| Generate has a clear action/result? | Yes. The generator emits wood-chain items and consumes/requires energy through tested seams. |
| Merge has a clear upgrade result? | Yes. Valid merge combines equal items into the next configured chain item; invalid merge is rejected. |
| Is drag feedback natural? | Input and merge contracts exist; tactile latency and naturalness are not proven hands-on. |
| Is order completion meaningful? | Yes. Order readiness/progress/completion, coins, XP, and history are explicit. |
| Does furniture change the room? | Yes. Decoration slots, thresholds, placement, and area completion are modeled. |
| Is the long loop novel? | Not established; one generator and a single wood-centered chain create high repetition risk. |

### Skin-Swap Gate

COFFEE_CORNER_TO_READING_NOOK_SKIN_SWAP_GATE = FAIL

Areas have distinct names, order thresholds, unlock timing, and slot mappings, but the inspected configuration reuses the same furniture references/types across areas and keeps the same Generate to Merge to Order to Place grammar. No area-specific rule, resource tension, placement constraint, or feedback grammar was found that clearly changes player decisions and risks.

### Gameplay Reality Check

- Gameplay Hypothesis: merging a wood chain to satisfy orders and unlock furniture will create a satisfying shop-to-decoration loop.
- Expected Player Behavior: generate efficiently, merge strategically, prioritize ready orders, then place unlocked furniture.
- Why It May Be Fun: tactile combining plus visible room transformation can connect action to ownership.
- Cheapest Prototype: one 5–10 minute slice with one generator, one chain, one order, one merge celebration, and one furniture placement.
- Success Signal: unfamiliar players choose what to merge next, notice the order target, and explain why the room changed.
- Failure Signal: players repeat merges mechanically, ignore the room, or cannot identify why an order/furniture unlock matters.
- Human Validation: PENDING.

## VISUAL QUALITY

- Theme tokens, Chinese furniture names, art-path mappings, and runtime centered geometry are covered by automated visual tests.
- Furniture types are distinct by name/configuration, but area-level asset reuse creates a potential “same room, renamed” impression.
- Existing evidence/screenshot paths were located, but pixel-level visual inspection was unavailable.
- A visual system exists; the remaining risk is differentiation and hierarchy under dense board/order states.

## REAL PLAYTEST STATUS

REAL PLAYTEST = PENDING

Available evidence is automated tests, type checks, platform-boundary checks, source/config inspection, and located screenshot artifacts. No developer hands-on session, unfamiliar human session, or real device session was available.

Mock is not 真人验收. Headless is not 真人试玩. Build PASS is not 游戏好玩.

## P0

- None established by this read-only audit.

## P1

1. Skin-Swap Gate failure: Reading Nook needs a player-facing rule, risk, choice, or feedback difference beyond reused furniture/order/merge grammar.
2. Missing area_complete audio asset: the passing test run logs [Audio] Missing asset: area_complete.
3. Repetition risk after the first wood chain: one generator and one main chain may exhaust novelty before the first shop reaches 100%.
4. Real device and human evidence absent.

## P2

1. Compare before/after room states at every furniture threshold on a portrait device.
2. Measure the first point at which a player repeats the wood chain without a new choice.
3. Add an area-specific decision/risk prototype before expanding decoration volume.
4. Validate order-card density and board-vs-order attention in 390x844 and notched-device matrices.
5. Run an unfamiliar-player timed session across 0–1, 1–3, 3–10, and 10–30 minutes.

## Game Design

The tested first loop is coherent: tutorial, generate, merge, order, reward, and first decoration. Progression contains intermediate furniture thresholds. Three areas are represented with thresholds and completion rewards. The design currently changes content and room labels more than decision structure, which is the reason for the Skin-Swap failure.

## Game Feel

These are provisional static ratings, not human feel approval.

| Event | Rating | Evidence / limitation |
| --- | --- | --- |
| Generate | APPROPRIATE | Generator/energy state and tutorial feedback are explicit; tactile punch unverified. |
| Merge | APPROPRIATE | Valid/invalid merge and standard/advanced sound selection are tested; impact unverified. |
| Order ready | APPROPRIATE | Ready state and deterministic tutorial order are tested. |
| Order complete | APPROPRIATE | Coins/XP/history and feedback seams exist; ceremony unverified. |
| Furniture unlock | TOO_WEAK | Thresholds exist, but satisfaction was not proven by human play. |
| Furniture placement | APPROPRIATE | Placement and area progress are explicit; transformation strength unverified. |
| Area completion | TOO_WEAK | Completion reward exists, but area_complete is missing in test output and ceremony is not device-verified. |

OVERFEEDBACK_GATE = PASS at static-contract level. Audio tests cap rapid SFX and bound combinations; no blocking animation or particle occlusion was proven. Dense-state human validation remains pending.

## UI/UX

Runtime geometry tests assert centered progress, HUD, and navigation. Board, order cards, tutorial, decoration flow, and bottom navigation are distinct layers. Order-card density versus board attention was not visually sampled on device.

## Mobile Layout

The project targets a portrait-friendly layout and includes safe-area/device adapter seams. Runtime tests cover centered geometry and web/douyin platform behavior. A complete physical matrix, including notches and narrow widths, was not run.

## UI Hard Gate Results

| Gate | Static/automated evidence | Real visual/device status |
| --- | --- | --- |
| UI_OVERLAP | 0 reported by geometry contracts | PENDING |
| CLIPPED_TEXT | 0 reported by automated contracts | PENDING |
| OFFSCREEN_CRITICAL_UI | 0 reported by geometry/platform contracts | PENDING |
| UNLABELED_CORE_TARGET | 0 for tested player-facing labels/targets | PENDING |
| SAFE_AREA_VIOLATION | 0 reported by platform/geometry contracts | PENDING |

## Art Direction

- Visual style: warm shop/decor presentation with explicit theme tokens.
- Palette/material/icon/UI direction: represented by ThemeConfig, ArtConfig, and asset mappings.
- Shape/proportion consistency: automated visual tests cover named furniture types and centered layout.
- Asset scale risk: shared references across areas may weaken room identity even if individual assets are consistent.
- Forbidden-style risk: asset collage/reuse and insufficient area-specific identity.
- Complete reference board: not proven in this audit.

## Asset Pipeline

The project has an art path/mapping layer and tests validating configured furniture/merge assets. Unknown art references can fall back to programmatic mappings; resilient fallback can conceal missing production assets. In-game preview/compare/approve evidence was not completed on a real device. Missing area_complete audio is a concrete reminder that approval must include runtime event coverage.

## VFX

Merge/order/decoration feedback seams are present and bounded by audio/visual contracts. No static evidence of particle/z-order blocking was found. Dense board, order, and decoration states still need runtime visual QA and mobile performance sampling.

## Animation

Tutorial, merge, completion, and placement transitions are represented by tested state/event seams. No hands-on timing review was performed; technically complete transitions can still feel slow or underpowered.

## Rendering

Cocos Creator 3.8.7 is the declared target. Platform boundary and core typecheck pass. No draw-call, texture-memory, shader-cost, or real-device frame-time sample was collected. Rendering status: static PASS / target-device PENDING.

## Audio Feedback

Audio tests pass configuration, deduplication, cap, mute, lifecycle, and bounded-combination behavior. The test run logs [Audio] Missing asset: area_complete. This is a concrete P1 integration/asset gap for area completion.

## Retention

| Window | Static audit result |
| --- | --- |
| 0–1 minute | Tutorial teaches welcome, Generate, Merge, order, reward, and first decoration. |
| 1–3 minutes | First merge/order/decor progression provides a clear near-term goal. |
| 3–10 minutes | More orders and furniture thresholds create intermediate progress, but the same wood chain may become repetitive. |
| 10–30 minutes | Novelty is NOT ESTABLISHED; no unfamiliar-player timed evidence and no second core merge system were found. |
| First repetition | Exact player-time point is UNKNOWN; likely risk begins after the first deterministic chain/order loop. |
| First wood-chain fatigue | UNKNOWN without timed human observation; structurally high risk due one generator/chain. |
| Why complete 100% shop? | Threshold furniture, area completion, rewards, and next-area progression are explicit; motivation PENDING. |
| Intermediate goals | Yes: Coffee Corner thresholds 1/3/5/8/12, Reading Nook 13/15/17/19/21, and later Bar Counter thresholds. |

No shop-management system was implemented or assumed by this audit.

## Performance

Platform boundary check PASS, core typecheck PASS, and 200/200 tests pass. Real mobile frame time, draw calls, memory, shader cost, and thermal behavior remain PENDING.

## Playtest

Completed: automated tests, source/config inspection, platform-boundary and typecheck evidence.

Not completed: developer playtest, unfamiliar human playtest, real platform/device playtest.

## Skin-Swap Risks

Coffee Corner to Reading Nook currently fails the strict gate. Shared furniture references and identical merge/order grammar may make new areas feel like renamed content. More thresholds and orders alone do not constitute a new area experience.

## Overfeedback Risks

Static contracts show restrained audio caps and bounded combinations. Remaining risks are weak furniture/area ceremony and missing completion audio, not excessive feedback. Validate rapid merge, order completion, and area completion in a human/device session.

## Evidence

- H:\hello\merge-decor\package.json
- H:\hello\merge-decor\game.json
- H:\hello\merge-decor\README.md
- H:\hello\merge-decor\assets\scripts\merge\MergeBoard.ts
- H:\hello\merge-decor\assets\scripts\orders\OrderSystem.ts
- H:\hello\merge-decor\assets\scripts\decoration\DecorationProgressSystem.ts
- H:\hello\merge-decor\assets\scripts\audio\AudioManager.ts
- H:\hello\merge-decor\assets\scripts\ui\LayoutGeometry.ts
- H:\hello\merge-decor\assets\scripts\ui\ThemeConfig.ts
- H:\hello\merge-decor\assets\scripts\ui\ArtConfig.ts
- H:\hello\merge-decor\tests\*.test.ts
- H:\hello\merge-decor\docs\evidence and docs\screenshots, located but not pixel-inspected
- npm run check: platform PASS, typecheck PASS, 200 passed, 0 failed
- project worktree status: clean for tracked files

## Unknowns

Real Generate/Merge drag satisfaction; furniture visual impact; exact time to first repetition; order-board versus merge-board attention; real safe-area/text/z-order/asset scale; actual completion-audio timing and audibility.

## Recommended Next Actions

1. Prototype an area-specific rule or risk that changes player decisions before adding more thresholds.
2. Supply and verify the area_complete audio asset.
3. Run a timed unfamiliar-player session across 0–1, 1–3, 3–10, and 10–30 minutes.
4. Capture before/after room states and verify every furniture unlock changes the visual focal point.
5. Collect Cocos device metrics for draw calls, frame time, texture memory, and shader cost.

## Audit Conclusion

MERGE_DECOR_AUDIT = PASS — the read-only pilot audit was executed and evidence was recorded.

This is not a gameplay-quality PASS. Current quality findings include COFFEE_CORNER_TO_READING_NOOK_SKIN_SWAP_GATE = FAIL, missing area_complete audio evidence, and REAL PLAYTEST = PENDING.
