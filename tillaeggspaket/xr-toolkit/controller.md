# Controller

## Prefab

Om du använder "Complete XR Origin Set Up" så syns dina kontroller som ett par generiska vita 3d-modeller i VR-rymden. Oavsett vilket kan du välja egna 3d-modeller att använda.

Expandera XR Origin och Camera Offset, och markera LeftHand Controller (eller RightHand Controller). Scrolla ner till "Model prefab". Lägg in den modell du vill använda.

De generiska vita 3d-modellerna finns under Assets → Samples → XR Interaction Toolkit → 2.3.2 → Starter Assets → Prefabs → XR Origin Pieces.

## Kod

Nedanstående är den kod som du kan använda för att få saker att hända när spelaren gör olika saker med VR-handkontrollerna.

### ActionBasedController

Komponenten ActionBasedController innehåller referenser till alla actions för VR-handkontrollerna.

```csharp
using UnityEngine.XR.Interaction.Toolkit

public class InteractionController : MonoBehavior
{
  [SerializeField]
  private ActionBasedController controller;
}
```

#### Tips: Hämta referensen automatiskt

Genom att lägga scriptet på den VR-handkontroll vars inputs ska läsas av kan man slippa manuellt ange vilken komponent som ska läsas i Unity, och istället göra det enkelt med kod:

```csharp
using UnityEngine.XR.Interaction.Toolkit

public class InteractionController : MonoBehavior
{
  private ActionBasedController controller;
  
  private void Awake()
  {
    controller = GetComponent<ActionBasedController>();
  }
}
```

### Actions

ActionBasedControllern ger tillgång till de **actions** som en VR-handkontroll normalt avfyrar. Lägg till egna metoder till dessa actions för att köra egen kod som reaktion på dem.

För att det ska fungera måste metoderna ta emot en parameter med datatypen InputAction.CallbackContext, som finns i UnityEngine.InputSystem-biblioteket.

Kolla listan under **Action Based Controller (XR)**-komponenten i Unitys Inspector för att se vilka actions som finns.

```csharp
using UnityEngine.InputSystem;

// --- //

  private void Awake()
  {
    // --- //
    
    controller.activateAction.action.started += OnTriggerPress;
  }
  
  void OnTriggerPress(InputAction.CallbackContext context)
  {
    print("Trigger pressed");
  }
```

#### Värden

Många actions har tillhörande **värden** – till exempel kan man läsa av hur mycket avtryckaren är nedtryckt eller exakt var handkontrollen är just nu.

```csharp
  void OnTriggerPress(InputAction.CallbackContext context)
  {
    print("Trigger pressed");
    
    // Läser värdet från kontexten - dvs en trigger-tryckning
    float triggerValue = context.action.ReadValue<float>()
    
    // Läser ett värde direkt från controllern
    Vector3 controllerPosition = controller.positionAction.action.ReadValue<Vector3>();    

  }
```
