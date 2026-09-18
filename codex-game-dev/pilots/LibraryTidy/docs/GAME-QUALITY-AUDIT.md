# LibraryTidy Game Quality Audit

- Project: H:\got book
- Scope: read-only pilot audit; no source, config, asset, save, or release file modified
- Audit date: 2026-09-18
- Evidence basis: source inspection, existing project tests, static UI contracts, and repository state
- Runtime test result: npm test — 73 passed, 0 failed
- REAL PLAYTEST: PENDING

## Executive Summary

LibraryTidy has a runnable archive loop: select a book, choose a shelf, receive success/failure feedback, and progress through a zone. Correctness evidence is strong and Combo has an explicit reward purpose. Under the strict Skin-Swap Gate, Lobby to Literature fails because the implementation keeps the same core action, shelf topology, failure model, and feedback structure while changing labels, category data, and presentation.

Automated evidence does not establish human enjoyment, tactile quality, or 3–10 minute novelty. A non-finite render-boundary diagnostic appeared during the passing suite, and the inspected portable audio seam is not proven audible.

## CODE QUALITY

- Automated regression suite: 73/73 passed.
- Covered behaviors include shelf correctness, wrong-shelf handling, capacity, Combo thresholds, upgrades, zone data, completion flow, restart, responsive viewport contracts, and platform boundaries.
- The test suite printed NON_FINITE_RENDER_VALUE with pointerX: NaN in renderBoundary. This is not a test failure, but it is a concrete robustness signal.
- The current playable set is Lobby plus Literature; later zone records exist but are locked/non-playable in the inspected domain model.
- No tracked changes were found in the project worktree after the audit.

## GAMEPLAY QUALITY

### Core loop

| Question | Static/source result |
| --- | --- |
| Does clicking a book and choosing a shelf require judgment? | Yes. The player maps book category to a shelf; a wrong shelf resets Combo and produces a wrong result. |
| Does Combo have an explicit purpose? | Yes. Thresholds grant rewards and unlock an ability at a defined threshold. |
| Is Literature meaningfully different from Lobby? | Category labels and the rule text change, and Literature uses a more similar taxonomy; the action, shelf layout, failure model, and progression grammar remain the same. |
| Is there a genuinely new decision/risk? | No strong evidence of a new resource, spatial constraint, risk, or strategy. |
| Is there novelty after the first playable areas? | Not established; later zones are not currently playable. |

### Skin-Swap Gate

LOBBY_TO_LITERATURE_SKIN_SWAP_GATE = FAIL

Literature changes background/palette, names, category data, and rule wording, but does not change enough of the player operation, decision structure, risk, or result feedback. “注意相似书籍分类” is a promising design direction, but the inspected implementation still resolves through the same shelf-selection loop and reward/combo grammar.

### Gameplay Reality Check

- Gameplay Hypothesis: category similarity in Literature will make shelf selection more deliberate.
- Expected Player Behavior: compare book cues and choose between similar shelves instead of relying on immediate color recognition.
- Why It May Be Fun: ambiguity can create recognition and mastery.
- Cheapest Prototype: one Literature micro-level with confusable pairs, a non-color cue, and a measurable recovery loop.
- Success Signal: unfamiliar players verbalize the distinction and improve after one mistake.
- Failure Signal: players guess by color, feel punishment arbitrary, or call Literature the same level with a new background.
- Human Validation: PENDING.

## VISUAL QUALITY

- The renderer uses a coherent programmatic library visual language with explicit shelf labels, category icons, counts, book shapes, and Literature palette variation.
- Shelf targets use text and icon cues rather than color alone.
- Book proportions and shelf geometry are generated consistently by the renderer.
- Existing screenshots were located but not pixel-inspected because the local image inspection helper failed.
- Visual difference does not satisfy the Skin-Swap Gate.

## REAL PLAYTEST STATUS

REAL PLAYTEST = PENDING

Available evidence is limited to automated tests, existing UI smoke contracts, screenshot artifact locations, and source inspection. No human tester, physical touch device, or unfamiliar-player session was available. The existing UI smoke contract also states that CDP/touch emulation is not physical touchscreen evidence and does not establish human enjoyment or human 3–5 minute completion.

## P0

- None established by this read-only audit.

## P1

1. Skin-Swap Gate failure: Literature needs a new player decision, risk, or feedback grammar.
2. Non-finite render-boundary diagnostic: investigate the pointerX: NaN path.
3. Audio feedback gap: the portable runtime audio function is not proven to provide sound for core actions.
4. Playable-content ceiling: later zone records are locked/non-playable; 10-minute novelty is not established.

## P2

1. Run an unfamiliar-player session focused on shelf recognition, error interpretation, and the Literature transition.
2. Capture target-device screenshots through first screen, crowded shelves, wrong placement, last book, completion, and unlocked Literature.
3. Validate safe-area behavior on real notched portrait screens and narrow widths.
4. Re-check Combo readability and whether its rewards change player behavior.

## Game Design

The archive loop is legible and test-covered. Literature has a stated design intention, but the current implementation does not demonstrate a sufficiently different decision/risk profile. Completion, map, and next-action paths exist; human comprehension is unverified.

## Game Feel

These are provisional static ratings, not human feel approval.

| Event | Rating | Evidence / limitation |
| --- | --- | --- |
| 选书 | APPROPRIATE | Selection state and target guidance exist; timing/tactile quality unverified. |
| 正确归架 | APPROPRIATE | Correct event, shelf feedback, movement/particle path, and reward hooks exist. |
| 错误反馈 | APPROPRIATE | Wrong-shelf state and Combo reset are explicit; fairness is unverified. |
| Combo 提升 | TOO_WEAK | Combo/reward state exists, but escalation was not proven by human play. |
| 最后一本书 | APPROPRIATE | Last-book/completion path exists; ceremony quality unverified. |
| 区域 100% 完成 | APPROPRIATE | Completion state, stats, reward, and next action exist. |
| 新区域解锁 | APPROPRIATE | Literature unlock path exists; transition excitement unverified. |

OVERFEEDBACK_GATE = PASS at static-contract level. No evidence of blocking animation, uncontrolled knockback, or particle occlusion; runtime visual confirmation remains pending.

## UI/UX

The source and automated contracts indicate a hierarchy of zone identity/rule, local/global progress, Combo, currency/upgrades, capacity, selected target, shelf labels, completion, and next-action states. The core shelf target uses text plus icon plus color.

## Mobile Layout

- Responsive tests cover portrait and landscape contracts, including 390x844 and 844x390.
- No horizontal overflow was reported by the existing UI smoke contract.
- Safe-area behavior is represented in layout/viewport code, but physical notched-device validation is pending.
- The orientation overlay path deserves device review because it has a non-blocking transparent override.

## UI Hard Gate Results

| Gate | Static/automated evidence | Real visual/device status |
| --- | --- | --- |
| UI_OVERLAP | 0 reported by existing UI contract | PENDING |
| CLIPPED_TEXT | 0 reported by contract tests | PENDING |
| OFFSCREEN_CRITICAL_UI | 0 reported by viewport/overflow checks | PENDING |
| UNLABELED_CORE_TARGET | 0; shelf text and icon cues exist | PENDING |
| SAFE_AREA_VIOLATION | 0 reported by layout contract | PENDING |

## Art Direction

- Visual style: warm, illustrated/programmatic library.
- Palette: general-library and Literature palettes are defined.
- Shape language: books, shelves, cards, and category markers are consistently programmatic.
- Perspective/proportions: shelf/book geometry is shared.
- Lighting/shadow/material: lightweight 2D treatment; no contradictory material system found.
- UI/icon style: category icons and shelf labels are integrated into the renderer.
- Main current art risk: theme variation may be mistaken for gameplay variation.
- Complete reference board: not found in this audit.

## VFX

Correct, wrong, selection, completion, and last-five paths expose visual feedback hooks. No evidence of uncontrolled full-screen effects or input-blocking feedback. Mobile particle cost and dense-scene readability remain unmeasured.

## Rendering

Canvas/programmatic rendering is covered by deterministic contracts. The non-finite boundary diagnostic must be investigated. No device frame-time, texture, memory, or draw-call sample was available.

## Audio Feedback

Event names and reward hooks exist. The portable runtime path is not proven audible for all core actions; this is a P1 follow-up. No human timing check was performed.

## Retention

| Checkpoint | Static audit result |
| --- | --- |
| 30-second hook | First screen exposes sorting and a clear first action; human hook strength PENDING. |
| First success | Correct shelf path and reward/Combo hooks exist. |
| First surprise | Combo threshold/ability and Literature unlock are candidate surprises. |
| First meaningful choice | Shelf classification is meaningful, but may be too obvious in Lobby. |
| 3-minute goal | Zone completion, upgrades, and next-zone unlock provide a short goal. |
| 10-minute novelty | NOT ESTABLISHED; only Lobby and Literature are currently playable. |
| Next unlock | Literature unlock path exists. |
| Visible long-term progress | Local/global progress and upgrade/capacity state exist. |
| Reason to continue | Completion rewards, upgrades, and unlocking exist; motivation is PENDING. |

## Performance

Automated startup, interaction, rapid-input, and viewport contracts pass. Real mobile frame-time, memory, draw-call, and thermal evidence was not collected. Status: static PASS / device PENDING.

## Playtest

Completed: automated tests, source inspection, and existing automated-interaction contract review.

Not completed: developer hands-on playtest, unfamiliar human playtest, and real platform/device playtest.

## Skin-Swap Risks

Lobby to Literature currently fails the strict gate. Category renaming and palette changes may create a false sense of content expansion. Future zones with zero books and locked status should not count as novelty until playable.

## Overfeedback Risks

Static code shows no obvious blocking or excessive feedback stack. The remaining risk is weak Combo salience and missing/uncertain audio, not overfeedback. Validate dense rapid sorting and completion celebrations with a human/device session.

## Evidence

- H:\got book\README.md
- H:\got book\src\click-game.js
- H:\got book\src\click-renderer.js
- H:\got book\src\click-data.js
- H:\got book\src\zone-domain.js
- H:\got book\src\platform-runtime.js
- H:\got book\tests\ui-smoke.mjs and tests\*.test.mjs
- H:\got book\artifacts\*.png, located but not pixel-inspected
- npm test: 73 passed, 0 failed
- project worktree status: clean for tracked files

## Unknowns

Unfamiliar-player comprehension and enjoyment; physical touch latency; pixel-level overlap/clipping/readability; target-build audio; sustained Literature novelty; device performance under dense book/particle state.

## Recommended Next Actions

1. Prototype one Literature rule that changes decision/risk/feedback and rerun the Skin-Swap Gate.
2. Fix or explain the non-finite boundary diagnostic.
3. Add or verify audio feedback for core actions.
4. Run a 3–10 minute unfamiliar-player session on a real mobile device.

## Audit Conclusion

LIBRARYTIDY_AUDIT = PASS — the read-only pilot audit was executed and evidence was recorded.

This is not a gameplay-quality PASS. Current quality findings include LOBBY_TO_LITERATURE_SKIN_SWAP_GATE = FAIL and REAL PLAYTEST = PENDING.
