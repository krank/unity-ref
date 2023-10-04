# Begrepp

### Projekt

Projektet är själva produkten - alla banor, alla 3d-modeller, alla ljud, alla inställningar, allting.

### Assets

Alla resurser som inte är knutna till en specifik scen. Generellt behöver det mesta som importeras läggas in som en asset först, t.ex. ljudfiler, 3d-modeller, texturer, material. Scener ligger också som assets.

### Scener

En scen kan vara till exempel en bana i spelet, eller en menyskärm. Något som är separat från resten av innehållet. Scener innehåller en eller flera spelobjekt.

### Spelobjekt/GameObject

Alla föremål, textrutor, kameror etc som finns i en scen är game objects, spelobjekt. Varje spelobjekt har minst en komponent, Transformkomponenten, men de flesta innehåller även andra komponenter.

### Komponenter

En komponent ger ett spelobjekt vissa egenskaper - det kan röra sig om utseende, beteende, hur objektet ska låta, hur det ska bete sig rent fysikaliskt (tyngd etc), hur dess hitbox ska se ut etc. Spelobjekt är i princip klumpar av komponenter.

### Collider

En collider-komponent är i princip en hitbox: den delen av objektet som "räknas" när det gäller kollisioner. Ett spelobjekt kan ha flera colliders.

### RigidBody

En rigidbody gör att spelobjektet omfattas av Unitys fysikmotor. Det betyder att objektet kan påverkas av gravitation och olika krafter. För att en kollision mellan två spelobjekt ska kunna hanteras av kod så måste minst ett av objekten i kollisionen ha en RigidBody.

### Taggar

Ett sätt att sätta etikett på spelobjekt. Det gör att flera spelobjekt kan klumpas ihop och underlättar också ifall man t.ex. vill undersöka vilket spelobjekt det är man kolliderat med.

### Prefab

Ett spelobjekt, inklusive transform-komponent och möjligen också andra komponenter, som ligger i Assets. Prefabs är alltså inte en del av någon scen, utan fungerar ofta som "mallar" för nya objekt som skapas i scenen.
