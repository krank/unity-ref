# Scener

Varje scen är som ett dokument, som i sin tur innehåller alla objekt som hör ihop. En scen kan vara en skärm ("Game Over", "Settings") eller en level.

Från början finns bara en scen, "SampleScene", som ligger i mappen Scenes. Den kan man byta namn på om man vill.

För att skapa nya scener kan man högerklicka i Assets, välja Create och Scene.

## Scenordning

För att en scen ska komma med när spelet körs så behöver den läggas till i File → Build Settings. Scener som läggs till där kan man växla mellan under spelets gång, antingen via deras namn eller deras nummer. Numret står längst ut till höger i listan; scenen högst upp har nummer 0, nästa scen är nummer 1, och så vidare.

Man lägger till scener i listan genom att dra dem dit från Assets-fönstret eller genom att öppna en scen och klicka på "Add open scenes".

![](<../.gitbook/assets/image (1) (1) (1) (1).png>)

Man kan byta ordning på scenerna genom att klicka och dra.

## SceneManagement

För att man ska kunna byta scen måste man importera SceneManagement-modulen i scriptet. Leta rätt på raden "using UnityEngine;" högst upp i scriptet och lägg till "using UnityEngine.SceneManagement;". Så här:

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;
```

### LoadScene()

Laddar in en scen, definierad av sitt nummer i Build settings eller av sitt namn

```csharp
SceneManager.LoadScene(1);
SceneManager.LoadScene("Level1");
```

### GetActiveScene()

Returnerar den nuvarande scenen, som en instans av klassen Scene. Därifrån kan man läsa av scenens namn och build index, till exempel.

```csharp
Scene currentScene = SceneManager.GetActiveScene();

SceneManager.LoadScene(currentScene.name); // Startar om nuvarande scen
```

## Scene

Klassen Scene kan såklart också användas till variabler som t.ex. kan exponeras i Inspector, och då kan man göra så att de refererar till scener i Assets.

```csharp
[SerializeField]
Scene nextScene;

void OnCollisionEnter2D(Collision2D col)
{
  if (col.gameObject.tag == "finish")
  {
    SceneManager.LoadScene(nextScene.name);
  }
}
```
