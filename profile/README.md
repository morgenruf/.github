<p align="center">
  <img src="logo.png" alt="Morgenruf: a rooster in sunglasses holding a mug of coffee" width="180">
</p>

<h1 align="center">Morgenruf</h1>

<p align="center">
  <strong>Async standups, coffee chats and kudos for Slack.</strong><br>
  Free for every seat, hosted or self-hosted. MIT licensed, all of it.
</p>

<p align="center">
  <a href="https://api.morgenruf.dev/install?utm_source=github&utm_medium=org-profile"><img alt="Add to Slack" height="40" width="139" src="https://platform.slack-edge.com/img/add_to_slack.png" srcset="https://platform.slack-edge.com/img/add_to_slack.png 1x, https://platform.slack-edge.com/img/add_to_slack@2x.png 2x"></a>
</p>
<p align="center">
  <sub>Free on the hosted instance, at any team size. Or <a href="https://morgenruf.dev/setup/">self-host it</a> with Docker or Helm and keep every answer in your own Postgres.</sub>
</p>

<p align="center">
  <a href="https://github.com/morgenruf/morgenruf/releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/morgenruf/morgenruf?label=release&color=2ea043"></a>
  <a href="https://github.com/morgenruf/morgenruf/blob/main/LICENSE"><img alt="MIT licence" src="https://img.shields.io/github/license/morgenruf/morgenruf?color=blue"></a>
  <a href="https://hub.docker.com/r/morgenruf/morgenruf"><img alt="Docker pulls" src="https://img.shields.io/docker/pulls/morgenruf/morgenruf?color=2496ed&logo=docker&logoColor=white"></a>
  <a href="https://github.com/morgenruf/morgenruf/actions/workflows/test.yml"><img alt="Tests" src="https://github.com/morgenruf/morgenruf/actions/workflows/test.yml/badge.svg"></a>
  <a href="https://status.morgenruf.dev"><img alt="Service status" src="https://img.shields.io/badge/status-live-2ea043"></a>
</p>

<p align="center">
  <a href="https://morgenruf.dev">Website</a> ·
  <a href="https://docs.morgenruf.dev">Docs</a> ·
  <a href="https://morgenruf.dev/compare/standup-bots/">Compare standup bots</a> ·
  <a href="https://www.linkedin.com/company/morgenruf">LinkedIn</a>
</p>

---

<img src="dashboard.jpg" alt="The Morgenruf dashboard: who has answered today's standup, who is blocked, recent kudos and the next coffee chat" width="100%">

Standup tools charge per person, per month, to send a message and collect a reply.
Pairing tools charge again for the introductions. Recognition tools charge a third
time. Morgenruf does all three in one app, for nothing.

## What it does

**Standups.** Questions by DM at each person's local hour, one summary in the channel,
blockers pulled out. As many standups as you need, each with its own schedule,
questions and people. Leave is skipped, not nagged.

**Coffee chats.** Pairs people from a channel on a cadence, avoiding repeat matches.
The pair votes on an hour that suits both working days, and Zoom books it.

**Kudos.** A daily allowance that resets at midnight in each person's timezone, your
own emoji as the token, and leaderboards for giving as well as receiving.

**Insights.** Questions that need two of those at once: a blocker nobody has cleared
in days, someone who answers every standup and is thanked by nobody.

**Who runs what.** Hand the standups to a team lead and coffee chats to someone in
HR, without giving either of them the whole workspace.

**Wiring it up.** Signed webhooks, automation rules, and an MCP server so Claude,
Cursor or Copilot can ask about any of it.

## Roadmap

Written the way the bot asks: what happened yesterday, what is happening today, what
comes next. No dates; [asking for one](https://github.com/morgenruf/morgenruf/discussions/new?category=ideas) moves it up.

| | |
|---|---|
| **Yesterday** | Per-feature admins (1.8.0) · Zoom meetings (1.8.0) · Google Chat (beta) |
| **Today** | Microsoft Teams · Celebrations: birthdays and work anniversaries |
| **Tomorrow** | Calendar holds for coffee chats · Meet and Teams rooms |
| **Someday** | Public REST API · Onboarding journeys |

## Run it yourself

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

Not on Kubernetes? Docker Compose is a `docker compose up -d` away; see
[setup](https://morgenruf.dev/setup/) and [docs.morgenruf.dev](https://docs.morgenruf.dev).

## Why Morgenruf

| | Morgenruf | Hosted standup bots |
|---|---|---|
| Price per seat | none, at any size | free up to a cap, then per person |
| Where answers live | your Postgres, or the free hosted instance | the vendor's |
| Source | MIT, all of it | closed |
| Standups, pairing and recognition | one app | usually three subscriptions |
| Kubernetes and Helm | first class | not offered |

For free plan limits and prices of eleven standup bots, each read from the vendor's
own pricing page, see the [comparison](https://morgenruf.dev/compare/standup-bots/).

## Repositories

| Repo | What it is |
|---|---|
| [morgenruf](https://github.com/morgenruf/morgenruf) | The app: Python, Flask, Postgres, the dashboard and the Helm chart |
| [docs](https://github.com/morgenruf/docs) | Documentation, at [docs.morgenruf.dev](https://docs.morgenruf.dev) |
| [website](https://github.com/morgenruf/website) | The site, at [morgenruf.dev](https://morgenruf.dev) |
| [helm-charts](https://github.com/morgenruf/helm-charts) | Published charts, at [charts.morgenruf.dev](https://charts.morgenruf.dev) |
| [aws-deploy](https://github.com/morgenruf/aws-deploy) | Docker Compose and CloudFormation templates |
| [status](https://github.com/morgenruf/status) | Status page, at [status.morgenruf.dev](https://status.morgenruf.dev) |
| [e2e-tests](https://github.com/morgenruf/e2e-tests) | Playwright suite for the app, docs, site and status page |

## Contributing

Issues and pull requests are welcome, including on the parts that are rough.
[CONTRIBUTING.md](https://github.com/morgenruf/.github/blob/main/CONTRIBUTING.md)
covers running it locally and what review looks for. Security problems go through
[SECURITY.md](https://github.com/morgenruf/.github/blob/main/SECURITY.md), privately.

[Report a bug](https://github.com/morgenruf/morgenruf/issues/new/choose) ·
[Suggest a feature](https://github.com/morgenruf/morgenruf/discussions) ·
hello@morgenruf.dev

---

<p align="center">
  <sub><em>Morgenruf</em> is German for <em>morning call</em>. Built over a weekend at a Tim Hortons in Kitchener, Ontario, by <a href="https://clouddrove.com">CloudDrove</a>.</sub>
</p>
