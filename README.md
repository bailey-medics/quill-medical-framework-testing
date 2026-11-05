# Quill Medical framework testing

This repository holds the frameworks Quill Medical's tests read. A
framework is one published document written as a set of competencies.
Somebody records their progress against it in their clinician passport
in Quill.

**Nothing here reaches App production.** This repository is not on the
list of framework repositories the live app reads, and its pipeline is
set never to start the framework sync.

## What is here

- `frameworks/` holds one file per framework. The four fixtures,
  `clinical`, `ghnft_radiotherapy_record`, `ruh_sact_passport` and
  `uk_sact_board_2023`, are test copies and need not match their
  publishers' frameworks. `quill_test` is a small framework made only for
  testing, with more than one version.

Quill keeps a copy of these files in `shared/framework-fixtures/`, made
by `just framework-fixtures-refresh`, so its unit tests run without the
network. Its integration test reads this repository itself.

## How a change is made

1. Make the change on a branch named `feature/...`, and raise the
   framework's `version` by exactly one.
2. Open a pull request. The pipeline checks the file with Quill's own
   loader, and lists every competency whose wording changed.
3. Merge it. Nothing more happens: the pipeline does not start the sync.

A version never goes down, and a competency id is never removed.

## Licence

The same licence as Quill Medical, the GNU Affero General Public License
version 3. See `LICENSE`.
