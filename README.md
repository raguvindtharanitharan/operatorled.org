# Manifesto for Operator-Led Software Development

This repository is the public home of **[operatorled.org](https://operatorled.org)**: the manifesto
that defines Operator-Led Software Development and coins the term.

> Operator-Led Software Development is a way of building software in which a human operator sets
> intent, grants bounded authority to AI agents, judges the evidence, and accepts the outcome. AI
> agents may do the work, but the operator remains accountable for every change that is accepted into
> the codebase. Nothing closes without the operator's verdict.

The manifesto is one page, `index.html`, with `robots.txt`, `sitemap.xml`, and `404.html` supporting
crawling and missing-page handling. No build step, no framework, no forms. Umami Cloud measures
visits through the site's dedicated account. Fonts load
from Google Fonts; everything else is in the file. Open it in a browser and you have the site.

Deploy all root files together. On Cloudflare Pages, a top-level `404.html` enables missing-page
handling instead of the default single-page-app fallback. If another host or a Worker serves the
files, configure its missing-page handler to serve `404.html` with HTTP 404; do not rewrite missing
paths to `index.html` with HTTP 200. See the
[Cloudflare Pages routing documentation](https://developers.cloudflare.com/pages/configuration/serving-pages/).

After deployment, verify `/robots.txt` returns HTTP 200 as text, `/sitemap.xml` returns HTTP 200 as
XML with `https://operatorled.org/` as its only URL, and both `/missing-page-check` and
`/missing/nested-page-check` return HTTP 404 with the custom page and a working home link.
The sitemap intentionally excludes the error page and does not invent a modification date.

`manifesto.md` is the same text in Markdown, for reading here, quoting, forking, and translating. The
page is canonical; when the text changes, both files change in the same commit. It is also served at
[operatorled.org/manifesto.md](https://operatorled.org/manifesto.md).

## Deploying

The site is hosted on Cloudflare Pages (project `operatorled-org`), connected to this repository.
Every push to `main` deploys automatically: there is no build command, the root of the repository is
the site, and the change is live within a minute or two. Nothing else has to be run or clicked.

To redeploy: commit, push to `main`, wait, then run the verification above. If a deployment fails or
a bad version goes live, open the Cloudflare dashboard, Workers & Pages, `operatorled-org`, and use
"Retry deployment" or "Rollback" on the deployment list. The domain `operatorled.org` and `www` are
attached to the project as custom domains; the `operatorled-org.pages.dev` alias serves the same
files.

## What is in the document

- The definition, and why the method exists: what changed in how software is built, and what broke.
- Nine values, each stated as a preference between two useful things.
- Twelve principles, each with its own permalink (`#p1` … `#p12`) so it can be quoted directly.
- The loop: seven states work moves through, two of which belong to the operator alone.
- The operating model, the structure of work, the anatomy of a proposal, and the practices the method
  deliberately rejects.
- A short vocabulary, and the final test: the questions an operator should be able to answer at any
  moment.
- The amendment log: every change to the document, with the observed problem that forced it, carried
  in full and unrewritten. The log is the document's history and its evidence.

## How this document changes

The manifesto is a governing document, not scripture. The same rule that governs the method governs
the text: **anyone can propose a change, the author decides, and the log records what happened.**

To propose an amendment, open an issue or a pull request here. A proposal is easiest to decide when
it carries the four things every log entry carries:

1. the observed problem that prompted it;
2. which principle or practice changes;
3. why the replacement is expected to work better;
4. what it would say instead.

Accepted changes appear as dated entries in the amendment log, on the page and in `manifesto.md`, and
the version and date in the header and footer move with them. Rejected proposals stay visible in the issue history.

## Provenance

Written by Raguvind Tharanitharan, first on 19 August 2026, while running two real projects with AI
agents doing most of the implementation. The commit history of this repository is the verifiable
record of when each part of the text existed. The working notes and the reference implementation the
method was developed against are not public yet; this page is the canonical text and does not depend
on them.

## License

The text of the manifesto is licensed under
[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).
Copy it, quote it, translate it, build on it, with attribution to the author and to operatorled.org.
See `LICENSE`.
