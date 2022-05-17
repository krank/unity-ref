# Komponenter

Alla spelobjekt i Unity består av ett antal komponenter. Varje komponent är en instans av en komponentklass, och alla komponentklasser har olika inbyggda variabler och metoder som ger komponenten och spelobjektet funktionalitet.

Några exempel på vanliga komponenter:

* **Transform:** Alla spelobjekt har en Transform-komponent som talar om objektets position, rotation och skalning.
* **Colliders:** Finns i olika varianter (box, sphere etc) och är olika för 2d och 3d-fysik (t.ex. BoxCollider2D). Funkar som hit boxes; ger en enkel volym eller 2d-yta som används för att känna av kollisioner. Colliders kan göras till triggers och påverkar då inte varandra i fysikmotorn; annars används colliders för att göra så saker kan hindra varandras förflyttning som fysiska objekt.
* **RigidBody, RigidBody2D:** Används för att tala om för fysikmotorn att objektet ska omfattas av fysiksimuleringen – man kan t.ex. ange objektets massa och via kod addera kraft i valfri riktning med hjälp av objektets rigidbody-komponent.
* **MeshRenderer, SpriteRenderer:** Används för att ge objektet ett utseende – MeshRenderer använder en 3d-modell som renderas ut på skärmen medan SpriteRenderer använder en 2d-bild.

## Komponentmenyn

Klicka på ![](<.gitbook/assets/image (20).png>) till höger om komponentens namn för att ta fram komponentmenyn.

* **Reset** återställer komponenten till dess utgångläge. För en Transform-komponent betyder det till exempel att position och rotationsvärdena blir 0 och skalningsvördena blir 1.
* **Copy Component** kopierar komponenten till minnet.
* **Paste Component As New** lägger in en ny kopia av komponenten i minnet till spelobjektet.
* **Paste Component As Values** fungerar bara om komponenten i minnet är av samma typ som den vars meny klickades på. Då ändras den klickade komponentens värden till att bli samma som komponenten i minnets.

## Presets

Presets är assets som innehåller färdiga uppsättningar värden för en komponent. ![](<.gitbook/assets/image (13).png>) öppnar listan med presets, och där finns också en "Save current to…"-knapp för att spara komponentens nuvarande variabelvärden till en preset.

Detta är användbar när man vill kunna återanvända en komponents variabelvärden till andra, framtida objekt som har samma komponent.
