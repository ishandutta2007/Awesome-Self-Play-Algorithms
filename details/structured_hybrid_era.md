# The Structured Hybrid Era (Longformer / BigBird, ~2020–2022)

## Overview
To address the isolation problem of early local attention, the Structured Hybrid Era introduced hybrid attention layouts that blended sliding local windows with global anchors and dilated steps.

## Technical Concept
Rather than using a purely local scope, hybrid architectures like Longformer and BigBird combined:
1. **Sliding Window Attention:** To capture local context.
2. **Dilated Window Attention (optional):** To skip tokens periodically and increase the receptive field.
3. **Global Attention:** Specific tokens (e.g., the `[CLS]` token or user-defined symbols) attend to all tokens, and all tokens attend to them.

```mermaid
graph TD
    subgraph Attention Pattern
        G1[Global Anchor (e.g., CLS)] <--> T1[Token 1]
        G1 <--> T2[Token 2]
        G1 <--> T3[Token 3]
        T1 <--> T2
        T2 <--> T3
    end
```

## Limitations
* **Hardware Overhead:** Non-standard sparse masks do not map efficiently onto modern GPU tensor cores, leading to execution latency.

---
[← Back to README](../README.md)
