# Installation & setup

* **Ladda ner och installera** [**Unity Hub**](https://unity3d.com/get-unity/download)**.**
  * **Starta Unity Hub** och följ instruktionerna – skapa ett Unity-konto om du inte redan har ett, skaffa en Unity-licens (välj gratislicensen).
  * När Unity Hub startar så får du frågan **om du vill installera Unity**. Du kan **tacka nej** till det, för den installationen inkluderar onödiga moduler som bara tar upp hårddiskutrymme.
  * Via Unity Hub, **installera manuellt en version av Unity (minst 2022)**. Du kan **klicka ur alla valbara extragrejer**, framför allt Visual Studio.
    * Om Visual Studio redan är installerat på datorn kan du inte kryssa ur det. Det är OK, du kan manuellt avinstallera Visual Studio senare.
  * Unity Hub och Unity tar tillsammans upp c:a **5.5 gb**
  * **MacOS:** Scrolla ner till "Download the Unity Hub" och välj "Download for Mac"
  * **MacOS:** Om du har [Brew ](https://brew.sh/)kan du installera via:`brew install --cask unity-hub`
  * **Windows:** Kan installeras via winget: `winget install Unity.UnityHub`
* **Ladda ner och installera** [**Visual Studio Code**](https://code.visualstudio.com/)**.**
  * I Code, installera följande extensions:
    * [C#](https://www.google.com/url?q=https%3A%2F%2Fmarketplace.visualstudio.com%2Fitems%3FitemName%3Dms-vscode.csharp\&sa=D\&sntz=1\&usg=AFQjCNGOzgSFj14Pbd9ut66JAvh0loJsEw) – Ger Visual Studio Code stöd för C#
    * [C# Dev Kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit) – Ger utökat stöd för C#
    * [Unity](https://marketplace.visualstudio.com/items?itemName=VisualStudioToolsForUnity.vstuc) – Officiell extension från Microsoft som får Unity och Code att funka ihop
    * [Unity Code Snippets](https://marketplace.visualstudio.com/items?itemName=kleber-swf.unity-code-snippets) – lägger till en del smarta kodkompletteringar för Unity.
    * [gitignore](https://www.google.com/url?q=https%3A%2F%2Fmarketplace.visualstudio.com%2Fitems%3FitemName%3Dcodezombiech.gitignore\&sa=D\&sntz=1\&usg=AFQjCNHu8aUEHuuoWIdAZQcCdvDqnSWhSQ) – Underlättar arbetet med git och Visual Studio Code. Om du söker efter den, se till att ta den av CodeZombie!
  * **Windows:** Kan installeras via winget: `winget install Microsoft.VisualStudioCode`
  * **MacOS:** Om du har [Brew ](https://brew.sh/)kan du installera via:`brew install --cask vscode`
  * Visual Studio Code inkl. extensions tar upp c:a **1gb**
* **Ladda ner och installera** [**Dotnet 8 SDK**](https://dotnet.microsoft.com/en-us/download) **eller nyare**
  * Behövs av för att C# Dev Kit ska kunna bidra med automatkomplettering av kod.
  * **Windows:** Kan installeras via winget: `winget install Microsoft.DotNet.SDK.8`
  * **MacOS:** Om du har [Brew ](https://brew.sh/)kan du installera via:`brew install --cask dotnet-sdk`
  * Tar upp c:a **1.2 gb**
* **Ladda ner och installera** [**Git**](https://git-scm.com/downloads)
  * Används för versionshantering och att dela med sig av kod/projekt (t.ex. för inlämningar)
  * Windows: Kan installeras via winget: `winget install git.git`
  * **MacOS:** Om du har [Brew ](https://brew.sh/)kan du installera via:`brew install --cask git`
  * **MacOS:** Om du inte har Brew och bara testar att köra `git` i terminalen så kommer Apples grundläggande utvecklingsverktyg att installeras – inklusive git.

Att installera allt ovanstående på en helt nyinstallerad dator kräver totalt c:a **8 gb** ledigt utrymme.

## Nytt projekt

* Välj själv den template (2D, 3D etc) som bäst matchar spelet du tänker bygga.
* Gå till **Window → Package Manager** och se till så att paketet **Visual Studio Editor** är uppdaterat (minst version 2.0.20).
  * Du kan behöva **avinstallera** metapaketet **Engineering** och sedan manuellt installera Visual Studio Editor.
* När projektet skapats, gå till **Edit →** **Preferences** och **External Tools**. Välj **Visual Studio Code** som **External Script Editor.**

## Unity och Git

Ett enkelt sätt att använda Git med Unity är Visual Studio Codes inbyggda Git-gränssnitt.

* Högerklicka i Assets och välj **"Open C# project"**.
* Följ instruktionerna för att skapa ett Git-repository [här](https://krank23.gitbook.io/csharp-ref/lathund-skapa-projekt), men lägg till en **gitignore** för **Unity** istället för Visual Studio.
