# Teleportation

## Enkel setup

Det behöver finnas en **Locomotion System**-komponent och en **Teleportation Provider**-komponent någonstans i scenen. Enklast är att bara lägga till dem i XR Origin-objektet.

Så länge VR-handkontrollerna har [Ray Interactors](interaktion.md#ray-interaction) är detta den enda setup som behövs.

* Videotips: [https://www.youtube.com/watch?v=eI1cgiz2JSw](https://www.youtube.com/watch?v=eI1cgiz2JSw)

## Giltiga mål för teleportationen

Det finns två sorters objekt som kan teleporteras till: Area och Anchor. I båda fallen genomförs teleportationen genom att spelaren markerar målobjektet och trycker på en knapp för att genomföra teleportationen.

Objekt med en **Teleport Area**-komponent låter spelaren teleporteras till den exakta punkt på objektet som hen pekade på. Oftast är detta ett objekt med ett Plane-mesh.

Objekt med en **Teleport Anchor**-komponent låter spelaren teleporteras till objektet mittpunkt.

De har ett antal viktiga inställningar gemensamma:

* **Interaction Layer Mask:** För att skilja teleportation från andra typer av interaktion kan det vara praktiskt att ge teleportations-mål ett eget Interaction Layer och se till så att de enbart finns på detta lager.
* **Custom Reticle:** Ett objekt som skapas när spelaren markerar objektet och placeras där hen planeras dyka upp efter teleportationen.
* **Teleportation Configuration** är en liten undermeny – den viktigaste här är nog Teleport Trigger, som är den händelse som får teleportationen att utföras. Här kan man bara välja mellan Select (greppknapp) och Activate (avtryckare).

## Avancerad setup

Hela den här delen är inspirerad av den här videon: [https://www.youtube.com/watch?v=9dc1zq8eH54](https://www.youtube.com/watch?v=9dc1zq8eH54)

Ett vanligt sätt att dela upp interaktionen i VR-projekt är att låta användaren plocka upp saker och interagera med miljön med sina egna händer ([Direct Interaction](interaktion.md#direct-interaction)), och använda VR-handkontrollens joystick för att teleportera ([Ray interaction](interaktion.md#ray-interaction)). Normalt kan man bara ha en sorts interactor per XR Controller.

Dela upp scenens interagerbara objekt via **interaction layers**. Ett exempel på hur det kan göras är att skapa ett lager med namnet "intractables" och se till så att alla vanliga interagerbara objekt är på det lagret, men att inga av teleporterings-målen är det.

De här instruktionerna kommer att använda två fördefinierade InputActions som finns i XRI Default Input Actions-asseten: **Locomotion/Teleport Mode Activate** och **Locomotion/Teleport Select**. Det finns separata Input Actions för vänster och höger hand.

Normalt anropas Mode Activate av att spelaren drar styrspaken på VR-handkontrollen framåt, och Select anropas av att spelaren släpper styrspaken.

![](<../../.gitbook/assets/image (7).png>)

### XR-controllers

Instruktionerna nedan beskriver hur Left Hand-controllern anpassas för det nya sättet att teleportera och interagera. Samma steg används för Right Hand; det enda som behöver ändras är vilket spelobjekt som modifieras och vilken hands kontroller och liknande som används.

Markera XR Origin -> Camera Offset -> **LeftHand Controller**. Ta bort alla komponenter som har med Ray Interactorn att göra: XR Ray Interactor, XR Interactor Line Visual och Line Renderer.

Lägg till en **Direct Interactor** och en **Sphere Collider**. Välj radie 0.1 för collidern och gör den till en trigger. Se till så att Direct Interaction har med Interactable-lagret i sin Layer mask.

Högerklicka på LeftHand Controller och välj **XR -> Ray Interactor (Action-based)**. Det lägger till ett nytt objekt under LeftHand Controller, med standardnamnet Ray Interactor. Tryck Enter för att acceptera namnet, och se till så objektet är markerat.

I objektets XR Controller, tryck på Preset-knappen (![](<../../.gitbook/assets/image (17).png>), mellan frågetecknet och de tre prickarna till höger om namnet). Välj **XRI Default Left Controller**.

Gör följande ändringar:

* Byt ut **Select Action** till **XRI LeftHand Locomotion/Teleport Select** (![](<../../.gitbook/assets/image (23).png>) för att få fram listan).
* Kryssa ur **Enable Input Tracking**. Objektet kommer redan att flyttas genom att det ligger under den vanliga LeftHand-controllern.
* Kryssa ur **Use Reference** för **Rotate Anchor Action** och **Translate Anchor Action**. Den här interactorn ska inte vrida och vända på objekt den interagerar med.
* Se till så **Model Prefab** är tom.
* Skapa och lägg till **RayToggler**-scriptet (se nedan), och dra in **XRI LeftHand Locomotion/Teleport Mode Activate** till dess Input Action-referens.

### RayToggler

Nedan finns ett exempel på hur ett script för att växla huruvida en Ray Interactor är aktiv (enabled) beroende på en InputActions avfyrade actions.

Scriptet har alltså en referens till en **InputActionReference**, som senare kopplas (enligt instruktionerna ovan) till XRI LeftHand Locomotion/Teleport Mode Activate eller dess högerhands-motsvarighet.

Den har också en referens till den **XRRayInteractor**-komponent som ska aktiveras eller avaktiveras, och en bool-variabel som håller reda på ifall den ska vara aktiveras eller avaktiverad just nu. **RequireComponent** används ovanför klassdeklarationen för att säkerställa att det alltid finns en sådan komponent.

När objektet skapas, hämtar det en referens till interactorn.

När scriptet aktiveras (**OnEnable**) så läggs metoden **ToggleRay** till InputActionens started och canceled-metoder, och när det deaktiveras (**OnDisable**) så tas den bort därifrån. Det gör att det bara är när scriptet är aktivt som det har någon effekt – så teoretiskt sett kan man bygga andra script som i sin tur aktiverar eller stänger av det här scriptet.

**ToggleRay**-metoden ser helt enkelt till så att **isEnabled**-variabeln har rätt värde beroende på om metoden avfyrades av att "knappen" trycktes ner (i det här fallet: att styrspaken dras framåt) eller av att den släpptes upp igen.

Sedan i **LateUpdate**, så ser scriptet till så att XRRayInteractor-komponentens läge synkas med isEnabled-variabeln.

```csharp
using UnityEngine;
using UnityEngine.InputSystem;
using UnityEngine.XR.Interaction.Toolkit;

[RequireComponent(typeof(XRRayInteractor))]
public class RayToggler : MonoBehaviour
{
  [SerializeField]
  private InputActionReference inputAction = null;

  private XRRayInteractor interactor = null;
  private bool isEnabled = false;

  private void Awake()
  {
    interactor = GetComponent<XRRayInteractor>();
  }

  private void OnEnable()
  {
    inputAction.action.started += ToggleRay;
    inputAction.action.canceled += ToggleRay;
  }

  private void OnDisable()
  {
    inputAction.action.started -= ToggleRay;
    inputAction.action.canceled -= ToggleRay;
  }

  private void ToggleRay(InputAction.CallbackContext context)
  {
    isEnabled = context.control.IsPressed();
  }

  private void LateUpdate()
  {
    if (interactor.enabled != isEnabled)
    {
      interactor.enabled = isEnabled;
    }
  }
}
```
