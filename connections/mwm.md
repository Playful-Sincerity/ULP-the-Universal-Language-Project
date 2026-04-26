# Connection — MWM (Memory as World Model)

*Date opened:* 2026-04-25
*Surfaced after:* the MWM paper revision pass against Eric Jennings' critique
*Status:* live insight, not yet a coupled implementation

## The connection

ULP is not just an efficient encoding for LLMs. It is a candidate **unified semantic substrate** for the nodes of MWM's experiential graph — the answer MWM's §9 (The Search for a Unified Substrate) is implicitly asking.

The MWM paper commits to a substrate where every node's canonical representation is readable by both model and human, and where modality-specific data (images, audio, sensor streams, inner states) hangs off that readable layer rather than replacing it. The current commitment uses *text* as the canonical layer — pragmatic for the initial implementation, philosophically incomplete because text is a lossy reduction for non-text modalities.

ULP's binary semantic run-length encoding could replace "text as canonical layer" with "binary semantic primitives as canonical layer" — same readability commitment, but genuinely modality-universal. A text memory, an image memory, an audio memory, an inner state are all encoded in the same structural format. The graph topology stays modality-agnostic; the node content becomes structurally semantic across every modality.

## Why this changes ULP's research program

ULP's primary positioning has been "make LLMs drastically more efficient." The honest problem with that target is that LLM weights and biases stay black-box even with a more efficient substrate underneath them — gains accumulate but the substrate's semantic legibility is wasted on an opaque consumer. The frontier-LLM efficiency benchmark is also a moving target in a fast-moving field; ULP risks chasing a metric that improves for everyone every quarter.

MWM-as-substrate-consumer changes that. MWM's nodes are *meant* to be inspectable. A ULP-encoded MWM node is structurally legible all the way down — primitives are readable, the graph topology is readable, the agent's belief structure becomes inspectable in the most rigorous sense available. ULP's compositional gains are visible at every step, and the validation criterion is structural ("does the encoding preserve cross-modal semantics with bounded loss?") rather than benchmarked-against-frontier ("did we beat GPT-N's perplexity?").

This is the research target ULP has been looking for. It's smaller than "LLM efficiency" in scope but larger in load-bearing significance for the broader Playful Sincerity research program — because every PS Research project that consumes MWM (which is SSP's memory subsystem, so basically all of SSP) ends up consuming ULP at the substrate level.

## What this means concretely

- ULP's near-term focus shifts (or splits) from LLM-efficiency-as-target to substrate-for-MWM-as-target. The two are not exclusive but the substrate framing is more concretely testable.
- MWM's §9 research program gets a specific candidate answer to investigate, rather than an open-ended substrate search.
- The coupling is staged: MWM's near-term prototype stays text-only as the paper commits. ULP-as-substrate is a Round 7 MWM research direction that runs on its own timeline and lands in a future MWM revision when ready.
- Both projects remain concept-stage. Coupling them couples timelines and risks. Worth doing carefully, not in a rush.

## The open question worth flagging

Today's LLMs read natural language. If MWM nodes are ULP-encoded, the rendering layer either translates ULP → language at render time (translation overhead, possible loss) or gets fine-tuned to read ULP directly (training cost, but cleaner architecture and consistent with MWM §8.4's "the LLM may get more specialized"). The native-read route is the more interesting long-horizon direction; the translation route is the realistic starting point.

## Cross-references

- MWM idea capture: `~/Playful Sincerity/PS Research/MWM/ideas/2026-04-25-ulp-as-mwm-substrate.md` (the same insight, from the MWM side)
- MWM paper §9: the substrate commitment and its current text-as-canonical-layer hedge
- MWM design note: `~/Playful Sincerity/PS Research/MWM/design/multimodal-unified-substrate.md` (where the ULP-as-substrate hypothesis should be added to the research program)
- SSP: as MWM's parent, SSP inherits this coupling at the substrate level
