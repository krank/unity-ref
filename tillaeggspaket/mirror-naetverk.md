# Mirror (nätverk)

Mirror är ett bibliotek av komponenter för att bygga multiplayerspel. Det finns gratis via Unitys [Asset Store](../andra-funktioner/asset-store.md).

### Den korta versionen

* Lägg till Mirror i projektet.
* Skapa ett nytt tomt GameObject, döp det till NetworkManager.
  * Lägg till komponenten NetworkManagerHUD.
  * Lägg till Kcp Transport.
* Ge alla spelobjekt som ska synkas över nätverket en NetworkIdentity-komponent. Även de som ska instantieras senare (t.ex. projektiler).
* Ge alla spelobjekt vars position/rotation ska synkas över nätverket en NetworkTransform-komponent.
  * Ställ in så att objekt som ska styras _direkt_ av spelare har Client Authority.
* Gör en prefab av objektet som ska spawnas när en spelare ansluter.
* Förbered för spawning:
  * Lägg till denna prefab i NetworkManager-objektets Player Prefab-variabel.
  * Lägg till de prefabs som ska kunna spawnas över nätverket (projektiler etc) till listan Registered Spawnable Prefabs.
* Gör så att scriptkomponenter som ska köra nätverkskod ärver från NetworkBehavior istället för MonoBehavior
  * Lägg till "using Mirror" högst upp
  * Använd boolen "isLocalPlayer" för att avgöra ifall det nuvarande objektet styrs av den lokala spelaren.
  * Skapa en override för metoden OnStartLocalPlayer för att få ett alternativ till Start() som bara körs för den lokale spelaren
  * Markera metoder som ska köras på servern med \[Command]
  * För objekt som ska spawnas på allas datorer, kör NetworkServer.Spawn().

## NetworkManager

En komponent som samlar in all data som ska synkroniseras över nätverket och använder en Transport-komponent för att skicka/ta emot den. Denna, Kcp Transport och NetworkManagerHUD kan med fördel läggas på samma objekt.

* Ställ in så **Network Transport** blir det objekt som har en Kcp Transport.
* Lägg till den prefab som ska instansieras för varje spelare som registrerar sig och bli den spelarens avatar i **Player Prefab**.
* Lägg till alla prefabs som ska kunna instansieras över nätverket i **Registered Spawnable Prefabs**-listan.

![](<../.gitbook/assets/image (2) (4).png>)

## NetworkManagerHUD

En komponent som ger spelaren ett gränssnitt för att starta en server eller ansluta till en existerande server.

![](<../.gitbook/assets/image (2).png>)

## Kcp Transport

En komponent som används för själva kommunikationen mellan klienter och server. Kan ligga på ett annat objekt än NetworkManager och NetworkManagerHUD.

## Network Identity

En komponent som alla objekt som ska vara unika (ha en egen unik identitet) på nätverket behöver ha. Till exempel alla spelaravatarer, powerups och projektiler

## Network Transform

En komponent som signalerar till NetworkManagern att objektets Transform ska synkroniseras över nätverket – position, rotation och storlek. Bör ges till spelar-avataren, projektiler och annat som flyttar på sig.

## NetworkBehavior

NetworkBehavior är en klass som ingår i Mirror-biblioteket och som i sin tur ärver från MonoBehavior. När man har scriptkomponenter som ska nyttja sig av nätverkskommandon och liknande så behöver deras klasser ärva från NetworkBehavior istället för från MonoBehavior.

```csharp
using UnityEngine;
using Mirror;

public class PlayerController : NetworkBehaviour
{
  // Kod
}
```

### IsLocalPlayer

En bool-variabel som är true ifall objektet tillhör och är styrt av den lokala spelaren.

```csharp
void Update()
{
  if (!IsLocalPlayer)
  {
    return;
  }
  
  // Kod som bara ska köras för den lokala spelaren
}
```

### OnStartLocalPlayer

En variant av Start() som bara körs för den lokala spelaren

```csharp
public override void OnStartLocalPlayer()
{
  // Färgar den lokala spelaren grön
  GetComponent<Renderer>().material.color = Color.green;
}
```

### Nätverkskommandon \[Command]

Metoder som markeras med \[Command] kommer att köras på servern istället för på klienten.

```csharp
[Command]
void CmdFire()
{
  GameObject bullet = Instantiate(bulletPrefab, bulletSpawnPoint.position, bulletSpawnPoint.rotation);
  NetworkServer.Spawn(bullet);
}
```

### NetworkServer.Spawn()

Ett kommando som tar emot ett GameObject, och ser till att instanser av denna skapas och synkroniseras över hela nätverket. Används ofta för att till exempel se till så att projektiler och powerups skapas likadant för alla spelare.

Observera att objektet som ska spawnas måste vara en instans av en prefab som lagts till som Registered Spawnable Prefab i scenens NetworkManager.

```csharp
GameObject bullet = Instantiate(bulletPrefab, bulletSpawnPoint.position, bulletSpawnPoint.rotation);
NetworkServer.Spawn(bullet);
```
