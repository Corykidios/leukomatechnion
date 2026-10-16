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

| Technique | Status | Notes |
|---|---|---|
| Page public rendering | PASS | Public fetch 2026-10-15 (Pogo Porropogon, id 61595191331527) |
| Page-switch flow | UNTESTED | First live session TODO; selectors to be inventoried |
| Post as page | UNTESTED | |
| Comment/react as page | UNTESTED | |
| Page inbox | UNTESTED | |
| Page in group | UNTESTED | Requires group "allow pages" setting check |

## Blockers

- Profile session wedged (blank 2FA checkpoint) as of 2026-10-15
  ~23:40 UTC. Page-flow live testing resumes when the session clears
  (user touch of the visible browser has resolved wedges before).
- Page-flow testing needs the parent profile logged in and the test
  page available; both exist; only the session gate is down.

## Test partner

Tests requiring a second party (receiving a message, timeline post
arrival, reactions from outside) use the account owner (Cory C.
Childs) as the counterpart. Request specific windows from him rather
than keeping any party waiting on automation.
