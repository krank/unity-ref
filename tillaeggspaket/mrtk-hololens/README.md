# MRTK (HoloLens 2)

## Färdigt grundprojekt

Här finns färdiga projekt att utgå från, med all setup redan fixad. Välj projektet som matchar din Unity-version:

* [Unity 2020.3.23](https://github.com/mikael-bergstrom-ntisthlm/MRTK-base-2020) (MRTK 2.7.2, OpenXR)
* [Unity 2019.4.32](https://github.com/mikael-bergstrom-ntisthlm/MRTK-base-2019) (MRTK 2.7.2, Legacy XR)

## Setup

Skapa ett nytt 3D-projekt i Unity.

{% hint style="warning" %}
**OBS:** det finns en bugg i Unity 2020.3.32 som krånglar till det med MRTK och Hololens2. Använd en tidigare eller senare version.
{% endhint %}

Ladda ner och packa upp [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).

Kör filen **MixedRealityFeatureTool.exe** för att starta verktyget. Tryck på **Start** och välj mappen ditt Unityprojekt ligger i. Klicka på **Discover Features**.

Kryssa i följande:   &#x20;

* Mixed Reality Toolkit
  * Mixed Reality Toolkit Foundation
  * Mixed Reality Toolkit Standard Assets
  * Mixed Reality Toolkit Tools
  * (Mixed Reality Toolkit Examples – om du vill ha några exempelscener etc)
* Platform Support
  * Mixed Reality OpenXR Plugin

Gå till Unity, och vänta på att de nya paketen ska laddas in. Unity kommer att fråga om editorn ska startas om och det nya input-systemet aktiveras. Tryck **Yes**.

![](<../../.gitbook/assets/image (19).png>)

När Unity startats om och projektet laddats in så startas **MRTK Project Configurator**. Ignorera den för tillfället och gå till menyn Mixed Reality -> Project -> Apply Recommended Project Settings for Hololens 2.

När du gjort det kommer MRTK project Configurator att se annorlunda ut än tidigare. Det kommer att stå något i stil med "**Important - for first time setup only**". Klicka Apply Settings och Next.

Nästa sida i Configurator låter dig välja vilka **Project Settings** och **UWP Capabilities** ditt projekt ska ha. Enklast är att bara lämna allt ikryssat. Tryck Next.

På nästa sida uppmanas du att importara **TMP Essentials**. TextMesh Pro är ett bra bibliotek för att få in text i Unityprojekt, som används av många MRTK-komponenter. Klicka på **Import TMP Essentials**.&#x20;

Därefter säger MRTK project Configurator att den är klar. Klicka **Done**.

Gå till Edit -> **Project Settings**. Klicka på **XR Plug-in Management**. Se om det finns någon varningstriangel bredvid OpenXR. Klicka i så fall på den. I rutan som dyker upp, tryck på "Fix All".

![](<../../.gitbook/assets/image (26).png>)

## Scen-setup

Gå till Mixed Reality -> Toolkit -> **Add to Scene and Configure**. Nu läggs tre objekt till i scenen:'

* **MixedRealityToolkit:** Objektet som funkar som nav för hela systemet, sköter alla inställningar etc.
* **MixedRealityPlayspace:** Objektet som sköter kameran – gör så att dess förflyttning blir relativt en viss punkt etc. Kameran här inne är utrustad med kod för att sköta t.ex. Gaze och att följa HoloLens-heaadsetets rörelser.
* **MixedRealitySceneContent:** Objekt för att placera saker relativt användarens perspektiv i scenen.

Markera MixedRealityToolkit-objektet. Se till så att **"DefaultHoloLens2ConfigurationProfile"** är vald i den översta dropdown-menyn i MixedRealityToolkit-komponenten.

![](<../../.gitbook/assets/image (25).png>)

Gå till Mixed Reality -> Project -> **Apply recommended scene settings for Hololens 2**.

Nu är projektet och scenen redo!

## Länkar

* [https://docs.microsoft.com/en-us/learn/paths/beginner-hololens-2-tutorials/](https://docs.microsoft.com/en-us/learn/paths/beginner-hololens-2-tutorials/)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/](https://docs.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/spatial-mapping-in-unity](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/spatial-mapping-in-unity?tabs=mrtk)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/design/scene-understanding](https://docs.microsoft.com/en-us/windows/mixed-reality/design/scene-understanding)

