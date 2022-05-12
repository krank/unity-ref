# Controller

## Prefab

Om du vill kunna se var dina händer/kontroller är i VR så måste du själv bestämma hur de ska se ut. Du kan importera 3D-modeller du själv skapat eller hittat i Asset Store, eller bara skapa enkla lådor själv. Vad som helst fungerar så länge du kan skapa [prefabs ](../../begrepp.md#prefab)av dem.

![Ett exempel på väldigt enkel prefab](<../../.gitbook/assets/image (11) (1).png>)

Du kan använda samma prefab för både vänster och höger VR-controller, eller ha olika.

Du bestämmer vilken prefab som ska användas för vilken hand genom att först gå till XR Origin -> Camera Offset i Hierarchy och markera den controller du vill välja prefab för.

![](<../../.gitbook/assets/image (6).png>)

## Kod

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
