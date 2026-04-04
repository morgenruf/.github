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
helm upgrade --install morgenruf \
  oci://ghcr.io/morgenruf/helm/morgenruf \
  --namespace morgenruf --create-namespace \
  --set secret.slackBotToken="xoxb-..." \
  --set secret.slackSigningSecret="..."
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
