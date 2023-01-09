# Påverka andra objekt

Om ett komponentscript på ett objekt ska kunna påverka (flytta, ta bort, etc) ett annat objekt så måste det ha en _referens_ till det objektet.

**Om båda objekten finns redan från början** kan man använda en enkel variabel:

```csharp
[SerializeField]
GameObject otherObject;
```

Sedan bestäms vilket objekt variabeln ska peka på genom att man gör kopplingen i Unity-editorn.

(Bild: Inspectorn, otherObject)

**Om objektet behöver hittas i realtid** finns ett par olika sätt att skapa referensen. Ett är att gå via kollisioner:

```csharp
void OnCollisionEnter(Collision collision)
{
  GameObject otherObject = collision.gameObject
}
```

Ett mycket ineffektivt sätt att göra det på är via Find – det bör man bara göra i undantagsfall och absolut inte varje bildruta. Find tar emot en string, och letar igenom alla scenens spelobjekt tills metoden hittar ett med ett namn som matchar.

```csharp
GameObject otherObject = GameObject.Find("enemy");
```

## Komponenter

När man väl har en referens till ett annat GameObject kan man dels påverka det direkt, dels komma åt dess komponenter via [GetComponent ](../komponenter.md#getcomponent-less-than-greater-than)och påverka dem. Det gäller även andra script-komponenter.

```csharp
void OnCollisionEnter(Collision collision)
{
  HealthScript enemyHealth = collision.gameObject.GetComponent<HealthScript>();
  
  enemyHealth.Injure(6);
}
```
