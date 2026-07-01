# The Flat Heuristic Era (Early Local Attention, ~2019–2020)

## Overview
The Flat Heuristic Era marked the initial phase of localized sparse attention mechanisms, introducing architectures designed to bypass the quadratic scaling limit ($O(N^2)$) of vanilla self-attention.

## Technical Concept
In early implementations, models restricted attention by defining a strict, symmetric local neighborhood. For a sequence of tokens, a token at index $i$ could only compute attention scores with keys located within a local window:
$$i - W/2 \le \text{key\_index} \le i + W/2$$
where $W$ is the fixed window size.

```mermaid
graph TD
    subgraph Attention Window
        T1[Token i-2]
        T2[Token i-1]
        T3[Token i (Target)]
        T4[Token i+1]
        T5[Token i+2]
    end
    T3 --> T1
    T3 --> T2
    T3 --> T4
    T3 --> T5
    T3 -.x Blocked .-> T_Far[Distant Tokens]
```

## Limitations
* **Isolation:** Because there was no global connectivity, representations of tokens at opposite ends of a sequence could not communicate in a single layer.
* **Information Bottleneck:** Models struggled with tasks requiring holistic contextual synthesis or long-range multi-turn reasoning.

---
[← Back to README](../README.md)
