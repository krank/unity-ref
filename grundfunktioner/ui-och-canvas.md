# UI och Canvas\*

## Canvas

Canvas betyder målarduk, och det är Canvas-objektet som samlar alla UI-element när man använder Unitys vanliga system för att skapa gränssnitt. Genom att lägga in bilder, knappar och andra element i Canvasen så blir de spelets gränssnitt.

### Canvas screen space

Canvas-objektet har samma proportioner som spelfönstret, och oavsett objektets storlek så projiceras objektet som helhet ovanpå spelkamerans vy när man spelar spelet. Canvasen skalas alltså så att dess kanter läggs precis på kamerans kanter.

När man normalt skapar en Canvas så är denna _jättestor_ i scenvyn. Det beror på att den har Render Mode **Screen Space: Overlay**. Då är canvasobjektets storlek frikopplad från kamerans storlek i scene view, vilket fungerar ganska bra för 3D-spel.

För 2D-spel, framför allt sådana som bara har en kamera, passar det ofta bättre att använda **Screen Space: Camera** som Render Mode. Det ställs in i Canvas-komponenten. Då behöver man också ange vilken kamera canvasen ska anpassa sig efter.

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Rect transform

En rect transform har fler delar än en vanlig transform.

* **Anchor** avgör hur ett UI-objekt ska positioneras. Anchor har Min X/Y och Max X/Y. Alla får från 0 till 1, där 0 är längst ner till vänster och 1 är högst upp till höger. Detta är relativt objektet som rect transformens objekt befinner sig i, så ett objekt som ligger i canvasen använder canvasen som utgångspunkt.
  * _Min Y och Max Y är likadana:_ använd Pos Y och Height på Y-led.
    * Pos Y bestämmer hur långt från Min/Max Y som objektet befinner sig.
    * Height bestämmer höjden på objektet.
  * _Min Y och Max Y är olika:_ använd Top och Bottom på Y-led.
    * Top bestämmer hur långt från Min Y som objektets övre del är.
    * Bottom bestämmer hur långt från Max Y som objektets nedre del är.
  * Min X och Max X fungerar på samma sätt.
    * De är olika: använd Pos X och Width.
    * De är lika: använd Left och Right.
* **Pivot** avgör var på objektet dess koordinater ska räknas från. Det gäller framför allt om Pos X eller Pos Y ska användas. Pivot X 0 och Y 0 innebär att det är objektets nedre vänstra hörn man bestämmer position för. X 1 och Y 1 innebär att det är objektets övre högra hörn man bestämmer position för.

Några exempel på hur man uppnår olika saker med ovanstående system:

* Objektet är lika stort som skärmen
  * Anchor Min X/Y 0, Max X/Y 1
  * Left/Right/Top/Bottom 0
* Objektet upptar hela vänsterkanten och är 300 pixlar brett
  * Anchor Min Y 0, Max Y 1
  * Anchor Min/Max X 0
  * Top/Bottom/Pos X 0
  * Width 300
* Objektet ligger i mitten längst ner på skärmen och är 500 pixlar brett och 100 högt
  * Anchor Min/Max X 0.5
  * Anchor Min/Max Y 0
  * Width 300, Height 100

### Genvägar

Längst upp till vänster i Rect Transform finns en grafisk ruta. Klickar på den fr man fram ett rutnät med 4x4 rutor och tillhörande rad- och kolumnrubriker.&#x20;

## Knappar

(Kommer…)

## Events

(Kommer…)
