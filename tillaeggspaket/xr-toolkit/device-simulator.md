# Device Simulator

När man inte har tillgång till ett VR-headset medan man arbetar med ett VR-projekt behövs något sätt att åtminstone göra enkel testning. Den lösning som just nu finns till Unitys XR Interaction Toolkit heter XR Device Simulator. Den är inte perfekt, men den medger enklare testning.

## Setup

1. Om du inte gjort det redan, gå till [Package Manager](../../andra-funktioner/package-manager.md) och **XR Interaction Toolkit**-paketet. Klicka in under Samples och importera **XR Device Simulator**.
2. Gå till din Assets och till mappen Samples > XR Interaction Toolkit > 2.0.1 > XR Device Simulator. Dra in **XR Device Simulator**-prefaben till din scen.
3. **ELLER:** Gå till Edit → Project Settings och XR Interaction Toolkit. Kryssa i "Use XR Device Simulator in Scenes".

### I Unity 2021.3, med InputSystem 1.4.0+

Det finns en bug som gör att WASD-styrning av simulatorn inte fungerar. Som en workaround, lägg följande script på ett GameObject någonstans i scenen.

{% code title="ShortcutDisabler.cs" lineNumbers="true" %}
```csharp
using UnityEngine;
using UnityEngine.InputSystem;

[DefaultExecutionOrder(-30000)]
public class ShortcutDisabler : MonoBehaviour
{
  private void Awake() {
    InputSystem.settings.SetInternalFeatureFlag("DISABLE_SHORTCUT_SUPPORT", true);
  }
}
```
{% endcode %}

## Kontroller

Styr det simulerade VR-headsetet med vanliga WASD-kontroller och mouselook (inklusive E och Q för att åka uppåt/nedåt). Håll nere **vänster shift** för att styra vänster handkontroll och **mellanslag** för att styra den högra. Vänster musknapp simulerar avtryckaren och G-knappen simulerar greppknappen.

<table><thead><tr><th width="268.7124701157594">Välja enhet att styra</th><th width="150">Toggle</th><th>Simulator</th></tr></thead><tbody><tr><td>Hålla nere vänster shift</td><td></td><td>Vänster VR-handkontroll (tillfälligt)</td></tr><tr><td>Hålla nere mellanslag</td><td></td><td>Höger VR-handkontroll (tillfälligt)</td></tr><tr><td>T</td><td>Ja</td><td>Vänster VR-handkontroll</td></tr><tr><td>Y</td><td>Ja</td><td>Höger VR-handkontroll</td></tr></tbody></table>

<table><thead><tr><th width="267.4204400031097">Styrning/rotation</th><th width="154.933434630245">Toggle</th><th>Simulator</th></tr></thead><tbody><tr><td>WASD</td><td></td><td>Flytta headset framåt / bakåt / vänster / höger</td></tr><tr><td>Flytta musen</td><td></td><td>Lookaround</td></tr><tr><td>Scrollhjulet</td><td></td><td>Rotera enhet</td></tr><tr><td>Mittenknappen</td><td></td><td>Flytta vald handkontroll</td></tr></tbody></table>

| Knappar          | Simulator                                           |
| ---------------- | --------------------------------------------------- |
| Vänster musknapp | Trigger                                             |
| G                | Grip                                                |
| B                | Primary button (Oculus: X/A)                        |
| N                | Secondary button (Oculus: Y/B)                      |
| M                | Menu button (Oculus: Start)                         |
| 4                | Primary 2D axis click (Oculus: Klicka analogspak)   |
| 6                | Primary 2D axis touch (Oculus: röra vid analogspak) |
| 8                | Primary button touch (Oculus: röra vid X/A)         |
| 9                | Secondary button touch (Oculus: röra vid Y/B)       |
|                  |                                                     |
