# Proposal Perspectives

Select affected facets using the sixteen named concerns in the
[system language guide](software-system-language.md). Use the concerns that help the developer decide what should change and how to verify it.

## Domain intentions and system boundary

Every proposal includes **Intentions**: one or more desired effects that explain
why the system should provide the proposed behavior, who benefits, and within
what scope. Derive them from the developer's request, governing design, and available
evidence. Distinguish a supplied or accepted intention from a proposed intention
or an inference from source. When intent is uncertain, state the assumption for
review; do not invent an accepted requirement. A retry-limit proposal can name
an intended effect such as returning control to callers after a bounded number
of failed attempts. Sparing application authors from writing their own retry
loops is a broader intention that can remain as unchanged context. State the
effects the proposal serves, rather than using "add a retry limit" as the
intention.

Keep independently meaningful intentions separate. Connect each to the
capability it requires and the checks that would demonstrate the outcome.
Where a rule applies, explain whose outcome it protects or what the system
must allow or prevent under that condition. Include an unchanged intention
as context in the opening overview when it explains why a component needs
to change. Retain the applicable intentions in later
revisions. If the developer requests only selected sections, refer back to
unchanged intentions and update any affected ones.

Use the shared system-boundary guidance to make the system under design the
focus. For a retry library, the application author needs a reusable capability
to invoke an operation again under selected failure conditions; the consuming
application uses the library's public API. Architecture assigns retry control
inside the library and keeps the consumer's responsibilities outside it.
Subsystem Design identifies the function or component that performs that work,
while Interfaces describes the callable and its exchanges. Keep the consumer's
example domain in context rather than turning it into the library's domain.
For frameworks, also identify the extension contract and the framework's
responsibility for invoking consumer-supplied behavior.

## Compare affected subjects

Identify which consequential rules the request or an existing contract settles
and which the proposal introduces. A requirement to give items a name leaves
open whether two spellings identify the same item. Explain that choice through
the result of creating the second item. Put the spelling of an API field or
wire value with its interface so the reader can distinguish the representation
from the rule it implements.

When work can wait in a queue or for a lock, separate the caller's eligibility
from the moment the system can act. If either arrival or execution could decide
eligibility, take one request whose circumstances change while it waits. State
the outcome under each policy and explain who bears the cost of waiting.
Recommend a policy and ask the developer to confirm it. If the contract already
fixes that moment, use the same case to verify it.

For each material change, explain the concrete subject, its existing behavior
or responsibility, the proposed difference, and its consequence. Name both
owners when responsibility moves. For a new subject, explain the gap it fills;
do not invent a previous arrangement to complete the comparison. Source
locations identify realization without changing the subject's perspective.

Use names established by the repository and keep them consistent across the
prose and diagrams. Check source before calling a component new. When a change
moves a responsibility or alters a relationship, identify both participants.

Include conditions, rationale, constraints, and material failure consequences
with the facet they affect. Architecture explains responsibility and placement;
Subsystem Design explains the internal work needed for the change. Interfaces
identify operations and exchanged information; State Management identifies
meaning, representation, and affected operations. Keep domain meanings distinct
from those realizations.

Explain state subjects through their state definition and state implementation: what
the state means, how its logical structure is represented, and which operations
create, change, derive, or read it. Select the details that change the developer's decision.

When the developer supplies a concrete example, carry it from the domain rule to
its acceptance check. If several views share an object, follow one identifier
through the operation. Show which fact changes, which references persist, and
what the user sees on the next read.

## Subsystem Design

For a substantive change to a subsystem, explain the **Components** facet
in a compact table under **Subsystem Design**. In the **Package or module**
column, show each affected name or path with its [change marker](diagrams.md#colors-and-corner-tabs)
(`new`, `changed`, or `deleted`). Name the component under **Components** and
compare its current and proposed responsibilities in the same row. Link to
existing code where it establishes the comparison.
When several modules share one package, name it above the table and use the
shorter module names in its rows. Group related files by the job they perform.
For a workflow without packages, label the first column for the steps or
resources that own the work.

## Verification

For a narrow change, give the assertion that distinguishes the new behavior
and the assertion for any existing guarantee the change must preserve. Name
the command or manual steps that would exercise them.

Put one test-kind tag beside each written verification entry, including a
single check in prose. Choose the tag by the primary boundary the scenario
exercises. Use `[unit]` for one small implementation responsibility,
`[component]` for a component's behavior through its own boundary,
`[integration]` for collaboration across an identified real implementation
boundary, and `[end-to-end]` for a user-visible path through its participating
layers from entry to outcome.

When several checks need comparison, group them under **Tests** by purpose and
layer, with one row per group. Serving an API request and upgrading an existing
database can both be integration checks and still warrant separate rows.
Include end-to-end checks where relevant and identify manual rehearsals by
what the user must observe.

For each row, give the expected assertion or signal, the prerequisites, and
the invocation. If several rows share a command, name those groups and give
the command once beside the table. Identify real dependencies or substitutes
for each group when they limit what it can establish. A claim about the
whole suite must also hold for its smoke and end-to-end checks. For a guarantee
introduced by the proposal, name a plausible failure and the observation that
would expose it.
If a substitute bypasses the behavior being promised, exercise that behavior
through its ordinary entry point or state what remains unverified. Include
checks for existing guarantees the change must preserve.

Distinguish a proposed check from one already available, and flag missing
checks or unknown entry points. For an actual run, report what was exercised
and what happened. Explain separately which claims the evidence verifies and
where coverage is still inadequate.
