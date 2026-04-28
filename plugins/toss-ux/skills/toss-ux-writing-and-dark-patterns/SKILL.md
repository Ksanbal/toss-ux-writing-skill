---
name: toss-ux-writing-and-dark-patterns
description: Use when designing, reviewing, or implementing Korean app UX copy and interaction flows that should follow Toss Apps UX writing tone and dark-pattern prevention guidance.
version: 1.0.0
author: Ksanbal
license: MIT
compatibility:
  codex: ">=0.0.0"
  claude-code: ">=2.0.0"
  opencode: ">=1.4.0"
metadata:
  priority: 8
  source_docs:
    - https://developers-apps-in-toss.toss.im/design/consumer-ux-guide.html
    - https://developers-apps-in-toss.toss.im/design/ux-writing.html
  tags: [toss, ux-writing, dark-patterns, korean, product-design, conversion, trust]
---

# Toss UX Writing and Dark Pattern Prevention

## Overview

Use this skill to write, rewrite, or review Korean product UX copy and interaction flows against Toss Apps design guidance. It combines two official Toss developer documents:

- 다크패턴 방지 정책: https://developers-apps-in-toss.toss.im/design/consumer-ux-guide.html
- UX 라이팅: https://developers-apps-in-toss.toss.im/design/ux-writing.html

This skill is an unofficial working checklist. It does not replace the official Toss documentation. When there is a conflict, follow the latest official Toss docs and policy review feedback.

## When to Use

Use this skill when the task involves:

- Korean UX writing for apps, mini apps, onboarding, consent, error, empty, benefit, CTA, dialog, toast, bottom sheet, notification, or ad flows.
- Reviewing whether a flow may feel like a dark pattern, forced consent, unexpected interruption, or misleading CTA.
- Rewriting product copy in a Toss-like tone: clear, friendly, active, positive, casual polite Korean.
- Checking whether a CTA tells users what happens next.
- Designing screens that should maintain user trust, autonomy, and predictability.

Do not use this as a legal/compliance substitute. For high-risk monetization, advertising, consent, privacy, or regulated-finance flows, escalate to policy/legal review after applying this checklist.

## Core Principle

Preserve trust by making the next step predictable and voluntary.

Every screen should answer:

1. What is happening now?
2. What can the user do next?
3. What happens if the user taps the CTA?
4. Can the user leave, decline, or continue without being trapped?
5. Is the copy easy to scan in Korean?

If a design improves conversion by hiding choices, delaying exit, exaggerating urgency, interrupting the user's intended task, or making the CTA ambiguous, treat it as a likely violation.

## Dark Pattern Prevention Checklist

Block or redesign the flow if any item below is true.

### 1. No interruptive bottom sheet on entry

Do not show an advertising, marketing, notification-consent, or benefit-push bottom sheet immediately after service entry when the user expected to land on the main task screen.

Better:

- Let users reach the expected content first.
- Ask for notification or marketing consent at a contextual moment after value is clear.
- Use inline guidance or a dismissible, non-blocking surface when possible.

### 2. Do not block back navigation with an extra persuasion sheet

When the user presses back to leave or explore something else, do not intercept the action with a bottom sheet whose primary purpose is to prevent exit or request notification consent.

Better:

- Respect back navigation.
- Save progress if necessary and communicate it plainly.
- Ask for opt-in later at a natural moment.

### 3. Always provide a way out

Do not create a structure where the user can only tap the partner-desired CTA and has no visible decline, close, back, or skip path.

Better:

- Provide `닫기`, `나중에`, `건너뛰기`, or a normal back path when the action is optional.
- Make the non-primary path visible enough to be discovered.
- Avoid visual hierarchy that makes refusal look disabled or dangerous.

### 4. Do not show unexpected full-screen ads mid-flow

Do not surprise users with an interstitial/full-screen ad after they tap a menu or item expecting to receive content, benefit, or an action result.

Better:

- Signal ad participation before the tap if ad viewing is required.
- Separate content navigation from ad reward flows.
- Make ad-triggering CTAs explicit, e.g. `광고 보고 리워드 받기` rather than a vague reward label.

### 5. CTA must predict the next action

A CTA should tell users what will happen after tapping. Do not repeat the already-explained benefit as the button label if it hides the actual action or destination.

Poor pattern:

- Heading says the benefit, CTA repeats the benefit, but the next step is unclear.

Better patterns:

- `동의하고 시작하기`
- `계좌 연결하기`
- `광고 보고 리워드 받기`
- `알림 받고 혜택 확인하기`
- `신청 내용 확인하기`

Also avoid exaggerated or redundant helper text above the CTA that blurs the button's job.

## UX Writing Checklist

### 1. Use 해요체 everywhere

Write product copy in consistent 해요체 regardless of screen type or context.

Examples:

- `확인했어요`
- `다시 시도해 주세요`
- `혜택을 받을 수 있어요`

Avoid mixing formal styles like `합니다`, `하십시오`, `해라`, or overly casual 반말.

### 2. Prefer active voice

Use active forms whenever they are clearer and more direct.

Rewrite patterns:

- `됐어요` → `했어요` when the user or system action is the focus.
- Remove unnecessary `~었` when it makes the sentence heavier.
- Replace noun-heavy constructions with verbs.

Good active-copy questions:

- Who is doing the action?
- Can this become a direct verb phrase?
- Is the result easier to understand if the user is the subject?

### 3. Speak positively when possible

Reduce negative phrasing such as `안 돼요`, `없어요`, `불가해요` when a helpful positive alternative exists.

Pattern:

- Instead of only saying what cannot happen, say what the user can do next.
- For errors, explain recovery in one clear next step.
- If a service is available but a specific benefit is unavailable, avoid making the whole product sound unavailable.

Examples:

- `지금은 가입할 수 없어요` → `조건을 확인하면 가입할 수 있어요`
- `혜택 대상이 아니에요` → `다음 조건을 충족하면 혜택을 받을 수 있어요`
- `입력값이 잘못됐어요` → `생년월일 8자리를 다시 입력해 주세요`

### 4. Use casual polite Korean, not excessive honorifics

Avoid over-honorific phrases that make product copy stiff:

- `~시겠어요?`
- `~시나요?`
- `~께`
- `계시다`
- `여쭈다`

Rewrite patterns:

- Remove unnecessary `~시` from verbs.
- `계시다` → `있다`
- `여쭈다` → `확인하다`, `묻다`
- `께` → `에게`

If mechanically removing `~시` sounds awkward, rewrite the sentence so the requested information is the subject.

### 5. Avoid `{명사} + {명사}` stacks

Korean UX copy becomes clearer when noun stacks become verbs or short clauses.

Patterns:

- Convert Sino-Korean nouns into verbs when natural.
- If a noun cannot be fully unpacked, use `{명사}가 {명사}해서` to make the relationship easier to scan.
- Prefer one idea per sentence.

Examples:

- `본인 인증 진행` → `본인 인증을 해요`
- `혜택 지급 완료` → `혜택을 지급했어요`
- `계좌 연결 필요` → `계좌를 연결해야 해요`

## Allowed Passive Voice Exceptions

Prefer active voice, but passive voice can be better when it makes the message shorter, clearer, or more reassuring.

Use passive voice carefully for:

1. Service end or period expiration, where the ended/expired object should be emphasized.
2. User-impact results such as overdue status, cancellation, termination, or application of terms, where cause and effect must be explicit.
3. Sensitive information or reassurance contexts, where passive phrasing can make data collection or processing feel less intrusive.

Language rule:

- Use `돼요`, not `되어요`.

## Dialog, Button, and CTA Rules

### Dialog left button

Use `닫기` for the left button when dismissing a dialog. Avoid `취소` if it could make users think their current task or progress will be canceled.

### CTA labels

A CTA should be action-specific, not value-only.

Checklist:

- Does the label include the main verb?
- Does it reveal the next screen or action?
- Would the user still understand the outcome if they only scanned the button?
- Is consent, ad viewing, payment, connection, application, or notification request explicit?

### Consent and notification prompts

Ask at contextual moments, not as forced entry/exit blockers.

Copy should state:

- What the user is consenting to.
- Why it helps the user.
- What happens if they decline.
- How they can change the setting later, if relevant.

## Review Procedure

When reviewing a product flow:

1. Identify the user's intent at each step.
2. List every interruption: bottom sheet, modal, ad, consent prompt, notification prompt, forced CTA.
3. Check whether each interruption is expected, contextual, and dismissible.
4. Inspect each CTA in isolation and ask whether the next action is predictable.
5. Rewrite copy using 해요체, active voice, positive framing, casual honorifics, and verb-based Korean.
6. Flag any flow that blocks entry, blocks exit, hides refusal, or surprises users with ads.
7. Provide concrete replacements: before/after copy, revised CTA labels, and recommended UI behavior.

## Output Format for Reviews

Return reviews in this structure:

```markdown
## Summary
- Overall risk: Low / Medium / High
- Main issue: <one sentence>

## Dark Pattern Risks
| Area | Risk | Why it matters | Fix |
|---|---|---|---|

## UX Writing Rewrites
| Current | Recommended | Reason |
|---|---|---|

## CTA Check
| CTA | Predictable? | Recommended label |
|---|---:|---|

## Launch Checklist
- [ ] No entry-blocking ad/notification bottom sheet
- [ ] Back navigation is respected
- [ ] Decline/close/skip path exists for optional actions
- [ ] Ads are expected and explicitly labeled
- [ ] CTA describes the next action
- [ ] Copy uses 해요체
- [ ] Copy is active, positive, and casual polite
```

## Common Pitfalls

1. Optimizing short-term conversion by making refusal hard to find.
2. Asking for notification consent before users understand product value.
3. Labeling an ad reward CTA as a normal benefit CTA.
4. Repeating the headline benefit in the CTA instead of naming the action.
5. Using `취소` in dialogs where the action only closes the dialog.
6. Making Korean copy stiff with `~시겠어요`, `계시다`, `께`, or noun stacks.
7. Saying only what is impossible instead of giving a recovery path.
8. Treating this checklist as complete legal approval.

## Verification Checklist

- [ ] Official Toss source docs were checked for the latest policy wording.
- [ ] Every forced surface has a user-centered reason.
- [ ] Optional choices have visible exit/decline paths.
- [ ] Ad, consent, notification, payment, and data actions are explicit before the tap.
- [ ] All core copy uses 해요체.
- [ ] CTA labels predict the next step without needing surrounding text.
- [ ] Before/after rewrites are concrete enough for design or engineering handoff.
