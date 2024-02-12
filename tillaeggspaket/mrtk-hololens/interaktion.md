# Interaktion

## Object Manipulator

Ett objekt som ges en **Object Manipulator**-komponent kan flyttas runt av användaren, som bara behöver peka på den med en av sina pekare (strecken som skjuter ut från händerna) och använda Select-gesten (knipa ihop tumme och pekfinger) för att påbörja interaktionen.

Objekt med en Object Manipulator-komponent får också automatiskt en Constraint Manager-komponent.

I Object Manipulator-komponenten finns inställningar för en- och tvåhandsmanipulation och till exempel smoothing (som får objektet att röra sig mjukt när det manipuleras).

För att skapa ett objekt som bara kan interageras med på nära håll – ändra i listan **Allowed Interaction Types**.

Det finns också **Unity Events** för när manipulationen börjar och slutar (On Manipulation Started/Ended) samt för när spelaren börjar/slutar markera objektet med sin pekare (On Hover Started/Exited).

### ~~Near Interaction Grabbable~~

~~Ett manipulerbart objekt som ges en Near Interaction Grabbable-komponent kan inte manipuleras på avstånd, utan användaren måste gå nära objektet och röra vid det med sina händer.~~

## Stateful Interactable

Komponent som ger ett objekt enkel interagerbarhet.

* **Selection mode** \[Button|Toggle|One-way toggle] avgör hur objektet ska fungera.
  * Button: En vanlig knapp. man klickar, något händer.
  * Toggle: En av/på-knapp som minns vilket "läge" den är i.
  * One-way toggle: Som toggle, men bara åt ett håll.

Listan "On Clicked" är händelser som sker (metoder som körs) när man klickar på knappen. "On Toggled" och "On Untoggled" dyker upp om man väljer att det ska vara en toggle-knapp, och gör så att olika metoder kan köras när man klickar, när den hamnar i "på"-läge och när den hamnar i "av"-läge.

## ~~Interactable~~

~~Objekt som inte ska kunna manipuleras utan bara reagera med kod på att vidröras, klickas på etc kan ges en **Interactable**-komponent.~~

~~**Input Actions** är vilken action komponenten ska reagera på.~~

~~**Voice Command** är vilket, om något,~~ [~~röstkommando~~ ](roeststyrning.md)~~den ska reagera på.~~

~~Under **Events** finns sedan framför allt **OnClick**, som är ett helt vanligt~~ [~~Unity Event~~](../../grundfunktioner/unity-events.md) ~~som kan kopplas till ett eller flera scripts och metoder.~~

~~Under **Receivers** går det att lägga till fler sorters events som interactable-objektet ska ta emot. Till exempel kan en InteractableOnFocusReceiver göra det möjligt att koppla script och metoder till när användaren markerar eller tittar på ett objekt.~~
