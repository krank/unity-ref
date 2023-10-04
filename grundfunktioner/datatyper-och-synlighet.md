# Datatyper och synlighet

## Synlighet

Synlighet i Unity fungerar som vanligt - privata variabler och metoder kan bara kommas åt av respektive script, publika variabler och metoder kan kommas åt även utifrån.

Om ett script som lagts till ett spelobjekt har publika variabler, så kommer dessa variabler att synas i inspectorn i Unity. Det betyder alltså att deras värden kan redigeras direkt i Unity. OBS: Det betyder också att värden som anges via inspectorn får högre prioritet än värden som anges där variablerna deklareras i koden.

Med andra ord; om man skriver:

```csharp
public int experience = 4;
```

Och sedan ändrar värdet till 9 i inspectorn så kommer det inte att spela någon roll vilket värde man senare ändrar fyran till i koden.

### SerializeField

SerializeField används för att göra så att en privat variabel visas i inspectorn. Med andra ord ger man Unity tillgång till variabeln, men andra scripts kan inte komma åt den.

```csharp
[SerializeField]
int experience = 4;
```

Huruvida man använder SerializeField eller public är lite av en smaksak, men den som vill vara extra noggrann med sin inkapsling använder så få publika variabler som möjligt och då kan SerializeField vara användbart som alternativ.

## Datatyper

### float

Decimaltal. Ingår egentligen i grund-C#, men står med här eftersom det är den decimaltals-datatyp som används av Unity.

```csharp
float speed = 4.5f;
```

### Vector3

Tredimensionella vektorer. En vektor innehåller värden för x, y och z (lagrade som floats).

```csharp
// Skapa en Vector3 som har x-värde 2.3, y-värde 4 och z-värde 0.
Vector3 movement = new Vector3(2.3f, 4f, 0f);
```

Vector3-klassen innehåller också bl.a ett antal färdiga vektorer och metoder för att manipulera vektorer.

```csharp
// Skapa en Vector3 som har x-värde 1 (från Vector3.right), y-värde 1 
// (från Vector3.up) och z-värde 0.
Vector3 diagonal = Vector3.right + Vector3.up
```

När man utför vanliga matematiska operationer som innefattar en Vector3 och ett tal så påverkar talet samtliga värden.

```csharp
// Skapa en Vector3 som har x-värde 4, y-värde 4 och z-värde 0.
Vector3 veryDiagnonal = diagonal * 4
```

### Vector2

Fungerar som Vector3 men saknar z-värde.

```csharp
// Skapa en Vector2 som har x-värde 2.3 och y-värde 4.
Vector2 movement = new Vector2(2.3f, 4f);
```

### Quaternion

Beskriver rotationer. Kluriga att använda; man skapar dem nästan aldrig själv utan använder olika metoder som genererar dem. Den vanligaste användningen är att man bara hämtar den färdiga "noll-roterade" Quaternion.identity och använder den i t.ex. Instantiate().

### GameObject

Beskriver spelobjekt. Innehåller bland annat referens till den obligatoriska transform-komponenten, metoden för att förstöra objektet, samt metoden för att hämta referenser till objektets olika komponenter.
