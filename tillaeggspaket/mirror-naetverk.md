# Mirror (nätverk)\*

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



* Mirror
* Objekt med NetworkManager & HUD

Spelar-objekt

* Player-objekt: NetworkBehavior, NetworkTransform, NetworkIdentity
* isLocalPlayer
* Registrera player-objekt
* Spawn points

### Objekt som ska instansieras över nätverket

* Spawnable Prefabs
* Nätverkskommando

### NetworkManager

### NetworkManagerHUD

### Network Identity

### Network Transform

### NetworkBehavior

#### OnStartLocalPlayer

#### isLocalPlayer

#### Nätverkskommandon – \[Command]
