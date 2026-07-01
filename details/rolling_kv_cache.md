# Rolling KV Cache (Mistral Framework)

## Overview
A sliding cache strategy where KV parameters are written in a circular buffer structure to maintain a constant memory footprint.

## Technical Concept
Rather than expanding the KV cache with each new token, Mistral uses a buffer of capacity $W$. The KV cache index for token $i$ is mapped via:
$$\text{cache\_index} = i \pmod W$$

```mermaid
graph TD
    subgraph Memory Cache (Size W=4)
        Slot0[Slot 0: KV_4]
        Slot1[Slot 1: KV_1]
        Slot2[Slot 2: KV_2]
        Slot3[Slot 3: KV_3]
    end
    NewKV[KV_5] -->|Overwrites Slot 1 (5 % 4 = 1)| Slot1
```

---
[← Back to README](../README.md)
