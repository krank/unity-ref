# Deployment\*

## Deployment till riktig hårdvara eller emulator

För att kunna kompilera och föra över projekt till en HoloLens 2 eller emulatorn, behövs Visual Studio 2019 eller 2022. De tar en hel del utrymme: räkna med **mellan 18.5 och 20.5 gb**!

* Behövs: C++ Desktop och UWP
* Obs: ta med C++ v143 i UWP-paketet.

Dessutom behövs **Universal Windows Platform support** i Unity – **ytterligare c:a 2 gb**.

Windows måste också vara inställt till Developer Mode (Settings→System→For Developers)

### Unity

* Mixed Reality → Project Validation Settings → Hololens 2 Application (UWP)
* Project Validation (XR Plug-in Management)
  * "Fix all"
  * "At least one interaction prodile must be added"
    * Player Settings -> OpenXR -> UWP -> Interaction Profiles -> Microsoft Hand Interaction Profile
  * "The speech interactor needs to be active and enabled"
    * Aktivera MRTK Speech-komponenten i MRTK-riggen
  * "For controller models to show up…"
    * Ignorera, eller lägg till com.unity.cloud.gltfast via Package Manager
* Build -> till egen mapp (skapa en!)

### Visual Studio

* När processen är klar: Gå till mappen, öppna SLN-filen
* (Om det inte redan är fetmarkerat: Universal Windows-projektet -> Högerklick, Set as Startup Project)
* Release, ARM64, Remote machine
* Project -> Properties -> Debugging -> Machine Name (IP)
  * (Om Hololensen är på och på samma nätverk bör man kunna anvönda Locate istf att skriva in IP-numret)
* Build -> Deploy Solution
* \~2–6min för att kompilera (Snabbare efter första gången)
* PIN
* \~3-5min för att överföra

[https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/build-and-deploy-to-hololens](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/build-and-deploy-to-hololens)

[https://docs.microsoft.com/en-us/windows/mixed-reality/develop/advanced-concepts/using-visual-studio?tabs=hl2](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/advanced-concepts/using-visual-studio?tabs=hl2)

### Hololens 2-emulator

Har man inte en riktig HoloLens 2 men vill pröva mer "på riktigt" än i Unitys simulering, finns [Hololens 2-emulatorn](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/advanced-concepts/using-the-hololens-emulator). Den kräver **c:a 12 gb** ledigt utrymme. Observera att Hyper-V måste vara aktiverat i Windows för att den ska fungera.
