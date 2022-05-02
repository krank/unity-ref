# Device Simulator

När man inte har tillgång till ett VR-headset medan man arbetar med ett VR-projekt behövs något sätt att åtminstone göra enkel testning. Den lösning som just nu finns till Unitys XR Interaction Toolkit heter XR Device Simulator. Den är inte perfekt, men den medger enklare testning.

## Setup

1. Om du inte gjort det redan, gå till [Package Manager](../../andra-funktioner/package-manager.md) och **XR Interaction Toolkit**-paketet. Klicka in under Samples och importera **XR Device Simulator**.
2. Gå till din Assets och till mappen Samples > XR Interaction Toolkit > 2.0.1 > XR Device Simulator. Dra in **XR Device Simulator**-prefaben till din scen.

## Kontroller

För att få vanliga WASD-kontroller och mouselook (inklueive E och Q för att åka uppåt/nedåt), tryck R och 3. Sedan kan du hålla nere höger musknapp för att flytta runt och styra simulatorn. Håll nere **vänster shift** för att styra vänster handkontroll och mellanslag för att styra den högra. Vänster musknapp simulerar avtryckaren och G-knappen simulerar greppknappen.

| Välja enhet att styra     | Simulator                             |
| ------------------------- | ------------------------------------- |
| Hålla nere höger musknapp | Headset (tillfälligt)                 |
| Hålla nere vänster shift  | Vänster VR-handkontroll (tillfälligt) |
| Hålla nere mellanslag     | Höger VR-handkontroll (tillfälligt)   |
| T                         | Vänster VR-handkontroll (toggle)      |
| Y                         | Höger VR-handkontroll (toggle)        |

| Styrning/rotation    | Simulator                              |
| -------------------- | -------------------------------------- |
| Flytta musen/scrolla | Flytta enhet i x/y/z-led               |
| Mitten-musknappen    | Rotera enhet i x/y/z-led (tillfälligt) |
| R                    | Byt plats på de två ovanstående        |
| 3                    | Aktivera WASD+EQ för förflyttning      |

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
