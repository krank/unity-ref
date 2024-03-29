# Ett Unityprojekts uppbyggnad

Ett unityprojekt innehåller ett antal **assets**.

Assets kan till exempel vara **scener**, texturer, 3d-modeller, sprites och C#-scripts.

Varje Scene är en separat del av projektet, som innehåller ett eget 3d-space.

I varje scene finns ett antal **GameObjects**, som kan vara nästan vad som helst – kameror, lampor, spelkaraktärer, fiender, powerups och så vidare.

Varje GameObject består av ett antal **Components**.

Varje Component är ett script som ger viss funktionalitet till det GameObject det sitter ihop med. Alla GameObjects har t.ex. en Transform-Component som ger objektet dess position, rotation och skalning.

I en Component kan det sedan finnas **variabler**. Transform-komponenten her till exempel [Vector3](../grundfunktioner/datatyper-och-synlighet.md#vector3)-variabler för position, rotation och skalning av objektet.
