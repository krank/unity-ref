# Input

## Tangentbordet (och handkontroller)

### Input.GetAxisRaw()

En metod som hämtar det nuvarande värdet hos en [axel](../../grundlaeggande-koncept/knappar-och-axlar.md). Returnerar resultatet som en float.

```csharp
float moveX = Input.GetAxisRaw("Horizontal");
```

## Musen

### Input.mousePosition

En [Vector3](../datatyper-och-synlighet.md#vector3) som innehåller musens nuvarande position i "screen space", alltså uttryckt i pixlar utifrån origo uppe i vänstra hörnet.

### Camera.main.ScreenToWorldPoint()

En metod som förvandlar en vektor som mäter position i "screen space" till en vektor som mäter position utifrån Unityenheter och unitys grid.

```csharp
Vector3 mousePosOnScreen = Input.mousePosition;
Vector3 mousePosInWorld = Camera.main.ScreenToWorldPoint(mousePosOnScreen);
```

### OnMouseUp()

En händelsemetod som man kan lägga till sitt projekt, lite som OnEnterCollision eller [Start eller Update](../../grundlaeggande-koncept/monobehavior.md#haendelse-metoder). Den anropas ifall användaren klickar på objektet. Det kräver att objektet har en collider.

```csharp
private void OnMouseUp()
{
    print("hey");
}
```
