# Software system language

Establish the system under discussion and the outcome it supplies. For a library, the application author is a user and the calling application is an external consumer. A sorting library may invoke a comparator supplied by the application. The library chooses which values to compare and uses the result to order them. The application defines what counts as less than, equal to or greater than another value. Name the public operation or setting through which the caller makes a choice before introducing a private helper that carries it out.

## Six perspectives

Each perspective answers a different question about the system. Use the facet names below to distinguish the subjects that explain a decision and to follow their relationships across diagrams, prose, and checks.

| Perspective | Facet | What to establish |
| --- | --- | --- |
| Domain | Purpose and Scope | Whom the system serves, in what situation, and how far its purpose extends. |
| Domain | Intentions | The effect a participant wants and why it matters. Distinguish accepted intentions from those inferred from source. |
| Domain | Concepts | The terms participants use for things in their work and the distinctions they rely on. |
| Domain | Participants | Who seeks the outcome and who contributes to it. |
| Domain | Required capabilities | What the system must enable a participant to do to achieve an intention. |
| Domain | Rules | Which outcomes are required or allowed under which conditions. |
| Architecture | System context | The system boundary, its external consumers, and the services or environment it relies on. |
| Architecture | Architectural participants | Which participant owns each responsibility and who collaborates with it. |
| Architecture | Runtime units | Which process, thread, or task runs the work, and which participants share it when placement matters. |
| Subsystem Design | Components | Which internal part performs a coherent job for an architectural participant. A function can own that job in a small library. |
| Subsystem Design | Local capabilities | What work a component offers and the result its caller can use. |
| Subsystem Design | Configuration controls | Which settings affect that work and how their values change the result. |
| Subsystem Interfaces | Interfaces | The callable, endpoint, command, event or extension point, who provides it, and who uses it. |
| Subsystem Interfaces | Exchanges | What crosses an interface, in which direction, and how the receiver interprets it. |
| State Management | State elements | What each fact or resource means, how it is represented, and which operations create, derive, read or change it. Identify conditions for persistence and recovery when they matter. |
| Verification | Tests | The behavior a check exercises, at which layer, and the assertion or signal a reader can inspect. |

## Connect the perspectives

Name the intention before describing its implementation. A writer wants to resume work on a draft. Saving the draft is the required capability. The editor owns the save command, its storage component records a revision, and the revision identifies the saved text. Reopening that draft through the editor checks what the writer recovers. A test that calls the storage method directly can establish what it saves while leaving the editor's choice of text untested.

Follow the connections the question needs. Introduce a component by its job, then give its source name when the reader needs to inspect it. Use the same name in prose, tables and diagrams. If a change moves a responsibility, name both the former and proposed owners and explain what the caller would observe.
