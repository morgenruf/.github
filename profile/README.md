# 🌅 Morgenruf

**Self-hosted daily standup bot for Slack — open source, Kubernetes-native, free forever.**

> *Morgenruf* (German) — "morning call"

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
| Custom questions | ✅ | ✅ | ✅ | ❌ |
| Skip today | ✅ | ✅ | ✅ | ❌ |
| Per-user timezone | ✅ | ✅ | ✅ | ❌ |
| Mood tracking | ✅ | ❌ | ✅ | ❌ |
| Analytics dashboard | ✅ | ✅ | ✅ | ❌ |
| Weekly email digest | ✅ | ✅ | ✅ | ❌ |
| Webhooks | ✅ | ❌ | ❌ | ❌ |

---

## Repositories

| Repo | Description |
|---|---|
| [morgenruf/morgenruf](https://github.com/morgenruf/morgenruf) | 🤖 Core bot — Python, Helm chart, Dockerfile |
| [morgenruf/helm-charts](https://github.com/morgenruf/helm-charts) | 📦 Helm chart repository — `charts.morgenruf.dev` |
| [morgenruf/docs](https://github.com/morgenruf/docs) | 📚 Documentation — `docs.morgenruf.dev` |

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

## Community

- 🐛 [Report a bug](https://github.com/morgenruf/morgenruf/issues/new?template=bug_report.md)
- 💡 [Request a feature](https://github.com/morgenruf/morgenruf/discussions/new?category=ideas)
- 💬 [GitHub Discussions](https://github.com/morgenruf/morgenruf/discussions)
- 📧 [support@morgenruf.dev](mailto:support@morgenruf.dev)

---

<p align="center">MIT License · <a href="https://morgenruf.dev">morgenruf.dev</a></p>
