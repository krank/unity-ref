# Flytta och rotera

## Time.deltaTime

Eftersom alla datorer är olika snabba så blir det lite konstigt om man har t.ex. en fast förflyttning eller fast rotation per bildruta.

Time.deltaTime är en float som innehåller tiden som gått sedan föregående bildruta i sekunder.

Det gör att om man multiplicerar en hastighet med Time.deltaTime så kommer det att bli en stor förflyttning om man har få fps och en mindre förflyttning om man har hög fps.

Om hastigheten ska vara 2 rutor per sekund så kommer objektet alltså att röra sig 2 \* 1/30 per bildruta på en dator som har 30fps och 2 \* 1/60 per bildruta på en dator som har 60fps.

```csharp
float speed = 2;
Vektor3 movement = Vektor3.right * speed * Time.deltaTime;
```

## Position

### transform.Translate()

En metod som tar emot en [Vector3 ](../datatyper-och-synlighet.md#vector3)och adderar den till den nuvarande positionen - samma sak som att addera själv alltså, men via en metod.

```csharp
Vektor3 movement = Vektor3.right * Time.deltaTime;
transform.Translate(movement);
```

### transform.position

En [Vektor3](../datatyper-och-synlighet.md#vector3) som motsvarar objektets nuvarande x, y- och z-position i världen.

```csharp
Vector3 newPosition = new Vector3(2f, 3.2f, 0f);
transform.position = newPosition;
```

Ovanstående exempel skapar en ny vektor med x-värde 2, y-värde 3.2 och z-värde 0. Därefter byts objektets nuvarande position ut mot den nya vektorn.

```csharp
Vector3 movement = Vector3.right * Time.deltaTime;
transform.position += movement
```

Ovanstående exempel skapar först en ny vektor som beskriver hur mycket objektet ska förflyttas, och sedan adderar den vektorn till transform.position så att det nya värdet som transform.position har är den nya positionen den ska ha.

### Vector3.Lerp()

Lerp står för "Linear interpolation". Förenklat kan man stoppa en "källvektor" och en "målvektor" och få ut en vektor som ligger mellan källan och målet. Man anger också en float som mäter hur långt längsmed rutten från källan till målet som den mellanliggande vektorn rört sig.

Detta brukar användas för att skapa "mjuka" rörelser och storleksförändringar.

```csharp
Vector3 newPosition = Vector3.Lerp(transform.position, target.transform.position, 0.5f);
// newPosition ligger precis mellan transform.Position och target.transform.Position.

transform.position = newPosition;
```

Kör man ovanstående kod i Update() så kommer objektet att flytta sig halva vägen varje bildruta. Det kommer alltså egentligen aldrig att komma fram…

Float-värdet behöver vara mellan 0 och 1, för 1 innebär "hela vägen".

## Rotation

Man jobbar sällan direkt med Quaternions i Unity; man skapar åtminstone sällan egna. Istället använder man olika metoder för att generera eller förändra quaternions.

### transform.Rotate()

Roterar objektet ett givet antal grader i x, y och z-led.

```csharp
transform.Rotate(90, 0, 0);
transform.Rotate(new Vector3(90, 0, 0));
```

Eller ett visst antal grader runt en given axel

```csharp
transform.Rotate(Vector3.up, 45);
```

### transform.RotateAround()

Snurrar objektet ett givet antal grader runt en punkt och en axel som skär denna punkt.

```csharp
Vector3 sunPosition = new Vector3(0, 10, 60);
transform.RotateAround(sunPosition, Vector3.up, 30);
```

### transform.rotation

Om man fått fram en quaternion eller vill använda en färdig – t.ex. nollrotationen Quaternion.identity – så an man ändra på transform.rotation direkt.

```csharp
transform.rotation = Quaternion.identity;
```

### transform.LookAt()

Används främst i 3D – roterar objektet så att dess interna "forward"-axel pekar mot en specifik position.

```csharp
// roterar objektet så dess forward pekar mot världens nollpunkt
transform.LookAt(Vector3.zero);
```

### Motsvarigheten till LookAt() i 2d

Det finns ett lite "fuskigt" sätt att rotera ett objekt i 2d så att det pekar mot ett annat objekt i scenen.

```csharp
transform.right = target.position - transform.position;
```
