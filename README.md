# Tanishq demo — a published copy

The **built** Karnival application for Tanishq: the receipt wallet, the document wallet, the
consent and document-access controls, and the counter screen.

This repository holds the compiled site only — no source. The source is private, in
`prasenjeet-sys/clients-tanishq`, because GitHub Pages serves a public site and the source carries
unreleased client work.

| Open | What you get |
|---|---|
| [`/`](https://prasenjeet-sys.github.io/tanishq-demo/) | The customer's app — three bills, the document wallet, the profile |
| [`/?reset`](https://prasenjeet-sys.github.io/tanishq-demo/?reset) | A first purchase: no account, empty wallet, one bill that cannot be paid until a PAN is given |
| [`/?returning`](https://prasenjeet-sys.github.io/tanishq-demo/?returning) | A customer who has bought before: PAN in the wallet, bills, certificates |
| [`/store/`](https://prasenjeet-sys.github.io/tanishq-demo/store/) | The counter — send the link, take the code, request access |
| [`/manager/`](https://prasenjeet-sys.github.io/tanishq-demo/manager/) | The central team's screen |

Open `/?reset` and `/store/` in two tabs of one browser to watch a request cross from the counter
to the phone.

## What does not work here, and why

GitHub Pages serves static files and cannot run a server, so the two API routes the application
calls are absent:

- **Reading the card.** `/api/read-document` reads the number and name off a photographed PAN. The
  application is written to expect it to fail — a reading that finds nothing returns nothing and the
  customer types the number instead — so the flow is unaffected. The number field simply does not
  fill itself, and a document is treated as unverified rather than checked.
- **The admin notice.** `/api/document-uploaded` emails the admin on upload. No notice is sent.

Everything else behaves as it does when the application is served with its API.

## Built from

`prasenjeet-sys/clients-tanishq` at the commit this copy was published from, built with
`--base=/tanishq-demo/` because a Pages project site is served under its repository name rather
than at a domain root.

Content provenance — what is sourced from the Tanishq documents and what is demo content — is in
the source repository's README, and in the comments of `src/data/receipts.ts` and `src/brand.ts`.
