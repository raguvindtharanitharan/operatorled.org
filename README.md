# operatorled.org — the manifesto's home

The canonical, public page for **Operator-Led Software Development**: `index.html`, self-contained
(fonts from Google Fonts; no other external dependency, no build step). It is Phase 0 of
`docs/concept-roadmap.md` — the single, dated, quotable document the movement is.

## What it is built from

`docs/manifesto.md` is the source of truth. The page renders that document for a public reader:

- The **values** and **principles** are the manifesto's own, restated as twelve citable principles,
  each with a permalink anchor (`#p1` … `#p12`) — the quotability gate.
- **Tool-specific passages are generalized to the method they express**, never invented: "Ingee
  must make the operator's next action obvious" becomes a statement about the tooling; the ATAM
  incubation plan (an implementation concern) is omitted. The reference implementation is not named
  in the body at all until it has a public address (decided 6 September 2026); until then Ingee
  appears only where the amendment log's history names it.
- The **amendment log is carried in full and unrewritten**, with the project names it was written
  under — it is the document's verifiable history and the evidence the method was worked, not
  theorized.

When `docs/manifesto.md` is amended, this page is amended in the same change, and the version and
date in the header and footer move.

## Where it should live

Until registration, it lives here. The Phase 0 gate requires the page's git history to be public or
archived so its date is verifiable — so once `operatorled.org` is registered, this folder moves to
its own public repository (the movement is bigger than the product and should not live inside the
product's private repo) and deploys as a static site. Any static host works; no server is needed.

## Deliberately not here

No analytics, no forms, no product pitch, no Ingee branding. The page must read as a methodology,
not a brochure — a reader who never clicks through to the reference implementation loses nothing.
