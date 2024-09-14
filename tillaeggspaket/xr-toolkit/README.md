# XR Toolkit

_Uppdaterat för XR Toolkit 2.6.3_

XR Toolkit är Unitys officiella sätt att arbeta med VR och liknande. Förhoppningsvis är det lite mer stabilt och långsiktigt än att köra med något fristående ramverk eller bibliotek, till exempel VRTK.

_De här instruktionerna har testats i Unity 2022.3 men bör fungera även med lite tidigare versioner._

**Termer**

* **VR-headset:** Den "hjälm" man sätter på huvudet för att se VR-världen.
* **VR-handkontroll:** De fysiska apparater man håller i respektive hand för att styra saker i VR-världen.

## Setup

Utgå från ett vanligt 3D-projekt.

Gå till [Package manager](../../andra-funktioner/package-manager.md) och installera paketen "XR Plugin Management" och "XR Interaction Toolkit" (version 2.6.3 eller nyare) från Unity Registry. Tacka ja ifall Unity frågar om du vill byta till det nya input-systemet.

{% hint style="info" %}
Om XR Interaction Toolkit 2.6.3 inte finns i Unity Registry-listan, klicka på plustecknet uppe till höger, "Add package by name" och skriv in **com.unity.xr.interaction.toolkit** som name och **2.6.3** som version.
{% endhint %}

När du lägger till paketet kommer Unity att fråga om du vill aktivera det nya input-systemet. Tacka ja. Det kommer att innebära att Unity-editorn startas om.

Du kan nu också få en varning om att "XR InteractionLayerMask Update Required". Den uppdateringen behöver du bara göra om du uppgraderar ett äldre VR-projekt, så du kan med gott samvete klicka "No Thanks".

Under "XR Interaction Toolkit" finns flera "Samples". Lägg till (importera) **Starter Assets**. **XR Device Simulator** lägger du till [om du tänker utveckla utan tillgång till ett VR-headset](device-simulator.md).

### Enkel scen-setup

Ta bort din Main Camera från scenen.

Sök i Assets efter "xr origin" och dra ut en instans av **XR Origin (XR Rig)** till scenen. Den prefaben finns annars i mappen Samples→XR Interaction Toolkit→\[version]→Starter Assets→Prefabs. Fördelen med att använda denna prefab är att man får med nästan allt man behöver direkt från början. Nackdelen är att man kanske inte gillar hur det fungerar…

Den kommer att fungera som mittpunkten som VR-trackingen utgår från. Placera den där du vill att spelaren ska börja, och tänk att den ligger på golvet mellan spelarens ben.

Lägg till en **Input Action Manager**-komponent till XR Origin-objektet i scenen. Lägg till **XRI Default Input Actions** till dess lista.

Lägg in en **XR Interaction Manager** i scenen (Högerklicka i hierarkin, XR → Interaction Manager).

{% hint style="info" %}
**OBSERVERA:** I prefab-versionen av XR Origin (XR Rig) används interaction layers för att skilja områden man ska kunna teleportera till från sådana man inte ska kunna teleportera till.

För att det ska fungera **måste interaction layer nummer 31 finnas och vara namngivet**. Eller så får man manuellt gå in och ändra vilket lager som ska användas.

Gå till valfri XR Interactor, till exempel den i XR Origin (XR Rig)→Camera Offset→Left Controller→Teleport Interactor. Leta rätt på "Interactor Layer Mask". Klicka på den och välj "Add layer…". I listan, ge lager 31 ett namn.
{% endhint %}

## Rekommenderade justeringar

XR Origin-riggen har ett par standardgrejer som kan upplevas som jobbiga eller opassande för många vana VR-användare – t.ex. har den inte bara teleportation inbyggd utan också åksjukekontroller (möjligheten att flytta sig i VR-världen genom att dra i vänster handkontrolls styrspak). Den har också strålar som utgår från båda handkontrollerna kontinuerligt och som kan användas för att interagera med saker i spelvärlden, där standard snarare är att man bara kan interagera med saker man kan röra vid.

* För att stänga av åksjuke-kontrollerna: Gå in under **XR Origin (XR Rig) → Locomotion Systems** och ta bort eller stäng av child-objektet **Move**.
* För att stänga av fjärrmanipulering: Gå in under **XR Origin (XR Rig) → Camera Offset → Left Controller** och plocka bort child-objektet **Ray Interactor.**

## Manuell scen-setup

De här instruktionerna ger dig en mer avskalad setup – du måste själv lägga in locomotion och annat.

Ta bort scenens Main Camera.

Lägg in en **XR Interaction Manager** i scenen (GameObject → XR → Interaction Manager).

Lägg in en **XR Origin** i scenen (GameObject → XR → XR Origin (VR)).

Expandera XR Origin och dess Camera Offset och markera LeftHand Controller. Klicka på "Select Preset" (<img src="../../.gitbook/assets/image (7).png" alt="" data-size="line">) och välj **XRI Default Left Controller**. Gör samma sak för RightHand Controller, men där väljer du **XRI Default Right Controller**.



