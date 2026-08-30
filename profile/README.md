<h1 align="center">🌅 Morgenruf</h1>

<p align="center">
  <strong>The daily standup bot you host yourself.</strong><br>
  Open source, Kubernetes-native, free for every seat, forever.
</p>

<p align="center">
  <em>Morgenruf</em> (German), <em>morning call</em><br>
  <sub>Built over a weekend at a Tim Hortons in Toronto 🇨🇦☕</sub>
</p>

<p align="center">
  <a href="https://github.com/morgenruf/morgenruf/releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/morgenruf/morgenruf?label=release&color=2ea043"></a>
  <a href="https://github.com/morgenruf/morgenruf/blob/main/LICENSE"><img alt="MIT licence" src="https://img.shields.io/github/license/morgenruf/morgenruf?color=blue"></a>
  <a href="https://github.com/morgenruf/morgenruf/actions/workflows/test.yml"><img alt="Tests" src="https://github.com/morgenruf/morgenruf/actions/workflows/test.yml/badge.svg"></a>
  <a href="https://github.com/morgenruf/e2e-tests/actions/workflows/e2e.yml"><img alt="End to end tests" src="https://github.com/morgenruf/e2e-tests/actions/workflows/e2e.yml/badge.svg"></a>
  <a href="https://status.morgenruf.dev"><img alt="Service status" src="https://img.shields.io/badge/status-live-2ea043"></a>
</p>

---

Standup tools charge per person, per month, to send a message and collect a reply.
Morgenruf does the same job on your own infrastructure, for nothing, and the data
never leaves it.

It DMs each teammate at their standup time, collects structured answers, and posts a
grouped summary to your channel. Multiple standups, per-person timezones, custom
questions, and a dashboard to read it all back.

## Install

```bash
helm repo add morgenruf https://charts.morgenruf.dev
helm repo update

helm upgrade --install morgenruf morgenruf/morgenruf \
  --namespace morgenruf --create-namespace \
  --set slack.clientId="YOUR_CLIENT_ID" \
  --set slack.clientSecret="YOUR_CLIENT_SECRET" \
  --set slack.signingSecret="YOUR_SIGNING_SECRET" \
  --set externalDatabase.url="postgresql://user:pass@host:5432/morgenruf" \
  --set flaskSecretKey="$(openssl rand -hex 32)" \
  --set app.url="https://api.your-domain.com"
```

Not on Kubernetes? [aws-deploy](https://github.com/morgenruf/aws-deploy) has Docker
Compose and CloudFormation. Full instructions at
[docs.morgenruf.dev](https://docs.morgenruf.dev).

> `flaskSecretKey` is required. It signs dashboard login tokens, so generate a real
> one rather than leaving it blank.

## What it does

**Standups.** As many as you need, each with its own channel, schedule, timezone,
questions and participants. A morning and an evening call for the same team is fine.

**Collection.** A DM at the scheduled time, a reminder if you want one, and an edit
window afterwards. People on leave are skipped rather than nagged.

**Summaries.** Grouped by person or by question, posted to the channel, optionally
threaded so the channel stays quiet. Optional AI summary via GPT or Claude.

**Reading it back.** A dashboard with participation per standup, per person, and
CSV export. Weekly digest by email if you want it out of Slack entirely.

**Wiring it up.** Signed webhooks on standup events, automation rules, and an MCP
server so Claude, Cursor or Copilot can query your standup history directly.

## Why self-host

|  | Morgenruf | Hosted alternatives |
|---|---|---|
| Price per seat | none | typically $2.50 to $4 per person per month |
| Where standup data lives | your database | the vendor's |
| Source | MIT, all of it | closed |
| Kubernetes and Helm | first class | not offered |
| Leaving | it is already yours | export and migrate |

Feature-by-feature comparisons age badly, so this table sticks to what is structural.
If a hosted tool does something Morgenruf does not and you need it,
[open an issue](https://github.com/morgenruf/morgenruf/issues/new/choose).

## Repositories

| Repo | What it is |
|---|---|
| [morgenruf](https://github.com/morgenruf/morgenruf) | The bot. Python, Flask, APScheduler, Postgres, plus the Helm chart |
| [docs](https://github.com/morgenruf/docs) | Documentation → [docs.morgenruf.dev](https://docs.morgenruf.dev) |
| [website](https://github.com/morgenruf/website) | Marketing site → [morgenruf.dev](https://morgenruf.dev) |
| [helm-charts](https://github.com/morgenruf/helm-charts) | Published chart repo → [charts.morgenruf.dev](https://charts.morgenruf.dev) |
| [aws-deploy](https://github.com/morgenruf/aws-deploy) | Docker Compose and CloudFormation templates |
| [status](https://github.com/morgenruf/status) | Status page → [status.morgenruf.dev](https://status.morgenruf.dev) |
| [e2e-tests](https://github.com/morgenruf/e2e-tests) | Playwright suite covering the app, docs, site and status page |

## Contributing

Issues and pull requests are welcome, including on the parts that are rough.
[CONTRIBUTING.md](https://github.com/morgenruf/.github/blob/main/CONTRIBUTING.md)
covers how to run it locally and what the review looks for.

Found a security problem? Please read
[SECURITY.md](https://github.com/morgenruf/.github/blob/main/SECURITY.md) and report
it privately rather than opening an issue.

- 🐛 [Report a bug](https://github.com/morgenruf/morgenruf/issues/new/choose)
- 💡 [Suggest a feature](https://github.com/morgenruf/morgenruf/discussions)
- 📧 [support@morgenruf.dev](mailto:support@morgenruf.dev)

---

<p align="center">
  MIT ·
  <a href="https://morgenruf.dev">morgenruf.dev</a> ·
  <a href="https://docs.morgenruf.dev">docs</a> ·
  <a href="https://status.morgenruf.dev">status</a>
</p>
