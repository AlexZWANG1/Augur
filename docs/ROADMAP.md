# Augur Roadmap

Augur is currently an early reference projection of a larger product thesis: AI should not only answer questions; it should help humans supervise, branch, and replay the way thinking develops over time.

The roadmap is organized around that thesis.

## Near Term

### 1. Clean Public Demo State

Create a small public dataset that can ship with the repository.

Goal:

- demonstrate raw -> source -> signal -> diary -> replay without private data
- keep the example manually inspectable
- show both graph view and run diary

### 2. Externalized Thinking Diary

Make the reasoning diary a first-class surface.

Each run should show:

- every source the AI read
- what it noticed in that source
- why the observation was interesting
- which node was created or changed
- how the step connects to the next one

This diary should be readable in the left rail and replayable in the timeline.

### 3. Node Contract

Document a minimal node contract that does not overfit to investment research.

Required node fields:

- id
- type
- content
- origin
- parents
- run_id
- status

Source and signal remain typed nodes, but the schema should also allow question, contradiction, fork, diary step, pinned insight, and community nodes.

### 4. Live State API

Move the UI away from mandatory static compilation.

Target flow:

```text
wiki/log state -> live state API -> Augur renderer
```

Static `data.js` should remain only as a fallback snapshot for demos.

## Mid Term

### 5. Fork Runtime

Forks are the key interaction primitive for serious thinking.

A fork should:

- preserve parent context
- isolate assumptions
- allow a branch to grow independently
- keep a link back to the parent line of thought
- support comparison between competing branches

This is how Augur moves from a graph viewer to an actual thinking sandbox.

### 6. Scene / State JSON

AI should not emit raw frontend code.

Instead, it should emit structured scene/state JSON:

```text
nodes
relations
communities
diary_steps
timeline_events
focus
pinned_items
layout_hints
```

The renderer can then project that state into graph, feed, replay, mobile cards, or other views.

### 7. Causal Replay

A run should be replayable as a causal sequence:

1. read source
2. notice observation
3. create or update node
4. connect dots across sources
5. form or revise signal
6. expose contradiction
7. update focus
8. suggest next branch or fork

The user should be able to scrub the timeline and see which nodes appeared, changed, or became important at each step.

### 8. Semantic Layout

Node position should be meaningful.

The graph should combine:

- embedding proximity
- explicit relation edges
- AI-generated communities
- run-time causal order
- pinned node stability

This prevents the graph from becoming either a random force layout or a rigid manually curated ontology.

## Long Term

### 9. Generalized Thinking Substrate

The long-term direction is a persistent reasoning layer above ordinary memory.

Ordinary memory remembers facts. Augur should preserve the structure of thought:

- why a node exists
- what created it
- what contradicted it
- what changed it
- which branch it belongs to
- whether it should survive across sessions

This is the real meaning of Supervised Thinking.

### 10. Projection Ecosystem

The same substrate should support multiple projections:

- research graph
- daily thought feed
- mobile replay
- strategy memo
- decision table
- fork comparison
- product planning canvas
- literature review map

The UI becomes a projection of thinking, not the source of truth.

### 11. Human-AI Review Loop

The final product direction is a review loop where the human can:

- approve or reject promoted nodes
- keep or archive insights
- challenge AI-generated relations
- ask why two nodes are connected
- fork from a disputed assumption
- force a replay from a different framing

This turns AI output from a black-box answer into an inspectable, corrigible, and evolving reasoning process.

### 12. Cross-Domain Templates

Investment research is only the first stress test.

The same architecture should support:

- product strategy
- technical architecture research
- legal case analysis
- medical literature review
- policy research
- academic synthesis
- personal knowledge work

Each domain can define its own vocabulary, but the substrate stays the same: nodes, provenance, relations, deltas, forks, and replay.
