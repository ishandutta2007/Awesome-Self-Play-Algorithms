# Dilated / Strided Sliding Window

## Overview
Dilated attention expands the receptive field of local attention windows without increasing the number of computations.

## Technical Concept
By skipping adjacent tokens at a regular interval (dilation rate $D$), a token at index $i$ only attends to keys at indices:
$$i - D \times k$$
where $k$ is the step index within the window.

```mermaid
graph LR
    T_i[Token i]
    T_i --> T_dilated1[Token i-2]
    T_i --> T_dilated2[Token i-4]
    T_i -.->|Skipped| T_skip1[Token i-1]
    T_i -.->|Skipped| T_skip2[Token i-3]
```

---
[← Back to README](../README.md)
