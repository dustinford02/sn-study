# Interview Prep: ServiceNow SPM Application Developer

A single-page, offline-capable preparation console for a ServiceNow
Strategic Portfolio Management (SPM) Application Developer interview.

The app states its own purpose in its metadata, and that statement is the
honest one: it prepares interview answers from documented evidence, and it
makes no judgment about the candidate.

## Scope of this work, stated plainly

This is personal interview preparation, not a product and not client work.
It is published openly because the underlying material is public
information and the work is mine, not because it is intended as a reusable
tool for anyone else.

The content was originally written against one specific job posting. That
posting is closed. Material that should not sit on the open web has been
removed or generalized: company and customer names, program and contract
identifiers, contract value and internal cost positions, clearance level
and adjudication details, the requisition, and the interview date. What
remains is the question bank, the evidence tiers, the quiz, the study
library, and a portfolio-level account of the work.

The ServiceNow University transcript, the screening deconstructions, and
the reference glossaries are reproduced from supplied sources. The resume
summary and the project-manager narrative are a public generalization of
supplied material, not a verbatim copy.

## What it contains

Eleven sections, reachable from the top navigation:

| Section | Purpose |
|---|---|
| Home | Landing view and entry point |
| Questions | Anticipated interview questions |
| Evidence | Documented support behind each answer |
| Defense | Anticipated challenges and responses |
| Path | Preparation sequence |
| Quiz | Self-testing |
| Learn | Study material |
| Background | Role and platform context |
| Reference | Lookup material |
| Screening | Deconstruction of each screening question |
| Review | Consolidated pass |

## How it is built

No build step and no dependencies. The whole application is one
`index.html` file of roughly 470 KB, served as a static file alongside a
progressive web app shell:

```
.
├── index.html           the entire application
├── manifest.json        PWA manifest
├── service-worker.js    offline caching
├── robots.txt           disallows all crawlers
├── icon-192.png
├── icon-512.png
├── icon-maskable-512.png
├── tools/
│   └── doc_drift.py     checks this README against the repository
└── .github/
    └── workflows/
        └── doc-drift.yml
```

The manifest uses the same name and the same `#F4FAFD` background as the
page. `service-worker.js` caches that shell network-first: a visit with a
network connection loads the current files, and a later offline visit can
still open them. The worker does not change how the study console behaves
while online.

`robots.txt` disallows every crawler. That is deliberate: the app is meant
to be reachable by me from any device, not to be indexed by search
engines. Note that this affects the served app only. It has no bearing on
the visibility of this repository itself.

## Checks

`doc_drift.py` runs on push and weekly. It verifies that every file drawn
in the tree above exists, that every relative link resolves, and that the
figures in the repository description agree with the figures here. It
fails the build on a broken tree entry or link, and warns rather than
fails on a numeric disagreement, because a README can legitimately contain
a historical figure alongside a current one.

It does not count the application's sections. It compares this file
against the repository description, not against `index.html`, so it will
not catch a case where both statements are updated and the app is not.

## Running it

Any static file server works:

```
python3 -m http.server 8080
# open http://localhost:8080/
```

The service worker requires a secure context, and localhost qualifies.

## Related

[`spm-screening-guide`](https://github.com/dustinford02/spm-screening-guide)
covered adjacent ground in a smaller, earlier form: question
deconstructions, vocabulary pairs, and a card drill. It was archived and
made read-only in August 2026, and this repository is its successor.

Its fourteen question deconstructions, giving for each screening question
the literal reading, what it tests, the trap wording, the nuance, and what
a strong answer contains, were ported verbatim into the Screening section
here before the archive. This is now the only editable copy, so the two
cannot drift apart.

Its five vocabulary pairs and fifty-card drill were not ported. They exist
only in the archive, which stays public, readable and forkable. Nothing was
deleted.

## Honest limitations

- Single-file architecture. Everything lives in `index.html`, which makes
  the file large and diffs coarse.
- The content was authored for one posting and generalized afterwards by
  removal. It was not rewritten from a general brief, and it carries the
  emphasis of the role it was written for.
- No unit tests. The only automated check is the documentation drift
  workflow described above, which validates claims about the repository
  rather than the behaviour of the application.
- Content reflects what was known at the time of writing and is not
  maintained against changes in the ServiceNow platform.

## License

MIT. See [LICENSE](LICENSE).
