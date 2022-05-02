# Installation & setup

* Ladda ner och installera [Unity Hub](https://unity3d.com/get-unity/download).
  * Följ instruktionerna – skapa ett Unity-konto om du inte redan har ett, skaffa en Unity-licens (välj gratislicensen)
  * Via Unity Hub, installera en version av Unity. 2020-versionerna är de mest stabila. Du kan klicka ur alla valbara extragrejer, du behöver generellt bara grund-Unity.
* Ladda ner och installera [.NET Framework SDK 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net471-developer-pack-offline-installer). Det behövs för att kodkompletteringen i Visual Studio Code ska fungera.
  * Om du fortfarande inte får kodkomplettering: Testa att avinstallera eller uppdatera Visual Studio om du har det installerat.

## Nytt projekt

* Välj själv den template (2D, 3D etc) som bäst matchar spelet du tänker bygga.
* När projektet skapats, gå till **Edit**, **Preferences** och **External Tools**. Välj **Visual Studio Code** som **External Script Editor**.
  * Se till så att _åtminstone_ följande är ikryssade under "Generate .csproj files for":
    * Embedded packages
    * Local packages
    * Built-in packages
  * Klicka på "Regenerate project files".
* (Gå till File → Build Settings och ändra Architecture till x86\_64.)

## Unity och Git
