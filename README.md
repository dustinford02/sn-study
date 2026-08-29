# Interview Prep: ServiceNow SPM Application Developer

A single-page, offline-capable preparation console built for a ServiceNow
Strategic Portfolio Management (SPM) Application Developer interview at
Data Systems Analysts, Inc.

The app states its own purpose in its metadata, and that statement is the
honest one: it prepares interview answers from documented evidence, and it
makes no judgment about the candidate.

## Scope of this work, stated plainly

This is personal interview preparation, not a product and not client work.
It was built for one role at one company. It is published openly because
the underlying material is public information and the work is mine, not
because it is intended as a reusable tool for anyone else.

Nothing here should be read as a claim about the outcome of that
application, or as a representation of Data Systems Analysts, Inc.

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
| Background | Role and organisation context |
| Reference | Lookup material |
| DSA Programs | Company program context |
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
└── icon-maskable-512.png
```

`robots.txt` disallows every crawler. That is deliberate: the app is meant
to be reachable by me from any device, not to be indexed by search
engines. Note that this affects the served app only. It has no bearing on
the visibility of this repository itself.

## Running it

Any static file server works:

```
python3 -m http.server 8080
# open http://localhost:8080/
```

The service worker requires a secure context, and localhost qualifies.

## Related

[`spm-screening-guide`](https://github.com/dustinford02/spm-screening-guide)
covers the same subject in a smaller, earlier form: question
deconstructions, vocabulary pairs, and a flashcard drill. This repository
is the fuller and more recent treatment. The two overlap by design and
have not been merged.

## Honest limitations

- Built for one role at one company. The content does not generalise.
- Single-file architecture. Everything lives in `index.html`, which makes
  the file large and diffs coarse.
- No tests and no validation tooling.
- Content reflects what was known at the time of writing and is not
  maintained against changes at the company or in the ServiceNow platform.

## License

MIT. See [LICENSE](LICENSE).
