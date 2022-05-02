# MonoBehavior

MonoBehavior är den basklass som alla komponenter bygger på. Den innehåller ett antal variabler som ger tillgång till Unitys olika funktioner, och framför allt till spelobjektet som komponenten är fäst vid. Några exempel:

* gameObject – direkt tillgång till spelobjektet
* transform – direkt tillgång till Transform-komponenten
* tag – spelobjektets tagg
* name – spelobjektets namn
* enabled – huruvida komponenten är aktiv eller ej

## Händelse-metoder

Det finns ett antal metoder som man kan lägga till i klasser som ärver från MonoBehavior, och som – om scriptet lagts till som komponent på ett spelobjekt – körs vid specifika tillfällen. Nedan är några exempel.

### Start()

Körs när objektet skapas.

```csharp
void Start()
{
  Debug.Log("I am alive!");
}
```

### Update()

Körs en gång varje bildruta. Här skrivs ofta en hel del av logiken för spelobjektet.

```csharp
void Update()
{
  Debug.Log("Ny bildruta, yay!");
}
```

### FixedUpdate()

Körs en gång varje gång fysikdelen av Unity kör en av sina loopar. Normalt sker det 30 gånger per sekund. Här skrivs också en del fysik, framför allt kanske sådan som berör fysikmotorn eller som inte behöver köras riktigt lika ofta som Update.

```csharp
void Update()
{
  Debug.Log("Ny bildruta, yay!");
}
```

## Livscykeln

Metoder som Update och även t.ex. kollisionsmetoder som OnEnterCollision körs i en viss ordning. Kolla gärna på schemat [här](https://docs.unity3d.com/Manual/ExecutionOrder.html). Där kan man till exempel se att innan Start körs en som heter Awake och en som heter OnEnable, och att det efter Update sker en massa saker och sedan LateUpdate.

Man behöver inte kunna det schemat utantill, mend et kan vara bra att veta att det finns, och att det finns en viss ordning saker och ting körs i.
