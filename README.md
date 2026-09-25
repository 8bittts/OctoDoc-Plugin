# OctoDoc

Read, prepare, verify and track signable documents with the OctoDoc command line.

## What it installs

One skill, `octodoc`, which drives the OctoDoc command line on your own machine.
Install the command line first, from https://octodoc.org/install — the skill calls it and does nothing without it.

## Claude Code and Cowork

Add this repository as a plugin marketplace, then install the plugin by name.

```bash
claude plugin install octodoc
```

## ChatGPT and Codex

Add this repository as a plugin marketplace with `codex plugin marketplace add`.
The same skill is discovered from the portable `plugin.json` at the root.

## What it will not do

A credential alone never authorizes a send or a signature.
Those acts need an attended authorization in your browser, or a mandate you granted that names the exact transaction.
