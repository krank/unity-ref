# Action-based Input System

Unity har ett nytt input-system. För att aktivera det, gå till [Package manager](../../andra-funktioner/package-manager.md) och lägg till **Input System** till projektet.

(Vidare läsning: [Complete guide to the new system](https://gamedevbeginner.com/input-in-unity-made-easy-complete-guide-to-the-new-system))

{% hint style="info" %}
**Det enklaste sättet** att börja arbeta med det här systemet är via en [Player Input](action-based-input-system.md#player-input)-komponent.
{% endhint %}

**Sammanfattning:**

* **Player Input**-komponenten kopplar ihop en **Input Action Asset** med spelets övriga kod.
* En **Input Action Asset** består av en eller flera **Action Maps**.
* Varje **Action Map** beskriver en uppsättning kontroller för en del av ett spel (t.ex. båtsekvenser, eller plattformshoppande). Och består av ett antal **Input Actions**.
* En **Input Action** kopplar ihop vissa knapptryck (t.ex. mellanslag och A på handkontroll) med ett värde med specifierad datatyp (t.ex. float). "Movement" kan vara en Input Action, medan WASD är ett sätt att mata Movement med data.

Man kan arbeta antingen separat med enskilda Input Actions, eller så kan man jobba mer övergripande med Input Action Assets och låta Unitys system hantera mer av strukturen.

## InputAction

Grunden till det nya systemet är **InputActions**. En InputAction knyter ihop knappar och andra inputs till värden. Detta kallas **bindings**.&#x20;

Exempel: En _Movement-InputAction_ som knyter WASD och en handkontrolls vänstra analoga styrspak till en 2D-vektor med X- och Y-värden.

Det går att lägga till en InputAction direkt i ett script, och då knyta knappar etc till denna action via gränssnittet i Unitys inspector.

Glöm inte `using UnityEngine.InputSystem` högst upp!

```csharp
using UnityEngine.InputSystem;

public class PlayerController : MonoBehaviour
{
  public InputAction moveAction;
  
  private void Awake()
  {
    moveAction.Enable(); // OBS!
  }
}
```

Innan en InputAction börjar fungera måste dess Enable()-metod först anropas.

I Inspectorn lägger man sedan till nya **bindings** med plus-knappen. Man bestämmer vilken typ av **värde** InputActionen ska ge ifrån sig genom att klicka på kugghjulet.

![En InputAction med en Up/Down/Left/right composite-binding som döpts till WASD](<../../.gitbook/assets/image (2) (1) (1).png>)

### ReadValue<>

Används för att läsa av en InputActions värde. Datatypen anges mellan <>. Om ingen binding har rätt datatyp, returneras ett nollvärde.

```csharp
  void Update()
  {
    Vector2 movement = moveAction.ReadValue<Vector2>();
    
    transform.Translate(movement * speed * Time.deltaTime;
  }
```

### Actions

Varje InputAction har tre [delegatvariabler](http://127.0.0.1:5000/s/-MHmNgpRz-b16wpwGwZI-887967055/grundlaeggande/delegates) av typen [`Action`](https://krank23.gitbook.io/csharp-ref/grundlaeggande/delegates#h.p\_qt3arehin8yt)`<InputAction.CallbackContext>`. Delegaterna heter **started**, **canceled** och **performed**.

**Started** anropas normalt sett när input påbörjas och **canceled** när input avslutas, så de är lätta att använda för att koppla kod till när en knapp till exempel trycks ner (started) eller släpps upp (canceled). **Performed** är mer komplicerad och när den anropas beror på vilken sorts InputAction det rör sig om (Value eler Button t.ex).

InputAction.CallbackContext-parametern innehåller information om den InputAction-händelse som anropade metoden, så man kan koppla samma metod till flera Actions och ändå göra skillnad i vad som händer.

```csharp
  void Awake()
  {
    fireAction.Enable();
    fireAction.started += OnFireStart;
    fireAction.canceled += OnFireEnd;
  }
  
  void OnFireStart(InputAction.CallbackContext context)
  {
    // Börja ladda upp skottet
  }
  
  void OnFireEnd(InputAction.CallbackContext context)
  {
    // Avfyra skottet
  }
```

## Input Action assets

En InputAction asset samlar ett flertal ActionAssets på ett och samma ställe. Man skapar en sådan genom att högerklicka i Assets och välja Create -> Input Actions.

En InputAction asset är tänkt att samla en spelares inputs. Har man flera spelare, så skapar man en asset per spelare för att hålla isär deras kontroller.

![](<../../.gitbook/assets/image (19) (1).png>)

### Action Maps

Används för att separera kontrollerna för olika delar av spelet. Man kan till exempel ha en Action Map för **menyer** och en för själva **spelet**. I spel där man ibland kör fordon och ibland springer omkring som ensam person kan Action Maps separera styrningen för de olika sekvenserna.

Varje Action Map innehåller ett antal InputActions. De har samma tillval som andra InputActions.

### Control Schemes

Control Schemes är sätt att gruppera och filtrera bindings i en InputAction asset. Till exempel kan projektet ha Control Schemes för **tangentbord+mus**, **handkontroll** och **touchscreen**.

### InputAction assets i kod

Lägg till en InputActionAsset-variabel och gör så att den [syns i inspectorn](../datatyper-och-synlighet.md#synlighet). Använd Unitys gränssnitt för att välja vilken asset som ska användas av scriptet.

Genom att anropa assetens Enable-metod så aktiveras den som helhet. Enskilda InputActions behöver inte aktiveras manuellt.

```csharp
using UnityEngine.InputSystem;

public class PlayerController : MonoBehaviour
{
  public InputActionAsset actionAsset;
  
  private void Awake()
  {
    actionAsset.Enable();
  }
}
```

### FindAction()

Metoden FindAction tar emot namnet på en InputAction som parameter och returnerar denna InputAction om den hittas i InputAction asseten som den anropas i.

```csharp
  private void Awake()
  {
    actionAsset.Enable();
    InputAction fireAction = actionAsset.FindAction("Fire");
    
    fireAction.started += OnFireStart;
    fireAction.canceled += OnFireEnd;
  }
```

## Player Input

PlayerInput är en komponent för att enkelt knyta ihop en InputAction Asset med kod som t.ex. flyttar på spelarkaraktären.

Om ingen Input Action Asset är vald, finns en knapp för att skapa en. Den som då skapas har tre Actions redan inlagda – Move, Look och Fire. Man kan enkelt lägga till flera, eller ta bort de man inte behöver, men det är i varje fall en ganska bra grund att utgå från.

<figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Default Scheme** och **Default Map** är det control scheme och den action map som används som standard. Ofta behöver man inte ändra på dem alls.

**Behavior** är det sätt Player Input-komponenten använder för att kommunicera med andra scripts. Send Messages är antagligen det enklaste.

### Send Messages

Om en scriptkomponent på samma spelobjekt som Player Input har metoder som är döpta på rätt sätt, så kommer de metoderna att anropas när spelaren trycker på knappar eller drar i analoga spakar. I en normal Input Action Asset finns till exempel en Action som heter Move. När spelaren trycker på, eller släpper upp, någon av knapparna eller spakarna som är knuten till denna Action, så körs OnMove-metoden om den finns.

```csharp
public class AvatarController : MonoBehaviour
{
  void OnMove()
  {
    print("Moving!");
  }
}
```

### Läsa av input-värden

För att läsa av exakt vilket värde en knapp eller spak har, till exempel för förflyttning, så kan man lägga till en **InputValue**-parameter till de metoder som anropas av Send Message-systemet.

Från ett InputValue-objekt kan man sedan få ut Vector2 eller float eller bool, beroende på vilken typ av data som skickas av motsvarande Action. Move har ofta en Vector2 som Action Type, till exempel.&#x20;

```csharp
using UnityEngine;
using UnityEngine.InputSystem;

public class AvatarController : MonoBehaviour
{

  [SerializeField]
  float speed = 2;

  Vector2 movement = new Vector2();

  void Update()
  {
    transform.Translate(movement * speed * Time.deltaTime);
  }

  void OnMove(InputValue value)
  {
    movement = value.Get<Vector2>();
  }
}
```
