# Kompilera och distribuera\*

Unityprojekt kan normalt bara öppnas och köras i Unity. Om de ska kunna spelas utan unity behöver de kompileras till körbara filer för önskad plattform. I normala fall, när Unity körs på en Windowsdator, kommer de körbara filerna i första hand att vara vanliga exe-filer som kan köras i 64-bitars windows.

## Kompilera

Gå till **File → Build Settings**.

Lägg till önskade scener till listan – antingen genom knappen **"Add Open Scenes"** eller genom att dra in dem från Assets.

Klicka på **Build**.

**Bläddra till eller skapa en mapp** som resultatet ska läggas i. Välj en mapp som inte används till något annat.

**Dubbelklicka på exe-filen** som skapas i mappen för att köra den kompilerade versionen av spelet.

**Alla filer i mappen behövs för att köra spelet**, så för att distribuera det så behöver du packa ihop och skicka hela mappens innehåll. Det enklaste sättet att göra det är antagligen att **komprimera mappen till en zip-fil**.

## Andra plattformar

Unity har normalt bara stöd för att exportera spelprojekt till Windows-format, det vill säga vanliga klassiska EXE-filer som kan köras i 64-bitars Windowssystem.

Det går att installera moduler för att exportera projekt till andra operativsystem eler ramverk – till exempel Android eller UWP (Universal Windows Platform).

* Öppna **Unity Hub**.
* Gå till **Installs**.
* Klicka på **kugghjulet** bredvid den Unityversion som ska ges nya exportmoduler.
* Klicka på **Add modules**.

Kryssa i de moduler du vill ha och sedan Install. Se till att kryssa ur Visual Studio 2019 om du inte absolut vill ha det programmet, och Documentation om du inte kommer att vilja komma åt Unitys egna dokumentation inuti programmet.

## Android

Installera modulerna **"Android Build Support"**, **"Android SDK & NDK Tools"** och **"OpenJDK"**.

I Unityprojekt som ska exporteras till Android, gå till F**ile → Build Settings**, markera **Android** och klicka **Switch platform**.

Koppla in en Android-enhet som har USB Debugging aktiverat, och klicka **Refresh** för att få enheten att dyka upp i listan. Använd Build and run för att build:a&#x20;

När man build:ar till Android får man en **APK-fil**, som sedan förs över till Androidenheten och installeras. APK är ett universellt format för Android-appar och kan användas för att installera appar på alla Androidenheter som tillåter installation från "okända källor".

## UWP

(Kommer…)
