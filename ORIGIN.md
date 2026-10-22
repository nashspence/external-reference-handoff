# Origin

This protocol was developed from the problem and operating experience recorded in
[Riverhog #903: non-authoritative external reference branches](https://github.com/nashspence/riverhog/issues/903)
and a conversation with `nashspence` about giving the mechanism an independent
home. The issue body, last updated on 2026-10-14 when inspected, and its two
comments were consulted for this initial contribution on 2026-10-21.

The source distinguishes reference material from repository authority, retains
producer provenance and exact handoff identities, and leaves reconciliation to
the repository's own integration process. This repository reformulates that
mechanism as a standalone, living protocol; it is not a verbatim issue export.

Two source comments also informed the boundary: a
[correction of an unauthorized local documentation change](https://github.com/nashspence/riverhog/issues/903#issuecomment-5789652477)
and a
[scoped history-rebaseline exception](https://github.com/nashspence/riverhog/issues/903#issuecomment-5969032963).
Their repository-specific decisions remain local. This repository does not
reopen them, extend them, or claim that their work has been verified here.

Publication of this repository does not itself supersede Riverhog #903 or change
any consumer. A separately authorized local update can replace active protocol
references with a pointer here, while retaining issue-local decisions, exceptions,
and historical provenance. Existing artifacts do not need retroactive rewriting.

## Initial contribution

| Field | Initial contribution |
| --- | --- |
| Producer | OpenAI ChatGPT |
| Exposed model identity | GPT-6 Astra Pro |
| Requester | `nashspence`, in the conversation commissioning this repository |
| Configuration / effort | Not separately exposed |
| Delivery | Local Git repository and downloadable archive; no GitHub publication or consuming-repository change |

The initial text, organization, naming, and MIT license selection are the
producer's recommended contribution, not a claim that the requester has already
reviewed or adopted them. Git author and committer metadata identify this local
packaging operation, not maintainer approval. Its `.invalid` email is deliberately
non-contact metadata, not an OpenAI support address or a verified signing identity.

The initial protocol has not been operationally validated as a standalone project.
Mechanical delivery checks are recorded alongside the archive, outside the
maintained protocol. Future contributions should preserve their own relevant
provenance without treating this initial delivery note as an ongoing status page.
