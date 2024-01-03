# Meddelanden

Att "skicka ett meddelande" betyder att alla komponenter på objektet kör en namngiven metod _om den finns_.

Båda dessa har en prestandakostnad – de bör inte användas om andra alternativ finns.

### SendMessage()

Kör en namngiven metod i alla komponenter på samma objekt som scriptet.

```csharp
// Kör metoden "DoSomething()" på alla scriptkomponenter som har den
SendMessage("DoSomething");
```

### BroadcastMessage()

Kör en namngiven metod i alla komponenter på samma objekt som scriptet – eller dess barnobjekt.

```csharp
// Kör metoden "DoSomething()" på alla scriptkomponenter som har den
BroadcastMessage("DoSomething");
```
