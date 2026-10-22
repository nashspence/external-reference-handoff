# Contributing

This repository maintains one protocol, not a collection of numbered standards.
Feedback from any participant is useful, including agents working in
`nashspence/*`. Nothing here grants permission to act outside the task or access
already authorized to that participant.

## Bring observations, not ceremony

Open an issue or comment on an existing discussion with the observed problem,
the relevant handoff or a minimal example that can be shared, the current
workaround, and the smallest proposed improvement. Include an actual outcome or
counterexample when available. Remove private code, credentials, and confidential
context before posting publicly. A private origin need not be made public to
explain the general problem.

Use a pull request for a concrete text change, or describe the proposed revision
in an issue when a patch is unnecessary. The README on `main`, not an issue's
status or a comment, supplies the current protocol. Closing a discussion does not
retire a protocol section. No RFC numbering, ratification states, release train,
or per-repository adoption registry is needed.

## Keep the implementation small

`README.md` is the protocol. `templates/` helps participants supply its information;
`examples/` exercises its interpretation. Update affected templates and examples
with a protocol change rather than letting them become competing definitions.
If they conflict, fix them; the README supplies the intended meaning.

Explain substantive changes and their motivation in the issue or pull request.
Git history preserves prior text. Do not create a separate changelog or require
compatibility with superseded formatting. The practical review is whether a new
producer can act on the current text and a consumer can still understand an older
artifact without rewriting its historical record.

Before proposing a change, check that it preserves the distinction between useful
reference material and authorized repository work; distinguishes artifact identity
from mutable guidance; states validation honestly; preserves producer provenance;
and allows rejection without first running or adopting the proposal. Walk through
the [examples](examples/README.md) and update any affected ones. Check relative
links and `git diff --check` as well. These are editing checks, not evidence that
the protocol has been exercised in production.

Do not add tooling, mandatory Git topology, provider-specific instructions, or new
product gates without an observed need. A handoff protocol should reduce the cost
of exchanging substantial evidence, not grow a parallel integration system.

## Keep changes local

A change here does not authorize changes in a consuming repository. Report
relevant divergence and propose a local update through that repository's process.
Do not automatically rewrite its guidance, active handoffs, or historical records.
Keep project-specific exceptions local unless experience shows a reusable case.

Contributions to this repository use its [MIT license](LICENSE). Do not import
third-party text or examples without appropriate rights and attribution. This
repository's license does not grant rights over artifacts exchanged under the
protocol.
