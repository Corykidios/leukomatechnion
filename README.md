# leukomatechnion

Facebook operation skills for AI agent personas. Three installable
skills for the Letta skill system, plus working documentation, built
from live validated sessions.

**Status: pre-release.** Skills written and internally reviewed; live
page-flow testing pending (see docs/TESTING.md). No release yet.

---

## What this is

A skill set that lets an AI agent persona operate a Facebook presence
on the user's behalf: signing in with vault-stored credentials, posting,
commenting, reacting, messaging, working a private group, and operating
a public Page — with verified-write discipline, session stewardship,
and honest reporting of what worked and what did not.

The skills are plain-technical by design: accurate terminology, no
invented vocabulary, warmth for the reader, zero costume. The repo's
name is a private joke between its two builders
(λεύκωμα, the whitened register + τεχνίον, a diminutive of τέχνη —
"the little art"); the skills inside are rigorous.

## The skills

| Skill | Load order | Covers |
|---|---|---|
| `facebook-craft` | first | Shared core: object model, browser techniques, verification law, session stewardship, wedge protocol, explore/engage modes, registers, safety lines |
| `facebook-profile` | after craft | Profile accounts: sign-in + 2FA, mirror check, POST / CHAT / GROUP arenas, profile setup, cadence patterns, live-tested checklist |
| `facebook-page` | after craft | Pages: credential boundary, page-switch flow, acting as the page, multi-persona operation, group participation rules, first-session TODOs |

### Directory layout

```
facebook-craft/SKILL.md    shared core (load first)
facebook-profile/SKILL.md  personal profiles
facebook-page/SKILL.md     pages
docs/AI-CONTEXT.md         orientation for AI collaborators
docs/START-HERE.md         the user's quick start
docs/TESTING.md            validation log: passed, pending, blocked
```

## Installation

Copy (or symlink) the three skill directories into the agent's skills
location. For Letta Code agents with MemFS memory, that is
`$MEMORY_DIR/skills/<skill-name>/SKILL.md`. Each skill's frontmatter
name and description control when the agent loads it.

## What is validated (and what is not)

Validated live (2026-10-14 through 2026-10-15, full two-day session):

- Sign-in with vault credentials; 2FA auto-resolution (20+ occurrences)
- Timeline posting (multi-pass long posts), post editing
- Commenting, comment editing, notifications-as-navigation
- Bio setup (101-char limit), cover photo upload
- Basic reactions; full picker rendering
- Group: join, group posts, group chat, admin acceptance, admin console
- Messenger: 1:1 and group sends, with grep-verification
- The wedge protocol: a 14-round blank-checkpoint wedge handled without
  forced actions; clean behavior throughout

Not yet validated (first live session TODOs, tracked in
docs/TESTING.md):

- Page-switch flow, posting/commenting as a page, page inbox
- Reaction swaps beyond basic Like under automation
- Share-sheet behavior under automation

## Provenance and method

The division of labor: the user (Cory C. Childs) defines need and
architecture; the AI builds, documents, tests, and revises until it
works; the user adds the final presentation layer and release. The
techniques in these skills were proven in live sessions by the agent
Corykidios Seio Clokydaros (Letta), then written down so any persona
can reuse them without re-learning the traps the hard way.

## License

MIT (see LICENSE).
