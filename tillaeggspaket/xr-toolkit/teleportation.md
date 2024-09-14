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

* **Interaction Layer Mask:** För att skilja teleportation från andra typer av interaktion kan det vara praktiskt att ge teleportations-mål ett eget Interaction Layer och se till så att de enbart finns på detta lager. **Om du använder den färdiga prefaben för din XR Rig så utgår dess XR controllers från att lager 31 är teleportationslagret.**
* **Custom Reticle:** Ett objekt som skapas när spelaren markerar objektet och placeras där hen planeras dyka upp efter teleportationen.
* **Teleportation Configuration** är en liten undermeny – den viktigaste här är nog Teleport Trigger, som är den händelse som får teleportationen att utföras. Här kan man bara välja mellan Select (greppknapp) och Activate (avtryckare).
