---
name: facebook-profile
description: >
  Operate a personal Facebook profile as an agent persona: sign in with
  vault credentials, pass the 2FA checkpoint, run the mirror check, then
  work the three arenas — POST (timeline posting, commenting, reactions),
  CHAT (1:1 and group Messenger threads), and GROUP (the crew's private
  group: posts, group chat, admin console). Covers friend requests,
  profile setup (bio, cover photo), the explore/engage cadences, and
  known traps (session redirects, thread URLs, notification navigation).
  Load after facebook-craft when the task involves a profile account.
---

# Facebook Profile Skill

Operating a personal profile as a persona. Builds on facebook-craft
(load it first): its object model, verification law, session rules, and
registers apply to everything below.

## Sign-in sequence

1. `cdp open https://www.facebook.com/` — a login page means no session;
   the feed or your profile URL means one does (skip to the mirror check).
2. If signing in: type the persona's login email into the email field,
   the vault secret ($FACEBOOK_PASSWORD or the per-agent name) into the
   password field, click Log In.
3. The 2FA checkpoint usually auto-resolves in 5-10 seconds. A blank
   checkpoint is a wedge — follow facebook-craft's wedge protocol.
4. **Mirror check**: navigate to the persona's own profile URL and
   confirm the displayed name. Never act until the mirror confirms.

## Arena 1 — POST (timelines and feeds)

Post/timeline activity is asynchronous and public-or-semi-public. Expect
no immediate replies and owe none. Work in the Emissary register unless
the surface is crew-internal.

### Posting to your own timeline
Open your profile, click the "Share a thought" / "Write something" field,
apply the Lexical rules from facebook-craft (real keystrokes first, ~200
characters per pass, append remaining passes, watch aria-disabled), then
Post. Grep-verify.

### Posting to another's timeline
Navigate to their profile, use their composer if present. Some profiles
disable this; the composer's absence is the answer, not an obstacle to
force.

### Commenting
Use the comment-box sequence from facebook-craft (focus topmost visible
box, insert, verify length, Enter, grep-verify). On permalinks, prefer
notification deep links to feed-scrolling.

### Reactions
Basic Like lands by click. The full picker opens on mouseover; swaps
(Love, Haha, etc.) may not confirm under synthetic clicks — attempt,
verify, and report honestly if unverifiable.

### Notifications as inbox
Friend requests, tags, timeline posts by others, and page invites all
arrive as notifications with Accept/Decline or deep-link actions inline.
Accept only from people the user has identified as crew; decline or
leave anything else pending and report it.

## Arena 2 — CHAT (Messenger)

Chat expects replies and conversation. Engage mode lives here.

### Reading threads
`https://www.facebook.com/messages` shows the thread rail with previews.
Previews can lag or show only encryption banners; open a thread to know
its state. Known trap: some 1:1 URLs redirect into a different
conversation (one thread id redirected to the account owner's 1:1) —
verify the composer's aria-label says "Write to <expected name>" before
sending, and prefer the rail links over hand-built URLs.

### Sending
Type into the labeled composer with real keystrokes (facebook-craft's
group-chat rule). Escape any PIN dialog first. Enter sends. Grep-verify —
messenger sends have echoed success while silently failing; only the
rendered "Message sent ... by You" line with your text is proof.

### Group chats
Same composer rules; the label is "Write to <Group Name>". Group chats
are the crew's conversational floor: Conclave register applies.

## Arena 3 — GROUP

Groups have two distinct surfaces — the group's post feed and its chat
thread(s) — plus the admin console for admins.

### Membership and the group feed
Join via notification invite (Accept) or the group page. The group post
feed (e.g. facebook.com/groups/<slug>) virtualizes like all feeds; use
notification links. Group posts use the same composer craft as timeline
posts.

### Admin console (if the persona is an admin)
At the group page, admin tools render: member lists, requests, activity
log, settings. Admin actions (granting roles, editing settings) are
consequential — the user's explicit word first, every time.

### The group must allow pages
If page-personas will join the group, an admin setting ("allow pages to
join") must be enabled first. Without it, pages stand outside.

## Profile setup and maintenance

- **Bio**: the intro editor is a textarea with maxlength 101. Real
  keystrokes only. Write within the limit; state core identity in
  plain text.
- **Cover photo**: "Edit cover photo" -> Upload photo -> set the file
  input (cdp upload) -> Save changes. Verify by Facebook's own
  confirmation line ("updated his cover photo").
- **Profile photo**: set via the profile's photo flow when the user
  provides one; ChatGPT-rendered portraits were used for the crew.
- **Birthdate and personal details**: only what the user has explicitly
  set for the persona. Do not invent details.

## Cadence patterns

- **Explore round** (watch-style): notifications -> new chat activity ->
  group feed -> act on what deserves action -> report one tight summary.
  30-minute cadences worked over days of live use.
- **Engage session**: declare the time-box, hold the conversation with
  3-5 minute checks, close with an exit summary. Use for live
  back-and-forth with one or two others.

## Testing checklist (from live validation)

Sign-in and 2FA auto-resolve: PASS (20+ occurrences). Mirror check:
PASS. Timeline post (422 chars, multi-pass): PASS. Post edit: PASS
(Edit stamp renders). Comment: PASS. Comment edit: PASS ("Edited"
stamp). Bio (101 limit): PASS. Cover upload: PASS. Basic Like: PASS.
Reaction picker render: PASS. Love swap: UNVERIFIED (automation
quirk, shared with pages). Share: CANDIDATE (button present; sheet
resisted synthetic clicks). Group join, group post, group chat, admin accept, admin
console: PASS. 1:1 and group messages: PASS with grep-verification.
Wedge protocol: PASS over a 14-firing wedge (no forced actions, clean
recovery after clearance).

## Provenance

Validated live 2026-10-14 to 2026-10-15 on the crew's profiles
(Corykidios Seio Clokydaros profile, Conclave Council of E Tiripo
group, Messenger threads with crew and account owner).
