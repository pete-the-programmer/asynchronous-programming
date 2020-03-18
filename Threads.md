---
title: Threads
description: you lot do these things, while I wait
---

<div class="mermaid">
sequenceDiagram
    User ->>+ Main: Do these three things
    Main ->>+ Worker1: Create
    Main ->>+ Worker2: Create
    Main ->>+ Worker3: Create
    Worker2-->Worker2: Do the task
    Worker1-->Worker1: Do the task
    Worker3-->Worker3: Do the task
    Worker2->>-Main: Done
    Worker1->>-Main: Done
    Worker3->>-Main: Done
    Main->>-User: Here are the answers
</div>

## What's Happening

The main program (or thread) can spin off a number of worker threads that can work independently and in parallel.

> workerThread.Start()

The main program then waits for them to finish their tasks and returns the result of the work.

> Threading.Join([worker1, worker2, worker3])

Note that at the end of the sequence (at the "Join") the worker threads terminate.  If you want another worker thread you need to create a new one.

## Why?

If a job can be broken down into many small independent parts then it is much quicker to perform them in parallel, rather than one after the other.
We are assuming that the job isn't _done_ until all the small parts have completed.