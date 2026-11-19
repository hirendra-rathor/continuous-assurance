# Using source evidence

Start with the behavior or decision the developer cares about. Establish which repository and revision supply the evidence. When the reader needs to reproduce a version-specific result, identify the revision once. If you cannot verify it, name the files you inspected. If local edits affect an answer, name the edited files and explain which behavior or conclusion depends on those edits. Follow applicable repository instructions and use the terminology in the governing design, public interfaces and tests.

## Follow a representative case

Trace one concrete input from the caller through the component that decides the outcome. For each consequential step, identify the condition inspected, who owns the relevant state, which operation reads or changes it, and what the caller observes. Follow a failure far enough to establish which effects already happened. A later error can leave an earlier write intact.

Before recommending a retry, a recovery read, or a check, ask whether the caller could see the same result after a different history. An identical record might predate the request, and state can change between two reads. Identify what links the observation to this operation, or tell the reader what remains uncertain.

Give the reader a source path and symbol for a consequential claim. Inspect both sides of an interface when its consumer interprets the result. A type declaration can establish the shape of a response. Its caller shows which fields actually affect behavior.

For an impact question, distinguish the callers you found from the callers a public interface allows. If a search finds no uses, check the exported interface, examples, and contract tests. Explain which change a downstream application could observe and where your evidence about actual consumers ends.

## Separate evidence from expectation

Read the assertion together with the entry point the test calls, the events its fixture controls and any substitutions. Could the caller receive a different result while this assertion still holds? If so, explain what the existing check establishes and where a check would have to enter to distinguish the caller's outcomes. A stub can record the requested write while leaving durability unverified. When predicting a failure, distinguish the first observable failure from later expectations the test would never reach. Describe a test as passing only when a run and its result are known.

A documented requirement, a behavior observed in code, and a proposed change can disagree. Attribute each to its source, explain which outcome the disagreement affects, and identify the decision or check that would resolve it. A previous implementation establishes what happened. A promise to callers needs evidence in the governing contract or the developer's request. Where intent is uncertain, state the assumption the developer can settle.

## Render and inspect diagrams

Choose a view that answers the question. Follow each named operation through the diagram on its own. Label a branch when an action belongs to only one operation. An arrow should connect the participants that actually exchange the call, message or result. When one operation blocks another, identify the shared resource, who manages it and who reports the outcome. Trace a failure to its last supported effect.

Follow the consuming skill's delivery requirements. If it allows a text diagram, a plain-text drawing the developer can read as written is a finished view. In a terminal, check diagrams and comparisons at the available width, using about 80 columns when the width is unknown. Where wrapping obscures a relationship, shorten the labels, name the actor on each line of a vertical sequence, or move an explanation out of a table cell into prose.

When delivering an image, render the diagram source and inspect label placement, clipping, arrow direction and containment at reading size. A fenced block of Mermaid or DOT still needs rendering before it can supply that image.

If you cannot render or inspect a useful diagram, tell the developer which view is missing, what it would show, and why you are explaining it in prose or a table. Describe the limitation you observed in this session. If you know what would enable the image, give a concrete next step, such as making an SVG renderer available to the assistant and asking it to render the supplied source. Share the diagram source as unverified.
