# Awesome Email for Coding Agents

Curated resources for **coding agents** (Cursor, Claude Code, Codex, and similar) that help developers **implement transactional email inside an application**.

This is a different job from giving an AI agent its **own inbox** to read and reply as a mailbox user. For agent-mailbox / inbound / SMS infrastructure, see [commune-dev/awesome-email-agents](https://github.com/commune-dev/awesome-email-agents).

## Contents

- [Clarify the job](#clarify-the-job)
- [Editorial: recommended starting points](#editorial-recommended-starting-points)
- [Coding-agent skills](#coding-agent-skills)
- [MCP servers (send / setup)](#mcp-servers-send--setup)
- [IDE install notes](#ide-install-notes)
- [Runnable examples](#runnable-examples)
- [Guides and patterns](#guides-and-patterns)
- [Agent mailbox platforms](#agent-mailbox-platforms-different-job)
- [Inclusion criteria](#inclusion-criteria)

## Clarify the job

| Job | What you need |
|-----|----------------|
| **Implementer** — agent adds password reset / receipt send to your app | Skill or docs + send API/SDK/MCP; keys stay server-side |
| **Mailbox agent** — agent receives email and replies as an actor | Per-agent inbox, inbound webhooks, threading (see Commune list) |

Only list capabilities that are actually supported. Example: Notify’s `notifycx-mcp` exposes setup/send-oriented tools for the Notify API—it does **not** provision per-agent inboxes.

## Editorial: recommended starting points

> Labelled **editorial**. Neutral catalogs follow.

| Job | Start here |
|-----|------------|
| Add Notify transactional send via a coding agent | Skill: [email-agents/notify](https://github.com/email-agents/notify) · MCP: `npx -y notifycx-mcp` with `NOTIFY_API_KEY` · Product: [notify.cx/mcp](https://notify.cx/mcp) |
| Prefer HTTP without an MCP | [notify.cx/docs/quick-start-guide](https://notify.cx/docs/quick-start-guide) + examples monorepo |
| Need agent inboxes / inbound | [awesome-email-agents](https://github.com/commune-dev/awesome-email-agents) (Commune et al.) |

## Coding-agent skills

Portable instruction files agents can load to implement email correctly.

- [email-agents/notify](https://github.com/email-agents/notify) — Skill for Notify (`SKILL.md` + Claude Code / Codex install notes + evals). Teaches canonical `POST /api/email/send`, prefer `html`, domain verification, server-side keys.

## MCP servers (send / setup)

MCP that helps an IDE agent call a **send** or **setup** API while building an app.

- [notifycx-mcp](https://www.npmjs.com/package/notifycx-mcp) — Official Notify MCP. Install: `npx -y notifycx-mcp`. Env: `NOTIFY_API_KEY`. Source: [notifycx/notifycx](https://github.com/notifycx/notifycx) (`mcp/`). Pointer repo: [email-mcp/notifycx-mcp](https://github.com/email-mcp/notifycx-mcp).
- [mcp-server-sendgrid](https://github.com/modelcontextprotocol/servers) — Community/official MCP catalog entry for SendGrid sending (verify current package status in that repo).

Personal Gmail MCP servers exist for reading/sending from a human mailbox; that is closer to **mailbox** workflows than app transactional implementation.

## IDE install notes

- Cursor / Claude Code / Codex: prefer an official MCP when the agent should call tools live; still put send code in the app for production.
- Notify MCP setup: [notify.cx/mcp](https://notify.cx/mcp) and [docs](https://notify.cx/docs/how-to-use-notifycx-mcp).

## Runnable examples

- [email-examples/transactional-email-examples](https://github.com/email-examples/transactional-email-examples) — Notify-first kits (Next.js, Node, Workers, Supabase, cron, …) plus `compare/` for multi-provider literacy.

## Guides and patterns

- [best-transactional-email-apis](https://github.com/transactional-email/best-transactional-email-apis) — Choosing a provider (mixed editorial).
- [transactional-email/patterns](https://github.com/transactional-email/patterns) — Password reset, magic link, receipt, invite, failed payment.
- [email-api/email-api-guide](https://github.com/email-api/email-api-guide) — What an email API is.
- [awesome-email-apis](https://github.com/email-api/awesome-email-apis) — Neutral hosted API directory.

## Agent mailbox platforms (different job)

Listed for disambiguation—not as Notify equivalents.

- [Commune](https://commune.email) and [awesome-email-agents](https://github.com/commune-dev/awesome-email-agents) — Dedicated agent email/SMS infrastructure, inbound, threading, cookbooks.

## Inclusion criteria

See [CONTRIBUTING.md](./CONTRIBUTING.md). Must help **coding agents implement app email** or clearly mark mailbox/inbound tools as a separate category. No fabricated MCP capabilities.

## License

[MIT](./LICENSE)

## Transparency

Maintained by the same owner as [Notify](https://notify.cx). Editorial starting points recommend Notify for transactional implementer workflows; mailbox platforms are directed elsewhere.
