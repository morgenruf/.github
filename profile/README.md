# 🌅 Morgenruf

**Self-hosted daily standup bot for Slack — open source, Kubernetes-native, free forever.**

> *Morgenruf* (German) — "morning call" · Built over a weekend at a Tim Hortons in Toronto 🇨🇦☕

[![Release](https://img.shields.io/github/v/release/morgenruf/morgenruf?label=latest&color=brightgreen)](https://github.com/morgenruf/morgenruf/releases/tag/v1.0.0)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/morgenruf/morgenruf/blob/main/LICENSE)
[![E2E Tests](https://github.com/morgenruf/e2e-tests/actions/workflows/e2e.yml/badge.svg)](https://github.com/morgenruf/e2e-tests/actions/workflows/e2e.yml)
[![Status](https://img.shields.io/badge/status-operational-brightgreen)](https://status.morgenruf.dev)

Morgenruf replaces expensive SaaS standup tools with a lightweight, self-hosted bot you fully control. It DMs your team at standup time, collects structured updates, and posts summaries to your channels — with zero vendor lock-in.

---

## Why Morgenruf?

| | Morgenruf | Geekbot | DailyBot | Standup & Prosper |
|---|---|---|---|---|
| Self-hosted | ✅ | ❌ | ❌ | ❌ |
| Free forever | ✅ | ❌ | ❌ | ❌ |
| Open source | ✅ MIT | ❌ | ❌ | ❌ |
| Kubernetes / Helm | ✅ | ❌ | ❌ | ❌ |
| Your data, your infra | ✅ | ❌ | ❌ | ❌ |
| AI standup summary | ✅ GPT-4o / Claude | ❌ | ❌ | ❌ |
| MCP server (AI tools) | ✅ | ❌ | ❌ | ❌ |
| Custom questions | ✅ | ✅ | ✅ | ❌ |
| Skip today | ✅ | ✅ | ✅ | ❌ |
| Per-user timezone | ✅ | ✅ | ✅ | ❌ |
| Mood tracking | ✅ | ❌ | ✅ | ❌ |
| Analytics dashboard | ✅ | ✅ | ✅ | ❌ |
| Weekly email digest | ✅ | ✅ | ✅ | ❌ |
| Webhooks | ✅ | ❌ | ❌ | ❌ |

---

## Quick Start

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

➡️ Full docs at [docs.morgenruf.dev](https://docs.morgenruf.dev)

---

## Repositories

| Repo | Description |
|---|---|
| [morgenruf/morgenruf](https://github.com/morgenruf/morgenruf) | 🤖 Core bot — Python, Flask, Helm chart |
| [morgenruf/docs](https://github.com/morgenruf/docs) | 📚 Documentation — [docs.morgenruf.dev](https://docs.morgenruf.dev) |
| [morgenruf/website](https://github.com/morgenruf/website) | 🌐 Marketing site — [morgenruf.dev](https://morgenruf.dev) |
| [morgenruf/status](https://github.com/morgenruf/status) | 📡 Status page — [status.morgenruf.dev](https://status.morgenruf.dev) |
| [morgenruf/helm-charts](https://github.com/morgenruf/helm-charts) | 📦 Helm chart repo — [charts.morgenruf.dev](https://charts.morgenruf.dev) |
| [morgenruf/aws-deploy](https://github.com/morgenruf/aws-deploy) | ☁️ One-click AWS & Docker Compose templates |
| [morgenruf/e2e-tests](https://github.com/morgenruf/e2e-tests) | 🧪 Playwright E2E test suite (80 tests) |

---

## Community

- 🐛 [Report a bug](https://github.com/morgenruf/morgenruf/issues/new?template=bug_report.md)
- 💡 [Request a feature](https://github.com/morgenruf/morgenruf/discussions/new?category=ideas)
- 💬 [GitHub Discussions](https://github.com/morgenruf/morgenruf/discussions)
- 📧 [support@morgenruf.dev](mailto:support@morgenruf.dev)

---

<p align="center">MIT License · <a href="https://morgenruf.dev">morgenruf.dev</a> · <a href="https://status.morgenruf.dev">status</a> · v1.0.0</p>
