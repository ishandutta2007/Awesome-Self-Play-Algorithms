# Attention Sink Augmentation (StreamingLLM)

## Overview
StreamingLLM discovered that keeping the initial 2–4 tokens ("sinks") in the KV cache prevents catastrophic perplexity degradation during long generations.

## Technical Concept
Even when older tokens are evicted to fit inside a sliding window, the first few tokens are permanently retained. This is because early tokens act as a "sink" absorbing high attention weights.

```mermaid
graph LR
    subgraph Active KV Cache
        S1[Sink Token 1]
        S2[Sink Token 2]
        W1[Window Token i-1]
        W2[Window Token i]
    end
    Evicted[Evicted Tokens] -.x S1
```

---
[← Back to README](../README.md)
