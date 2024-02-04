# ProBuilder

ProBuilder gör att man kan bygga enkel 3D-geometri snabbt direkt i Unity-editorn istället för att bygga saker i ett 3D-program som Blender och sedan importera därifrån.

## Komma igång

* Använd [Package Manager](../andra-funktioner/package-manager.md) för att lägga till **ProBuilder** från Unity Registry.
* Skapa en ny **ProBuilder Cube**, eller lägg till en ProBuilder MeshFilter-komponent till ett existerande projekt.
* Klicka på **Open ProBuilder** i ProBuilder MeshFilter-komponenten.

## Grundläggande manipulering

ProBuilder har fyra grundläggande redigeringslägen – object, vertex, edge och face.

![](<../.gitbook/assets/image (9).png>)

Beroende på vilket läge man är i, så är det olika saker som markeras när man klickar på dem och som sedan kan flyttas, roteras och skalas.

* **Object:** Hela objektet.
* **Face:** En "sida" av objektet.
* **Edge:** En "kant" av objektet.
* **Vertex:** En av objektets "punkter".

Grundtanken här är alltså att ett objekt egentligen består av ett antal punkter i 3d-rymden. Punkterna är ihopkopplade med linjer – "kanter" – och mellan linjerna uppstår ytor – "sidor".

## Andra verktyg

ProBuilder innehåller också en stor verktygslåda med mer avancerade verktyg för att ändra på och skapa nya 3d-former. Vilka verktyg som syns beror på vilket läge ProBuilder är i. Några exempel nedan:

### New shape (Alla lägen)

Skapar en ny 3d-form. Klocka på plus-knappen för att få fram en ny ruta där man kan välja mellan olika förbestämda former, t.ex. kub, cylinder, trappa etc.

### Export (Alla lägen)

Gör att man kan spara geometrin man skapat i ett format som 3d-program som t.ex. Böender kan läsa. Därmed kan man börja med att skapa en enkel version av en level i Unity, och sedan skapa snyggare och mer detaljerad eller stiliserad grafik till den i ett 3d-program med Unitys grundgeometri som bas.

### Extrude face (Face-läget)

"Drar ut" den markerade ytan och skapar ny geometri av den.

