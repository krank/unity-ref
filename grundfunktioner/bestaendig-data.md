# Beständig data

## Spara data mellan scener

### Static

Ett väldigt enkelt sätt att spara data så att den inte förstörs vid scenbyte är att lagra datan i en [statisk](http://127.0.0.1:5000/s/-MHmNgpRz-b16wpwGwZI-887967055/klasser-och-objektorientering/static) variabel.

```csharp
public class AvatarController : MonoBehaviour
{
  public static int score = 100;
}
```

Eftersom statiska variabler inte är knutna till någon specifik instans av klassen så finns de kvar även när alla instanser som finns i scenen förstörts. Därför kan de användas för att lagra data som ska föras över från en scen till en annan.

### DontDestroyOnLoad()

Objektet som anges som parameter kommer inte att förstöras när en ny scen laddas, utan ligga kvar i minnet. Det betyder att alla objektets variabler också behåller sina värden. Objektet kan sedan hittas i den nya scenen genom t.ex. [Find](hitta-spelobjekt.md#find), och dess värden läsas av.

```csharp
public class ScoreHandler : MonoBehaviour
{
  public int score = 0;

  void Start()
  {
    DontDestroyOnLoad(this.gameObject);
  }
}
```

## Spara data mellan körningar av spelet

### PlayerPrefs

Kan användas för att spara strings, ints och floats för spelet.

#### Save()

Sparar alla värden till hårddisk.

#### HasKey()

Tar emot en string som parameter, returnerar true ifall det finns ett värde med det namnet.

```csharp
if (PlayerPrefs.HasKey("score"))
{
  score = PlayerPrefs.GetInt("score");
}
```

#### DeleteKey()

Tar emot en string som parameter, tar bort värdet med det namnet (om det finns).

#### DeleteAll()

Tar bort alla värden.

#### GetInt(), SetInt()

Läser av respektive ändrar på ett int-värde med det namn som anges som parameter.

```csharp
PlayerPrefs.SetInt("Score", 300);

score = PlayerPrefs.GetInt("score");
```

#### GetFloat, SetFloat

Läser av respektive ändrar på ett int-värde med det namn som anges som parameter.

```csharp
PlayerPrefs.SetFloat("modifier", 3.4f);

modifier = PlayerPrefs.GetFloat("modifier");
```

#### GetString, SetString

Läser av respektive ändrar på ett string-värde med det namn som anges som parameter.

```
PlayerPrefs.SetString("name", "Mira");

name = PlayerPrefs.GetString("name");
```

### WriteAllText, WriteAllLines

[Samma metoder som används i vanliga C#](http://127.0.0.1:5000/s/-MHmNgpRz-b16wpwGwZI-887967055/filhantering/laesa-och-skriva) för att läsa och skriva data fungerar precis likadant i Unity. Däremot bör man använda **Application.persistentDataPath** som första del av alla filnamn för att se till så filerna sparas i rätt mapp (spelets data-mapp).

```csharp
string name = "Mira";
string filename = Application.persistentDataPath + "/name.txt";

File.WriteAllText(filename, name);
```

I Windows är Application.persistentDataPath lika med:

```
%userprofile%\AppData\LocalLow<companyname><productname>
```

Där %userprofile% är din användares mapp (t.ex. C:\Users\Krank) och \<companyname> och \<productname> är de som angetts under Player Settings (Edit → Project Settings → Player).

### JsonUtility

Även om senare versioner av Dotnet har [inbyggda bibliotek](http://127.0.0.1:5000/s/-MHmNgpRz-b16wpwGwZI-887967055/filhantering/serialisering-.../json-serialisering) för att serialisera och deserialisera [JSON ](http://127.0.0.1:5000/s/-MHmNgpRz-b16wpwGwZI-887967055/filhantering/filformat/json)så saknas dessa i den version av Dotnet som ingår i Unity. Istället har Unity **JsonUtility**.

För att förbereda en klass för serialisering med JsonUtility, markera den som \[System.Serializable].

{% code title="GameData.cs" lineNumbers="true" %}
```csharp
[System.Serializable]
public class GameData
{
  public int score;
  public string name;
}
```
{% endcode %}

Sedan kan instanser av klassen serialiseras / deserialiseras.

{% code title="ScoreHandler.cs" lineNumbers="true" %}
```csharp
public class ScoreHandler : MonoBehaviour
{
  public GameData data = new GameData();

  public void SaveData()
  {
    string jsonString = JsonUtility.ToJson(data);
    string filename = Application.persistentDataPath + "/data.txt";
    File.WriteAllText(filename, jsonString);
  }

  public void LoadData()
  {
    string filename = Application.persistentDataPath + "/data.txt";
    string jsonString = File.ReadAllText(filename);
    data = JsonUtility.FromJson<GameData>(jsonString);
  }
}
```
{% endcode %}

#### JsonUtility.ToJson()

Tar emot ett objekt som parameter, returnerar JSON-kod. Lägger man med både ett objekt och ett boolskt värde så avgör det boolska värdet huruvida JSON-koden är snyggt formaterad med indrag etc.

```csharp
string jsonString = JsonUtility.ToJson(data);
string jsonStringPretty = JsonUtility.ToJson(data, true);
```

#### JsonUtility.FromJson<>()

Tar emot en klass mellan <> och en string som parameter. Returnerar en instans av klassen, baserad på den deserialiserade JSON-koden i stringen.

```csharp
data = JsonUtility.FromJson<GameData>(jsonString);
```
