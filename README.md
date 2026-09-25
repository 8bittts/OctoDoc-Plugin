<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://octodoc.org/brand/octodoc-mark-inverse.svg">
    <img src="https://octodoc.org/brand/octodoc-mark.svg" alt="OctoDoc" width="128" height="128">
  </picture>
</p>

<h1 align="center">OctoDoc for Claude and Codex</h1>

<p align="center">
  <strong>The document that answers — from the agent you already use.</strong>
  <br>
  <a href="https://octodoc.org">OctoDoc.org</a>
</p>

<p align="center">
  <img alt="Claude Code" src="https://img.shields.io/badge/Claude%20Code-installed%20and%20checked-0A0A0B">
  <img alt="Codex" src="https://img.shields.io/badge/Codex-installed%20and%20checked-0A0A0B">
  <img alt="Cowork and ChatGPT" src="https://img.shields.io/badge/Cowork%20and%20ChatGPT-same%20bundle-2B3A67">
  <img alt="License MIT" src="https://img.shields.io/badge/license-MIT-2B3A67">
</p>

---

Ask your agent to read a contract, fill a form, send it for signature, and tell you who has signed.
An answer comes back with the page it came from. The file that gets sealed is the file a human approved.

<p align="center">
  <img src="https://octodoc.org/about/octo/hello-1024.webp" alt="Octo, a soft lavender octopus with a rounded mantle and eight short arms, raising one arm in greeting" width="200" height="200">
  <br>
  <em>Meet Octo. They have eight arms, which is exactly as many jobs as a document has.</em>
</p>

## What you can ask for

- **"What is waiting for my signature?"** — the list, and who is holding each one up.
- **"Summarize this NDA for the receiving party."** — cited to the page it came from.
- **"Fill the W-9 with my business details and tell me what is still missing."** — from a reviewed reusable form.
- **"Send it to Dana for signature."** — prepared by the agent, authorized by you.
- **"Check this sealed PDF against the digest the sender published."** — offline, on your own machine.

## Install

**1. Install the command line.** The plugin drives it, and does nothing without it.

```bash
curl -fsSL https://octodoc.org/install | sh
```

**2. Add the plugin.**

Claude Code and Cowork:

```bash
claude plugin marketplace add 8bittts/OctoDoc-Plugin
claude plugin install octodoc@octodoc
```

ChatGPT and Codex:

```bash
codex plugin marketplace add 8bittts/OctoDoc-Plugin
codex plugin add octodoc@octodoc
```

**3. Sign in once.** `octodoc login` opens your browser and authorizes that machine.

## What it will not do

This is the part worth reading before you let any agent near a signature.

- **A stored credential alone never signs or sends.**
  Each binding act needs a transaction digest the server computed, plus either an authorization you complete in your browser or a delegation you granted in advance that names that exact operation.
- **No agent edits the bytes you sign.**
  Summaries, answers and citations sit beside the file. What gets sealed is what a human approved.
- **A summary is not advice from an attorney**, and the skill says so rather than guessing.

## How it works

The plugin installs one skill. The skill drives the `octodoc` program on your own machine, which talks to your workspace.
Reading a local PDF and checking a sealed one stay on your machine.
Summarizing sends bounded document text to an approved model provider and returns what it answered.

## Learn more

- [What OctoDoc is](https://octodoc.org/about) — the guide, in plain language
- [The whitepaper](https://octodoc.org/whitepaper) — how signing, sealing and checking actually work
- [Privacy notice](https://octodoc.org/privacy) · [Terms](https://octodoc.org/terms)

## License

MIT, covering this plugin bundle. The OctoDoc service and its source are not MIT; see [LICENSE](LICENSE).
