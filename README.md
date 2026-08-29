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
posting is closed, and the employer-specific material has since been
removed: the company program section, the customer context, the posting
narrative, the requisition number, and the interview date. What remains is
the part that was never company-specific, namely the question bank, the
evidence, the quiz, the study library, and the candidate's own background.

Where a passage is marked verbatim, it is reproduced from a supplied
source and the comment naming that source has been left in place, even
where the filename mentions the original employer. Rewriting a provenance
note to hide where content came from would defeat the purpose of marking
it verbatim.

## What it contains

Ten sections, reachable from the top navigation:

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
| Review | Consolidated pass |

## How it is built

No build step and no dependencies. The whole application is one
`index.html` file of roughly 455 KB, served as a static file alongside a
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
covers adjacent ground in a smaller, earlier form: question
deconstructions, vocabulary pairs, and a card drill.

The two were assumed to overlap. They do not. A phrase-level comparison
found no shared text between them, and the earlier repository holds a
structure this one lacks: for each screening question, the trap wording,
the nuance, what the question actually tests, and a literal definition.
The two have not been merged.

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
