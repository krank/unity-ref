# Interaktion

I VR-sammanhang är "interaktion" specifikt när VR-utrustningen interagerar med den virtuella miljön. Till exempel är en VR-handkontroll används för att plocka upp något eller trycka på en knapp.

## XR Interaction Manager

Om du tänkt ha någon form av interaktion i din scen så behöver också något objekt ha en **XR Interaction Manager**-komponent. Lägg till den i XR Origin eller skapa ett helt nytt objekt som bara innehåller komponenten genom att högerklicka i Hierarchy och välja XR och Interaction Manager.

## Controllers

XR-controllers kan ha två olika typer av interaktion: **ray interaction** och **direct interaction**. Varje handkontrolls-objekt kan normalt bara ha komponenter för en av dem, så om man vill kombinera behövs en workaround – se [teleportation ](teleportation.md)för ett exempel.

Objekten som motsvarar dina VR-handkontroller finns i din XR Origin, under Camera Offset.

![](<../../.gitbook/assets/image (20) (1).png>)

### Ray interaction

Vid ray interaction så skjuter långa "strålar" ut från VR-handkontrollerna och föremål som träffas av strålarna kan handkontrollerna interagera med. Till exempel kan man då plocka upp föremål på distans genom att sikta på dem med strålarna och trycka på en knapp på controllern.

Som minst behöver VR-handkontrolls-objektet som ska använda ray interaction en **XR Ray Interactor**-komponent. Normalt lägger man också till en **XR Interactor Line Visual**-komponent som för att strålen som skjuter ut syns. Då läggs också en Line Renderer-komponent till automatiskt.

När XR Origin-objektet skapas så ges båda VR-handkontrollerna de komponenter som behövs för ray interaction.

### Direct interaction

Vid direct interaction måste VR-handkontrollen fysiskt röra vid målobjektet för att interaktion ska kunna se. Då kan man inte interagera med saker på distans utan måste vara nära dem.

Lägg till en **XR Direct Interactor**-komponent till det VR-handkontroll-objektet som ska använda direct interaction. Lägg också till en Sphere Collider (Trigger); den kommer att användas för att känna av kollisionen mellan interactorn och objekten.

### Interaction layer mask

Oavsett om det gäller ray interaction eller direct interaction kan **interaction layers** användas för att bestämma vilka objekt som ska kunna interageras med. Interaction layers fungrar ungefär som vanliga [lager](../../lager-och-taggar.md).&#x20;

Både XR Ray Interactor och XR Direct Interactor-komponenterna har en **Layer Interaction Mask**-variabel.

![](<../../.gitbook/assets/image (17) (1).png>)

Precis som med vanliga lager används Add Layer för att skapa nya lager. Se till så att bara de lager just denna interactor ska kunna interagera med är förkryssade. Detta blir extra viktigt om du vill ha olika sorters interactors för [teleportation ](teleportation.md)och att plocka upp föremål.

## Föremål som kan interageras med

För att göra så att ett objekt kan interageras med, behöver det en Interactable-komponent. Det finns flera olika.

<table><thead><tr><th width="194">Komponent</th><th>Beskrivning</th></tr></thead><tbody><tr><td>XR Grab Interactable</td><td>Objekt som kan plockas upp genom att man trycker på Grab-knappen</td></tr><tr><td>XR Simple Interactable</td><td>Enklast möjliga: objektet kan interageras med men saknar inbyggd funktionalitet.</td></tr><tr><td>XR Socket Interactable</td><td>Objekt som andra objekt kan sättas fast på. En mer detaljerad genomgång finns t.ex. <a href="https://www.youtube.com/watch?v=rRNvq09Itdw">här</a>.</td></tr></tbody></table>

Objektet behöver också en collider av något slag, och antagligen en RigidBody. Fysik-systemet används för att avgöra om objektet kolliderar med en VR-handkontroll eller med en stråle från ray interaction.

### Reagera visuellt

En **XR Tint Interactable Visual**-komponent gör att objektet får en tydlig visuell indikation på att det är det nuvarande målet för interaktionen.

### Reagera med kod

Objekt som har någon form av Interactable-komponent kommer att ha ett antal Interactable Events som kan knytas till specifika metoder i kod – precis som events i [det vanliga UI-systemet](../../grundfunktioner/ui-och-canvas.md#events).

I listan är det mesta ganska självförklarande, men det finns tre viktiga begrepp:

* **Hover** betyder att spelaren markerat objektet med en stråle (ray interactor) eller en VR-handkontroll (direct interactor).
* **Select** betyder att spelaren tryckt på **grepp-knappen** på sin VR-handkontroll. Man kan ändra vilken knapp som gör "select" om man vill.
* **Activate** betyder att spelaren tryckt på **trigger-knappen** på sin VR-handkontroll. Man kan ändra vilken knapp som gör "activate" om man vill.

I exemplet nedan aktiveras metoden **DoSomething** i **CapsuleController**-scriptet som finns i objektet **Capsule** när spelaren **markerat** objektet med antingen sin stråle (ray interactor) eller sin VR-handkontroll (direct interactor)

![](<../../.gitbook/assets/image (13) (1).png>)

