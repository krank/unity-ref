# Komponenter

Alla spelobjekt i Unity består av ett antal komponenter. Varje komponent är en instans av en komponentklass, och alla komponentklasser har olika inbyggda variabler och metoder som ger komponenten och spelobjektet funktionalitet.

Några exempel på vanliga komponenter:

* **Transform:** Alla spelobjekt har en Transform-komponent som talar om objektets position, rotation och skalning.
* **Colliders:** Finns i olika varianter (box, sphere etc) och är olika för 2d och 3d-fysik (t.ex. BoxCollider2D). Funkar som hit boxes; ger en enkel volym eller 2d-yta som används för att känna av kollisioner. Colliders kan göras till triggers och påverkar då inte varandra i fysikmotorn; annars används colliders för att göra så saker kan hindra varandras förflyttning som fysiska objekt.
* **RigidBody, RigidBody2D:** Används för att tala om för fysikmotorn att objektet ska omfattas av fysiksimuleringen – man kan t.ex. ange objektets massa och via kod addera kraft i valfri riktning med hjälp av objektets rigidbody-komponent.
* **MeshRenderer, SpriteRenderer:** Används för att ge objektet ett utseende – MeshRenderer använder en 3d-modell som renderas ut på skärmen medan SpriteRenderer använder en 2d-bild.
