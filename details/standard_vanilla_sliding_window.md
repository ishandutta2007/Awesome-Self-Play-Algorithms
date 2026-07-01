# Standard Vanilla Sliding Window

## Overview
A baseline implementation where attention is restricted to a symmetric local neighborhood centered around each token.

## Technical Concept
Stacking multiple layers ($L$) of sliding window attention ($W$) allows the receptive field to expand linearly with depth. At layer $L$, a token can receive information from up to $L \times W$ tokens away.

```mermaid
graph TD
    L1_T1[T1] <--> L1_T2[T2] <--> L1_T3[T3]
    subgraph Layer 1
        L1_T2
    end
    subgraph Layer 2
        L2_T3[T3] <--> L2_T4[T4] <--> L2_T5[T5]
    end
    L1_T3 --> L2_T3
```

---
[← Back to README](../README.md)
