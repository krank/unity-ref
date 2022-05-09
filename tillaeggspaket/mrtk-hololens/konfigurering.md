# Konfigurering\*

Det finns väldigt många inställningar som kan göras i MRTK, och de är ordnade i olika konfigurerings-filer. De filerna hänvisar sedan till varandra: En stor övergripande Configuration Profile innehåller information om till exempel vilken Camera Profile som ska användas.

Normalt sett används standardprofiler som inte kan ändras, så för varje profil som något ska ändras i måste en klon skapas och väljas.

## Configuration Profile

Den övergripande inställningsfilen kallas för en Configuration profile. För att kunna göra några ändringar alls i inställningarna behöver en klon av denna skapas.

Gå till MixedRealityToolkit-objektet. Se till att den profil som ska klonas är vald – t.ex. DefaultHololens2ConfigurationProfile. Klicka på Clone till höger om dropdown-menyn.

![](<../../.gitbook/assets/image (4).png>)

Ge din nya profil ett namn och välj en mapp i dina Assets&#x20;
