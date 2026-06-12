# email-triage skill for Odysseus

This repository contains a GitHub-ready Odysseus skill for inbox triage, email summarization, reply drafting, follow-up extraction, and converting email into actionable tasks.

## Folder layout

```text
email-triage-skill/
└── email-triage/
    └── SKILL.md
```

## Import into Odysseus

Open **Add Skill** in Odysseus and use the GitHub tree or folder URL that points directly to the `email-triage/` directory containing `SKILL.md`.

## What this skill does

- Classifies messages into operational buckets such as urgent, needs-reply, waiting, informational, newsletter, spam, and archive.
- Summarizes important email threads into short actionable context.
- Drafts reply suggestions in a concise and practical tone.
- Extracts task candidates, deadlines, and follow-up actions from inbox content.
- Encourages safe behavior by preferring drafts over auto-send for ambiguous or risky messages.

## Expected runtime tools

This skill is most useful when the runtime already exposes email and task related tools such as:

- `get_emails`
- `get_email_thread`
- `draft_email_reply`
- `send_email`
- `tag_email`
- `archive_email`
- `mark_spam`
- `create_task`
- `create_note`

The skill itself is instruction-only. It does not install backend integrations by itself.
