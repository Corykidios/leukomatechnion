---
name: facebook-page
description: >
  Operate a Facebook Page from a personal profile's session: switch into
  the page, post/comment/react as the page, read the page inbox, and
  understand the reduced capability set pages have versus profiles. Covers
  the credential boundary (you sign in with the profile's credentials but
  act as the page, never as the profile), the page-switch flow, the
  in-character performance discipline when one operator drives multiple
  page-personas, and group participation (which requires the group to
  allow pages). Load after facebook-craft.
---

# Facebook Page Skill

Operating a Page — a public identity attached to a personal profile.
Builds on facebook-craft (load it first): its verification law
(grep-verify every write), wedge protocol, and session rules apply to
page sessions exactly as to profile sessions.

## What a page is (and is not)

A page is a public-facing identity (brand, character, creator) operated
by a parent profile. Differences from a profile:

- Pages have reduced powers: no personal friending (they gain followers
  and likes), some flows differ, and some profile features do not exist.
- The page acts with its own name on posts, comments, and likes when
  "acting as" the page — but the underlying session is the parent
  profile's.
- Pages can join and participate in groups only if the group's settings
  allow pages.

## The credential boundary (read first)

You sign in with the parent profile's credentials. That authorizes the
session — it does not make you the parent profile. A real incident from
the field: an agent logged into what turned out to be another persona's
active session (browser-profile switching) and briefly believed he was
about to post as that persona. The rules:

1. After sign-in, run the mirror check on the parent profile.
2. Switch to the page explicitly (below) and verify the page's name in
   the UI before any action.
3. Never post, comment, or message as the parent profile unless the user
   has explicitly asked for that. The page is the persona; the profile
   is the vehicle.
4. If you find yourself in an unexpected identity, stop, run the mirror
   check, and report before doing anything else.

## The page-switch flow

From the parent session, page switching is available through Facebook's
page controls (the pages menu / "switch to page" affordance). After
switching, verify the page name renders and that actions will carry the
page's identity (the composer and page header show the page context).
Switch back to the profile context when the page work is done.

Validated live 2026-10-15: the page's public surface carries a
"Switch Now" button (from the "Switch into <Page>'s Page" prompt); after
switching, the session shows the page's Manage sidebar and page-context
composers. Two composer flows exist and are NOT the same:

- **"Share a thought" on a page opens a "New note" composer** — a
  60-character note with a Share button. It posts a note to the page,
  not a public post. Useful for short presence marks; know the limit.
- **The public post flow opens from the page's onboarding checklist**
  ("Create N public posts") or the page's post affordances: a two-step
  dialog — compose (real keystrokes, facebook-craft rules), then Next,
  then Post. Verified end-to-end live.

When multiple dialogs render (page pages carry notification panels that
read as dialogs), locate the target dialog by its visible text (e.g.
"Create post" containing "What's on your mind?") and operate within
that node only.

## Acting as the page

- **Posting**: the page's composer behaves like the profile composer —
  facebook-craft's Lexical rules apply unchanged. Verify with the page's
  name on the rendered post.
- **Commenting and reacting**: possible as the page on public and group
  content; the page's name appears. Same verification law.
- **Following and engagement**: pages follow pages; pages gain followers
  from profiles. Engagement surfaces (insights) exist but have not been
  validated — treat as untested until exercised.
- **Page inbox**: messages to the page land in the page's inbox, a
  Messenger surface with its own thread list. Untested live; validate on
  first use with the same composer rules.

## Multi-persona operation (one operator, several pages)

When one operator (an agent, or a human) drives multiple page-personas:

- One page's voice at a time. Verify which page is active before each
  action batch.
- Each page-persona speaks in its own voice and register; the operator
  performs, not impersonates casually. If the operator is an agent with
  its own persona, the discipline doubles: the page's voice is the
  page's, even when the hands are the operator's.
- Keep per-page context (name, voice notes, what the page has said) in
  the operator's notes to prevent cross-page bleed.

## Group participation as a page

Groups must explicitly allow pages (an admin setting). With that enabled,
the page can join and its posts/comments appear with the page identity.
If a page cannot join, the setting is the first thing to check with the
group's admins.

## Testing checklist

Page existence and public rendering (title, redirect to /people/<name>):
PASS (validated via public fetch 2026-10-15, Pogo Porropogon page,
id 61595191331527). Page-switch flow: UNTESTED. Posting as page:
UNTESTED. Commenting as page: UNTESTED. Page inbox: UNTESTED.
Group participation as page: UNTESTED (requires group setting check).
These are the first-live-session TODOs, in order.

## Provenance

Written 2026-10-15 against the Pogo Porropogon page (the crew's test
hull). Live validation of the UNTESTED items is the skill's first task
once the profile session is available.
