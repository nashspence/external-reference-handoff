# Interpretation examples

These are hypothetical cases for reading and reviewing the protocol, not reports
of validation or new requirements. The [README](../README.md) is the definition.

## Complete, tested design proposal

A producer supplies a whole candidate scheduler and a passing test suite to show
that a proposed design is workable. Its handoff identifies the experimental
source, environment, checks, and untested assumptions. The code and tests remain
evidence: neither the scheduler's behavior nor the test expectations become the
repository's contract by being included. The consumer can reuse the candidate,
reimplement its idea, or decide the design is inappropriate.

## Rejection without execution

The owning issue has already ruled out an architectural dependency required by a
reference implementation. The consumer records the exact handoff considered and
rejects it for that reason without executing it. That is a valid disposition;
there is no requirement to run producer tests before rejection. The owning issue
can remain open for a different implementation.

## New source was inspected, not tested

An experiment was built and tested on one exact repository commit. Later, the
producer reads a newer commit and notes that a relevant interface changed. The
handoff names both and explains the difference. Updating the source audit or
adding a merge parent does not turn the earlier test results into validation of
the newer code. The consumer chooses what reconciliation and checks are needed.

## Publication preserves the tree, not the commit

A producer supplies an exact commit and a complete artifact, but the authorized
publisher's interface can only reconstruct the tree. The publisher verifies
paths, contents, modes, and source relationship, preserves the original producer
record, and records the newly published commit as the handoff identity. The
original commit remains provenance, not a falsely claimed published identity.
Inserting the final hash into the committed handoff would change the artifact;
the publisher instead records it in the owning issue.

## The protocol changes during a handoff

A producer reads the current protocol and starts a substantial experiment. Before
publication, the protocol's recommended organization changes. The completed work
still has its original provenance and source record. The consumer can read it,
ask a focused question, or reject it; a template migration is not a prerequisite
to evaluation. A genuinely new handoff consults the current protocol rather than
copying stale instructions. No compatibility negotiation is required.

## Only a witness is reused

A large proposal includes a small fixture that demonstrates an unrelated bug.
A second issue uses only that fixture and records its own decision and validation.
That use neither endorses the large proposal nor makes the first issue a dependency.
The original owner can reject the proposed implementation independently.

## A reference branch is retired

The owner records that a handoff has been superseded and checks that no active
consumer depends on its branch. If the historical commit is still needed, the
owner retains a ref or records a self-contained, restore-verified archive before
deleting the branch. The branch can disappear without erasing the evidence or
keeping a stale alternative implementation active. An exceptional authorized
history rewrite needs its own recoverable source-to-replacement record.
