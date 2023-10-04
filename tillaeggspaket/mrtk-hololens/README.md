# MRTK (HoloLens 2)

## Färdigt grundprojekt

Här finns färdiga projekt att utgå från, med all setup redan fixad. Välj projektet som matchar din Unity- och Hololensversion:

**Hololens 2:**

* [MRTK3\_BASE\_HL2\_2021](https://github.com/mikael-bergstrom-ntisthlm/MRTK3\_BASE\_HL2\_2021) (MRTK 3, Unity 2021.3.26)
* [MRTK\_BASE\_HL2\_2020](https://github.com/mikael-bergstrom-ntisthlm/MRTK\_BASE\_HL2\_2020) (MRTK 2.x, Unity 2020)

**Hololens 1 (ej uppdaterade):**

* [Unity 2020.3.23](https://github.com/mikael-bergstrom-ntisthlm/MRTK-base-2020) (MRTK 2.7.2, OpenXR)
* [Unity 2019.4.32](https://github.com/mikael-bergstrom-ntisthlm/MRTK-base-2019) (MRTK 2.7.2, Legacy XR)

## Manuell setup (MRTK 3.x)

Installera [UWP-modulen](../../kompilera-och-distribuera.md#uwp) till Unity

Skapa ett nytt 3D-projekt i Unity.

{% hint style="warning" %}
**OBS:** det finns en bugg i Unity 2020.3.32 som krånglar till det med MRTK och Hololens2. Använd en tidigare eller senare version.
{% endhint %}

Ladda ner och packa upp [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).

Kör filen **MixedRealityFeatureTool.exe** för att starta verktyget. Tryck på **Start** och välj mappen ditt Unityprojekt ligger i. Klicka på **Discover Features**.

Kryssa i följande:

* Platform Support
  * Mixed Reality OpenXR Plugin
* Spatial Audio
  * Microsoft Spatializer
* MRTK3
  * MRTK Input
  * MRTK UX Components

Gå till Unity, och vänta på att de nya paketen ska laddas in. Unity kommer att fråga om editorn ska startas om och det nya input-systemet aktiveras. Tryck **Yes**.

![](<../../.gitbook/assets/image (19).png>)

Unity kommer att fråga ifall du vill uppdatera dina XR InteractionLayer Masks. Välj **No thanks**.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

Mixed Reality -> Project -> Apply recommended project settings for Hololens 2

* Project Settings
  * MRTK3
    * Assign MRTK Default
  * XR Plug-in management
    * Windows, Mac, Linux
      * OpenXR
      * Windows Mixed Reality Feature Group
    * UWP
      * OpenXR
      * Microsoft Hololens Feature Group
    * OpenXR Project Validation
      * Fix All för så många som möjligt
      * Spatializer
  * OpenXR
    * Interaction Profile
      * Eye Gaze Interaction Profile&#x20;
      * Microsoft Hand Interaction Profile&#x20;
      * Microsoft Motion Controller Profile

### Scen-setup

Sök i Assets efter prefaben **MRTK XR Rig**. Om du inte hittar den, se till så att din sökning är i **Packages**, inte i Assets. Lägg till en instans av den i scenen.

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Sök också efter **MRTKInputSimulator**. Lägg till en instans av den också.

## Länkar

* [https://docs.microsoft.com/en-us/learn/paths/beginner-hololens-2-tutorials/](https://docs.microsoft.com/en-us/learn/paths/beginner-hololens-2-tutorials/)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/](https://docs.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/spatial-mapping-in-unity](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/spatial-mapping-in-unity?tabs=mrtk)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/design/scene-understanding](https://docs.microsoft.com/en-us/windows/mixed-reality/design/scene-understanding)

