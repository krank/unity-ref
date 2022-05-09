# MRTK (HoloLens 2)\*

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

När Unity startats om och projektet laddats in så startas MRTK Project Configurator. Ignorera den för tillfället och gå till menyn Mixed Reality -> Project -> Apply Recommended Project Settings for Hololens 2.

När du gjort det kommer MRTK project Configurator att se annorlunda ut än tidigare. Klicka på "Apply".

* Skapa 3D-projekt i Unity
* Ladda ner & packa upp Microsoft Mixed Reality Feature Tool
*

## Simulering

## Scen-setup

## Enkel interaktivitet

## Komplex interaktivitet

## Spatial awareness

## Manuell setup



## Länkar

* [https://docs.microsoft.com/en-us/learn/paths/beginner-hololens-2-tutorials/](https://docs.microsoft.com/en-us/learn/paths/beginner-hololens-2-tutorials/)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/](https://docs.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/spatial-mapping-in-unity](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/spatial-mapping-in-unity?tabs=mrtk)
* [https://docs.microsoft.com/en-us/windows/mixed-reality/design/scene-understanding](https://docs.microsoft.com/en-us/windows/mixed-reality/design/scene-understanding)



* Grundkoncept
  * Pekare
  * Luftklick
* Setup
  * Unity: projektet gjort i 2019.4
    * Unity: MixedRealityToolkit
      * Mixed Reality Feature Tool
    * (Emulator)
    * (Visual Studio, UWP och C++)
* Scen-setup
  * Mixed Reality Toolkit -> Add to scene and configure
  * DefaultHololens1ConfigurationProfile
* Konfigurationer
  * Och konfigurationer i konfigurationer
* Enkel interaktivitet
  * Near Interaction Grabbable
  * Object Manipulator
* Mer komplicerad interaktivitet
  * Klickbara objekt
  * Händerna
    * Transform
* Spatial mapping
* Simulering
* Deployment

