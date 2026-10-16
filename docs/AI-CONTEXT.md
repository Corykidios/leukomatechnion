# AI Context — leukomatechnion

This document orients an AI collaborator (or a future session of the
same one) to this repository. Read it before touching anything.

## What was built and why

Three Letta skills for operating Facebook as agent personas, built at
the request of Cory C. Childs for his crew of persistent AI personas
(the "Seekers"). The crew was given Facebook profiles; operation through
the Letta visible browser (Chrome via the `cdp` CLI) was proven live
over two days and then codified here so every persona can do it
without re-deriving the traps.

The division of labor (the "paradigm"): the user conceptualizes and
brainstorms; the AI builds the complete package, documents it
rigorously, tests, and revises until it works; the user adds the final
fun layer (clever descriptions, the narrative README intro, the
release name) at the end. This repo is at the pre-release stage: the
AI's build-and-test phase.

## Architecture

The skills describe operation of an external website through an
existing tool; there is no server code here. The moving parts:

```
Agent (Letta persona, e.g. Corykidios)
    | loads skills by frontmatter description triggers
    v
facebook-craft (core)  ->  facebook-profile  ->  facebook-page
    | all three drive
    v
cdp CLI (Letta's visible-browser client, Chrome DevTools Protocol)
    |
    | open/inventory/type/click/eval/key/upload/screenshot
    v
Chrome (visible, on the sandbox desktop)  ->  facebook.com
```

- **facebook-craft** holds everything shared: object model, Lexical
  composer rules, comment-box craft, verification law, wedge protocol,
  session stewardship, explore/engage modes, registers, safety lines.
- **facebook-profile** holds profile-account operation: sign-in, the
  three arenas (POST, CHAT, GROUP), setup flows, cadences, and the
  live-tested checklist.
- **facebook-page** holds page operation: the credential boundary (the
  critical identity discipline), the page-switch flow (selectors
  pending first live validation), multi-persona operation rules, and
  the page-specific TODOs.

## Conventions that matter

- Skill names are plain and dashed: facebook-craft, facebook-profile,
  facebook-page. No fantasy vocabulary inside the skills. The repo's
  Greek name (Λευκωματεχνίον) lives in conversation, not in code.
- Every technique claim is labeled with its provenance: validated live,
  or UNTESTED/pending. Do not upgrade a claim's status without
  re-running the validation.
- The verification law is absolute: no write counts until its text is
  found rendered on the page. Tool success reports and "You:" echoes
  are not proof.
- The wedge protocol is absolute: blank checkpoints get one settled
  wait, one fresh-cycle attempt, then honest reporting. Never force.

## Current state and known gaps

- The page-switch flow and all page-arena actions are UNTESTED (the test
  hull, the Pogo Porropogon page, was created 2026-10-15; the profile
  session was wedged at writing time). See docs/TESTING.md.
- Reaction swaps and share-sheets resisted synthetic clicks in live
  sessions; marked as automation quirks, honestly reported as such.
- The 2FA auto-resolution is an observed behavior of this setup (20+
  occurrences, then a 14-round wedge), not a guaranteed property.

## Where things are

- Skills: facebook-craft/, facebook-profile/, facebook-page/
- Testing log: docs/TESTING.md
- User quick start: docs/START-HERE.md
