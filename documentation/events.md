# **Events**

Events are an essential part of AlternateLife.RageMP.Net and there are two kinds of events: ClientEvents and ServerEvents. 

## Client-Events

Client-Events, also called Remote-Events, are custom events which are callable by every player. 

### Event registration

You can register new eventhandlers by calling following method:

```cs
MP.Events.Add(string eventName, PlayerRemoteEventDelegate callback);
```

#### Example 

So, if you want to react to an event, in this example `PLAYER_INTERACT`, you could register it like this:

```cs
MP.Events.Add("PLAYER_INTERACT", async (player, eventName, arguments) => {
    // React to player interaction
});
```

## Server-Events

Server-Events are special events, which are defined by the server and notify your resource about certain events like player-connect or commands executions. You can find a documentation for all events in the interface [IEventScripting](~/api/AlternateLife.RageMP.Net.Interfaces.IEventScripting.yml).

> [!NOTE]
> You should register all events inside the constructor's-class that implements `IResource`, so you can react to all events, before the first player connects.

### Event registration

Server-Events are standard [C# events](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/events/), so you can subscribe to a special event by using the `+=` operator.

#### Example

As mentioned before, you should register all events inside the constructor, so it should look like this:

```cs
public MyFirstResource() {
    MP.Events.PlayerReady += OnPlayerReady;
}

public async Task OnPlayerReady(IPlayer player) {
    await MP.Players.BroadcastAsync($"Player {player.name} connected!");
}
```