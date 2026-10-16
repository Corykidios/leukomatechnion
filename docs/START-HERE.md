# Start Here — leukomatechnion quick start

## The one-sentence version

Three skills teach a Letta agent persona to run a Facebook presence:
facebook-craft (the core), facebook-profile, facebook-page — install
all three, load craft first, everything else builds on it.

## Installing

1. Copy the three skill folders into the agent's skills location. For a
   Letta Code agent with MemFS memory, that is:
   `$MEMORY_DIR/skills/facebook-craft/SKILL.md` (and likewise for
   profile and page).
2. Put the Facebook password in the agent's vault if it is not already
   there (e.g. `letta secret set FACEBOOK_PASSWORD` from stdin). Never
   store it in a file or paste it into conversations.
3. Have the persona say something like "check my Facebook" — the skills
   load on their description triggers.

## What the persona can then do

- Sign in (2FA checkpoints usually auto-resolve), verify its own
  identity before acting, and hold sessions without churning logins.
- Post to timelines, comment, edit its own work, react, and verify every
  write before claiming it.
- Message in 1:1 and group chats (with the known traps handled).
- Work a private group: posts, group chat, and the admin console if it
  holds a role.
- Operate a public Page in-character, with the credential boundary
  respected.

## Known limits (honest ones)

- The reaction picker renders fully; swapping past basic Like has
  resisted synthetic clicks. Reported as-is, not hidden.
- Share sheets have resisted synthetic clicks too.
- 2FA sometimes wedges to a blank page. The skill handles it by
  protocol: wait once, retry once, then report and hold. Never forced.
- Live conversation works well between two personas; more is slow.

## Where things are

- Skills: the three folders at the repo root.
- Full testing log with pass/quirk/untested statuses: docs/TESTING.md.
- Orientation for AI collaborators: docs/AI-CONTEXT.md.

Built for the crew, by the crew's captain, at the Architect's order.
