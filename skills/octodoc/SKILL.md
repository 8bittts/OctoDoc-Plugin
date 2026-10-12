---
name: octodoc
description: >-
  Find reviewed reusable PDF forms, fill supplied facts, review, summarize and prepare signable documents with OctoDoc, and verify sealed PDFs offline.
  Invoke with /octodoc or $octodoc.
  Use for a contract, NDA, agreement, signature request, e-signature, sealed PDF, or signing status.
  Review and verification stay local, while summarize sends bounded canonical document text through Vercel AI Gateway and returns model output.
  A bearer credential never authorizes a send or signature by itself: binding acts require a transaction-bound attended assertion or an explicit delegation mandate.
---

## Before anything else

Every command below is the `octodoc` program on this machine.
Check `octodoc --help` before using these commands.
If the program is missing or its help omits a command below, say so and give the person this line:

```bash
curl -fsSL https://octodoc.org/install | sh
```

On Windows, use https://octodoc.org/install/windows.
After installing or updating, check `octodoc --help` again before continuing.

# OctoDoc

Use only arguments present in the generated reference.

## Boundary

`review` is byte-deterministic, local, requires no account or model, and never changes the file.
`summarize` sends bounded canonical text through Vercel AI Gateway and requires a supported `--party` role.
Both `verify` modes check local evidence offline.
Never interpret a structural signature-field result as cryptographic, certificate, revocation, trust, or legal validity.
Do not invent an authenticated CLI command that is absent from the generated reference.
Treat approval and decline as terminal human decisions.
Run either command only after the person explicitly gives that exact instruction for the displayed file and version.

## Commands

<!-- octodoc:commands:begin -->

```toon
command: octodoc
description: "Prepare, share, and sign existing documents from the current workspace."
usage[54]: "octodoc [--json]","octodoc ask <text> [--file <uuid>] [--json]","octodoc register [--human] [--no-open] [--json]","octodoc login [--test] [--human] [--no-open] [--json]","octodoc auth status [--json]","octodoc logout [--json]","octodoc show <id> [--full | --fields <fields>] [--json]","octodoc status <id> [--json]","octodoc withdraw <id> --reason <text> [--json]","octodoc transaction inspect <transaction-id> [--json]","octodoc download <id> --output <path> [--source | --sealed] [--json]","octodoc handoff <id> [--no-open] [--json]","octodoc forms list [--query <text>] [--json]","octodoc forms use <form-id> --title <title> [--value <field>=<value>] --idempotency-key <uuid> [--wait <seconds>] [--json]","octodoc import <file> --idempotency-key <uuid> [--wait <seconds>] [--no-open] [--json]","octodoc query <id> --question <text> [--json]","octodoc prepare <id> parties [--json]","octodoc prepare schema [--json]","octodoc prepare <id> preflight --document-version <uuid> [--access-code <party-id>=<code>] [--json]","octodoc prepare <id> facts --document-version <uuid> --revision <number> --idempotency-key <uuid> [--document-class <class>] [--value-minor <amount> --currency <ISO>] [--json]","octodoc prepare <id> value --field <name> --value <value> --party-id <uuid> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> party add --document-version <uuid> (--name <name> --email <email> | --username <name> [--name <name>]) [--required-tier <t0_link|t1_link_code>] [--capacity <text> --on-behalf-of <text>] --idempotency-key <uuid> [--json]","octodoc prepare <id> party remove --party-id <uuid> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> party move --party-id <uuid> --to <position> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> copy add (--name <name> --email <email> | --username <name> [--name <name>]) --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> copy remove --copy-id <uuid> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> mark place --field <name> --party-id <uuid> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> mark find --text <words> [--json]","octodoc prepare <id> mark beside --text <words> --side <right|left|above|below> --kind <signature|initials|date_signed|name|email|phone|address|text|checkbox> --party-id <uuid> [--occurrence <number>] [--optional] --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> mark assign --mark-id <uuid> --party-id <uuid> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc prepare <id> mark remove --mark-id <uuid> --document-version <uuid> --revision <number> --idempotency-key <uuid> [--json]","octodoc <id> review --to <name-and-email> --idempotency-key <uuid> [--json]","octodoc approve <id> [--as <approver>] --idempotency-key <uuid> [--mandate <uuid>] [--json]","octodoc decline <id> --reason <text> [--as <signer|approver>] --idempotency-key <uuid> [--mandate <uuid>] [--json]","octodoc signature list [--limit <1-100>] [--offset <number>] [--json]","octodoc signature create --adoption <typed|drawn|uploaded> --image <path> [--name <name> --font <font>] --idempotency-key <uuid> [--json]","octodoc signature select <uuid> [--json]","octodoc send <id> --document-version <uuid> --idempotency-key <uuid> [--consumer-disclosure <json-file>] [--acknowledge-covered-text <sha256>] [--access-code <party-id>=<code>] [--mandate <uuid>] [--wait <seconds>] [--no-open] [--json]","octodoc sign <id> --document-version <uuid> [--value <mark-id>=<value>] --output <file.pdf> --idempotency-key <uuid> [--signature <uuid>] [--mandate <uuid>] [--access-code <code>] [--accept-esign-disclosure] [--confirm-capacity] [--wait <seconds>] [--no-open] [--json]","octodoc mandate create --operation <send|approve|decline|sign> --starts-at <iso> --expires-at <iso> --use-limit <number> --idempotency-key <uuid> [--counterparty <email>] [--document-class <class>] [--exclude-policy <rule>] [--value-ceiling-minor <amount> --currency <ISO>] [--signature <uuid>] [--wait <seconds>] [--no-open] [--json]","octodoc mandate list [--limit <1-100>] [--offset <number>] [--json]","octodoc mandate inspect <uuid> [--json]","octodoc mandate simulate <uuid> --transaction <uuid> [--json]","octodoc mandate revoke <uuid> [--json]","octodoc billing status [--json]","octodoc billing catalog [--json]","octodoc billing manage [--no-open] [--json]","octodoc payments report [--period <month|quarter|year>] [--json]","octodoc <file.pdf> review [--debug] [--json]","octodoc <file.pdf> summarize --party <customer|vendor|buyer|seller|receiving|disclosing> [--render] [--json]","octodoc verify --sealed <file.pdf> --sha256 <hex> [--json]","octodoc verify --ledger <bundle.json> [--trust-anchors <directory>] [--json]","octodoc setup terminal --theme <auto|dark|light|high-contrast|ansi|no-color> [--json]","octodoc setup agent [--remove] [--json]"
exitCodes[4]{code,meaning}:
  0,success
  1,operational error or negative verification verdict
  2,usage error before any document dependency runs
  3,"waiting for authorization, processing, or another signer; inspect blockedOn"
```

<!-- octodoc:commands:end -->

## Review and verify

Run `octodoc <file.pdf> review` first when asked to inspect a local PDF.
When review returns `ocr_required`, `ocr_refused`, or `ocr_unreadable`, follow `nextSteps[]` exactly; `accountRequired` is true for those outcomes.
Use `review --debug` only to diagnose a failed local extraction; it writes artifacts to a bounded temp directory.
Use `--json` only when a downstream program needs JSON; otherwise keep TOON.
Run `octodoc verify --sealed <file.pdf> --sha256 <hex>` only with a digest obtained independently from the file being checked.
Run `octodoc verify --ledger <bundle.json>` for an OctoDoc ledger bundle; use `--trust-anchors <directory>` only for a trust set the user selected.
Report a negative verification verdict as a failure.

## Summarize

Run `octodoc <file.pdf> summarize --party <role>` only when the user asked for a model-backed explanation and established one supported party perspective.
State before running it that the command uses the network and sends canonical document text through Vercel AI Gateway.
Treat its overview, clauses, risk flags and cited-span selections as model output, and keep their `source` and `modelId` evidence when reporting them.
Preserve a `document_policy_block` as a refusal; the policy check runs before the summarizer and no summary model call follows that verdict.
Every citation is an exact span of the document; that check does not make the explanation legal advice.
Carry the committed disclosure, including "not a substitute for the advice of an attorney", whenever reporting summary content.
State that the summary is not a substitute for reading the complete document.
Do not add `--render` unless the user explicitly authorizes pixel egress after seeing the command disclosure.

## Account and credentials

Run `octodoc auth status` first; `not_authorized` means no stored credential, and authenticated reads exit 1 with recovery steps.
Use `octodoc register` only when the person has no OctoDoc account: it opens account creation in the browser, and the person confirms their email and authorizes this CLI on the printed `/profile/cli` page.
Use `octodoc login` when the account already exists; it opens the same code page.
Present the printed URL and eight-letter code as the normal path, and never enter the code, answer the browser or approve the request on the person's behalf.
It polls until the browser answers or ten minutes pass; rerunning it resumes the request.
`already_authorized` means a credential is stored; run `octodoc logout` first for a different account.
New credentials grant the displayed machine scopes for 90 days; existing credentials retain their original scopes.
Binding acts still need attended authorization or a mandate.
Never report the credential itself.
In CI, set `OCTODOC_API_KEY` to an operator-issued machine credential and skip login.
Manage credentials at `/profile`.

## Natural-language requests

Use `octodoc ask "<request>"` or MCP `request.answer` for ordinary requests, such as "what files do i have?".
Pass a known UUID through `--file`; otherwise ask the person to resolve clarification choices.
Relay recovery `nextSteps` for missing credentials.
Routing is local and deterministic; questions never authorize mutations.

## Open and prepare

Address a signer or a person on copy by exactly one of `--email` or `--username`.
Use `--username` only with the exact name the person gave, such as `@8lee`; never derive one from a display name, an email address or a similar-looking name.
The CLI looks the name up, selects it and fills the account's consented defaults; `--name` overrides only the name on this document.
Report an `unavailable` answer as that name being unable to receive the document, and ask the person rather than guessing another name.
If the document is missing or ambiguous, ask which file before looking up anyone.
A username send always needs the person's attended approval at the returned link, even under a mandate; prepare it, show the review and wait.

Run `octodoc forms list --query <text> --json` when the person asks to start from a reusable form.
If the result is `exact`, use that exact `formId` only when the person's own request named the matched form or alias.
If the result is `ambiguous`, present every candidate and ask the person to select one exact `formId`.
If the result is `none`, preserve the zero result and offer a PDF or Word import.
Never choose from match order, fuzzy score, title similarity, or a misspelling.
Pass only facts the person supplied through repeatable `--value <field>=<value>` arguments.
You may format an unambiguous amount such as `$200k` as `$200,000`, but never infer a missing legal fact.
Leave every unspecified field for human review.
For employment, use `octodoc forms use octodoc-us-general-employment-agreement` with the title, supplied field values, and idempotency key.
Reuse the same idempotency key only for the same form, title, and field values.
Never claim a file exists until `octodoc.cli.form-instance.v1` returns a `fileId` and `workspaceUrl`.
Present the returned workspace URL as the required human review step before preparation or sending.
`create` is retired because it authored document text; use `forms use` for a reviewed PDF form.
Use `octodoc import <file> --idempotency-key <uuid> [--wait <seconds>]` for a PDF or a Word file.
A Word file exits 3 at a review URL where the person checks every converted page and chooses Use this PDF; rerun with the same key and `--wait` for the `fileId`.
For scanned PDFs, `--wait` polls until ingest and routed-page OCR finish; exit 3 with `blockedOn` resumes through `octodoc status <id>`.
Reuse the same idempotency key only for the same file.
Branch on structured `error.code` rather than message prose when import refuses:

| `error.code` | Meaning |
|---|---|
| `ocr_required` | No readable text layer; needs routed-page OCR or a searchable export |
| `ocr_declined_by_org` | The organization turned off scanned-page reading |
| `processing` | Ingest or routed-page OCR is still running; resume with `import --wait` or `status` |
| `encrypted_pdf` | Password-protected; upload an unlocked copy |

Use `octodoc query <id> --question <text>` for one cited factual answer from the current document.
Treat a legal-judgment refusal as final and preserve the returned disclosure.
For signing activity, run `octodoc` for workspace counts or `octodoc show <id> --fields id,title,role,state,nextBinding,activityAt` for one file.
These are signing status, not reading analytics; platform growth data belongs only to the operator's `$growth` workflow.
Run `octodoc prepare <id> parties` before changing preparation and use its exact `documentVersionId`.
Use `prepare party add` for one signer; supply capacity and on-behalf-of together.
Use the document version and revision `parties` returns for every other mutation.
Reuse an idempotency key only for the same mutation, target and position.
Use `review --to` only when the pending signer names the approver.
Use `approve` only after the approver explicitly approves the displayed request.
Use `decline` only after the approver declines and gives the reason.
Use `withdraw` only when the person names the file and gives the reason.
Never infer approval from document discussion, silence, prior conduct, or a request to summarize.
Run `mark place` or `value` only on a field the person named, from `declaredFields` in `parties`, which also gives `mark assign` and `mark remove` an id.
With no declared field, run `mark find` on words the person named, then `mark beside` at the occurrence they mean.
The CLI never confirms a mark; the person confirms every change in the browser workspace before any send.
Keep every proposed change separate from the document until the person explicitly accepts it.
When asked whether to sign, explain the document in neutral terms and recommend qualified counsel for the decision.
Carry the sentence "not a substitute for the advice of an attorney" verbatim whenever discussing document content.

## Engagement contract and the guided interview

Run `octodoc prepare schema` before interviewing anyone about preparation; it returns the engagement contract as data.
Interview section by section in the schema's order, and skip a section its `visible_when` rule hides.
Treat every field the schema marks `confirmation_required` as the person's own answer: relay the question verbatim, submit only what they answer, and never infer or default it.
Write free text in the person's own words and correct grammar only.
Persist answers through `prepare` commands as the interview goes; each returns the shared draft every surface resumes.
Before any binding handoff, show the person the full `prepare <id> parties` snapshot and every collected answer together, once.
Then run `octodoc prepare <id> preflight --document-version <uuid>`; it writes nothing and lists every remaining defect in `fields`, which you resolve with the person, not around them.
Run the preflight to resolve defects, never in a retry loop.
The schema, the rendered review, and a passing preflight are never authority; binding acts continue only through the human gestures below.

## Human gestures

Never add `--yes`, `--force`, `--non-interactive`, or `--headless` to search for a bypass.
Prefix `approve`, `decline`, `send`, `sign`, and `mandate create` with `OCTODOC_AGENT=1` so OctoDoc records agent origin without treating it as authority.
When output carries `blockedOn`, report exactly `waiting for you at <url>` and stop at that boundary.
Never background a command waiting for a human, redirect it to a log, or continue as though the URL finished the action.
When no browser opens, the CLI prints the confirmation URL; present it as the normal phone-confirmation path.
Explain that the human URL is why the sealed file can carry evidence of the person's own act.

## Billing and payments

Run `octodoc billing status` before send-meter or paid-plan work: `sends.remaining` is this month's sends left (`null` is unmetered); at `sendAllowance.state` `low` or `reached`, relay `sendAllowance.notice`.
Run `octodoc billing catalog` for the sellable Team plan; every product carries `disableCheckout: true`, so purchase completes on Profile.
Run `octodoc billing manage` when the person must check out, open the billing portal or change plan; present the printed URL if no browser opens.
Run `octodoc payments report [--period quarter]` for requested, collected, refunded and net payment activity; it needs `payments:read`, so an older credential logs in again.
Never treat billing or payment reads as payment authority.

## Reporting and recovery

Report `sent` only from a send receipt and `signed` only from a signature receipt.
Claim a sealed file or local copy only from its sealed verdict or download receipt.
Never claim success because a URL was printed.
Never say "legally binding", "tamper-proof", "court-admissible", "military-grade", or "bank-grade". <!-- banned-vocabulary-allow: documents the five refused claims -->
Never say a security procedure shifts the burden of proof. <!-- banned-vocabulary-allow: states the ban -->
If `login` ends in `access_denied` or expires unanswered, report that plainly; never retry it as registration — only `octodoc register` creates an account.
If a command exits 2, fix only the named usage error and do not try synonymous bypass flags.
If a command exits 1, preserve its structured error or negative verdict and do not soften it.
On exit 3, report `blockedOn` and its recovery URL or command; distinguish authorization, processing, and another signer.
