---
name: email-triage
description: Classify emails, summarize threads, draft replies in the user's style, extract actionable tasks, and propose follow-ups from the inbox.
version: 1.0.0
category: productivity
tags: [email, imap, smtp, triage, inbox, tasks, followup, productivity]
platforms: [linux, macos, windows]
requires_toolsets: [email, notes, tasks]
status: published
confidence: 0.96
source: taught
created: 2026-06-12T19:01:00Z
---

## When to Use
Use this skill when the user wants to process an inbox, classify incoming mail, summarize long threads, draft replies, identify urgent messages, extract tasks or follow-ups, clean up low-value email, or turn email into an actionable work queue.

## Procedure
1. Determine the user's goal: triage inbox, summarize a thread, draft a reply, identify urgent items, extract tasks, create follow-ups, or process a batch of emails.
2. Read only the messages relevant to the requested scope, such as unread mail, today's mail, a specific sender, a label, or a thread.
3. Classify each message into a small operational set such as: urgent, needs-reply, waiting, informational, newsletter, spam, or archive.
4. Summarize each relevant email or thread in one compact operational summary focused on what matters, what changed, and what action is needed.
5. If a reply is appropriate, draft a response that matches the user's likely tone: clear, concise, professional, and specific rather than generic.
6. Extract tasks, deadlines, follow-ups, decisions, requested documents, and blockers from the message content.
7. If task or note tools are available, convert actionable items into structured tasks or notes with due dates when those are explicitly present.
8. If the email is ambiguous, missing context, or risky, ask for confirmation before drafting or suggesting a response.
9. For low-value mail such as newsletters, notifications, or obvious spam, recommend archive, mute, unsubscribe, or spam handling rather than spending model effort on full replies.
10. Return a concise result grouped by priority: urgent items first, then reply-needed items, then extracted tasks and optional draft replies.

## Pitfalls
- Do not hallucinate commitments, dates, attachments, or facts that are not present in the email.
- Do not draft a confident reply when the message is emotionally sensitive, legal, financial, or unclear without flagging the risk.
- Do not convert vague ideas into hard deadlines unless the email explicitly states one.
- Do not summarize every detail of long threads; focus on decisions, asks, blockers, and next actions.
- Do not treat newsletters, automated alerts, and transactional mail the same way as human conversation.
- Do not auto-send replies unless the environment explicitly supports and authorizes that behavior.

## Verification
- Confirm which emails or threads were processed and by what scope.
- Confirm the classification for each important message.
- Confirm which messages need reply, which can be archived, and which look like spam or low priority.
- Confirm any extracted tasks, deadlines, and follow-up actions.
- Confirm that any proposed reply matches the user's intent and does not introduce facts not present in the thread.

This skill assumes the runtime exposes email-capable tools such as `get_emails`, `get_email_thread`, `draft_email_reply`, `send_email`, `tag_email`, `archive_email`, `mark_spam`, `create_task`, and `create_note`.

Recommended tool semantics:

- `get_emails`: retrieve email summaries or message lists for a scope such as unread, sender, tag, or date range.
- `get_email_thread`: fetch the full thread context for accurate summarization or reply drafting.
- `draft_email_reply`: create a draft reply without sending it.
- `send_email`: send only after explicit user confirmation or policy approval.
- `tag_email`: add or update labels such as urgent, reply-needed, waiting, newsletter, spam, or archive.
- `archive_email`: remove low-priority handled messages from the inbox.
- `mark_spam`: classify obvious spam or malicious mail.
- `create_task`: convert actionable items into tasks.
- `create_note`: store extracted context, decisions, or reference information.

Recommended classification labels:

- `urgent`
- `needs_reply`
- `waiting`
- `informational`
- `newsletter`
- `spam`
- `archive`

Recommended extracted fields:

- `message_id`
- `thread_id`
- `from`
- `subject`
- `received_at`
- `priority`
- `summary`
- `requested_action`
- `deadline`
- `follow_up_needed`
- `draft_reply`
- `tags`
- `task_candidates`
