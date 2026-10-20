# Raul B · 7sh1d0w7x

**Linux hardening and self-hosted automation, with a focus on AI/MCP security.**

I work with small teams and solo developers who run their own Linux server and do not have
a sysadmin — people who need to know what is actually exposed, what is worth fixing, and
what it costs to change it safely.

Everything is delivered in writing: a report you can read at your own pace, where each
finding names the command that reproduces it.

**Async, in writing, no calls.** Timișoara, Romania · the handle reads *seven-shadow-sevenx*.

---

## Start here

| | |
|---|---|
| **Services and prices** | [7sh1d0w7x.github.io](https://7sh1d0w7x.github.io) |
| **What a report looks like** | [a worked hardening report](https://7sh1d0w7x.github.io/blog/hardening-report-example.html) |
| **Contact** | [zshadowdev@duck.com](mailto:zshadowdev@duck.com) |
| **How it works** | written request → scope agreed → quote → agreed work → verification and handover |

---

## What I do

**Server Health Check.** An assessment of one Linux server with no configuration changes:
what is exposed, what matters, and what to fix first — a prioritized report with the evidence
behind each finding. Implementing the fixes is not included.

**Server Hardening.** An initial assessment, then the changes agreed in writing — SSH,
firewall, accounts and sudo, kernel parameters, updates — each one verified before the next,
followed by a before/after report with the evidence and the rollback step for each change.
Full reversal depends on the snapshot taken before the work and on what the change touched;
where a clean rollback is not possible, the report says so before the change is applied.

**Self-hosted automation.** n8n on your own server (Docker, Postgres, TLS), on a host that
has been hardened first, with backups and a documented handover.

**AI / MCP security review.** What an agent or MCP server can reach, where untrusted text
can steer it, and which read tools pair with write or egress tools. Written findings, with
a scanner you can re-run.

| Service | Public evidence | What you receive |
|---|---|---|
| **Server Health Check** | [linux-doctor](https://github.com/7sh1d0w7x/linux-doctor) · [state-witness](https://github.com/7sh1d0w7x/state-witness) | A prioritized report with the evidence behind each finding. No configuration changes. |
| **Server Hardening** | [worked lab report](https://7sh1d0w7x.github.io/blog/hardening-report-example.html) · [state-witness](https://github.com/7sh1d0w7x/state-witness) | Agreed changes, verification after each one, a before/after report with evidence, and rollback steps. |
| **Self-hosted automation** | [n8n lab summary](https://7sh1d0w7x.github.io/work.html) | A running n8n instance and the agreed workflows, operating docs, backup and a restore procedure. |
| **AI / MCP security review** | [poisoning lab](https://7sh1d0w7x.github.io/blog/tool-poisoning-by-hand.html) · [mcp-tool-scanner](https://github.com/7sh1d0w7x/mcp-tool-scanner) | Findings with their limits, priorities, and verification steps for each fix. |

Each service lists what it includes, what it excludes, and what you receive before any
work starts. Prices and current availability are on the site.

---

## Selected projects

**[Linux Doctor](https://github.com/7sh1d0w7x/linux-doctor)** — read-only Linux health
checks with plain-language explanations, copy-paste fixes, and a diff against the previous
run. CLI, web dashboard and desktop app share the same checks.

**[state-witness](https://github.com/7sh1d0w7x/state-witness)** — a Rust auditor for the
state a Linux host actually enforces: SSH, firewall, users and sudo, kernel parameters,
and ostree/bootc deployment facts. v0.1.0 — the project README lists exactly what is shipped.

**[mcp-tool-scanner](https://github.com/7sh1d0w7x/mcp-tool-scanner)** — a heuristic scanner
for tool descriptions that carry hidden instructions, with catalog validation and a
documented list of false positives and false negatives. A review aid, not a guarantee.

---

## Writing

- [What a hardening report actually looks like](https://7sh1d0w7x.github.io/blog/hardening-report-example.html)
  — a worked example, including the trap that makes a "hardened" server not hardened.
- [I poisoned my own MCP server](https://7sh1d0w7x.github.io/blog/tool-poisoning-by-hand.html)
  — build a server, poison one tool description, capture what the client receives, then
  detect it. The scanner came out of this lab.
- [Linux Doctor, heal thyself: 20 ways my Linux health checker was wrong](https://dev.to/7sh1d0w7x/linux-doctor-heal-thyself-20-ways-my-linux-health-checker-was-wrong-1b2a)
  — building a diagnostic tool in public, mistakes included.

The repositories carry the rest: tests next to the behaviour they protect, and documentation
that states limits as well as capabilities.

---

## How I work

- **Evidence over assertion.** Reproduce the problem before fixing it; every claim is tied
  to a command or a test.
- **Read-only first.** Diagnosis does not change the system. Changes are scoped in writing,
  agreed before they happen, and reversible.
- **AI drafts, the human owns.** AI assistance is disclosed in the projects; I can explain
  every design and code decision.

---

## Technologies

Rust · Node.js · Python · Bash · Linux (Fedora, Debian) · systemd · Docker / Podman ·
PostgreSQL · n8n · GitHub Actions

---

<sub>Open to collaborations around Linux tooling, security and self-hosting.</sub>
