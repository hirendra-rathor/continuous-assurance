---
name: ca-design-proposal
description: Prepare or revise a design proposal for a requested software or workflow change by comparing the current system, proposed design, and verification needs. Use when a developer requests a design proposal or a plan for a change. Excludes implementation-only requests and reviews of existing pull requests.
---

# Design Proposal

Prepare a proposal the developer can assess and revise before implementation.
Start from their request, a supplied issue, or the current discussion. A direct
request for implementation alone does not require a proposal.

Investigate the repository read-only. Present and revise the proposal in the
current chat. Write a separate proposal document when the developer requests one.

## Establish the change

Establish the requested outcome, scope, constraints, and acceptance criteria
from the supplied request and discussion. When an issue supplies the work
contract, read it in full. Read applicable repository instructions, governing
design and contracts, and implementation. Follow the [source evidence guide](references/using-source-evidence.md) to trace
one relevant case through its callers, decisions, state, and tests. Cover the
affected repositories and identify the revision or local changes when the
comparison depends on them.

Establish the existing implementation or operating arrangement used as the
comparison baseline. Distinguish observed behavior, governing requirements,
and proposed behavior. An approved requirement or delivered supporting tool
does not establish that affected components or workflows already behave as
proposed.
Preserve relevant uncertainties and unresolved decisions, including previous
behavior that cannot be established. Ask for missing information when it changes
a material decision; otherwise state the assumption needed to make the proposal
reviewable.

Read the [system language guide](references/software-system-language.md) to
establish the system boundary and its consumers, including when the system is
a library or framework. Use the [perspective guide](references/perspectives.md)
to establish the required domain intentions and select the other affected
facets from the six perspectives. Investigate deeper behavior when the change
or a governing requirement makes it material to the proposal.

## Present the proposal

Begin every proposal with one sentence stating who needs the requested outcome
and why. Follow it immediately with a rendered overview in six side-by-side
perspective columns, read from left to right. Name the principal participants
and show which capability serves each intention and who provides it. Connect
each domain rule to the intention it protects or the capability it constrains.
Trace the change through its implementation to a check that distinguishes the
proposed outcome from today's behavior. Even when one component changes, show
the surrounding callers and guarantees that explain its scope. Mark unchanged
subjects as `context`.

Introduce the technical explanation with a second rendered diagram showing
how the affected parts collaborate. Follow the developer's case through the
participants that actually do the work. For a small change, one call from its
caller through the responsible component to the result can suffice. When the
developer specifies an expected value, carry it through to the check. The
[diagram guide](references/diagrams.md) explains how to draw both views and
where a sequence, instance diagram, or decision table can clarify the case.

Use the system language guide's facet names in headings, table columns, or bold
prose to identify the affected subjects. Use **State Management** for the
state account. Introduce each new concept where the reader first needs it.
Keep rationale and constraints with the facet they affect, and explain material
failure consequences and uncertainties. For a breaking change, explain when
existing callers first encounter the failure and put the migration decision
to the developer, such as enforcing the rule immediately or allowing a
deprecation period.
When the requirements leave two reasonable rules open and the same input would
produce different results, show that input and both caller-visible outcomes.
Recommend a rule and explain the tradeoff. Bring consequential open choices
back to the developer in the closing approval question. Retain **Intentions**
even when they are unchanged. Let the diagrams carry the relationships. A
single-component proposal may need only a few paragraphs around the figures.
For a substantive proposal, aim for 800–1,100 words of prose or fewer,
including table text, with space for material comparisons and uncertainties.

Keep diagram sources and rendered images with the response, outside the
repository unless the developer requests another location. Use the diagram
guide's [delivery instructions](references/diagrams.md#examples-and-rendering)
for inline images and text terminals.

Lead each facet paragraph with the concrete subject. For every materially
changed subject, explicitly compare its existing behavior or responsibility
with the proposed one and explain the consequence. Include the previous behavior
needed to understand the difference; a description of the proposed result alone
is insufficient. For a new subject, state what is missing today and identify the
proposed addition. Do not invent previous behavior to complete a comparison.
Use the shared guides for subject names, relationships, implementation context,
and evidence. Distinguish proposed interfaces and entry points from existing
ones. Explain mechanism, failure, and recovery details when they affect the
proposed behavior or an approval decision.

## Revise and conclude

Ask the developer to approve the proposal or request revisions, then finish the
proposal turn awaiting that decision. Keep revisions and their approval in this
chat so the accepted scope remains identifiable. When feedback changes a
premise, subject, or decision, update the affected passages, diagrams, and
verification connections together against the same comparison baseline.
When the developer asks for selected sections, return those sections and any
dependent corrections, including a fresh rendering of each affected diagram.
Refer back to the parts of the proposal that still apply.

Approval accepts the presented design and scope. If the developer asked only
for a proposal, acknowledge approval and end the turn. Begin implementation
when the developer requests it, including when they previously asked you to
implement the change once they approved the proposal. Bring any material
departure from the approved design back for review before implementing it.
