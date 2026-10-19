# Raul B · 7sh1d0w7x

I build Linux diagnostics and security tooling, and I use it on real hosts.

Freelance, Timișoara, Romania. The handle reads **seven-shadow-sevenx**. I work async,
in writing, without calls.

Most of my work answers one question: **what is this machine actually doing right
now** — not what its config files claim. Then it tries to make that answer
something you can act on.

---

## Selected projects

### Linux Doctor — diagnose a Linux host, explain each finding, remember what changed

A read-only health checker for Linux: it finds what is actually wrong, explains
why it matters in plain language, and gives you a copy-paste fix. Every run is
diffed against the previous one, so you see what is new, what got fixed, and
what stayed the same. CLI, web dashboard and a native desktop app share the same
checks.

- Diagnostics never modify the host. The only files it writes are its own
  history and cache.
- `--fix` prints a dry-run plan; `--fix --yes` runs only the `[apply]` commands
  from a pinned catalog, and `[manual]` items are never executed for you.
- Ships as `npx`, npm package, RPM, `.deb` or AppImage; works on immutable hosts
  (Silverblue, Bazzite).

→ [github.com/7sh1d0w7x/linux-doctor](https://github.com/7sh1d0w7x/linux-doctor)

### state-witness — effective-state security audit for immutable Linux

A Rust auditor that reports what the running system enforces, not what a file
says: `sshd -T`, `sysctl -n`, the live packet filter, `/etc/passwd` and
`/etc/shadow`, plus ostree/bootc deployment facts (`/etc` drift, signature
state).

**Real status: v0.1.0.** Five commands — `ssh`, `atomic`, `sysctl`, `firewall`,
`users` — with text and JSON output, and one exit-code policy (0 = no failures,
1 = at least one finding failed, 2 = the audit could not run). Every finding
names the command or file its value came from. Line numbers inside config files
are **not** emitted yet, and SARIF, remediation and a versioned JSON schema are
on the roadmap, not shipped.

→ [github.com/7sh1d0w7x/state-witness](https://github.com/7sh1d0w7x/state-witness)

### mcp-tool-scanner — a heuristic smoke detector for poisoned MCP tool descriptions

Tool descriptions go straight into the model's prompt, which makes them an
attack surface. This scanner flags the obvious cases — file reads, "ignore
previous instructions", concealment lines — and validates the catalog it is
given instead of reporting an unreadable input as clean.

It is a **review aid, not protection**: no signal does not mean a server is
safe. The limit that actually holds is capability — if a tool cannot reach a
sensitive file, an instruction to read it has nothing to exfiltrate.

→ [github.com/7sh1d0w7x/mcp-tool-scanner](https://github.com/7sh1d0w7x/mcp-tool-scanner)

---

## Writing

- **[I poisoned my own MCP server](https://7sh1d0w7x.github.io/blog/tool-poisoning-by-hand.html)**
  — build a server, poison a tool description, watch a real client act on it,
  then detect it. The scanner above came out of this lab.
- **[Linux Doctor, heal thyself: 20 ways my Linux health checker was wrong](https://dev.to/7sh1d0w7x/linux-doctor-heal-thyself-20-ways-my-linux-health-checker-was-wrong-1b2a)**
  — building a diagnostic tool in public, including the mistakes.

The repos carry the rest: tests next to the behaviour they protect, and design
notes that say why, not just what.

---

## How I work

- **Evidence over assertion.** Reproduce the problem before fixing it; if a
  result is wrong, it gets a failing test first.
- **Read-only by default.** A diagnostic tool should not change what it
  diagnoses; when a change is needed, it is explicit, scoped and reversible.
- **AI drafts, the human owns.** AI assistance is disclosed in the projects, and
  I can explain every design and code decision. If I cannot explain a line, it
  does not ship.

---

## Services

Fixed scope, fixed price, delivered in writing. The two open-source tools above
are the same checks I run on a server.

| Service | What it covers |
|---|---|
| **Server hardening** | SSH keys only, default-deny firewall, patching, before/after report and how to roll back |
| **Self-hosted automation** | n8n on your own server (Docker + Postgres + TLS), so the data stays yours |
| **MCP / agent security review** | What is exposed, what a poisoned description can reach, which read tools pair with write/egress tools, and how to verify each fix |

Nothing here is a compliance certification or a security guarantee — it is a
scoped review with a written record of what was checked.

→ **[7sh1d0w7x.github.io](https://7sh1d0w7x.github.io)** (services, pricing, FAQ)

**Contact:** [zshadowdev@duck.com](mailto:zshadowdev@duck.com) · available for
freelance, async, no calls.

---

## Technologies

Rust · Node.js / JavaScript · Python · Bash · Linux (Fedora, Debian) · systemd ·
Docker / Podman · PostgreSQL · n8n · GitHub Actions

---

<sub>Also on [GitHub](https://github.com/7sh1d0w7x). Open to collaborations around
Linux tooling, security and self-hosting.</sub>
