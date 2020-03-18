---
title: Synchronous Programming
description: what's the problem
---

<div class="mermaid">
sequenceDiagram
    User ->>+ Main: Do these three things
    Main -->> Main: Do job 1
    Main -->> Main: Do job 2 (which takes a really long time...)
    Note over User: Gotten bored
    Note over User: shut down 
    Note over User: went home
    Main -->> Main: Do job 3
    Main -->>-User: Here are the answers
</div>