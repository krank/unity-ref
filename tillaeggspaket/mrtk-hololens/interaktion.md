# Interaktion\*

## Object Manipulator

Ett objekt som ges en **Object Manipulator**-komponent kan flyttas runt av användaren, som bara behöver peka på den med en av sina pekare (strecken som skjuter ut från händerna) och använda Select-gesten (knipa ihop tumme och pekfinger) för att påbörja interaktionen.

Objekt med en Object Manipulator-komponent får också automatiskt en Constraint Manager-komponent.

I Object Manipulator-komponenten finns inställningar för en- och tvåhandsmanipulation och till exempel smoothing (som får objektet att röra sig mjukt när det manipuleras).

Det finns också **Unity Events** för när manipulationen börjar och slutar (On Manipulation Started/Ended) samt för när spelaren börjar/slutar markera objektet med sin pekare (On Hover Started/Exited).

### Near Interaction Grabbable

Ett manipulerbart objekt som ges en Near Interaction Grabbable-komponent kan inte manipuleras på avstånd, utan användaren måste gå nära objektet och röra vid det med sina händer.

## Interactable

Objekt som inte ska kunna manipuleras utan bara reagera med kod på att vidröras, klickas på etc kan ges en **Interactable**-komponent.

* Interactable
  * Reagera på handlingar (t.ex fokus, klick
