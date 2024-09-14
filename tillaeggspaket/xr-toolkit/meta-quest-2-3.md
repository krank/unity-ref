# Meta Quest 2/3

Material:

* Dator med Unity
  * För att testköra via kabel: c:a 4–500mb ledigt
  * För att kompilera och installera i headset: c:a 2–3 gb ledigt
* Meta Quest 2/3
* USB-C-kabel

## Testköra på Meta Quest med kabel

Oculus Link kan användas för att testköra VR-grejer direkt i headsetet utan att de behöver exporteras eller installeras. Link kan köras både trådat (med USB 3-kabel) och trådlöst (vilket kräver bra nätverk).

### Förberedelser

* Ladda ner och installera [Meta Quest Link](https://www.oculus.com/download\_app/?id=1582076955407037)-appen. (kräver c:a 400mb)
  * Starta appen, gå igenom dess start-procedur.
  * Inklusive att skapa eller logga in på ett Meta-konto.
* Unity
  * Se till så att du lagt till XR Plugin Management-paketet i [Package Manager](../../andra-funktioner/package-manager.md).
  * I Project Settings, gå till XR Plugin Management, kryssa i Oculus under PC-fliken.

### Kör

* Skapa ett VR-projekt.
* Ta bort XR Device Simulator ur scenen, eller stäng av den tillfälligt.
* Koppla in headsetet med USB-kabel.&#x20;
  * Du får nu troligen frågan om du vill aktivera Oculus Link. Svara ja.
  * Om du inte får frågan, gå in i Oculus' snabbmeny (klicka där klockan och ikoner för nätverk etc är) och välj Oculus Link
* Gå till Unity, testkör spelet med playknapen som vanligt.

## Bygga/exportera till Oculus Quest

### Förberedelser

{% hint style="danger" %}
**VIKTIGT:** Om scenen innehåller en [Device Simulator](device-simulator.md) – ta bort den eller deaktivera den! Om den är aktiv i scenen kommer ingenting att fungera när projektet körs i Oculusen.
{% endhint %}

#### Oculus Quest 2

* Starta headsetet.
* Gå till Settings->System->Developer. Aktivera USB Debugging.
* Koppla in headsetet via USB. Du bör få en dialogruta i headsetet som ber dig bekräfta att du vill ansluta via USB. Klicka "Allow".

#### Unity build tools

{% hint style="danger" %}
**VIKTIGT:** Använd **Unity 2022** (eller senare) för detta!
{% endhint %}

Starta Unity Hub och gå till **Installs**.

Klicka på kugghjulet bredvid din Unity-installation och välj **Add modules**.

Kryssa i **Android Build Support**, och både **Android SDK & NDK Tools** samt **OpenJDK**. Tryck Continue och vänta tills modulerna laddats ner och installerats. Det här behöver du bara göra en gång – Android-utvecklingsverktygen installeras på datorn, inte i något specifikt projekt.

![](<../../.gitbook/assets/image (8).png>)

Öppna ett projekt och gå till Edit -> Preferences och klicka på External Tools. Dubbelkolla så att alla rutor under Android är ifyllda och att Unity därmed hittat alla verktyg.

#### Unity build settings

Gå till File -> Build Settings. Välj Android som Platform. Glöm inte att trycka på Switch Platform.

Välj Quest 2-headsetet som "Run device". Om du inte ser headsetet i listan – testa koppla ur det och sedan koppla i det igen, och se till så att det är påslagen och att det inte visar någon dialogruta som väntar på input. Tryck "Refresh".

### Unity project settings

Se till så att du lagt till XR Plugin Management-paketet i [Package Manager](../../andra-funktioner/package-manager.md).

Gå till Edit -> Project Settings. Klicka på **XR Plugin Management**. Klicka på Android-fliken (den till höger) och kryssa i Oculus.

![](<../../.gitbook/assets/image (4) (1) (1).png>)

Gå till **Player**, även här Android-fliken, och gå ner till och expandera rubriken **Other Settings**.

![](<../../.gitbook/assets/image (22).png>)

Gå ner till underrubriken **Identification** och dubbelkolla så att **Minimum API Level** är API Level 23 (Android 6.0).

![](<../../.gitbook/assets/image (3) (1) (1) (1).png>)

Nu är projektet redo att deployas och köras på en Quest 2.

## Build and run

Gå till File -> Build settings och dubbelkolla så att Quest 2-headsetet är valt som Run Device.

Tryck på "Build And Run".

Välj en mapp att lägga den kompilerade versionen av projektet i. Skapa gärna en ny mapp; lägg den inte direkt i projektmappen.

Den kompilerade versionen av projektet kommer att vara en APK-fil, vilket är Androids standardformat för program som kan installeras. Unity använder sedan automatiskt Android-utvecklingsverktygen för att föra över APK-filen till headsetet och installera den. Därefter körs den också automatiskt.

Därefter finns programmet installerat under "Unknown sources" i Questens app-meny.

