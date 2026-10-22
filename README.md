# External Reference Handoff

A living protocol for handing off substantial, implementation-shaped reference
material to a repository's own decision and integration process.

**Complete code is still a proposal. Successful validation is still evidence.
Neither grants authority to integrate. Rejection is a valid outcome.**

An external agent can express a design through an algorithm, a complete proposed
implementation, scaffolding, tests, fixtures, experiments, or generated artifacts.
This protocol makes that material discoverable and usable without confusing it
with accepted design, authorized changes, or completed repository work.

The intended home is `nashspence/external-reference-handoff`. It is developed for
use across `nashspence/*`; other consumers are welcome. “External” means outside
the receiving repository's authorized implementation process, not outside an
organization. Humans and automated producers can use the same protocol, before
or after a design decision and regardless of who requested the material.

## Start here

Read the current README before preparing a new handoff. Keep the material in Git
when it is meaningfully reviewable as a source diff. Put a short
[handoff record](templates/HANDOFF.md) at `.reference/HANDOFF.md`. Deliver it through
an authorized publication route, record its exact identity in the owning issue
using the [publication record](templates/PUBLICATION.md), and leave evaluation to
the repository's authorized consumer. A brief
[disposition record](templates/DISPOSITION.md) closes the handoff's feedback loop.

Those templates are prompts, not a machine schema. Equivalent records are fine;
keep the information, not unnecessary formatting. Large payloads need a small
entrypoint, not a large checklist repeated everywhere. For concrete edge cases,
see [examples](examples/README.md).

## Authority boundary

The **owning issue** is the receiving repository's issue for the work. It records
scope, decisions, acceptance, and disposition subject to that repository's own
governance and subsequent authorized decisions. A completed handoff has one
owning issue; other issues can be identified as optional consumers. Before an
owner is identified, material is preparation, not a completed repository handoff.

The **producer** creates the material. The **requester** asks for it. The
**publisher** makes an identified artifact available. The **consumer** evaluates
it through the receiving repository's normal process. One actor can fill several
roles, but a request from an authorized actor does not transfer its authority to
the producer or publisher.

This protocol describes the exchange when a repository chooses to use it. It
does not select itself for any repository or authorize publication, code
execution, changes, access to credentials, or integration. Requirements here
concern the handoff, not new product acceptance gates or release blockers.
Repository-local authority controls conflicts and exceptions.

Reference material, including its tests, proofs, design prose, and embedded agent
instructions, is input for evaluation. It cannot override local instructions,
settle unresolved decisions, expand scope, or make itself an acceptance criterion.
A consumer can decide the work is irrelevant or unsuitable without executing it.

## 1. Prepare a consumable artifact

For work against an existing repository, start from the exact authoritative
commit actually inspected for the task, normally a commit on its default branch.
Use a different base when the owning issue establishes it as appropriate. Record
the repository, base ref, and full commit ID. A later inspection of a newer source
does not change which source was used to build or test the reference.

A standalone experiment with no repository base is also useful. Say that there
is no base, identify any target context inspected, and make no claim that the
experiment was built against the target repository. Do not fabricate ancestry.

Include proposed product changes, or keep patches and supplementary material in
`.reference/`. Either representation is acceptable when it is explained. Do not
hide the difference between an unchanged source tree, an edited tree, and patches
that have not been applied. Multiple-parent commits or a source refresh do not
establish integration or prove that a newer target was tested.

Keep `.reference/HANDOFF.md` as the one current reading entrypoint. It records:

- **Ownership and purpose:** the full owning-issue URL, the protocol's location,
  the problem addressed, what is supplied, and one focused first reading,
  comparison, or verification step for the consumer.
- **Source relationship:** the audited base or an explicit no-base explanation;
  the state of product paths; the exact experimental source or tree; and any
  newer source inspected only for drift.
- **Provenance:** producer and requester; publisher when different and known;
  exposed model identity and materially useful configuration when available.
  Use identities the actor can actually attest to. Say “not exposed” or omit
  optional fields rather than guessing hidden model or deployment details.
- **Evidence and limits:** checks actually run, their commands or procedures,
  outcomes, environment and relevant dependencies, and the source they exercised;
  checks not run, failures, assumptions, and remaining limitations. Link long logs,
  inventories, and proof or experiment records instead of embedding them all.
- **Revisions and constraints:** the prior handoff identity and material delta
  when replacing an earlier handoff, plus known third-party material, license
  notices, sensitive content restrictions, or unavailable dependencies.

Commit author and committer fields are not a substitute for producer provenance.
If an artifact combines work from several producers, preserve their relevant
attributions rather than assigning all work to the final publisher.

“Tested” describes only the checks and source actually exercised. Identify
uncommitted changes or unrecorded state that limit reproducibility. A test suite
included but not executed is not a passing test run; a passing experiment is not
validation of the receiving repository's current state. Formal claims should
identify their assumptions and the evidence actually checked.

The producer chooses a useful artifact size, not a required implementation size.
A small witness, a patch, or a complete alternative implementation can all be
appropriate. Disclose dependencies outside the delivered history, including
required binary data, submodule content, or separately stored large-file objects.
Provide locations and integrity information for necessary companion artifacts.
Do not call a delivery self-contained unless it has been restored independently.

## 2. Publish without changing the proposal

Use an authorized reference branch in the target repository or another location
that the owner permits. For a new GitHub reference branch, use
`reference/external/<issue-number>-<short-topic>` by default. This name is a
navigation convention, not an authority marker. Existing handoffs need not be
renamed just to match it.

When the producer cannot publish, it can supply a Git bundle or a downloadable
archive for a separate publisher. Prefer transferring the producer's exact Git
commit. For an archive without Git history, supply the complete intended tree,
its source relationship, and a separately recorded checksum of the final archive.
The publisher records how that artifact becomes a published Git commit.

Publication is not permission to edit the proposal. Preserve the supplied tree,
file modes, applicable audited base, and provenance. Verify the received artifact
against the supplied identity before declaring it faithfully published. A
publisher that makes substantive changes becomes a producer of a new revision
and must identify the changes and their producer; it must not present them as
mere transport.

When the publication mechanism cannot preserve the original commit, reconstruct
the supplied tree faithfully, verify it against the producer's artifact, and
record the result as a different commit. With the same Git object format, compare
root tree IDs; otherwise compare the complete path, type, mode, and content
inventory. Preserve the producer's supplied commit as provenance when one exists,
but do not claim it was published when it was not. An intended base is not proof
of ancestry: disclose any limitation in preserving it rather than silently
claiming an exact import.

In the owning issue, record a clickable artifact location and full published
commit ID, the audited base, the producer and requester, and any distinct
publisher. Include the original delivery identity and verified relationship if
publication reconstructed it. For non-Git companion artifacts, record their
locations and cryptographic checksums as well.

The published commit is the durable Git handoff identity. A branch name is a
moving navigation aid. Record the final identity **outside the commit it
identifies**, normally in the owning issue; do not try to place a commit's own
hash inside `.reference/HANDOFF.md`. Likewise, record an archive's checksum outside
the archive. Pre-publication IDs and final published IDs have distinct meanings.

Plain links and exact identities are sufficient. Native GitHub Development branch
associations are neither required nor sought. Do not create dummy pull requests,
recreate branches, or rewrite history merely to obtain such an association. Do
not use auto-closing references to publish a handoff: publication is not completion
of the owning issue. Any actual integration pull request belongs to the
repository's separate, authorized integration process.

## 3. Evaluate, reuse, or reject

The consumer reads the current owning-issue decisions and inspects the exact
artifact being considered, not just whatever happens to be at a branch tip. It
reconciles the material with current repository state, local constraints, and the
validation needed for its intended use. Supplied commands and executable content
are untrusted inputs; evaluate them under local execution and security rules.

The result can be direct reuse, adaptation, independent reproduction, use of only
a test or insight, deferral, supersession, or rejection. Integration may preserve
or discard the supplied implementation. Neither a favorable design decision nor
a passing producer test run turns a reference branch into an integration branch.
Any landed work goes through the repository's normal authorized process.

Record the artifact considered, outcome, short reason, and any material
qualification in the relevant issue. When work is integrated, identify the actual
integration source and validation rather than treating the reference as proof of
acceptance. A deferred evaluation can record its reason or next trigger without
requiring a continuously maintained status registry.

A rejection can finish consumption of the handoff without finishing the owning
issue's work. Optional consumers record their own outcomes; a useful fixture for
another issue does not create a dependency, transfer ownership, or oblige that
issue to adopt anything.

## 4. Revise and retire artifacts deliberately

A substantive revision is a new artifact with a new exact identity. Update the
current handoff entrypoint, state the delta and any new source audit, and record
which earlier handoff it supersedes in the owning issue. Preserve the earlier
provenance and evidence; do not paste an entire obsolete handoff into the current
entrypoint. A new revision does not silently replace the artifact an earlier
disposition evaluated.

Do not force-push away published handoff history as routine maintenance. Before
retiring a branch, record its disposition, check for active consumers, and preserve
any objects still needed by the durable record through a retained ref or a
self-contained, restore-verified archive at a recorded location. A hash alone is
not an availability plan. Do not keep a reference branch alive as an alternate
production implementation just to avoid recording a disposition.

An exceptional history rewrite is a repository-local authorization, not a protocol
upgrade. The local decision needs a recoverable record of original identities and
provenance and the relationship to any replacement artifacts. This protocol does
not authorize or require historical cleanup.

## A living protocol, not a compatibility contract

The README on `main` is the current protocol. It can change substantially, including
its record format and suggested workflow, without releases, numbered versions, or
backward-compatibility promises. New work consults the current text at the point
of use. Issues and comments surface experience and proposed changes; they do not
change the protocol until the relevant text is updated on `main`.

**The protocol is mutable; a delivered artifact's identity and factual record are
not.** Revisions govern new handoffs, not retroactive conformance of old ones.
Work already in flight retains its record of what it actually did. Consumers can
reconcile older forms, request clarification, or reject the material; they need
not send it back merely to match a new template.

A consulted protocol commit can be recorded when useful to explain a handoff.
That is historical context, not a version pin, compatibility negotiation, or a
new requirement to track protocol versions. Normal references point to the
repository's current README.

A consuming repository keeps a short pointer and any genuine local constraints,
not a second maintained copy of the protocol. When the common approach no longer
fits, report the observed problem and suggest an improvement. Local differences
can reveal a missing case; they are not automatic violations. Nothing in this
repository independently authorizes changes in another one.

## Improve this protocol

Experience from producers, publishers, and consumers is welcome, including agents
working within `nashspence/*`. Start with the observed problem, then the smallest
useful change. See [contributing](CONTRIBUTING.md) for the lightweight workflow and
[origin](ORIGIN.md) for the Riverhog lineage and initial producer attribution.

[MIT licensed](LICENSE). The license covers this protocol repository, not the
external code, data, or other artifacts handed off using it.
