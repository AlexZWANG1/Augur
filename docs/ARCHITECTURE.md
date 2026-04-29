# Augur Technical Architecture

Augur is a Supervised Thinking system. The current repository is an early reference projection of a broader idea: a node-first substrate where AI can turn loose human intent and raw material into replayable thinking state.

The architecture is designed around one principle:

> The UI should not be the source of truth. The UI should be a projection of a persistent, inspectable thinking state.

## 1. Human-AI Interaction Layer

Augur starts from a user focus, not from a fixed form.

The user can say what they are thinking about in natural language. The AI then reads relevant material, creates nodes, proposes relationships, records an externalized reasoning diary, and updates the current thinking state.

Core interaction verbs:

| Verb | Role |
|---|---|
| `continue` | Grow the current focus forward. |
| `branch` | Expand one node into a new direction. |
| `fork` | Create an isolated sandbox from a line of thought. |
| `keep` | Preserve a node across sessions. |
| `reframe` | Reorganize the current surface without discarding provenance. |

The user is not expected to manually build the graph. The user supervises the AI as it grows and reorganizes the thinking surface.

## 2. Node-First Substrate

Augur's deepest primitive is the node.

A node can represent:

- a source observation
- a cross-source signal
- a question
- a diary step
- a contradiction
- a fork
- a community
- a pinned insight
- a run or scene

The current prototype uses `source` and `signal` as important typed nodes, but the architecture should not collapse into a rigid source/signal-only ontology.

Minimum node contract:

| Field | Meaning |
|---|---|
| `id` | Stable node identity. |
| `type` | Soft type such as source, signal, question, fork, diary, contradiction. |
| `content` | Human-readable thought object. |
| `origin` | User, AI, source material, or prior node. |
| `parents` | Nodes or raw materials that produced this node. |
| `run_id` | Reasoning run where this node appeared or changed. |
| `status` | Active, pinned, archived, challenged, or forked. |

The substrate records what changed, not only what exists. Thought deltas are first-class objects.

## 3. Source and Signal Path

Source and signal remain useful because they provide the shortest path from raw material to judgment.

| Object | Role |
|---|---|
| `raw` | Original material. Preserved, not rewritten. |
| `source` | AI's structured observation after reading one raw item. |
| `signal` | Cross-source discovery that connects multiple source observations. |
| `community` | Higher-level problem space that groups multiple signals. |
| `run log` | Replayable record of how one reasoning pass evolved. |

The intended hierarchy is:

```text
raw -> source nodes -> signal nodes -> communities / forks / replay state
```

A signal is not a summary. It should answer:

- What cross-source pattern appeared?
- Why is it interesting?
- Which source observations created it?
- What contradicts it?
- What should be watched next?

## 4. Externalized Reasoning Diary

Augur should not store or claim access to hidden model chain-of-thought. It should store an externalized, reviewable reasoning diary.

Each run should make visible:

- what the AI read
- what it noticed
- why that observation mattered
- which node it created or updated
- what relation it discovered
- what should happen next

This diary is the audit trail that makes cross-session reasoning supervisable.

## 5. Semantic Layout Layer

The graph should not be arranged only by arbitrary force-directed physics.

The current direction combines:

- explicit node relations
- AI-generated communities
- source-to-signal links
- contradiction or tension links
- embedding-based semantic proximity
- stable layout constraints for replay

The goal is that spatial position carries meaning. Nearby nodes should be semantically or structurally related, not merely visually adjacent.

## 6. Projection Layer

Augur's UI is a projection of thinking state.

Possible projections:

- Thinking Network
- Thought Feed
- Signal Index
- Source Reader
- Replay Timeline
- Mobile Scene Player
- Fork Comparison
- Written Memo
- Decision Table

The current graph UI is one projection, not the product boundary.

Longer term, the AI should output structured scene/state JSON. A stable renderer should turn that state into graph, feed, timeline, mobile replay, or future generative views. This keeps the system flexible without asking AI to emit unsafe or brittle raw frontend code.

## 7. Live State and Fallback Data

The preferred direction is live state:

```text
wiki objects / run logs / semantic layout -> state API -> UI projection
```

Static `data.js` can remain as a fallback snapshot for demos and offline preview, but it should not be the conceptual source of truth.

## 8. Privacy Boundary

The public repository includes:

- framework
- schema direction
- UI shell
- skills / execution protocol
- architecture docs
- screenshots and design assets

It intentionally excludes:

- private raw material
- generated source pages
- generated signal pages
- live graph state
- credentials
- personal research notes

This boundary matters because Augur is meant to publish the system design without exposing the private knowledge base.
