# Skapa och förstör

## Instantiate

För att skapa en kopia av ett GameObject används Instantiate.

```csharp
Instantiate(somePrefab);
```

Ofta används denna för att skapa kopior av prefabs. Då deklarerar man en GameObject-variabel som public eller använder [SerializeField](../datatyper-och-synlighet.md#serializefield). Sedan använder man Unitys editor, och inspectorn, för att göra så att variabeln länkar till prefaben i Assets.

```csharp
[SerializeField]
GameObject somePrefab;
```

### Bestämma position och rotation

Det finns flera [överlagrade](https://krank23.gitbook.io/csharp-ref/grundlaeggande/egna-metoder#oeverlagring) varianter av metoden Instantiate. Vilken version som används beror på vilka parametervärden som anges.

En av de vanligaste är den som anropas när man anger en Vector3 och en Quaternion. Då används vektorn som position för det nya objektet och quaternionen som rotation.

```csharp
Instantiate(somePrefab, new Vector3(1, 3, 0), Quaternion.identity);
```

I exemplet ovan placeras det nya objektet på x=1, y=3, z=0.

För att placera det skapade objektet på samma plats som det objekt som skapar det, till exempel om man vill skapa en projektil som avfyras från spelarens rymdskepp, så kan man givetvis använda trandsform.position, som ju är en vektor som beskriver objektets egen position.

```csharp
Instantiate(somePrefab, transform.position, Quaternion.identity);
```

I exemplen ovan används Quaternion.identity för rotation. Identity är en färdig Quaternion som är neutral - motsvarigheten till Vector3.zero.

### Att använda objektet efter att det skapats

Ofta vill man göra saker med det nya objektet efter att det skapats. Ett vanligt exempel är att man vill ändra dess parent, dvs lägga in det som child-objekt till det nuvarande. På så vis får man ju en snygg hierarkisk struktur.

Turligt nog returnerar Instantiate-metoden en referens till det nyskapade objektet.

```csharp
GameObject newThing = Instantiate(somePrefab, 
  transform.position, Quaternion.identity);

newThing.transform.SetParent(this.transform);
```

## Destroy

För att förstöra ett spelobjekt används Destroy.

```csharp
Destroy(this.gameObject);
```

Denna kod förstör det spelobjekt som det här scriptet sitter fast vid.

Man kan också påverka andra spelobjekt.

```csharp
GameObject g = GameObject.Find("Door");
if (g != null)
{
  Destroy(g);
}
```

Letar rätt på spelobjektet med namnet "Door" och förstör det, om det finns.

```csharp
private void OnTriggerEnter2D(Collider other)
{
  if (other.gameObject.tag == "Door")
  {
    Destroy(other.gameObject);
  }
}
```

När det här objektet kolliderar med ett objekt som har en trigger-collider, kolla om det objektet har taggen "Door", och förstör det i så fall.
