---
name: ca-explore-design
description: Explain how a software system works or what a change would affect using its code, tests, and documentation. Use for questions about responsibilities, behavior, rules, state, failures, and change impact.
---

# Explore Design

Answer the developer's question in the current conversation. Reuse the scenario, repository and level of detail already established. For an open request to explore, give a brief orientation. Explain the purpose and follow one ordinary use through the main collaborators. Stop where the developer has enough context to choose what to explore next.

Use the [system language guide](references/software-system-language.md) to identify the perspectives that explain the question and the [source evidence guide](references/using-source-evidence.md) to substantiate the answer.

For a behavior question, follow an input through the decision and state change to the outcome the caller can observe. When one participant requests a decision or records its result and another makes it, identify the decision-maker and the rule they apply. If another event order, failure, or recovery path changes the answer, briefly explain what happens in that case and why. For an impact question, trace the callers, guarantees, and tests that depend on the affected behavior.

If a reference is stale or a dependency is unclear, use symbols, callers, or version history to locate the relevant code. Verify the claim at the revision under discussion. If the evidence covers only part of the path, say what it establishes and what would settle the remaining question.

Lead with the answer. Name the participants and explain how they work together, citing the source that supports each consequential claim. When documentation and implementation differ, locate the disagreement and explain its consequence. Label inferences, untested failure paths and open questions where they affect the answer.

For a hypothetical change, start with the difference a caller would observe. Several implementations may produce that outcome while retaining different state or assigning work to different participants. Distinguish the checks of the requested outcome from checks that depend on a particular implementation, and state the assumption behind the latter.

When suggesting wording a developer could publish, read it on its own against the boundary cases in the source. Include the conditions a caller needs to predict the outcome.

When a visual makes the outcome easier to understand or predict, include it alongside the explanation in the same answer. Choose the simplest view for the part the reader would otherwise have to reconstruct. A sequence diagram or timeline can show event order, an interaction diagram can show responsibilities and exchanges, and a state diagram can show which transitions are possible. Reuse an existing figure when it answers the specific question. Check the visual’s [meaning and legibility](references/using-source-evidence.md#render-and-inspect-diagrams) and show it inline when the client supports it.

Investigate by reading the repository and keep any rendered figure files with the response assets. Running the application, editing the developer's files, or writing a separate report requires a request that calls for that work.

If the developer asks for a proposal, carry the established context forward into the available `ca-design-proposal` skill.
