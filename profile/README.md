<h1 align="center">🌅 Morgenruf</h1>

<p align="center">
  <strong>The team rituals you host yourself.</strong><br>
  Async standups, coffee chats, kudos and the insights they add up to.<br>
  Open source, Kubernetes-native, free for every seat, forever.
</p>

<p align="center">
  <em>Morgenruf</em> (German), <em>morning call</em><br>
  <sub>Built over a weekend at a Tim Hortons in Kitchener 🇨🇦☕</sub>
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
Pairing tools charge again for the introductions. Recognition tools charge a third
time. Morgenruf does all three on your own infrastructure, for nothing, and the data
never leaves it.

Four modules over one deployment and one database. Each owns its schedule, its Slack
handlers and its dashboard pages, and any of them can be switched off without
touching the others.

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
A DM at the scheduled time, a reminder if you want one, and an edit window
afterwards. People on leave are skipped rather than nagged. Summaries post to the
channel grouped by person or by question, optionally threaded so the channel stays
quiet, and each standup can email its own lead rather than one address for the lot.

**Coffee chats.** Pairs people from a channel on a cadence, avoiding whoever they met
last time. Groups of two to eight, and a remainder of two forms its own group rather
than being folded into a larger one. The introduction carries an opener and times
that suit both people's working hours; they vote with a button, and the hour they
both pick becomes the meeting. Connect Zoom and it is booked at that hour, on the
account of whoever in the pair linked it. Anyone can ask for a different match, once
per round. Three days later it nudges pairs who have not met; on day six it asks
whether they did.

That answer is reported four ways rather than two, because *did not meet*, *never
answered* and *never delivered* mean different things, and only the last is a fault
of ours.

**Kudos.** `kudos @teammate nice work on the deploy`, with a daily allowance that
resets at midnight in each person's own timezone. Leaderboards for who is recognised
and for who does the recognising, since the second is what keeps the habit alive.

**Insights.** The questions that need two of those datasets at once: a blocker nobody
has cleared in days, someone who answers every standup and is thanked by nobody.

**Who runs what.** Roles used to be workspace-wide, so putting a team lead in charge
of the standups meant handing them webhooks and API keys as well. A grant is per
feature: the lead runs the standups, someone in HR runs coffee chats and kudos, and
neither can mint a key or publish the workspace's standups. Handed over from the
Members page, one press per feature.

**Wiring it up.** Signed webhooks, automation rules, and an MCP server with seventeen
tools so Claude, Cursor or Copilot can ask about any of it. The tool list respects
the same per-workspace switches the dashboard does, so an assistant is never offered
a feature that workspace has turned off.

## Why self-host

|  | Morgenruf | Hosted alternatives |
|---|---|---|
| Price per seat | none | typically $2.50 to $4 per person per month |
| Where standup data lives | your database | the vendor's |
| Source | MIT, all of it | closed |
| Kubernetes and Helm | first class | not offered |
| Standups, pairing and recognition | one app | usually three subscriptions |
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
