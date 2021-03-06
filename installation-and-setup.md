# Installation & setup

* **Ladda ner och installera** [**Unity Hub**](https://unity3d.com/get-unity/download)**.**
  * Följ instruktionerna – skapa ett Unity-konto om du inte redan har ett, skaffa en Unity-licens (välj gratislicensen)
  * Via Unity Hub, **installera en version av Unity**. 2020-versionerna är de mest stabila. Du kan **klicka ur alla valbara extragrejer**, framför allt Visual Studio.
* **Ladda ner och installera** [**Visual Studio Code**](https://code.visualstudio.com/)**.** I Code, installera följande extensions:
  * [C#](https://www.google.com/url?q=https%3A%2F%2Fmarketplace.visualstudio.com%2Fitems%3FitemName%3Dms-vscode.csharp\&sa=D\&sntz=1\&usg=AFQjCNGOzgSFj14Pbd9ut66JAvh0loJsEw) – Ger Visual Studio Code stöd för C# bl.a via programmet "OmniSharp".
  * [C# Toolbox of Productivity](https://marketplace.visualstudio.com/items?itemName=RichardZampieriprog.csharp-snippet-productivity) – Lägger till en del extra användbara genvägar och funktioner, t.ex. för att skapa nya projekt och klasser.
  * [Unity Code Snippets](https://marketplace.visualstudio.com/items?itemName=kleber-swf.unity-code-snippets) – lägger till en del smarta kodkompletteringar för Unity.
  * [gitignore](https://www.google.com/url?q=https%3A%2F%2Fmarketplace.visualstudio.com%2Fitems%3FitemName%3Dcodezombiech.gitignore\&sa=D\&sntz=1\&usg=AFQjCNHu8aUEHuuoWIdAZQcCdvDqnSWhSQ) – Underlättar arbetet med git och Visual Studio Code. Om du söker efter den, se till att ta den av CodeZombie!
* **Ladda ner och installera** [**.NET Framework SDK 4.7.1**](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net471-developer-pack-offline-installer)**.**&#x20;
  * Behövs av OmniSharp.
* **Ladda ner och installera** [**Dotnet 6 SDK**](https://dotnet.microsoft.com/en-us/download)
  * Behövs av OmniSharp.

## Nytt projekt

* Välj själv den template (2D, 3D etc) som bäst matchar spelet du tänker bygga.
* När projektet skapats, gå till **Edit →** **Preferences** och **External Tools**. Välj **Visual Studio Code** som **External Script Editor**.
  * Se till så att _åtminstone_ följande är ikryssade under "Generate .csproj files for":
    * Embedded packages
    * Local packages
    * Built-in packages
  * Klicka på **"Regenerate project files"**.

### Problem med autokomplettering/Omnisharp?

* **Tryck F1 och välj "Restart Omnisharp".**
* **Om du har Visual Studio installerat** – kör Visual Studio Installer och uppdatera eller avinstallera programmet.
* Ladda ner och installera [**.NET Framework SDK 4.7.1**](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net471-developer-pack-offline-installer) om det inte redan är gjort.
* **Stäng av "Use modern .NET" i VS Code**
  * Ladda ner och installera [**Build Tools**](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022).
  * Högerklicka i Assets och välj **"Open C# project"** för att öppna Visual Studio Code.
    * Det bör nu finnas en **"settings.json"** i mappen **".vscode"**. Öppna den och lägg till:\
      `"omnisharp.useModernNet": false,`\
      på raden ovanför\
      `"files.exclude": {`
  * Starta om VS Code eller åtminstone Omnisharp

## Unity och Git

Ett enkelt sätt att använda Git med Unity är Visual Studio Codes inbyggda Git-klient.

* Högerklicka i Assets och välj **"Open C# project"**.
* Följ instruktionerna för att skapa ett Git-repository [här](https://krank23.gitbook.io/csharp-ref/lathund-skapa-projekt), men lägg till en **gitignore** för **Unity** istället för Visual Studio.
