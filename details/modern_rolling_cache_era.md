# The Modern Rolling Cache & Attention Sink Era (~2023–Present)

## Overview
Modern architectures optimize sliding windows by coupling them with hardware-fused caching. This preserves VRAM limits while utilizing permanent "attention sinks" to maintain linguistic stability during infinite text generation.

## Technical Concept
During generation, the Key-Value (KV) cache is restricted to a fixed size $W$. An attention sink (typically the first few tokens of the prompt) is kept in the cache permanently, preventing catastrophic perplexity spikes.

```mermaid
graph LR
    subgraph KV Cache Buffer
        S1[Sink Token 1]
        S2[Sink Token 2]
        R1[Rolling Token i-2]
        R2[Rolling Token i-1]
        R3[Rolling Token i]
    end
    NewToken[New Token i+1] -->|Overwrite R1 via modulo| R1
```

## Advantages
* Stable perplexity at extreme sequence lengths.
* $O(1)$ memory growth relative to generation length.

---
[← Back to README](../README.md)
