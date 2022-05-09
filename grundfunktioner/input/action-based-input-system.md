# Action-based Input System\*

Unity har ett nytt input-system. För att aktivera det, gå till [Package manager](../../andra-funktioner/package-manager.md) och lägg till **Input System** till projektet.

## InputAction

Grunden till det nya systemet är **InputActions**. En InputAction knyter ihop knappar och andra inputs till värden. Detta kallas **bindings**. Exempel: En Movement-InputAction som knyter WASD och en handkontrolls vänstra analoga styrspak till en 2D-vektor med X- och Y-värden.

Det går att lägga till en InputAction direkt i ett script, och då knyta knappar etc till denna action på plats.

Glöm inte `using UnityEngine.InputSystem` högst upp!

```csharp
using UnityEngine.InputSystem;

public class PlayerController : MonoBehaviour
{
  public InputAction moveAction;
  
  private void Awake()
  {
    moveAction.Enable();
  }
}
```

Innan en InputAction börjar fungera måste dess Enable()-metod först anropas.

I Unity lägger till nya bindings med plus-knappen och vilken typ av värde InputActionen ska ge ifrån sig genom att klicka på kugghjulet.

![En InputAction med en Up/Down/Left/right composite-binding som döpts till WASD](<../../.gitbook/assets/image (2).png>)

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

Varje InputAction har tre [Action](https://krank23.gitbook.io/csharp-ref/grundlaeggande/delegates#h.p\_qt3arehin8yt)\<InputAction.CallbackContext> -delegatvariabler. **Started** anropas normalt sett när input påbörjas och **canceled** när input avslutas, så de är lätta att använda för att koppla kod till när en knapp till exempel trycks ner (started) eller släpps upp (canceled). **performed** är mer komplicerad och när den anropas beror på vilken sorts InputAction det rör sig om (Value eler Button t.ex).

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
  
  void OnFireEnd(InputAction.CallbackContext context(
  {
    // Avfyra skottet
  }
```

## Input Action assets

En InputAction asset samlar ett flertal ActionAssets på ett och samma ställe. Man skapar en sådan genom att högerklicka i Assets och välja Create -> Input Actions.

En InputAction asset är tänkt att samla en spelares inputs. Har man flera spelare, så skapar man en asset per spelare för att hålla isär deras kontroller.

![](<../../.gitbook/assets/image (19) (1).png>)

### Action Maps

Används för att separera kontrollerna för olika delar av spelet. Man kan till exempel ha en Action Map för menyer och en för själva spelet. I spel där man ibland kör fordon och ibland springer omkring som ensam person kan Action Maps separera styrningen för de olika sekvenserna.

Varje Action Map innehåller ett antal InputActions. De har samma tillval som andra InputActions.

### Control Schemes

Control Schemes är sätt att gruppera och filtrera bindings i en InputAction asset. Till exempel kan projektet ha Control Schemes för tangentbord+mus, handkontroll och touchscreen.

### InputAction assets i kod

Lägg till en InputActionAsset-variabel och gör så att den [syns i inspectorn](../../datatyper-och-synlighet.md#synlighet). Använd Unitys gränssnitt för att välja vilken asset som ska användas av scriptet.

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

(Kommer…)
