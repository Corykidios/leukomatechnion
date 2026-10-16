# Testing Log — leukomatechnion

Every technique claim in the skills carries a status here. Upgrade a
status only after re-running the validation and recording the date.

Legend: PASS (validated live), QUIRK (works partially / automation
limitation, honestly reported), UNTESTED (written, not yet exercised),
BLOCKED (cannot test right now — external dependency).

A technique only reaches PASS when its result was verified by the
verification law (the submitted text found rendered on the page) —
tool success reports alone never count.

## facebook-craft / facebook-profile (shared validation base)

Validated live 2026-10-14 to 2026-10-15 (two-day session, profile
"Corykidios Seio Clokydaros", group "The Conclave Council of E Tiripo"):

| Technique | Status | Notes |
|---|---|---|
| Sign-in, vault password | PASS | 20+ occurrences |
| 2FA auto-resolution | PASS (observed) | Auto-resolved ~20x; then one 14-round blank wedge — observed behavior, not guaranteed |
| Mirror check | PASS | Caught identity from session state |
| Timeline post, multi-pass | PASS | 422-char post via real-keys + append passes |
| Post edit | PASS | Edit stamp rendered |
| Comment | PASS | Focus-verify-Enter sequence |
| Comment edit | PASS | "Edited" stamp rendered |
| Bio setup | PASS | maxlength 101 discovered and obeyed |
| Cover photo upload | PASS | File-input upload; Facebook confirmation line |
| Basic Like | PASS | Counter tick observed |
| Reaction picker render | PASS | Full 7-reaction picker via mouseover |
| Reaction swap (Love) | QUIRK | Click registered; swap unconfirmed under synthetic click |
| Share | QUIRK | Button present and clickable; sheet resisted synthetic clicks |
| Notifications-as-navigation | PASS | All deep links; feeds virtualize |
| Group join (invite) | PASS | Accept via notification |
| Group post | PASS | Same composer rules |
| Group chat send | PASS | Labeled-composer rule; grep-verified |
| PIN dialog handling | PASS | Escape + refocus recovery proven |
| Admin invite accept | PASS | Verified on members page (badge + console) |
| 1:1 message send | PASS | Rendered "Message sent ... by You" |
| Wedge protocol | PASS | 14 rounds, never forced, honest reporting |
| Mixed-script extraction | PASS | innerText workaround proven |

## facebook-page

Validated live 2026-10-15 (~00:45-01:10 UTC), after human cleared the
checkpoint wedge (the touch worked instantly):

| Technique | Status | Notes |
|---|---|---|
| Page public rendering | PASS | Public fetch + logged-in view (Pogo Porropogon, id 61595191331527) |
| Page-switch flow | PASS | "Switch Now" button on the page; verified by Manage Page header + page-context composer after switch |
| Mirror check (page context) | PASS | Page identity confirmed before acting |
| Post as page (public) | PASS | Two-step flow: compose -> Next -> Post; verified rendered on page |
| Page "Share a thought" = NOTE, not post | PASS (quirk documented) | Opens a "New note" composer (60-char limit, Share button) — NOT the public-post flow; the public post lives behind the "Create N public posts" onboarding checklist item |
| Comment as page (reply to human) | PASS | 2026-10-15: replied to the account owner's comment in character ("Comment as Pogo Porropogon" box; insertText + Enter; grep-verified) |
| Outside-viewer rendering | PASS | Account owner's comment + Pogo's reply both render on the public page view |
| Page inbox (Meta Business Suite) | PASS | 2026-10-15: page inbox reached via the message notification deep link (business.facebook.com/latest/inbox); account owner's message read; in-character reply sent and rendered in thread ("You: POGO CONFIRM...") with timestamps |
| Page in group | PASS | 2026-10-15: after the account owner enabled "allow pages", the page requested to join the private group; membership approved; Pogo Porropogon renders as the 5th member of the members list |

## Blockers

- None currently. The session wedge (2026-10-15) was cleared by a human
  touch of the visible browser and the full page battery then ran.
- Remaining optional validations: reaction-swap and share-sheet under
  automation (known quirks, not page-specific); engage-loop live run
  with a human partner (cadence test, not a page feature).

## Test partner

Tests requiring a second party (receiving a message, timeline post
arrival, reactions from outside) use the account owner (Cory C.
Childs) as the counterpart. Request specific windows from him rather
than keeping any party waiting on automation.
