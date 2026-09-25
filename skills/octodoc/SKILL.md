---
name: octodoc
description: >-
  Find reviewed reusable PDF forms, fill facts the user supplied, open, review, summarize and prepare signable documents with OctoDoc, and check a sealed PDF offline against the digest its sender published.
  Invoke with /octodoc or $octodoc.
  Use for a contract, NDA, agreement, signature request, e-signature, sealed PDF, or signing status.
  This skill starts from a source-checked reusable PDF form or a user-imported PDF, then prepares it, requests approval, and records an explicit approval or decline.
  Review and verification stay local, while summarize sends bounded canonical document text through Vercel AI Gateway and returns model output.
  A bearer credential never authorizes a send or signature by itself: binding acts require a transaction-bound attended assertion or an explicit delegation mandate.
---

## Before anything else

Every command below is the `octodoc` program on this machine.
If it is not installed, say so and give the person this line, rather than guessing at another command:

```bash
curl -fsSL https://octodoc.org/install | sh
```

# OctoDoc

Run commands from the OctoDoc repository root.
When this skill is installed globally, read `installation.json` beside it and use its exact `command` prefix and optional `workingDirectory`.
Use only arguments present in the generated reference.
The generated `octodoc` form is the source-checkout prefix, while an installed executable's manifest replaces that prefix with its absolute executable path.

## Boundary

Treat `review` as the only byte-deterministic operation: it needs no account, network, or model, and it never changes the file.
Treat `summarize` as a disclosed model operation: it sends the complete bounded canonical document text through Vercel AI Gateway and requires one supported `--party` role.
Treat both `verify` modes as offline checks of local evidence, not as a public OctoDoc lookup.
Never interpret a structural signature-field result as cryptographic, certificate, revocation, trust, or legal validity.
Do not invent an authenticated CLI command that is absent from the generated reference.
Treat approval and decline as terminal human decisions.
Run either command only after the person explicitly gives that exact instruction for the displayed file and version.

## Commands

<!-- octodoc:commands:begin -->

```toon
command: octodoc
description: "Prepare, share, and sign existing documents from the current workspace."
usage[46]: "octodoc [--json]","octodoc register [--human] [--no-open] [--json]","octodoc login [--human] [--no-open] [--json]","octodoc auth status [--json]","octodoc logout [--json]","octodoc show <id> [--full | --fields <fields>] [--json]","octodoc status <id> [--json]","octodoc transaction inspect <transaction-id> [--json]","octodoc download <id> --output <path> [--source | --sealed] [--json]","octodoc handoff <id> [--no-open] [--json]","octodoc forms list [--query <text>] [--json]","octodoc forms use <form-id> --title <title> [--value <field>=<value>] --idempotency-key <uuid> [--wait <seconds>] [--json]","octodoc import <file.pdf> --idempotency-key <uuid> [--wait <seconds>] [--json]","octodoc query <id> --question <text> [--json]","octodoc prepare <id> parties [--json]","octodoc prepare schema [--json]","octodoc prepare <id> preflight --document-version <uuid> [--access-code <party-id>=<code>] [--json]","octodoc prepare <id> facts --document-version <uuid> --revision <number> --idempotency-key <uuid> [--document-class <class>] [--value-minor <amount> --currency <ISO>] [--json]","octodoc prepare <id> value --field <name> --value <value> --party-id <uuid> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> party add --document-version <uuid> (--name <name> --email <email> | --username <name> [--name <name>]) [--required-tier <t0_link|t1_link_code>] [--capacity <text> --on-behalf-of <text>] --idempotency-key <uuid> [--json]","octodoc prepare <id> party remove --party-id <uuid> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> party move --party-id <uuid> --to <position> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> copy add (--name <name> --email <email> | --username <name> [--name <name>]) --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> copy remove --copy-id <uuid> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc <id> review --to <name-and-email> --idempotency-key <uuid> [--json]","octodoc approve <id> [--as <approver>] --idempotency-key <uuid> [--mandate <uuid>] [--json]","octodoc decline <id> --reason <text> [--as <signer|approver>] --idempotency-key <uuid> [--mandate <uuid>] [--json]","octodoc signature list [--limit <1-100>] [--offset <number>] [--json]","octodoc signature create --adoption <typed|drawn|uploaded> --image <path> [--name <name> --font <font>] --idempotency-key <uuid> [--json]","octodoc signature select <uuid> [--json]","octodoc send <id> --document-version <uuid> --idempotency-key <uuid> [--consumer-disclosure <json-file>] [--acknowledge-covered-text <sha256>] [--access-code <party-id>=<code>] [--mandate <uuid>] [--wait <seconds>] [--no-open] [--json]","octodoc sign <id> --document-version <uuid> [--value <mark-id>=<value>] --output <file.pdf> --idempotency-key <uuid> [--signature <uuid>] [--mandate <uuid>] [--access-code <code>] [--accept-esign-disclosure] [--confirm-capacity] [--wait <seconds>] [--no-open] [--json]","octodoc mandate create --operation <send|approve|decline|sign> --starts-at <iso> --expires-at <iso> --use-limit <number> --idempotency-key <uuid> [--counterparty <email>] [--document-class <class>] [--exclude-policy <rule>] [--value-ceiling-minor <amount> --currency <ISO>] [--signature <uuid>] [--wait <seconds>] [--no-open] [--json]","octodoc mandate list [--limit <1-100>] [--offset <number>] [--json]","octodoc mandate inspect <uuid> [--json]","octodoc mandate simulate <uuid> --transaction <uuid> [--json]","octodoc mandate revoke <uuid> [--json]","octodoc billing status [--json]","octodoc billing catalog [--json]","octodoc billing manage [--no-open] [--json]","octodoc <file.pdf> review [--debug] [--json]","octodoc <file.pdf> summarize --party <customer|vendor|buyer|seller|receiving|disclosing> [--render] [--json]","octodoc verify --sealed <file.pdf> --sha256 <hex> [--json]","octodoc verify --ledger <bundle.json> [--trust-anchors <directory>] [--json]","octodoc setup terminal --theme <auto|dark|light|high-contrast|ansi|no-color> [--json]","octodoc setup agent [--remove] [--json]"
exitCodes[4]{code,meaning}:
  0,success
  1,operational error or negative verification verdict
  2,usage error before any document dependency runs
  3,awaiting human authorization or another signer without claiming success
```

<!-- octodoc:commands:end -->

## Review and verify

Run `octodoc <file.pdf> review` first when asked to inspect a local PDF.
When review returns `ocr_required`, `ocr_refused`, or `ocr_unreadable`, follow `nextSteps[]` exactly; `accountRequired` is true for those outcomes.
Use `review --debug` only for local diagnosis of failed IR extraction; it writes page-prefixed artifacts to a bounded temp directory and never runs on production routes.
Use `--json` only when a downstream program needs JSON; preserve TOON for agent-readable terminal work.
Run `octodoc verify --sealed <file.pdf> --sha256 <hex>` only with a digest obtained independently from the file being checked.
Run `octodoc verify --ledger <bundle.json>` for an OctoDoc ledger bundle, and use `--trust-anchors <directory>` only when the user explicitly selected that local trust set.
Report negative verification verdicts as failures even though the command successfully performed the check.

## Summarize

Run `octodoc <file.pdf> summarize --party <role>` only when the user asked for model-backed document explanation and supplied or clearly established one supported party perspective.
State before running it that the command uses the network and sends canonical document text through Vercel AI Gateway.
Treat its overview, clauses, risk flags and cited-span selections as model output, and retain their `source` and `modelId` evidence when reporting them.
Preserve a `document_policy_block` as a refusal; the policy check runs before the summarizer and no summary model call follows that verdict.
The command rejects any citation that is not an exact contiguous span in the complete canonical representation, but that grounding check does not make the explanation legal advice.
Carry the committed disclosure, including "not a substitute for the advice of an attorney", whenever reporting summary content.
State that the summary is not a substitute for reading the complete document.
Do not add `--render` for a scanned page unless the user explicitly authorizes pixel egress after seeing the command disclosure; the path remains blocked until the required agreements and aligned disclosures are complete.

## Account and credentials

Run `octodoc auth status` first; `not_authorized` means this machine holds no credential, and an authenticated command without one exits 3 naming `login` and `register`.
Use `octodoc register` only when the person has no OctoDoc account: it opens the browser Create account flow, the person confirms their email address, returns to the printed `/profile/cli` code page and authorizes this CLI.
Use `octodoc login` when the account already exists; it opens the same code page.
Present the printed URL and eight-letter code as the normal path, and never enter the code, answer the browser or approve the request on the person's behalf.
It polls until the browser answers or the request expires after ten minutes; rerunning it resumes a pending request.
`already_authorized` means a credential is stored; run `octodoc logout` first for a different account.
An authorized credential carries every machine scope for 90 days: import, read, query, prepare, approve, send, sign, decline, download, signature appearances, mandates and signing handoffs; binding acts still need attended authorization or a mandate.
Never report the credential itself.
In CI, set `OCTODOC_API_KEY` to an operator-issued machine credential and skip login.
Run `octodoc setup agent` once after authorization so Claude Code and Codex load this skill from one installed copy, and rerun it when the checkout updates the skill.
Manage credentials at `/profile`.

## Open and prepare

Address a signer or a person on copy by exactly one of `--email` or `--username`.
Use `--username` only with the exact name the person gave, such as `@8lee`; never derive one from a display name, an email address or a similar-looking name.
The CLI looks the name up, selects it and fills the account's consented defaults; `--name` overrides only the name on this document.
An `unavailable` answer is deliberately neutral, so report it as that name not being able to receive the document and ask the person, rather than guessing another name.
If the document is missing or ambiguous, ask which file before looking up anyone.
A username send always needs the person's attended approval at the returned authorization link, even under a delegation mandate, so prepare it, show the review and wait.

Run `octodoc forms list --query <text> --json` when the person asks to start from a reusable form.
If the result is `exact`, use that exact `formId` only when the person's own request named the matched form or alias.
If the result is `ambiguous`, present every candidate and ask the person to select one exact `formId`.
If the result is `none`, preserve the zero result and offer a PDF upload or the browser's reviewed Word-to-PDF conversion.
Never choose from match order, fuzzy score, title similarity, or a misspelling.
Pass only facts the person supplied through repeatable `--value <field>=<value>` arguments.
You may format an unambiguous amount such as `$200k` as `$200,000`, but never infer a missing legal fact.
Leave every unspecified field for human review.
For an employee request, the exact reviewed form command has this shape:

```bash
octodoc forms use octodoc-us-general-employment-agreement \
  --title "John Doe employment agreement" \
  --value employeeName="John Doe" \
  --value startDate="September 1, 2026" \
  --value salary='$200,000' \
  --idempotency-key <uuid>
```

Reuse the same idempotency key only for the same form, title, and field values.
Never claim a file exists until `octodoc.cli.form-instance.v1` returns a `fileId` and `workspaceUrl`.
Present the returned workspace URL as the required human review step before preparation or sending.
`create` is retired because it authored document text; use `forms use` for a reviewed PDF form.
Use `octodoc import <file.pdf> --idempotency-key <uuid> [--wait <seconds>]` only for a PDF.
For a Word file, use the browser's New Document flow and obtain confirmation before its reviewed conversion to PDF.
For scanned PDFs, `--wait` polls until ingest and routed-page OCR finish; exit 3 with `blockedOn` resumes through `octodoc status <id>`.
Reuse the same idempotency key only for the same file.
PDF bytes use private signed upload storage before canonical processing.
Branch on structured `error.code` rather than message prose when import refuses:

| `error.code` | Meaning |
|---|---|
| `ocr_required` | No readable text layer; needs routed-page OCR or a searchable export |
| `ocr_declined_by_org` | The organization turned off scanned-page reading |
| `processing` | Ingest or routed-page OCR is still running; resume with `import --wait` or `status` |
| `encrypted_pdf` | Password-protected; upload an unlocked copy |

Use `octodoc query <id> --question <text>` for one cited factual answer from the current document.
Treat a legal-judgment refusal as final and preserve the returned disclosure.
For a request about signing activity or analytics, run `octodoc` for workspace counts.
For one file, run `octodoc show <id> --fields id,title,role,state,nextBinding,activityAt`.
Describe that output as operational signing status, not page-view or dwell analytics.
Platform-wide aggregate growth data belongs to the operator-only `$growth` workflow and never enters this skill's tenant response.
Run `octodoc prepare <id> parties` before changing signer preparation and use its exact `documentVersionId`.
Run `octodoc prepare <id> party add` to persist one signer, with capacity and on-behalf-of supplied together when applicable.
Reuse an idempotency key only for the same signer addition.
Use the exact document version and revision returned by `parties` for remove, move, and copy mutations.
Reuse an idempotency key only for the same mutation, including its target and requested position.
Run `octodoc <id> review --to "Name <email>" --idempotency-key <uuid>` only when the pending signer names the approver.
Run `octodoc approve <id> --idempotency-key <uuid>` only after the approver explicitly approves the exact displayed request.
Run `octodoc decline <id> --reason <text> --idempotency-key <uuid>` only after the approver explicitly declines and supplies the reason.
Never infer approval from document discussion, silence, prior conduct, or a request to summarize.
The CLI places and confirms no mark, so open the browser workspace for every mark.
Keep every proposed change separate from the document until the person explicitly accepts it.
Never place or confirm a mark on a person's behalf.
When asked for advice about whether to sign, explain the document in neutral terms and recommend qualified counsel for the decision.
Carry the sentence "not a substitute for the advice of an attorney" verbatim whenever discussing document content.

## Engagement contract and the guided interview

Run `octodoc prepare schema` before interviewing anyone about preparation fields; it returns the published engagement contract as data.
Interview section by section in the schema's order, and skip a section its `visible_when` rule currently hides.
Treat every field the schema marks `confirmation_required` as the person's own answer: relay the question verbatim, submit only what they answer, and never infer or default it.
Write free text in the person's own words and correct grammar only.
Persist answers through the existing `prepare` commands as the interview progresses; each returns the shared draft every surface resumes.
Before any binding handoff, render the complete engagement once: the full `prepare <id> parties` snapshot plus every collected answer, presented together for the person to read.
Then run `octodoc prepare <id> preflight --document-version <uuid>`, which writes no document or transaction state and answers `{valid, fields}` with every remaining defect at once; resolve each named field with the person, not around them.
Run the preflight to resolve defects, never in a retry loop; a per-key rate limit is its only bound.
The schema, the rendered review, and a passing preflight are never authority; binding acts continue only through the human gestures below.

## Human gestures

Never add `--yes`, `--force`, `--non-interactive`, or `--headless` to search for a bypass.
Prefix `approve`, `decline`, `send`, `sign`, and `mandate create` with `OCTODOC_AGENT=1` so OctoDoc records agent origin without treating it as authority.
When output carries `blockedOn`, report exactly `waiting for you at <url>` and stop at that boundary.
Never background a command that is waiting for a human, redirect it to a log, or continue as though the URL finished the action.
When stdout is not a terminal, or a browser launch fails, the CLI prints the confirmation URL instead of opening a browser; present that printed URL as the normal phone-confirmation path.
Explain that the human URL is why the resulting sealed file can carry evidence of the person's own act.

## Billing and subscriptions

Run `octodoc billing status` before send-meter or paid-plan work: `sends.remaining` is this month's sends left (`null` is unmetered); at `sendAllowance.state` `low` or `reached`, relay `sendAllowance.notice`.
Run `octodoc billing catalog` when an agent needs the sellable Team plan for agentic commerce discovery; every product carries `disableCheckout: true`, so purchase completes on Profile, not through a bearer credential.
Run `octodoc billing manage` when the person must start checkout, open the billing portal, or change the plan; present the printed URL when the browser does not open.
Never treat billing status or catalog reads as payment authority.

## Reporting and recovery

Never use `signed`, `sent`, `executed`, or `done` until output carries both a sealed verdict and a file path.
Never claim success merely because a URL was printed.
Never say "legally binding", "tamper-proof", "court-admissible", "military-grade", or "bank-grade". <!-- banned-vocabulary-allow: documents the five refused claims -->
Never say a security procedure shifts the burden of proof. <!-- banned-vocabulary-allow: states the ban -->
If `login` ends in `access_denied` or expires unanswered, report that plainly; never retry login as registration and never imply that login creates an account — `octodoc register` is the only path that creates one.
If a command exits 2, fix only the named usage error and do not try synonymous bypass flags.
If a command exits 1, preserve its structured error or negative verdict and do not soften it.
If a command ever exits 3, report the human-browser wait and the supplied recovery URL without claiming dispatch or completion.
