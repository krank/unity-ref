# Importera grafik\*

Att få in grafik till Unity är ganska lätt. Det finns två sätt:

* Spara bilder och 3d-modeller direkt i Unity-projektets **Assets-mapp**. Då importas de automatiskt av Unity.
* Importera dem genom att dra in dem till Assets-delen av gränssnittet eller använda **Asset → Import new asset**.

Beroende på originalens filformat så skapar Unity någon form av "Asset" kring det, till exempel en Texture2D för bilder.

## Texture2D

En texture2D är helt enkelt en bild. Hur bilden ska användas bestäms genom att man väljer "texture type" i inspectorn.

<figure><img src="../.gitbook/assets/image (4) (3).png" alt=""><figcaption></figcaption></figure>

De vanligaste texturtyperna är:

* **Default** – Texturen agerar som en vanlig 3D-textur, som används för att ge ett 3D-objekt en grafisk yta. Kräver sällan några speciella inställningar.
* **Sprite (2D and UI)** – Texturen agerar som en "sprite"; en egen, fristående, tvådimensionell bild som visas i spelet utan att behöva någon 3d-modell.

### Sprite

{% hint style="info" %}
**OBSERVERA:** I nyare versioner av Unity, eller i 3D-projekt, kan du behöva installera paketet "2D Sprite" via [Package manager](../andra-funktioner/package-manager.md) för att ha tillgång till Sprite editor-fönstret.
{% endhint %}

För sprites finns tre "Sprite modes":

* **Single** – Bilden innehåller en sprite.
* **Multiple** – Bilden innehåller en eller flera sprites, och de ska delas in genom rektanglar.
* **Polygon** – Bilden innehåller en eller flera sprite, och de ska delas in genom mer komplexa former (polygoner)

För att redigera rektanglarna eller polygonerna används **Sprite editor**-fönstret.

Klicka på den här knappen för att öppna det fönstret: ![](<../.gitbook/assets/image (6).png>)

\[BILD HÄR: Single/Multiple/Polygon]

#### Pixels per unit

En sprite består alltid av ett antal pixlar i bredd och höjd. Pixels per unit bestämmer hur många pixlar som ska motsvara en unity-enhet när objektets Scale är 1.0. Skriver man 32 i den rutan så kommer alltså en sprite på 32×32 pixlar att uppta en hel unity-enhet i bredd och höjd.

Högre siffror här ger alltså lägre storlek.

\[BILD HÄR: 32×32 @ 32, 64, 16]

### Sprite sheets

På ett sprite sheet finns flera olika bilder till spelet på samma bild, Ofta brukar man ha ett sprite sheet per karaktär, eller till och med ett sprite sheet per animation

\[BILD HÄR: Ett enkelt sprite sheet]

För sprite sheets i Unity används normalt sett Sprite mode: Multiple. I Sprite editorn kan man då använda Slice-funktionen för att automatiskt dela in bilden i mindre delar. Man väljer att dela in den efter hur stor varje bild ska vara eller hur många bilder det ska vara i bredd respektive höjd.

\[BILD HÄR: Slice]

(Mer kommer…)

### Pixelart och texturer

Importen för bilder är anpassad för högupplösta texturer, vilket betyder att de fokuserar på komprimering och snabbhet snarare än precision. När man jobbar med pixelart funkar inte det – då måste man ändra lite inställningar

(Mer kommer…)

## 3D-modeller
