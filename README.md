# Raul B · 7sh1d0w7x

**Read-only Linux security tooling: auditors that report what a host actually enforces,
not what its configuration files claim.**

I build the tools I use in my own lab, and publish the lab notes with them: SSH, firewall,
accounts, kernel parameters, immutable/atomic hosts, and the text an AI agent is allowed to
read. Timișoara, Romania · async, in writing · the handle reads *seven-shadow-sevenx*.

---

## Open source

**[state-witness](https://github.com/7sh1d0w7x/state-witness)** · Rust, single binary, no runtime engine

An effective-state auditor for Linux, with first-class support for immutable hosts
(Fedora Atomic, Bazzite, bootc / RHEL Image Mode). 25 checks across SSH, firewall, users,
sudo and sysctl. Every finding names the source that produced it (`sshd -T`, `sysctl -n`,
the live ruleset, the file it was read from), and the README is explicit about what each
source proves and what it does not. Text and JSON output, meaningful exit codes.

**[linux-doctor](https://github.com/7sh1d0w7x/linux-doctor)** · Node, CLI and desktop app

Read-only health checks with plain-language explanations, copy-paste fixes, and a diff
against the previous run. The CLI, the dashboard and the desktop app run the same checks.
The [latest release](https://github.com/7sh1d0w7x/linux-doctor/releases/latest) ships
`.deb`, `.rpm` and AppImage builds, each with a detached signature.

**[mcp-tool-scanner](https://github.com/7sh1d0w7x/mcp-tool-scanner)** · Python, standard library only

Scans an MCP `tools/list` catalog for tool descriptions that carry hidden instructions.
Exit codes separate "clean", "signal found" and "cannot read the input", so a failed scan
is never reported as clean. A review aid with a documented false-positive list, not a
guarantee.

## The lab work behind it

The failures are published too, because they are the part that teaches something:

- [Four doors to root](https://github.com/7sh1d0w7x/state-witness/blob/main/docs/case-studies/2026-10-27-four-doors-to-root.md): four ways to reach root on a disposable VM, and what an auditor reports at each step.
- [Runbooks with their raw output](https://github.com/7sh1d0w7x/state-witness/tree/main/docs/runbooks): SSH, firewall, sudoers, vault backup and restore, each with the evidence file from the run.
- [An evidence pack you can check](https://7sh1d0w7x.github.io/evidence.html): checksums, the before/after diff, and the downloadable pack you can verify yourself.
- [A worked hardening report](https://7sh1d0w7x.github.io/blog/hardening-report-example.html): the document a client actually receives.

## Writing

- [What a hardening report actually looks like](https://7sh1d0w7x.github.io/blog/hardening-report-example.html): a worked example, including the trap that makes a "hardened" server not hardened.
- [I poisoned my own MCP server](https://7sh1d0w7x.github.io/blog/tool-poisoning-by-hand.html): build a server, poison one tool description, capture what the client receives, then detect it. The scanner came out of this lab.
- [Linux Doctor, heal thyself: 20 ways my Linux health checker was wrong](https://dev.to/7sh1d0w7x/linux-doctor-heal-thyself-20-ways-my-linux-health-checker-was-wrong-1b2a): building a diagnostic tool in public, mistakes included.
- [No space left on device, with 56 MB free](https://github.com/7sh1d0w7x/linux-doctor/blob/main/docs/case-studies/inode-exhaustion.md): reproduce inode exhaustion on a throwaway filesystem, confirm the cause by hand, verify the fix. A lab, not an incident.

## How I work

- **Evidence over assertion.** Reproduce the problem before fixing it. Every claim is tied to a command or a test.
- **Read-only first.** Diagnosis does not change the system. Before any change I assess its impact and agree the rollback step in writing. Some changes revert cleanly, some depend on a snapshot taken beforehand, and some cannot be reversed at all; where that is the case, it is said before the change, not after.
- **AI-assisted, with explicit verification.** AI assistance is used in these projects. The repositories document the verification steps, the known limitations, and what remains unverified.

## Contributing and asking

Issues and questions are welcome in all three repositories; linux-doctor also has
Discussions enabled. state-witness and mcp-tool-scanner are small enough to read in a
sitting, and both list what they do not do.

---

## Work with me

I take a small number of freelance engagements: the same tools and the same standard of
evidence, on your server instead of my lab. Prices and availability are on
[the site](https://7sh1d0w7x.github.io). Everything is delivered in writing, with the evidence behind each finding. No calls: scope, quote and handover stay in writing.

**Server Health Check.** An assessment of one Linux server with no configuration changes: what is exposed, what matters, what to fix first, a prioritized report with the evidence behind each finding. Implementing the fixes is not included. If the audit finds no medium or high severity finding, you do not pay. Evidence: [state-witness](https://github.com/7sh1d0w7x/state-witness), [linux-doctor](https://github.com/7sh1d0w7x/linux-doctor).

**Server Hardening.** The assessment, then the changes agreed in writing (SSH, firewall, accounts and sudo, kernel parameters, updates), each verified before the next, followed by a before/after report with the evidence and the rollback step for every change. Evidence: [a worked report](https://7sh1d0w7x.github.io/blog/hardening-report-example.html).

**Self-hosted automation.** n8n on your own server (Docker, Postgres, TLS) on a host that has been hardened first, with backups and a documented handover. Evidence: [the n8n lab summary](https://7sh1d0w7x.github.io/work.html).

**AI / MCP security review.** What an agent or an MCP server can reach, where untrusted text can steer it, and which read tools pair with write or egress tools. Written findings, with a scanner you can re-run. Evidence: [the poisoning lab](https://7sh1d0w7x.github.io/blog/tool-poisoning-by-hand.html), [mcp-tool-scanner](https://github.com/7sh1d0w7x/mcp-tool-scanner).

Every service lists what it includes, what it excludes and what you receive before work
starts. How it works: written request, scope agreed, quote, agreed work, verification and
handover. Contact: [zshadowdev@duck.com](mailto:zshadowdev@duck.com).

---

## Technologies

Rust · Node.js · Python · Bash · Linux (Fedora, Debian) · systemd · Docker / Podman ·
PostgreSQL · n8n · GitHub Actions

<sub>Open to collaborations around Linux tooling, security and self-hosting.</sub>
