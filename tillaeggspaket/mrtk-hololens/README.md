# MRTK (HoloLens 2)\*

**\[UNDER UPPBYGGNAD]**

## Grundkoncept

### Pekare

### Klick/luftklick

## Färdigt grundprojekt

Här finns färdiga projekt att utgå från, med all setup redan fixad. Välj projektet som matchar din Unity-version:

* [Unity 2020.3.23](https://github.com/mikael-bergstrom-ntisthlm/MRTK-base-2020) (MRTK 2.7.2, OpenXR)
* [Unity 2019.4.32](https://github.com/mikael-bergstrom-ntisthlm/MRTK-base-2019) (MRTK 2.7.2, Legacy XR)

## Simulering

## Scen-setup

## Enkel interaktivitet

## Komplex interaktivitet

## Spatial awareness

## Manuell setup



## Deployment till riktig hårdvara eller emulator

För att kunna kompilera och föra över projekt till en HoloLens 2 eller emulatorn, behövs Visual Studio 2019 eller 2022. De tar en hel del utrymme: räkna med **mellan 18.5 och 20.5 gb**!

* Behövs: C++ Desktop och UWP
* Obs: ta med C++ v142 i UWP-paketet.

Dessutom behövs **Universal Windows Platform support** i Unity – **ytterligare c:a 2 gb**.

* Build Settings -> Universal Windows Platform
* Player Settings -> OpenXR -> UWP -> Interaction Profiles -> Microsoft Hand Interaction Profile
  * OpenXR Feature Groups -> Hand Tracking
* Build -> till egen mapp (skapa en!)
* När processen är klar: Gå till mappen, öppna SLN-filen
* (köra projektet)



### Hololens 2-emulator

Har man inte en riktig HoloLens 2 men vill pröva mer "på riktigt" än i Unitys simulering, finns [Hololens 2-emulatorn](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/advanced-concepts/using-the-hololens-emulator). Den kräver **c:a 12 gb** ledigt utrymme. Observera att Hyper-V måste vara aktiverat i Windows för att den ska fungera.

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

