---
description: UNDER UPPDATERING // Micke, 2024-02-04
---

# Interaktion\*

I VR-sammanhang är "interaktion" specifikt när VR-utrustningen interagerar med den virtuella miljön. Till exempel är en VR-handkontroll används för att plocka upp något eller trycka på en knapp.

## XR Interaction Manager

Om du tänkt ha någon form av interaktion i din scen så behöver också något objekt ha en **XR Interaction Manager**-komponent. Lägg till den i XR Origin eller skapa ett helt nytt objekt som bara innehåller komponenten genom att högerklicka i Hierarchy och välja XR och Interaction Manager.

## Interactors och interactibles

Interaktion i XR Toolkit sker mellan **interactors** och **interactibles**.

Objekt som har en interactible-komponent kan man göra något med – plocka upp, kasta, trycka på, dra i, öppna.

Objekt som har en interactor-komponent kan sedan påverka dessa interactible-objekt.

_Exempel: Man vill kunna trycka på en knapp med sin VR-handkontroll. Knappen behöver då en interactible-komponent och VR-handkontrollen behöver en interactor-komponent._

### Interaction layer mask

Oavsett om det gäller ray interaction eller direct interaction kan **interaction layers** användas för att bestämma vilka objekt som ska kunna interageras med. Interaction layers fungrar ungefär som vanliga [lager](../../grundlaeggande-koncept/lager-och-taggar.md).&#x20;

Både XR Ray Interactor och XR Direct Interactor-komponenterna har en **Layer Interaction Mask**-variabel.

![](<../../.gitbook/assets/image (17) (1).png>)

Precis som med vanliga lager används Add Layer för att skapa nya lager. Se till så att bara de lager just denna interactor ska kunna interagera med är förkryssade. Detta blir extra viktigt om du vill ha olika sorters interactors för [teleportation ](teleportation.md)och att plocka upp föremål. Om du använder prefab-versionen av XR-riggen så utgår den från att lager 31 är "teleportationslagret".

## Interactors\*

Det finns tre huvudsakliga interactors:

* **XR Ray Interactor** – En stråle som normalt utgår från VR-handkontrollen och gör att man kan interagera med det strålen träffar.
* **XR Direct Interactor** – Använder en collider och gör att man kan interagera med det collidern rör vid.
* **XR Poke Interactor** – Gör att man kan interagera med objekt, och med UI-element, genom att "peta" på dem.

Man kan bara ha en av dem på varje XR-controller, så om man vill använda flera – se [teleportation](teleportation.md) till exempel – får man hitta en workaround av något slag. Oftast sker det genom att man har flera under-objekt som var och ett har en egen interactor. Så är det t.ex. löst i **XR Origin (XR Rig)**-prefaben.

Objekten som motsvarar dina VR-handkontroller finns i din XR Origin, under Camera Offset.

![](<../../.gitbook/assets/image (20) (1).png>)

### Ray interaction

Vid ray interaction så skjuter långa "strålar" ut från VR-handkontrollerna och föremål som träffas av strålarna kan handkontrollerna interagera med. Till exempel kan man då plocka upp föremål på distans genom att sikta på dem med strålarna och trycka på en knapp på controllern.

Som minst behöver VR-handkontrolls-objektet som ska använda ray interaction en **XR Ray Interactor**-komponent. Normalt lägger man också till en **XR Interactor Line Visual**-komponent som för att strålen som skjuter ut syns. Då läggs också en Line Renderer-komponent till automatiskt.

När XR Origin-objektet skapas så ges båda VR-handkontrollerna de komponenter som behövs för ray interaction.

### Direct interaction

Vid direct interaction måste VR-handkontrollen (eller den collider som är på samma objekt som Direct Interactor-scriptet) fysiskt röra vid målobjektet för att interaktion ska kunna se. Då kan man inte interagera med saker på distans utan måste vara nära dem.

Lägg till en **XR Direct Interactor**-komponent till det VR-handkontroll-objektet som ska använda direct interaction. Lägg också till en Sphere Collider (Trigger); den kommer att användas för att känna av kollisionen mellan interactorn och objekten.

### Poke interaction\*

### Interactors och kod

Oavsett vilken typ av interactor som används så kan man använda kod för att till exempel läsa av vilket eller vilka objekt den hovrar över just nu:

```csharp
public class ControllerController : MonoBehaviour
{
  XRBaseInteractor interactor; // Basklassen för alla interactors

  void Awake()
  {
    interactor = GetComponentInChildren<XRRayInteractor>();
  }

  void Update()
  {
    foreach (IXRHoverInteractable interactable in interactor.interactablesHovered)
    {
      // skriver ut namnet på objektet som hovras över
      Debug.Log(interactable.transform.name);
    }
  }
}
```

## Interactables – föremål som kan interageras med

För att göra så att ett objekt kan interageras med, behöver det en Interactable-komponent. Det finns flera olika.

<table><thead><tr><th width="194">Komponent</th><th>Beskrivning</th></tr></thead><tbody><tr><td>XR Grab Interactable</td><td>Objekt som kan plockas upp genom att man trycker på Grab-knappen</td></tr><tr><td>XR Simple Interactable</td><td>Enklast möjliga: objektet kan interageras med men saknar inbyggd funktionalitet.</td></tr><tr><td>XR Socket Interactable</td><td>Objekt som andra objekt kan sättas fast på. En mer detaljerad genomgång finns t.ex. <a href="https://www.youtube.com/watch?v=rRNvq09Itdw">här</a>.</td></tr></tbody></table>

Objektet behöver också en collider av något slag, och antagligen en RigidBody. Fysik-systemet används för att avgöra om objektet kolliderar med en VR-handkontroll eller med en stråle från ray interaction.

### Reagera visuellt

En **XR Tint Interactable Visual**-komponent gör att objektet får en tydlig visuell indikation på att det är det nuvarande målet för interaktionen.

### Reagera med kod via Events

Objekt som har någon form av Interactable-komponent kommer att ha ett antal Interactable Events som kan knytas till specifika metoder i kod – precis som events i [det vanliga UI-systemet](../../grundfunktioner/ui-och-canvas.md#events).

I listan är det mesta ganska självförklarande, men det finns tre viktiga begrepp:

* **Hover** betyder att spelaren markerat objektet med en stråle (ray interactor) eller en VR-handkontroll (direct interactor).
* **Select** betyder att spelaren tryckt på **grepp-knappen** på sin VR-handkontroll. Man kan ändra vilken knapp som gör "select" om man vill.
* **Activate** betyder att spelaren tryckt på **trigger-knappen** på sin VR-handkontroll. Man kan ändra vilken knapp som gör "activate" om man vill. OBS: För att Activate ska ske måste Grab ha skett först.

I exemplet nedan aktiveras metoden **DoSomething** i **CapsuleController**-scriptet som finns i objektet **Capsule** när spelaren **markerat** objektet med antingen sin stråle (ray interactor) eller sin VR-handkontroll (direct interactor)

![](<../../.gitbook/assets/image (13) (1).png>)

### Reagera med kod – bara kod

I scripts som ligger på det interagerbara objektet kan man skriva kod för att lägga till metoder direkt – utan att gå via den visuella Events-listan. Man gör då detta genom att använda AddListener-metoden på Interactable-komponenten.

Exemplet nedan gäller XR Grab Interactables, men motsvarande gäller också övriga.

{% code title="CubeController.cs" %}
```csharp
using UnityEngine.XR;
using UnityEngine.XR.Interaction.Toolkit;

public class CubeController : MonoBehaviour
{
  XRBaseInteractable interactable;

  void Awake()
  {
    interactable = GetComponent<XRGrabInteractable>();
    interactable.activated.AddListener(ActivateEvent);
  }

  void ActivateEvent(ActivateEventArgs args)
  {
    // Det som ska hända
  }
}
```
{% endcode %}

## Exempel: Köra kod på objekt man pekar på, när man trycker på avtryckaren

Om man vill att något ska hända direkt när spelaren pekar sin controller, med [ray interactor](interaktion.md#ray-interaction), mot ett föremål och trycker på avtryckaren så kan man kombinera tekniker så här:

{% code title="EnemyController" %}
```csharp
public class EnemyController : MonoBehaviour
{
  public void Damage()
  {
    Debug.Log("Damaged!");
  }
}
```
{% endcode %}

EnemyController läggs på objektet som ska kunna påverkas – skadas, i det här fallet.

GunController, nedan, läggs på Left Controller och Right Controller.

Det GunController gör är att först hitta referenser till ActionBasedController (som sköter input-delen) och XRRayInteractor (som sköter kollen av vilka objekt man pekar på).

När spelaren sedan trycker på Activate-knappen (avtryckaren) så körs metoden Fire, som går igenom alla objekt som XRRayInteractorn känner av, och ifall de har en EnemyController-komponent så körs dess Damage-metod.

{% code title="GunController.cs" %}
```csharp
using UnityEngine;
using UnityEngine.InputSystem;
using UnityEngine.XR.Interaction.Toolkit;

public class GunController : MonoBehaviour
{
  ActionBasedController controller;
  XRBaseInteractor interactor;

  void Awake()
  {
    controller = GetComponent<ActionBasedController>();
    interactor = GetComponentInChildren<XRRayInteractor>();

    controller.activateAction.action.started += Fire;
  }

  void Fire(InputAction.CallbackContext ctx)
  {
    foreach (IXRHoverInteractable interactable in interactor.interactablesHovered)
    {
      if (interactable.transform.TryGetComponent<EnemyController>(out EnemyController controller))
      {
        controller.Damage();
      }
    }
  }
}
```
{% endcode %}
