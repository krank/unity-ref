# Deployment\*

## Deployment till riktig hårdvara eller emulator

För att kunna kompilera och föra över projekt till en HoloLens 2 eller emulatorn, behövs Visual Studio 2019 eller 2022. De tar en hel del utrymme: räkna med **mellan 18.5 och 20.5 gb**!

* Behövs: C++ Desktop och UWP
* Obs: ta med C++ v143 i UWP-paketet.

Dessutom behövs **Universal Windows Platform support** i Unity – **ytterligare c:a 2 gb**.

* Build Settings -> Universal Windows Platform
* Player Settings -> OpenXR -> UWP -> Interaction Profiles -> Microsoft Hand Interaction Profile
  * OpenXR Feature Groups -> Hand Tracking
* Build -> till egen mapp (skapa en!)
* Windows: Developer Mode
* När processen är klar: Gå till mappen, öppna SLN-filen
* Universal Windows-projektet -> Högerklick, Set as Startup Project
* Release, ARM64, Remote machine
* Project -> Properties -> Debugging -> Machine Name (IP)
* Build -> Deploy Solution
* \~2min för att kompilera
* PIN
* \~3-5min för att överföra

### Hololens 2-emulator

Har man inte en riktig HoloLens 2 men vill pröva mer "på riktigt" än i Unitys simulering, finns [Hololens 2-emulatorn](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/advanced-concepts/using-the-hololens-emulator). Den kräver **c:a 12 gb** ledigt utrymme. Observera att Hyper-V måste vara aktiverat i Windows för att den ska fungera.
