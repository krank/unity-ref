# XR Toolkit\*

XR Toolkit är Unitys officiella sätt att arbeta med VR och liknande. Förhoppningsvis är det lite mer stabilt och långsiktigt än att köra med något fristående ramverk eller bibliotek, till exempel VRTK.

_De här instruktionerna bör fungera i Unity 2020.3 och senare, men bör fungera även med lite tidigare versioner._

**Termer**

* **VR-headset:** Den "hjälm" man sätter på huvudet för att se VR-världen.
* **VR-handkontroll:** De fysiska apparater man håller i respektive hand för att styra saker i VR-världen.

## Setup

Utgå från ett vanligt 3D-projekt.

Gå till [Package manager](../../andra-funktioner/package-manager.md) och installera paketen "XR Plugin Management" och "XR Interaction Toolkit". Tacka ja ifall Unity frågar om du vill byta till det nya input-systemet.

Under "XR Interaction Toolkit" finns två "Samples", "Starter Assets" och "XR Device Simulator". Lägg till åtminstone Starter Assets. XR Device Simulator lägger du till [om du tänker utveckla utan tillgång till ett VR-headset](device-simulator.md).

### Starter assets

För att förenkla för dig att bestämma vilka knappar på VR-kontrollerna som gör vad så finns färdiga kontroll-presets. Följer du nedanstående så kommer dessa presents användas som standard för nya VR-kontrollers som läggs in i scenen.

Gå till Assets och navigera till Samples > XR Interaction Toolkit > 2.0.1 > Starter Assets.

![](<../../.gitbook/assets/image (25).png>)

Fem av sakerna i mappen är Presets. Klicka på var och ett av dem och på "Add to … default" högst upp i Inspector.

![](<../../.gitbook/assets/image (15).png>)

Gå sedan till Edit->Project Settings och Preset Manager. Under ActionBasedController finns två kontroll-presets. Skriv in "left" i filter-rutan för den som heter XRI Default Left Controller, och "right" i filter-rutan för XRI Default Right Controller.

![](<../../.gitbook/assets/image (16).png>)

### Scen-setup

Det här behöver du göra i varje scen: Högerklicka i Hierarchy och välj XR och **XR Origin (Action based)**. Det lägger till själva bas-objektet som styr kameran och VR-kontrollerna. Om du redan har en main-kamera i scenen så läggs den in i XR Origin-objektet.

XR Origin kommer att fungera som mittpunkten som VR-trackingen utgår från. Placera den där du vill att spelaren ska börja, och tänk att den ligger på golvet mellan spelarens ben.

#### Input Action Manager

Något spelobjekt i scenen behöver ha en **Input Action Manager**-komponent. Skapa ett nytt objekt och lägg till en sådan, eller lägg till komponenten till din XR Origin.

{% hint style="info" %}
I Unitys nya Input-system bygger allt på "actions", som i princip är händelser som aktiveras av att spelaren gör något. Sedan knyter man konsekvenser till dessa actions – så när spelaren gör sin action så leder det till att en specifik sak händer. Det Input Action Manager&#x20;
{% endhint %}

I din Input Action Manager, lägg till **XRI Default Input Actions** från Starter Assets.

![](<../../.gitbook/assets/image (7) (1).png>)



#### Controller prefab

Om du vill kunna se var dina händer/kontroller är i VR så måste du själv bestämma hur de ska se ut. Du kan importera 3D-modeller du själv skapat eller hittat i Asset Store, eller bara skapa enkla lådor själv. Vad som helst fungerar så länge du kan skapa [prefabs ](../../begrepp.md#prefab)av dem.

![Ett exempel på väldigt enkel prefab](<../../.gitbook/assets/image (11).png>)

Du kan använda samma prefab för både vänster och höger VR-controller, eller ha olika.

Du bestämmer vilken prefab som ska användas för vilken hand genom att först gå till XR Origin -> Camera Offset i Hierarchy och markera den controller du vill välja prefab för.

![](<../../.gitbook/assets/image (6).png>)

I komponenten **XR Controller (Action-based)** finns, en bit ner, rubriken **Model** och därunder variabeln **Model Prefab**. Dra in din önskade prefab dit.

![](<../../.gitbook/assets/image (14).png>)
