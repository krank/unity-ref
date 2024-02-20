# MRTK3 (HoloLens 2)

## Färdigt grundprojekt

Här finns färdiga projekt att utgå från, med all setup redan fixad. Välj projektet som matchar din Unity- och Hololensversion:

**Hololens 2:**

* [MRTK3\_BASE\_HL2\_2021](https://github.com/mikael-bergstrom-ntisthlm/MRTK3\_BASE\_HL2\_2021) (MRTK 3, Unity 2021.3.26)

## Manuell setup

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

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Gitignore

Lägg till följande två rader till din gitignore:

```gitignore
# Hololens WSA test certificate
/[Aa]ssets/WSATestCertificate.pfx
```

WSATestCertificate.pfx är en fil som skapas i samband med att man testar projektet mot en riktig Hololens, men bör inte laddas upp till t.ex. Github.

### Project settings

Gå till Project settings.

Under **MRTK3**, klicka på **Assign MRTK Default.**

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

Under **XR Plug-in Management** finns flikar för olika plattformar. Under fliken för "Windows, Mac, Linux settings", kryssa i:

* Initialize XR on Startup
* OpenXR
* Windows Mixed Reality feature group

Under fliken för "Universal Windows Platform settings" (om du har den), kryssa i:

* OpenXR
* Microsoft HoloLens feature group

Under **Project Validation**, klicka "Fix all" under både "Windows, Mac, Linux settings" och "Universal Windows Platform settings" (om du har den).

Under **OpenXR**, under "Enabled Interaction Profiles", lägg till "Eye Gaze Interaction Profile", "Microsoft Hand Interaction Profile" och "Microsoft Motion Controller Profile".

<figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

### Scen-setup

Sök i Assets efter prefaben **MRTK XR Rig**. Om du inte hittar den, se till så att din sökning är i **Packages**, inte i Assets. Lägg till en instans av den i scenen.

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Sök också efter **MRTKInputSimulator**. Lägg till en instans av den också.

## Länkar

* [https://docs.microsoft.com/en-us/learn/paths/beginner-hololens-2-tutorials/](https://docs.microsoft.com/en-us/learn/paths/beginner-hololens-2-tutorials/)

### MRTK2 (gamla)

* [https://docs.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/](https://docs.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/spatial-mapping-in-unity](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/spatial-mapping-in-unity?tabs=mrtk)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/design/scene-understanding](https://docs.microsoft.com/en-us/windows/mixed-reality/design/scene-understanding)

