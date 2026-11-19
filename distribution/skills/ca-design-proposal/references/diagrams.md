# Proposal diagrams

The opening overview explains why the change matters and how to verify it.
The collaboration diagram introduces the technical explanation by showing who
performs the work. Carry the same example and comparison baseline through
both figures. Give shared subjects the same names so the developer can
follow a responsibility from one figure to the other.

## Expanded summary

Place all six column headings on one horizontal row. From left to right they
are Domain, Architecture, Subsystem Design, Subsystem Interfaces, State
Management, and Verification. Stack subjects under their own heading. Keep
the heading visible when a column has no relevant subject. If space is tight,
provide a full-size view or split the overview into legible figures. Each
overview keeps the six columns and repeats the subjects that connect it to
the others.

Give each box one named subject and a short [facet label](software-system-language.md).
In Domain, identify who seeks the outcome, what they want to achieve, and
which capability they need. Give each material rule its own box. Draw an
arrow from the rule to the intention it protects or the capability it
constrains. Show both relationships when both explain the decision. Label
the arrow with the reason or limiting condition so the two subjects and the
label read as a claim. Links can run within a column, point back, or branch
across columns according to their meaning. For example, a component can
implement an interface and a test can exercise one of its operations.

In Architecture, name the principal participants in separate boxes and connect
them by the work they do for one another. Identify the caller, who provides
the capability, and any other participant on which the outcome depends. For
example, a browser sends a request to an API, and the API writes to a store.
Name the actual participants even when they share a process. Put the stored
facts in State Management. For each principal participant in the collaboration
diagram, check that the overview identifies it by the same name. Introduce
its internal components under their owner as needed.

End the relevant paths in checks with observable assertions, including
a retained guarantee when it matters. For a line counter that adds piped input,
a two-line pipe and a two-line named file should each yield two. A separate
check inspects whether the borrowed stream remains open after the call.
Identify proposed or missing checks and the limits of any executed checks.

Read the rendered overview on its own. Can the developer read the six headings
across the page, identify who works with whom, and follow each rule to the
outcome it protects or the limit it imposes? Can they predict what the caller
would observe at the check?

## Implementation collaboration view

Draw the affected architectural participants and components, the interfaces and
information they exchange, and the state they read or maintain. Arrange them
around their collaboration. Use labeled calls, exchanges, and state operations,
with boxes or edges for interfaces according to whether the interface needs
independent explanation. A single changed component can appear with its
existing caller and the information they exchange. A sequence diagram fits
when the order of calls and replies explains how those participants deliver
the outcome.

For a library or framework, make its system boundary and consuming software
visible. Place public callables or extension interfaces on the relevant
collaborations and name the internal function or component performing the work.
Show callbacks in their actual direction while preserving the consumer's role.
Use a separate boundary or annotation for a shared process so it does not erase
the distinction between the system and its consumer.

Use separate paths or views when a reader needs to distinguish which operation
reads, changes, or releases each resource. Label a call with its actual caller
and destination. Distinguish the component that makes a decision, the mechanism
that enforces it, and the record that survives it.

Do not repeat the six perspective lanes or add columns for Subsystem Design,
Subsystem Interfaces, or State Management. Group elements only where the system
has a meaningful subsystem, ownership, process, or storage boundary. Identify
what each boundary means. Shared code used in separate processes must not look
like a shared running service; containment must not imply unsupported deployment
or ownership. Natural role labels can help identify a client, component, or
stored record without making perspective classification the layout.

Draw the participants in the proposed operation, including a production
validator when it performs part of the work. Include consequential failure
and recovery paths where they clarify effects, caller observations, or
retained state.

Show proposed collaborations and the existing surroundings needed to understand
them. Keep removed components clearly marked, with their former connections
identified or in a separate removal group, so they do not appear to participate
in the proposed operation. Use the proposal's names and change markers
while spending this view's space on interactions and ownership.

## Illustrate a decision

Use the developer's example inside either figure or add a focused illustration
alongside it. An instance with its identifiers and links can show what survives
a shared-state change. A short sequence can show an end-user interaction.
A transition table can show the result of repeating an action in each state.
For an open choice, use one input for which the alternatives produce different
outcomes. For a timing boundary, show events on either side and at equality
using values exactly representable in the implementation's units. If rounding
or clock resolution decides the outcome, verify the comparison in source or
with a read-only run, or identify the result as unverified.

## Select useful surrounding context

Include an unchanged subject when it explains why a change matters, identifies
a producer or consumer, establishes ownership, exposes an interface that must
remain compatible, or makes a preserved condition understandable. An
existing intention can explain a changed rule in the overview. The client
that uses the affected interface can show where the collaboration begins.
Include participants supported by the implementation or needed for the
proposed behavior.

Mark those subjects as `context` and state their relevant role briefly. A
context marker means no proposed semantic change to that subject; the absence
of a source-file edit does not establish that its responsibility or behavior is
unchanged. Mark a changed relationship independently when its endpoints remain
unchanged. Base each marker on the current implementation or governing contract.

## Name subjects and compare changes

Lead each box with its subject and keep behavior in the supporting text.

| Perspective | Subject to name | Supporting text explains |
| --- | --- | --- |
| Domain | An intention, concept, participant, capability, or rule | Meaning, conditions, required outcome, and proposed change. |
| Architecture | An architectural participant, system boundary, or runtime unit | Who performs the work and how responsibilities or placement change. |
| Subsystem Design | A component, local capability, or configuration control | Its changed job, offered work, or behavioral effect. |
| Subsystem Interfaces | A named interface or exchange | Providers, consumers, inputs, responses, and conditions. |
| State Management | A named state element, such as a context, record, identity, or resource | Meaning, occurrence scope, representation, and affected operations. |
| Verification | An existing or proposed test or test family | Its bounded subject, expected assertion or signal, and execution limits. |

An interface title such as "Command-line input" names the interface; "Agent checks
inputs and routes work" does not. Keep state labels centered on the information
or resource. Name both owners when responsibility moves. When an owner stays
the same, compare its old and new duties.

In overviews and collaboration diagrams, compare materially changed subjects
against the existing behavior or arrangement. Separate concise `Today:` and `Proposed:` text
within the box. Render the `Today:` passage in a muted, readable gray and the
`Proposed:` passage in the normal, stronger foreground. Keep both at a legible
size, with sufficient contrast against the actual background. Use text color
to reduce the old passage's emphasis; do not fade the whole box, subject name,
status tab, or relationship. The labels must make the comparison understandable
without relying on color alone.

Mute only the previous behavior being compared. Put continuing conditions in
normal text, so partial replacement does not imply that the whole subject or
all of its earlier behavior disappears. Keep unchanged context in normal text
with its gray outline and `context` tab. The temporal comparison and the change
status have different meanings.

A new subject should explain the gap it fills; a deleted subject should identify
what is removed. Do not invent a previous arrangement to complete a comparison.
Keep the main label stable rather than replacing it with an action sentence.
Use the same comparison baseline across views and revisions: revising a proposal
does not make a proposed new subject an existing one. If the developer changes the
baseline, reassess every comparison and marker.

## Colors and corner tabs

For overviews and collaboration diagrams, use neutral fills with these outline
colors and matching corner tabs. In a supplementary timeline, sequence, or
instance diagram, label events, outcomes, and identities directly. Use change
markers there only when the reader needs the comparison.

| Meaning relative to the comparison baseline | Outline | Corner text |
| --- | --- | --- |
| New subject, relationship, or obligation | Green `#22a06b` | `new` |
| Changed subject, relationship, or obligation | Blue `#3b82f6` | `changed` |
| Deleted subject, relationship, or obligation | Red `#dc2626` | `deleted` |
| Unchanged surrounding context | Gray `#a3a3a3` | `context` |

Place a compact legend in the upper-right corner of each image. For each
status used in that image, put its lowercase word inside a badge filled with
the corresponding color. Use contrasting text on both the legend badges and
the matching subject tabs. When edge colors mark change status, say so in
the image header. Include the color meanings in the image's text alternative.
Omit any footer that repeats the key.

Place the matching status tab on each subject's upper-right border, clear of
the subject and facet labels. Mark a changed relationship on the edge and
retain its relationship label even when its endpoints are unchanged.

Mark an aggregate as changed when the proposal alters its behavior,
responsibility, contract, state arrangement, or placement. Split it when an
important addition or deletion would otherwise be hidden. Apply deletion to
the thing actually removed, not to a broader capability that remains. Keep
retained conditions outside a removal group's boundary. Do not invent
deletions to use every color. Verification uses the same notation: green means
a new test, not a passed check; red means removal, not failure.

## Examples and rendering

The [line-counter example](diagram-examples.md) opens with an overview of a
change to input selection. Its collaboration diagram shows which component
opens or borrows each input. A decision table compares what the caller
observes under the two stream-ownership policies.
For views with change markers, choose a renderer that supports muted existing
behavior and corner tabs. If it loses those distinctions, lay out the diagram
in SVG and render it for inspection.

Render and inspect the figures, keep their editable sources with the response
assets, and show the images inline when the client supports it. In a text
terminal, explain the decisive sequence or comparison in the response and
give the developer a complete, copyable path to the rendered figure or, for
several figures, their index. Check that the exact path in the answer
opens the intended file and the index resolves its figures. Prefer storage
the developer can revisit and identify temporary storage when used.

If you cannot render a required figure, tell the developer which figure is
still due and what prevented rendering. If you can render it but cannot
inspect it, explain the limitation beside its path and mark it as unverified.
Follow the shared
[rendering and meaning checks](using-source-evidence.md#render-and-inspect-diagrams).
Inspect at reading size. For boxes with change markers, check the tabs, muted
comparisons, and contrast against the actual background. For each important
collaboration arrow, identify who acts, on what, and when. A test arrow should
name what the test can observe. Check for ambiguous paths, clipped labels, and
containment that implies the wrong process or owner. Revise the views and
prose together when the premise, comparison baseline, or decision changes.
