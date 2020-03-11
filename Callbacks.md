---
title: Callbacks
description: Tell my assistant when you're done
---

<div class="mermaid">
sequenceDiagram
    User ->>+ Me: Do something
    Me ->> Slow: Please get me the data
    Me --> Callback: and tell my assistant when you're done
    activate Slow
    Me ->>- User: The request has started
    Slow ->> Slow: Processing...
    Slow ->> Callback: It's ready now
    deactivate Slow
    Callback ->> User: Display results

</div>


```cs
class Me{
    private Slow _slow = new Slow();

    public bool DoSomething(int id){
        _slow.GetData(id, this.Callback);
        return true;
    }

    public void Callback(int id, SlowData data){
        Context.GetObject(id).SetData(data);
    }
}

```