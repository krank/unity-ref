# Sprite editor\*

Sprite Editor-fönstret används för att bestämma saker om en sprite. Förutom vilken textur som ska ligga till grund för spriten behöver Unity nämligen veta till exempel hur den ska delas upp (för spritesheets och tilesets), hur dess kollisions-form ska vara och var dess pivot ska befinna sig.

## Slicing

Spritesheets och tilesets är båda exempel på när man packat in flera bilder i en bildfil. I ett spritesheet samlas alla bildrutor för en eller flera animationer på samma bild. I ett tileset samlas istället alla unika rutor som används för att rita upp en [tilemap](../../andra-funktioner/tilemaps.md).

Se till att "Sprite Mode" är Multiple i texturens import settings innan du börjar arbeta i sprite editorn.

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

För att börja dela upp bilden klickar man på Slice. Därefter kan man välja slice type – vilken princip som ska användas för uppdelningen.

* **Automatic:** Låt Unity gissa
* **Grid by Cell Size:** välj hur många pixlar stor varje ruta ska vara.
* **Grid by Cell Count:** välj hur många kolumner resp. rader bilden ska delas upp i.

De två senare är oftast väldigt bra för tilesets och spritesheets, framför allt när det gäller pixel art.

Klicka på **Slice** för att göra uppdelningen och skapa rutorna.

## Sprite

Klickar man på en av rutorna så kan man redigera den.

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

Här kan man manuellt justera koordinater och bredd och höjd. Man kan också välja **pivot**.

## Pivot

En sprites pivot är den punkt som den roteras kring, när man snurrar på den eller flippar den. Oftast funkar det bra att bara låta den ligga i mitten (Center), men det kan vara bra att flytta på den. Den bör ligga på karaktärens "mittpunkt" när det gäller spritesheets – eller möjligen karaktärens fötter, beroende på vad man vill uppnå.

## Physics shape\*
