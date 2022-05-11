# Konfigurering

Det finns väldigt många inställningar som kan göras i MRTK, och de är ordnade i olika konfigurerings-filer. De filerna hänvisar sedan till varandra: En stor övergripande Configuration Profile innehåller information om till exempel vilken Camera Profile som ska användas.

Normalt sett används standardprofiler som inte kan ändras, så för varje profil som något ska ändras i måste en klon skapas och väljas.

## Configuration Profile

Den övergripande inställningsfilen kallas för en Configuration profile. För att kunna göra några ändringar alls i inställningarna behöver en klon av denna skapas.

**Rekommendation:** skapa en mapp i Assets specifikt för att samla alla inställningsprofiler för MRTK.

Gå till **MixedRealityToolkit**-objektet. Se till att den profil som ska klonas är vald – t.ex. **DefaultHololens2ConfigurationProfile**. Klicka på **Clone** till höger om dropdown-menyn.

![](<../../.gitbook/assets/image (4).png>)

Ge din nya profil ett namn och välj en mapp i dina Assets där du vill lägga den.

Att välja den nya Configuration profile i MixedRealityToolkit-objektet ger nu tillgång till övergripande inställningar för till exempel kameran, input-systemet, Diagnostics och [Spatial Awareness](spatial-awareness.md).

### Mer specifika inställningar och profiler

För mer specifika inställningar behövs sedan ytterligare, mer specifika profiler skapas. För att göra egna inställningar för Spatial Awareness måste en Spatial Awareness System Profile skapas. Det görs på samma sätt – välj en profil att utgå från, tryck Clone och välj var den nya profilen ska läggas.

