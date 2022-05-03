# Teleportation\*

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

* Mål: Bara plocka upp direkt med handen, teleportera med ray interactors
* Interaction layers: Interactable/Teleportable
  * Se till så alla interactable objekt finns på Interactable-lagret och alla teleportbara finns på Teleportable.
* XRI Default Input Actions
  * XRI LeftHand Locomotion->Teleport Select, Activate
* Controller: Byt till direct interactors
  * Lägg till Ray Interactor
    * XR Controller
      * Apply default
      * Ändra Select Action till XRI LeftHand/RightHand Locomotion/Teleport Select
      * Stäng av
        * Enable Input Tracking
        * Rotate Anchor Action
        * Translate Anchor Action
      * Ta bort Model Prefab (Markera, tryck delete)
* Script: RayToggler
  * RequireComponent XRRayInteractor
  * InputActionReference activateReference
  * XRRayInteractor reference
  * bool isEnabled
  * OnEnable/OnDisable
    * lägg till ToggleRay från activateReference.action.started/canceled
  * ToggleRay: isEnabled = context.control.IsPressed()
  * LateUpdate: om interactors enable är olik isEnabled, gör dem lika
  * Unity: Dra in LeftHand/RightHand Locomotion/Teleport Mode Activate



[https://www.youtube.com/watch?v=eI1cgiz2JSw](https://www.youtube.com/watch?v=eI1cgiz2JSw)
